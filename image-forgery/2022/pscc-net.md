---
description: >-
  PSCC-Net: Progressive Spatio-Channel Correlation Network for Image
  Manipulation Detection and Localization
---

# PSCC-Net

> X. Liu, Y. Liu, J. Chen, and X. Liu, “PSCC-Net: Progressive Spatio-Channel Correlation Network for Image Manipulation Detection and Localization,” _Ieee T Circ Syst Vid_, vol. PP, no. 99, pp. 1–1, 2022, doi: 10.1109/tcsvt.2022.3189545.

<figure><img src="https://s2.loli.net/2022/12/21/ZUHRxrJolha5edE.png" alt=""><figcaption></figcaption></figure>

文章提出了一个渐进式的空间频道相关网络，主要分为两个部分，一个是从上到下的路径，使用HRNet用来提取输入图片的局部和全局特征；以及一个从下到上的路径用来检测输入的图片是否有被操纵，并从不同的尺度估计篡改的掩码图，每个掩码都会作为一个下一个估计的先验，同时一个空间通道相关模块（spatial-channel correlation module, SCCM）聚合了局部特征之间的全局上下文，用来捕获空间和通道相关性，来服务特征整体线索，使得网络能够应对广泛的篡改攻击。

## **介绍**

通常来说，图像篡改内容独立和内容不独立两种过程，前面的包括想image splicing，copy move，removal；而后面的包括全局的修改，像是光照，对比对，锐化，噪声，图像压缩，它们不怎么创造新的误解的信息，但是可以很好的隐藏一些篡改区域和原始图片之间的差异。一些提出的方法也从针对单一的篡改类型到更通用的多种篡改的类型。但是这些方法依然存在以下三个问题：

1. 尺度的多变：当检测不同大小的篡改区域的时候往往会遇到苦难，也忽视了尺度变化的重要性。
2. 图像的相关性：以前的方法忽视了图像空间的相关性，只是天真的学习从篡改图像到篡改掩码的映射容易造成对某种特定篡改类型的过拟合。
3. 检测：大部分的工作都会假设图片是存在篡改的，这样很容易导致一些误报，让检测结果不可信。

## **相关工作**

1. 检测：两种方法，隐式的（通过预测的篡改掩码的统计信息，最大值或者平均）和显式的（专门的分类模块计算得到的分数）。说最近的方法都是专注在像素级别上的篡改定位，而忽略了图像级别上的检测。
2. 定位：说一些方法对具体的某一种篡改类型可能表现很好，但是当面对未知篡改类型的，通用性很差。但是最近的一些整合多种操作类型的模型，也有各自的问题。J-LSTM和H-LSTM因为基于patch的设计，很耗时间，检测的区域也被patch的大小所限制；RGB-N用了隐写分析的模型和Faster R-CNN，但是它只能提供边界框而没有办法得到分割的掩码图；ManTra-Net需要很多额外的打标签，相机传感器什么的参数都要；SPAN延续ManTra-Net的哦工作，通过自注意力模块和金字塔的传播，但是它只考虑到局部区域的相关性；他们都没有很好的利用空间的相关性，泛化能力也很有限。
3. 渐进式机制：coarse to fine，从小尺度到大尺度，每一个小尺度的结果又会作为下一个大尺度估计的先验。（哎，就一个coarse to fine，都造了多少名字出来了，金字塔结构，多尺度结构，渐进式机制... 好好讲故事很重）
4. 注意力机制：注意力机制通常可以划分为空间注意力机制，和通道注意力；和现在的QKV的注意力机制可能不太一样，通道注意力，其实就是两个全连接层的叠加，压缩h \times w 的信息来构造；那么空间注意力就是压缩通道，构造在空间维度上的信息，C \times W \times H 的信息压缩成 1 \times W \times H，再通过带有注意力权重的卷积来提取注意力信息。

## **方法**

### 网络结构

1.  自上而下的路径

    为了解决常见的之前的使用传统encoder decoder结构或者非池化的结构来提取特征，导致的对不同尺度特征的忽略，所以选用了HRNet。用HRNet有两方面的好处，首先就是，从不同尺度提取道德特征计算是并行的，不同尺度之间的紧密联系可以实现有效的信息交换，有利于处理尺度变化；其次，由于每个尺度都进行了局部和全局特征融合，因此每个特征都包含足够的信息来预测相应尺度上的篡改掩码。
2.  自下而上的路径

    将前面得到的四个特征和对应的mask，从上到下得到的是Feature1 F1, F2, F3, F4, 然后对应的Mask1 M1, M2, M3, M4, M4就会直接等于把F4丢到SCCM里面得到的，而自下而上，M3就需要先和之前尺度的上采样的mask做一个关联，用于特征调制，然后再丢到sccm里面得到mask。

    ```
    mask4, z4 = self.getmask4(s4)
    mask4U = F.interpolate(mask4, size=s3.size()[2:], mode='bilinear', align_corners=True)
    ​
    s3 = s3 * mask4U
    mask3, z3 = self.getmask3(s3)
    mask3U = F.interpolate(mask3, size=s2.size()[2:], mode='bilinear', align_corners=True)
    ​
    s2 = s2 * mask3U
    mask2, z2 = self.getmask2(s2)
    mask2U = F.interpolate(mask2, size=s1.size()[2:], mode='bilinear', align_corners=True)
    ​
    s1 = s1 * mask2U
    mask1, z1 = self.getmask1(s1)
    ​
    return mask1, mask2, mask3, mask4
    ```

### 空间通道相关模块

<figure><img src="https://s2.loli.net/2022/12/21/e5iZKX6b3C8WFc1.png" alt=""><figcaption></figcaption></figure>

### 损失函数

BCE: binary cross entropy

### 训练数据合成

## **实验**

### 测试集和微调

1. 四个标准的测试集，Columbia，Coverage，CASIA，NIST16；以及一个真实世界的数据集IMD20.
2. 大概都是依照之前的方法，对测试用的数据集，再进一步划分为用来微调的训练集，和测试。
3. 例如，Coverage有100张图片，其中75张用来训练，25张用来测试；CASIA，则是5123张来自V2.0的图片用来训练，921张来自V1.0的用来测试。NIST16有564张图片，404张用来训练，160张用来测试；IMD20有2010张图片。

### 评价指标

Pixel-level的AUC(Area Under Curve)以及F1-score。

### 细节

1. 自上而下的网络有2百万参数，自下而上的网络有1.6百万个参数。（相比MantraNet, SPAN的参数还是少了很多）
2. 在1080Ti上训练的，backbone是ImageNet的预训练模型。
3. 优化过程使用Adam，初始的学习率是0.0002 2e-4, batch-size是10；学习率是每5个epochs减半，总共训练25个epochs。

### 在定位上的比较

1. 比较的方法，J-LSTM，H-LSTM，RGB-N，ManTra-Net，and SPAN.
2. 用了两个模型来比较，一个是pre-trained model，这个预训练模型在合成数据集上进行训练，然后在完整的测试数据集上进行评估，这主要是要体现泛化能力强。而另一个是fine-tuned模型，微调模型是进一步对测试数据集进行分割出一部分的训练集来进行微调训练，再用剩下的测试集来进行评估，这就是研究当domain差异缓解的时候的定位表现。
3.  pre-trained model的结果&#x20;

    <figure><img src="https://s2.loli.net/2023/01/01/VwJ9xu27Y3GDpvT.png" alt=""><figcaption></figcaption></figure>
4.  Fine-tuned model的结果

    <figure><img src="https://s2.loli.net/2023/01/01/F3WNalu7koOY5cb.png" alt=""><figcaption></figcaption></figure>

### 在检测上的比较

## GitHub

[https://github.com/proteus1991/PSCC-Net](https://github.com/proteus1991/PSCC-Net)
