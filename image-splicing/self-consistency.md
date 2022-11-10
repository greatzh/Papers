---
description: 'Fighting Fake News: Image Splice Detection via Learned Self-Consistency'
---

# Self consistency

_Minyoung Huh, Andrew Liu, Andrew Owens, and Alexei A Efros. 2018. Fighting Fake News: Image Splice Detection via Learned Self-Consistency. Arxiv (2018)._

<figure><img src="https://s2.loli.net/2022/04/15/l1EkJfqBTDHGZYy.png" alt=""><figcaption></figcaption></figure>

算法利用图片自动记录的**EXIF Metadata**（_通常被数码相机在拍摄照片时自动添加，比如相机型号、镜头、曝光、图片尺寸等信息，不同的两个source image自然就会不一样_）作为一个自监督的信号，训练的时候也不用打标签什么的，也是用真实的图片去训练，训练也主要是看看在众多EXIF metadata里面影响比较多的到底是哪个tag（因为实际在测试的时候，不会拿到两张图片可以直接进行比对，所以也是要训练，不同的图片，去比较，然后一个个patch去计算匹配），来判断一张图片是不是**self consistency**。

主要贡献：

1. 把图像取证的问题看成是检测问题，学习检测自我一致性，检测其中的异常。
2. 提出了使用图片的metadata进行自监督学习来学习一致性。
3. 利用这种提出的方法去检测拼接篡改和定位。

\
