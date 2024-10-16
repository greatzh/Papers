# CIMD

> Zhang, Z., Li, M., & Chang, M.-C. (2024). A New Benchmark and Model for Challenging Image Manipulation Detection. AAAI Conference on Artificial Intelligence (AAAI), 7405–7413. https://doi.org/10.1609/aaai.v38i7.28571

![image-20240910122818977](https://s2.loli.net/2024/09/10/eoO9ETIhW2ltvAM.png)

这篇文章主要是提出了一个新的具有挑战性的图像篡改检测数据集，Challenge Image Manipulation Detection （CIMD）benchmark dataset。作者观察到当前基于编辑的图像篡改很难发现一张大图片中的小部分篡改，基于压缩来进行的也面临这双重压缩的挑战（当使用相同的量化矩阵进行双重压缩时，基于直方图的方法并不有效，因为存在很少的压缩不一致性），于是为了研究SOTA方面对这些挑战的情况，作者纯手工制作该数据集。

整个数据集都是小区域篡改，篡改区域平均小于1.5%，它包含针对上述基于编辑的篡改**CIMD-R**(300张TIFF图片，未压缩防止提供压缩伪影这一线索，分辨率2048 x 1365，提供GT，有经过后处理)和基于压缩的篡改**CIMD-C**（100张JPEG图片，2048 x 1365，QF均匀分布在50-100之间，篡改的方式和RAW一样，只包括拼接篡改200张，不同之处在于使用JPEG压缩算法保存，背景是双重压缩，篡改区域是单次，数据集还包含了用于压缩的二进制掩码和量化因子QF），即压缩和未压缩两个部分。

针对该数据集作者也提出了一个基于 HRNet 的 RGB 和 frequency 双分支检测方法。

该方法的结果如下，用于训练的数据集都来自 CAT-Net (Learning jpeg compression artifacts for image manipulation detection and localization, Kwon et al. 2022),而用于评估的数据集则是本文提出的两个部分，图一是CIMD-Raw，图2是CIMD-Compressed，CIMD-R即意味着未压缩的图片，-C则是经过了双重压缩。

![image-20240910124317618](https://s2.loli.net/2024/09/10/F6EhJrMDXk47sNv.png)

![image-20240910124420440](https://s2.loli.net/2024/09/10/OTaDeXG9LU2oflv.png)

方法的具体框架如下

![image-20240910131549573](https://s2.loli.net/2024/09/10/p5KFBwTab8nWvXj.png)

![image-20240910131409085](https://s2.loli.net/2024/09/10/4R8NlI2psLrhi7a.png)

![image-20240910131440327](https://s2.loli.net/2024/09/10/WcEqXYoV7tyuPe5.png)

图一为整体的框架图，图二为频率分支中HRNet变体里第一部分CAL Compression Artifact Learning，图三则是 ASPP 通道注意力和空间注意力。

ablation study上面则是简单的讨论了只有RGB stream 或 Frequency Stream 以及都包括两种情况。

作者没有给出该模型在其他常用的评估图像篡改检测方法的数据集上的结果，但该工作的重点也不并在于这个方法，更多的是放在benchmark dataset之上，最后的结果无论是从image level还是pixel level来看都能表示这确实是一个具有挑战性的数据集，但是我下载了该数据集，其实里面的一些copy move，splicing，还是removal都并不是那种现实世界里面真正具有语义上的层次的修改，更多的还是扣除一个object，复制过去或者拼接上去，removal上面是用了PS自带的修复功能。所以再具有挑战性一点是不是可以给篡改加上语义，让每一张篡改的图片都具有现实世界的意义。反过来想，如果单纯是为了打败这样的数据集，是不是给模型加上语义检测或者分割的功能，作为一个辅助的分支，是不是会更容易处理这样的篡改。

而在方法上，毕竟用HRNet做backbone，然后结合RGB和Frequency的工作已经相当多，像是HiFi-Net，CVPR2023的工作，还有CAT-Net则是结合了RGB和DCT histogram，本文也是Y-channel DCT Map, ASPP 空洞金字塔池化或者空洞卷积也不是新东西。不同之处在于对频率信息的提取上作者使用了专门的JPEG压缩伪影学习模块，以及除了HRNet大的框架之外，整个的框架结构上都有不同。

---

解释了一些 HRNet 好使的原因，1. 没有池化层可以确保特征一直在高分辨率，不容易丢失信息；2. 能并行处理不同尺度的特征，同时有效进行信息交换；3. 输入尺寸适合 DCT 特征。
