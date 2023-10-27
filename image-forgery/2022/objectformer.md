---
description: ObjectFormer for Image Manipulation Detection and Localization
---

# ObjectFormer

J. Wang _et al._, “ObjectFormer for Image Manipulation Detection and Localization,” _2022 Ieee Cvf Conf Comput Vis Pattern Recognit Cvpr_, vol. 00, pp. 2354–2363, 2022, doi: 10.1109/cvpr52688.2022.00240.

作者提出了使用frequency特征以及将它和RGB特征结合，以embedding的形式输入到encoder里面，主要的贡献点是1. 用了这个high frequency feature，2. 对frequency feature应用了一个边界敏感上下文不一致模块boundary-sensitive contextual incoherence module，用来对特征做fine-grain，3. 利用了object prototype，学习mid-level feature。

作者在做消融研究的时候，baseline是efficientNet-B4？因为他用的backbone就是efficient-B4，

<figure><img src="https://s2.loli.net/2022/10/24/Im6GnLiCJWXz81e.png" alt=""><figcaption></figcaption></figure>

## Result

![image-20230711173825281](https://s2.loli.net/2023/07/11/FOKdqfyeSIVNvtZ.png)
