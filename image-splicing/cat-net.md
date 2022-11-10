---
description: >-
  CAT-Net: Compression Artifact Tracing Network for Detection and Localization
  of Image Splicing
---

# CAT-Net

_Myung-Joon Kwon, In-Jae Yu, Seung-Hun Nam, and Heung-Kyu Lee. 2021. CAT-Net: Compression Artifact Tracing Network for Detection and Localization of Image Splicing. 2021 Ieee Winter Conf Appl Comput Vis Wacv 00, (2021), 375–384. DOI:https://doi.org/10.1109/wacv48630.2021.00042_

__

<figure><img src="https://s2.loli.net/2022/04/25/Mevp5qExJPV13LS.gif" alt=""><figcaption></figcaption></figure>

<figure><img src="https://s2.loli.net/2022/04/25/u6AMmEOaKXybPx8.gif" alt=""><figcaption></figcaption></figure>

<figure><img src="https://s2.loli.net/2022/04/25/Ib7hrEdsgxDvuAn.gif" alt=""><figcaption></figcaption></figure>

<figure><img src="https://s2.loli.net/2022/04/25/eDU74OsVQS6Jmp8.gif" alt=""><figcaption></figcaption></figure>

### 概述

端到端的卷积神经网络结构，是第一个考虑包括了RGB stream (就是以图片的像素作为输入)和DCT Stream（以Y-Channel的DCT coefficients DCT系数，以及一个Y-Channel quantization table作为输入，（_Y通道指的就是将原始图像的色彩空间从`RGB`转换到`YCbCr`，`YCbCr`模型广泛应用在图片和视频的压缩传输中，`Y`表示的是亮度`Luminance`, `Cb`和`Cr`分别表示的是绿色和红色的`色度成分 chroma components`_）），（**这里是不是可以尝试换成Noise Stream**），一起去学习RGB domain和DCT domain的**压缩伪影Compression Artifact**的方法，每个stream都考虑了多种分辨率来处理拼接对象的各种形状和大小；DCT stream主要是利用了JPEG的伪影，在两次的JPEG检测上进行了预训练，来区分真是的和拼接的统计指纹（**statistical fingerprints**）？？这也是第一次将二次jpeg压缩检测问题迁移学习到了图像的篡改检测上。是基于**HRNet**进行修改的。

### **Improve**

在这上面再加上一个pixel-wise的attention，以及一个DCT-channel的attention。

### **问题**

1. 就是这个网络限制了只能训练JPEG的图片，因为她使用了压缩伪影的方法，用了JPEG压缩，所以，不太好，同时，JPEG往往本来就对图片进行了压缩，而高解析度的图片，往往会以PNG出现，同时也说明，这不好应用到更多的范围上。
2. built on top of HRNet, **语义分割**的方法会一定适用在篡改检测里面吗，如果被篡改的部分不具有区别性的语义？
3. 权重文件太大了

### GitHub

[https://github.com/mjkwon2021/CAT-Net](https://github.com/mjkwon2021/CAT-Net)
