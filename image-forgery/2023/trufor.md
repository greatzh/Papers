# TruFor

> Guillaro, F., Cozzolino, D., Sud, A., Dufour, N., & Verdoliva, L. (2023). TruFor: Leveraging all-round clues for trustworthy image forgery detection and localization. IEEE/CVF Conference on Computer Vision and Pattern Recognition (CVPR), abs/2212.10957. https://doi.org/10.48550/arXiv.2212.10957

![title](https://s2.loli.net/2023/06/10/XtwLjhaKW8YIGyc.png)

现在（2023）提出的篡改检测都必须能够有应对基于深度学习的篡改检测的能力，作者提出的方法是之前被广泛采用的，将RGB特征和noise-sensitive fingerprint，两个特征经Transformer的结构融合起来，能够实现对传统的图像编辑篡改（cheapfakes）和最近几年的基于深度学习（deepfakes）的篡改。不过作者这里使用的noise fingerprint是经过学习之后的noise fingerprint，它通过自我监督的方式，使用真实数据进行训练，学习嵌入和相机内部及外部处理相关的伪影artifact，所以与传统的 RGB + handcrafted feature 不一样。同时为了提供更可靠的检测结果，作者在给出localization mask之外还引入了 confidence map 来展示可能的误报。

![image-20240330101228161](https://s2.loli.net/2024/03/30/cXJMzf2qH4UYARk.png)

## 方法与实现

![framework](https://s2.loli.net/2023/06/10/AyzgIiMlUBXothR.png)

### 出发点

1. 有限的泛化能力，只针对某一种篡改类型，只针对某一种图片格式，只采用某一个low feature，在真实场景下的表现不佳。
2. 有限的鲁棒性
3. 检测能力不足，目前的方法都把定位当作重点，而没有重视检测，检测的结果往往就是根据定位的heatmap来计算，但是在现实世界里面，这样的检测准确性较差，误报高，应该考虑直接地解决检测任务。

### 概述

一样采用了fusion，但是使用了跨模态的特征校准来结合noise和RGB特征，而为了直接考虑检测这一问题，作者设计了一个**篡改检测模块**，通过输入异常分析图和置信度图来获得最后的检测结果。

展开来讲，输入 RGB 图片，通过一个**Noiseprint++ Extractor** 得到图片的noise fingerprint，然后将RGB图片和noise fingerprint一起输入到encoder网络种提取密集特征，再将提取到的特征分别输入到两个decoder网络种，一个用来提取异常map（localization mask），一个则是提取置信map（区分篡改区域的有效预测和随机异常）；提取到的异常分析map将结合置信度map确定池化的权重，得到一个紧凑的描述符，通过篡改检测器后得到一个完整性的评分。

### Noiseprint++

![image-20240330142947467](https://s2.loli.net/2024/03/30/wFBj6shLvdSM7ca.png)

作者曾在其2018年的文章种提出过[基于深度学习的方法](https://github.com/grip-unina/noiseprint)来提取图片的noiseprint，当时采用的方法是使用原图来进行自监督训练，而没有考虑到相机之外的后处理所带来的鲁棒性问题；而这次提出的 Noiseprint++则是不仅考虑了相机内的流程，硬件处理信息（不同型号）等，也考虑到了相机外可能的篡改痕迹历史等，来提高可靠性。具体的实现如上图所示，在extractor中，作者采用了自监督的对比学习，与之前的方法一样，使用[DnCNN](https://github.com/cszn/DnCNN)网络架构，[InfoNCE](https://github.com/HobbitLong/SupContrast)对比损失，将来自相同相机模型，相同位置，相同编辑历史的patch输出之间的距离最小化。

作者为了确保Noiseprint++是在未经修改的图片上进行训练，对相机模型，手机图片的解析度，JPEG的压缩量化矩阵，元数据的统一等进行控制变量。训练中，在每个batch中包含160个64x64像素的patch，这160个patch是由4张不同的图片经5个相机模型拍摄得到，共20张，接着这20张图片再经过4种不同的编辑方式，随机的大小裁剪，压缩，对比度和亮度的调整，总共有512种可能的编辑结合方式。

![image-20240330172718888](https://s2.loli.net/2024/03/30/Y3xwVhPQcJeWz8L.png)

### 异常定位map



## 结果

## 总结

1. 作者表示该方法还无法检测完全由 ai 生成的图片；其次，训练的异常map和最后的检测得分是分开的，并不是端到端的训练；最后还提到需要在更多的由生成模型局部编辑的图片数据集上进行泛化性的评估。

## GitHub

Project page: https://grip-unina.github.io/TruFor/

Code: https://github.com/grip-unina/TruFor