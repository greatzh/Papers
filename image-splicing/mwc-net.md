# MWC-Net

![Cover](https://s2.loli.net/2023/05/13/xjRhUnIBiTKyuOg.png)

> Bi, X., Zhang, Z., Liu, Y., Xiao, B., & Li, W. (2021). Multi-task wavelet corrected network for image splicing forgery detection and localization. 2021 IEEE International Conference on Multimedia and Expo (ICME), 1–6.

## 导读

论文也是说现阶段的方法大都含有pooling，而池化（最大/平均池化）又会影响到学习到的特征不够全面，不具有代表性。所以作者提出了利用**多任务小波校正网络**来解决这个问题，它利用小波池化和小波反池化来压缩和重构伪造图像的特征以减少特征学习过程的信息损失。同时，作者还应用多任务来提高网络学习能力去利用更多更全面更具有代表性的特征。

## 引言

小波池化和传统池化的不同在于，传统池化只是通过在每个池化窗口选取最大值或者平均值，而小波池化则是使用小波变换将信号分解为多个频带，然后对每个频带进行池化操作。所以看起来是一个在RGB上池化，一个在频率信息上操作。

然后都是说传统方法robustness不行，我随便做一下后处理可能就没用了。而在深度学习的方法里面，一开始是把它当作一个检测问题，提出了一些patch-based的检测网络，然后也把这个问题当作图像分割的问题，所以也提到无论是用U-Net还是其他异常检测的网络，都会有要池化这个问题，最大池化或者平均池化，而池化作者认为，会造成一些不可逆转的信息的丢失。然后作者提出由于单任务也会让网络学习到的一些特征更不具有代表性，局限性更高。

基于能够学习来自拼接伪造图像的全面和代表性的特征，且不会丢失信息，并解码已学习的特征以像素级别定位篡改区域这个目标，作者使用**小波池化和反池化以及多任务**来实现这个目标。

## 主要贡献

1. 利用小波池化和反池化，避免了信息的损失，网络可以学习到更多具代表性的特征用来进行篡改检测。
2. 研究了多任务策略对学习到更多更全面更具代表性的特征的效果。
3. 根据前面这两点提出了一个网络MWC-Net，Multi-task Wavelet Corrected Network.

## 方法

作者在这里先介绍了小波池化和反池化的操作，他们一般有4个kernel，LL（Low Pass Filter，低通滤波器，捕获光滑的表面和纹理信息），LH，HL，HH，（High-Pass Filter，提取在图片上边缘部分的水平的，垂直的，对角线的信息）。

![Architecture](https://s2.loli.net/2023/05/13/FTv8zkEOLNMXGpY.png)

如图所示，一个编码器，三个解码器，多任务，分别对应篡改区域的解码器（主要学习篡改图片里面的表面喝纹理的特征区别，所以只用低通滤波LL），篡改边缘的解码器，以及一个拼接篡改的重构的图像。同时，由于拼接篡改可以视为一个全局的二分类问题（伪造/真实），所以作者在编码和解码之中，加入一个全局块，[Global Block](https://github.com/nothinglo/Deep-Photo-Enhancer)，用来学习全局特征。但是这些表面和纹理的特征差异又会因为后处理导致不明显，所以作者这边多任务的第二个任务就是对边缘进行解码，因此高通滤波的输出LH，HL，HH通过跳过连接到解码器，得到边缘特征。同时，根据作者在技术贡献里面提到的确保编码器能够学习到全面的，具有代表性的特征，多任务的第三个任务就是重构输入图像，编码器学习到的信息越多，重构的篡改图像质量就越好，这边就包含4个kernel的信息。同时，这三个任务，都有自己的损失函数，来优化最后的结果，帮助解码器得到更全面，更具代表性的篡改特征。

## 实现

作者在CASIA v2.0, Columbia, NIST206, FantasticReality上进行了实验，具体的数据信息如下图所示，评价指标只用了precison, recall, 和F。

![Dataset info](https://s2.loli.net/2023/05/15/b2svefGACPu5MDp.png)

网络的三个损失函数通过相加的方法来共同训练，对每个损失函数使用不同的权重，篡改区域的权重是1，边缘是0.2，重构篡改图是0.1，使用Adam进行优化。

### Ablation

这里的对照实验，主要就是讨论了用小波池化/小波反池化，还是最大池化/上采样，用多任务，还是单任务，就这两点。

![Ablation result](https://s2.loli.net/2023/05/15/xq2B4WMi6YEstem.png)

### Result

如图所示，前面两个ADQ和ELA是传统方法，后面两个是深度学习的方法，作者提到传统方法的召回率都比较高的原因是，它们可以将整个图片都作为篡改区域进行检测，因此可以更好的识别到正例，但是precision就不行。

![Result](https://s2.loli.net/2023/05/15/hGVjzMdSs41l8qL.png)

关于鲁棒性的问题，做了噪声攻击，JPEG压缩，Resize三个后处理，大概就是可以看到随着后处理强度的增加，结果都变差了。

![Robustness Result](https://s2.loli.net/2023/05/15/enwZKyhCqlT8D3p.png)

## 总结

我觉得未来的方向可以是优化这个网络的效率，目前好像有点儿臃肿。而且做Evaluation好像只计算TP，FP，TN之类的，没有算IoU之类的，是不是不太完整。
