# MSFF-AES

![image-20230709151408438](https://s2.loli.net/2023/07/09/6Vo5cfgUuLbZOMh.png)

> Li, F., Pei, Z., Zhang, X., & Qin, C. (2022). Image Manipulation Localization Using Multi-Scale Feature Fusion and Adaptive Edge Supervision. In IEEE Transactions on Multimedia (pp. 1–15). IEEE. https://doi.org/10.1109/TMM.2022.3231110

作者指出现有的对特征进行融合的方法忽略了不是所有图片都有这些信息（噪声不一致，二次压缩不一致，局部不一致）的事实，而特征的冗余带来了大量的误报。为了解决这个问题，作者提出的方法是将它看做一个特别的sod的问题来解决，提出了一个端对端的高置信度定位网络，首先从CNN中得到图片的多尺度RGB信息，然后经过一个语义精炼双向特征融合模块将这些多尺度的相邻特征融合来增强特征表示。同时，形态学操作被引入用来提取多尺度的边缘信息，