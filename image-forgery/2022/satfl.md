# SATFL

> L. Zhuo, S. Tan, B. Li and J. Huang, "Self-Adversarial Training Incorporating Forgery Attention for Image Forgery Localization," in IEEE Transactions on Information Forensics and Security, vol. 17, pp. 819-834, 2022, doi: 10.1109/TIFS.2022.3152362.

*Self-Adverserial Training incorporating Forgery Attention for Image Forgery Localization*

![satfl](https://s2.loli.net/2022/03/08/k485TqYBhX2dG9l.gif)

![mind_satfl](https://s2.loli.net/2022/03/12/nGclHarTfR1oiXQ.png)

### Overview

论文提出了使用由粗到细的网络结构以及自对抗的训练策略，利用基于CW-HPF(Channel Wise High Pass Filter block, 来自WISERNet，用于图像隐写分析，数字化图像隐藏秘密信息的分析)的自注意力机制，叫做**Forgery Attention**来获取丰富的上下文信息，以及篡改区域的不一致？？，进而定位篡改的区域。而CW-HPF是利用了不同通道之间的特征的联系，以及从（高通过神经元？？）得到的噪声特征之间的联系来实现的。（所以模型并不是向其他模型一样直接用CNN提取特征，而是先通过了一个channel wise high pass filter, 通道级别的高位通过过滤）

而文章要解决的问题主要是篡改检测方向上数据集的不足，导致结果鲁棒性不好，利用文章提出的方法，包括向自我对抗以及coarse2fine的训练策略，以及自注意力机制的加持，来达到比较好的效果。

### Details

#### COS2FINE

**Coarse net**

一张篡改过的图片$H \times W \times 3$先输入到**CW-HPF**里面，然后是**VGG**，然后接着是**Dilated Conv**, 再经过VGG得到最后的粗糙的预测结果，prediction mask $H \times W$,以及一个特征图，feature map $H \times W \times k$, $k$的意思是16，因为最后一个卷积输出的block有16个通道。

**CW-HPF**

通道级别（逐通道）的**高通滤波**，高通滤波是一种过滤方式，规则为高频信号能通过，而低于设定临界值的低频信号则被阻隔/减弱。但是阻隔/减弱的幅度会依据不同的频率以及不同的滤波程序（目地）而改变。首先是因为篡改基本上都集中在中高频率的信号上，然后很多工作却忽视了在通道之间的联系，使用了一些不必要的噪声特征，为了更准备的获取噪声特征，加入inter-channel，<u>加强了在真实图片和篡改图片上噪声的不一致性。？？</u>基本上就是来源于**WISERNet**。WISERNet的缺点在于他用的CW-HPF是用了固定的权重，然后就是三个RGB的颜色通道作为预处理层的最后一步。而改善后的CW-HPF通道，权重，可用的通道，放在框架中的位置都更随意。利用多通道之間的聯繫，它能提取到更多更準確的噪聲，这样做一边放大了真实和篡改之间的细小差别，又提高了整体的表现。

![cw-hpf](https://s2.loli.net/2022/03/21/9BvRCZfO25GE4Ss.gif)

The three SRM filter kernels used to extract noise features. (CW-HPF is also same as the upper image, KV filter, KB filter, and a first order kernel)

**Dilated ConV**

a.k.a. atrous convolution, 就是空洞卷积。

普通卷积：$(F\times k)=\sum_{s+t=p}F(s)k(t)$

空洞卷积：$(F\times_lk)(p)=\sum_{s+lt=p}F(s)k(t)$, $s+lt=p$就意味着我们在卷积的过程中会跳过一些点，当$l=1$ 的时候，他就是一个标准的卷积；当$l>1$ 的时候，他就是一个空洞卷积，具体的可以看下图；

标准卷积：

![standard ConV](https://s2.loli.net/2022/03/08/2RqMxwFaSncDUQH.gif)

空洞卷积 ($l=2$)：

![dilatedConV](https://s2.loli.net/2022/03/08/9IhsnTPbLg2xpl6.gif)



![example](https://s2.loli.net/2022/03/08/ESg9xDB8chCfkrL.png)

$l=1$ (left), $l=2$ (middle), $l=4$ (right) 

这基本上就是coarse net的内容。

**Refined net**

Refine net 和Coarse net 基本上是一样的结构，将粗粒度网络的feature map的那个输出，输入到细粒度网络结构中，另外一个coarse mask的输出呢？？，而细粒度网络结构就是比粗粒度的在进行空洞卷积（dilated Conv）之后要多了一个**FA** forgery attention的模块。将特征图输入之后，我们会得到精炼后的预测结果，预测掩码，Refined Mask $I_M$

**Forgery Attention**

伪造注意力机制主要有两个部分，一个是**SAM**，*spatial-wise*, 一个是**CAM**，*channel-wise*。作者先是说别人的方法用了注意力机制，但是不好，缺点是

1. 忽视了颜色通道的依赖
2. 只注意了那些突出的物体，一些在细小部分做出的篡改检测不到。

所以作者通过这两个基于不同的尺度开展的注意力机制分支，就能解决这样的问题。提取到的注意力特征可以提供在通道和空间上的噪声特征的相似图，相似图能反映在噪声域上长期的上下文信息，<u>因为两个位置如果有比较相似的噪声特征，。。。</u>（两个具有相似特征的位置，他们可以相互促进。

*而这种Dual Attention机制，其实最早是出现在[DANet, CVPR 2019](https://github.com/junfu1115/DANet)的工作里面，他们在传统的基于空洞卷积（Dilated/Astrous ConV）的FCN里面添加了两种注意力模块，分别对空间维度和通道维度的语义相互关联进行建模。*

**SAM: spatial attention mechanism branch**

最后得到的SAM，即Spatial Attention Matrix of noise feature, 就是用来描述在噪声特征图的空间维度上任意两个位置的相似度；然后在噪声图上这两个位置的相似度越高，在最初的特征图上，这两个点的相关性就越大。

**CAM: channel sttention mechanism branch**

这个也跟SAM一样，就是换成了channel，具体地对矩阵的处理可能不太一样，但是没太看出来，attention体现在哪里？

而且，dual attention的机制好像用得也挺多的，在之前的[DOA-GAN](#DOA-GAN)里面也是用到了。

![dual-order-attention](https://s2.loli.net/2022/03/12/zBFsaAwjECbvdZn.gif)

![forgery-attention](https://s2.loli.net/2022/03/12/nhAeczUDXGarwqy.gif)

#### self adversarial training strategy

其实就是有两个训练阶段，第一个就是常规的训练，把训练集的每张图片丢到网络里面去，网络会输出一张预测的mask，然后再根据ground truth进行loss function的计算，反响传播，更新参数。那么同时还会有一个第二阶段的训练，就是输入的图片，首先会通过FGSM，就是一个对抗攻击的方法，会生成一张带有攻击样本的图片，再把这张图片输入到网络里，网络会生成一张新的预测结果的mask，也是跟ground truth去比较，反向传播。这两个阶段，貌似没有更明显的连接，只是作为两个训练阶段，所使用的网络是同一个，意味着，我在第一个普通阶段更新的网络参数，同时也会同步到第二个训练上，第二个训练上更新的参数也会同步到第一个上面。  

那么这个和GAN的区别是在于，GAN的训练策略是用自己的模型生成了一个input adv，而不是借用其他的经典的，有名的，快速的，对抗攻击的方法来生成。

## Result

![image-20230709181319173](https://s2.loli.net/2023/07/09/oyi8GFRQef3XSur.png)

### Conclusion

其实就是利用了noise feature，不是像普通的CNN直接去提取feature，而是利用CW-HPF获得的noise feature，使用noise feature的好处在于，原图和篡改后的图，他们的noise feature更不可能匹配上，再进行一个之后的无论是，使用coarse to fine的策略，以及加上dual attention进一步确定篡改的地方，dual attention的点子是来源于一个场景分割的工作，然后还是因为数据集太少，采用的self adversarial 训练策略，都在解决了篡改的地方不一定显著，数据集不一定足够这些问题。本质还是一个CNN的监督结构，自对抗或者说自攻击样本的生成只是利用了FGSM，同时，coarse to fine的策略，在coarse net里面生成了粗略的预测结果predict mask以及feature map，然后仅仅是将feature map放进去fine net里面继续卷积，而coarse net阶段生成的predict mask好像并没有起到作用，这，我觉得没有很好的为模型的参数优化真正做出贡献。