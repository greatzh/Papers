# ET

![COVER](https://s2.loli.net/2023/05/13/fugdWHisk1FJLnM.png)

> Sun, Y., Ni, R., & Zhao, Y. (2022). ET: Edge-Enhanced Transformer for Image Splicing Detection. In IEEE Signal Processing Letters (Vol. 29, pp. 1232–1236). IEEE. https://doi.org/10.1109/LSP.2022.3172617

## 导读

这篇论文发表在SPL，只有5页，作者从目前仍然存在一些误报false alarm，检测的完整性被忽视这些问题，认为原因是没有充分利用拼接的边界，（GT mask的边缘像素）才导致了较普通的准确率，所以作者提出使用Edge-enhanced Transformer（ET），一个双分支的边缘感知Transformer配以一个特征增强模块来进行篡改定位。

## 介绍

图像拼接篡改是指将一个图像中的某个区域复制并粘贴到另一张图片中，其目的通常是突出或者掩盖一些物体。一些已经提出的方法可以分为传统方法和基于深度学习的方法；传统方法依靠具体的统计特征来区分真实区域和篡改区域，包括像Color Filter Array 颜色滤波阵列CFA，噪声模式以及JPEG相关的痕迹，但传统方法的缺点是这些手工制作的特征对于后处理鲁棒性不高，并且很难生成有区分性的特征；而深度学习的方法，最早使用图片的EXIF原数据进行模型的训练，然后把定位问题当成图像分割任务，用一些分割网络来进行定位。

那之前也有一些方法提出过使用Edge，作者说他们使用卷积网络来优化参数，在池化的时候，会丢失很多信息，导致不准确的边缘信息被计算，以及在反向传播里面出现的梯度下降问题等。

## 技术贡献

1. 双分支的边缘感知（识别边缘的）的边缘增强Transformer网络结构，将拼接边缘信息引入到不包含池化的基于图像分割的篡改定位网络。
2. 一个自注意力模块用来对边缘特征进行增强，生成有效的，高准确的，低误报的特征。
3. 作者说自己是第一个从像素和边缘层次去评估定位准确率的。

## 方法介绍

边缘特征起作用的原因可能是在对拼接篡改进行后处理的时候，通常会处理边缘，以一些羽化或者颜色调整来让拼接的部分更自然。而不采用CNN是因为感受野小，而ViT的出现解决了CNN的问题，所以作者就用ViT。具体的框架如下图所示，Transformer被设计成编码器用来做特征提取（直接就是预训练的ViT），一个分支直接将编码器的最后一层的输出作为篡改特征$F_{for}$, 另外一个分支则是结合了编码器浅层到深层（总共有12层，同时采用和[SETR, CVPR '21](https://arxiv.org/abs/2012.15840)一样的方法，在生成边缘特征的模块中，3，6，9，12层会经过一个reshape操作）的特征来生成边缘特征$F_{edge}$，然后两个分支的一个边缘特征，一个篡改特征经过特征强化模块，得到最后的强化特征$F_{enh}$，强化特征经过对应的解码器得到最后的篡改掩码。边缘的和篡改的两个解码器是一样的结构，只是共享权重。

![Framework](https://s2.loli.net/2023/05/13/zelgwOHhZYVtUCB.png)

特征增强的模块如上图的右边所示，普遍的融合两种不同类型特征的方法都是在对应的channel维度上进行相加concatenate，但作者说这样效果不好，于是为了突出边缘特征的重要性，作者在相加concatenate之前，先增强了篡改特征在空间域的边缘位置，做法就是先把边缘特征的信息跟篡改特征的信息结合，再把结合了边缘信息后的篡改特征和边缘特征做相加。如图所示，篡改特征和边缘特征先进性族元素乘积（点积），将得到的特征重塑，得到三个卷积张量$S_1, S_2,S_3$，然后再取两个卷积张量，一个经过transpose后进行矩阵乘法，通过softmax得到注意力矩阵，再reshape到和篡改特征一样的维度，最后通过和边缘特征进行连接得到增强特征。
$$
F_{enh}=[F_{for}\oplus[A\otimes S_{1}]_{reshape}; F_{edge}] \\
A=softmax(S_3\otimes S^T_2)
$$
损失函数上，就是一个篡改损失，和边缘损失，都是采用二元交叉熵函数定义。

## 实验

### 数据集

CASIA v1.0（921张压缩的图片，384x256）, CASIA v2.0（5123张图片，图片大小从240×600 到 800×600），在CASIA的两个版本数据集里面都是包括拼接篡改和复制移动篡改两个伪造图片，以及 NC2016（561张图片，平均的解析度在3561×2516，主要的篡改类型有splicing，copy-move，和removal）三个数据集用来评估。

### 训练

对每个数据集，都采用8：1：1的比例来做训练，验证和测试；采用的ViT模型是，ViT-Base，在ImageNet-21K上预训练的模型。

### 评估

就$F_1$和IoU，但是作者从像素层次和边缘层次都进行了两个度量的计算，但是在边缘层次的$F_1$和IoU计算上，作者觉得边缘定位有难度，在边缘级的F1计算上，TP，FP，FN是只由边缘上的像素来计算的，而为了让难度下降，所以作者设置了一个容错参数，N，表示在以边缘标签为中心N×N 区域内存在预测的边缘像素。（说白了看就是，纯用边缘上的像素计算得到的结果不好。）

### 消融研究

Ablation是只在CASIA V2.0上实验，ablate了只用篡改特征；使用篡改特征和边缘特征，但是两种特征结合只是不同的连接；以及使用两种特征同时用增强模块进行连接。

![ablation result](https://s2.loli.net/2023/05/13/eMgpbTYXjB4GA1U.png)

总觉得还有什么不够，根据它的技术贡献，这个评估呢，起到了什么作用，可有可无吗，说用Transformer结果搞双分支，那个base的确认，但5页，spl大概都足够了。

### 结果

![Result](https://s2.loli.net/2023/05/13/olAcEbKrsFZOMQu.png)

可以看到，结果都是比较的网络里面最好的，CFA和NOI是传统方法，Mantra-Net是直接报告了论文里面它自己写的结果，因为Mantra-Net说是在自己的未公开数据集上训练的。

最后也报告了在CASIA v2.0上鲁棒性研究的结果，不过没有比较，和没有经过后处理的结果相差还算不大。

## 总结

其实作者提出的这些问题是比较空泛的，包括像用CNN去处理边缘信息，说会有梯度下降，丢失信息等等，以及一开始说深度学习的方法会有一些误报和准确率不高，当然，很正常。

结果好就是王道，论文的亮点就是把边缘特征和篡改特征放进了ViT的结构里面，可以得到区别性强的特征。所以其实可以再研究的，边缘特征再来一个multi-scale，篡改特征再分RGB和frequency，或者noise，这边反正是不同的图片的拼接篡改，就，套娃！

再有，随着现在这种篡改检测的方法都要提出一个大一统了，其实单纯对splicing检测好像，很难找到亮点。