---
description: >-
  A Serial Image Copy-Move Forgery Localization Scheme With Source/Target
  Distinguishment
---

# CMSDNet

> Beijing Chen, Weijin Tan, Gouenou Coatrieux, Yuhui Zheng, and Yun-Qing Shi. 2021. A Serial Image Copy-Move Forgery Localization Scheme With Source/Target Distinguishment. _Ieee T Multimedia_ 23, (2021), 3506–3517. DOI:https://doi.org/10.1109/tmm.2020.3026868

<figure><img src="https://s2.loli.net/2022/04/26/Esz8qDBaMfAVRkP.gif" alt=""><figcaption></figcaption></figure>

<figure><img src="https://s2.loli.net/2022/04/26/F8lsuwyAf7hpnJg.gif" alt=""><figcaption></figcaption></figure>

<figure><img src="https://s2.loli.net/2022/04/26/QmnOrc6qEVLTIzu.gif" alt=""><figcaption></figcaption></figure>

指出Buster Net两个缺点，首先是他不能确保两个分支都能准确定位，其次是它在相似度计算那个分支用的VGG16只能得到单一水平，低分辨率的特征。

提出了两个子网络，CMSD Net和STRD Net，引入了空同卷积而不用池化来获取更高分辨率，更多level的特征，然后也用了空间空洞金字塔池化和注意力机制来得到更多尺寸的特征，STRD Net就是用来决定这些从CMSD Net中得到的相似的区域是不是source，target，或者说tampered or untampered, 但是是从image-level，而不是从pixel-level。

相比来说，

* 从parallel的方案过渡到serial的方案，
* 用了ASPP来提高检测的相似度，
* 区分相似区域的时候是以图片的层次，而不是像素的层次，

不足之处在于：

检测的网络性能不好，影响了后面区分是source还是target的子网络，后处理方面针对某些特定的，新提出的攻击，鲁棒性可能不是那么好。

### GitHub

[https://github.com/imagecbj/A-serial-image-copy-move-forgery-localization-scheme-with-source-target-distinguishment](https://github.com/imagecbj/A-serial-image-copy-move-forgery-localization-scheme-with-source-target-distinguishment)
