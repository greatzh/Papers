# TruFor

> Guillaro, F., Cozzolino, D., Sud, A., Dufour, N., & Verdoliva, L. (2023). TruFor: Leveraging all-round clues for trustworthy image forgery detection and localization. IEEE/CVF Conference on Computer Vision and Pattern Recognition (CVPR), abs/2212.10957. https://doi.org/10.48550/arXiv.2212.10957

![title](https://s2.loli.net/2023/06/10/XtwLjhaKW8YIGyc.png)

现在（2023）提出的篡改检测都必须能够有应对基于深度学习的篡改检测的能力，作者提出的方法是之前被广泛采用的，将RGB特征和noise-sensitive fingerprint，两个特征经Transformer的结构融合起来，能够实现对传统的图像编辑篡改（cheapfakes）和最近几年的基于深度学习（deepfakes）的篡改。不过作者这里使用的noise fingerprint是经过学习之后的noise fingerprint，它通过自我监督的方式，使用真实数据进行训练，学习嵌入和相机内部及外部处理相关的伪影artifact。

## 方法与实现

![framework](https://s2.loli.net/2023/06/10/AyzgIiMlUBXothR.png)

## 结果

## GitHub

Project page: https://grip-unina.github.io/TruFor/

Code: https://github.com/grip-unina/TruFor