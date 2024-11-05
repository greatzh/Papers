# MSTAF

> Tan, Y., Li, Y., Zeng, L., Ye, J., Wang, W., & Li, X. (2023). Multi-scale Target-Aware Framework for Constrained Splicing Detection and Localization. Proceedings of the 31st ACM International Conference on Multimedia, abs/2308.09357. https://doi.org/10.1145/3581783.3613763

![image-20231112103316516](https://s2.loli.net/2023/11/12/ynqRs5ILNtXalTo.png)

## 摘要

作者观察到现有的受限图像拼接篡改检测和定位的网络框架会将**特征提取**和**相关性匹配**作为独立的过程来设计，作者认为这会阻碍模型学习用于匹配具有区分性的特征。于是作者提出多尺度目标感知框架，将特征提取和相关性匹配融合在一个统一的流程中。目标感知的注意力机制能够共同学习和促进在供体和受体图片上的特征和相关性匹配。同时为了实现多尺度的变换，作者引入了一种多尺度投影方法，可以使注意力过程在不同尺度信息的标记之间进行，并轻松集成到目标感知框架中。

![image-20231112103038565](https://s2.loli.net/2023/11/12/gP2er8QAniG1fat.png)

1. 动机/要解决的问题：将特征提取与相关性匹配分开会无法利用两幅图像之间的相似图像块的相关性来感知目标特征；而在匹配上，独立的过程也也不能提供两张图片特征信息的交流。
2. 框架的启发来源：MixFormer (CVPR '22) 和 SimTrack (ECCV '22)，根据前面提到的问题输入两张图片进行检测而不是在一个统一的过程，作者从这两个框架中得到启发，设计了统一的框架，将特征学习和相关性的匹配结合起来。在做相关性匹配的同时，模型也能在特征学习接管感知到相关区域，然后根据注意力机制来抑制这些非相关和背景区域的影响。
3. 框架的重要部分：和一般的多头注意力机制不同，**目标感知注意力机制** 将两个输入图片的特征作为输入，然后将注意力过程分为两个头，另一个头用来出来交叉注意力以计算相关性匹配和提取另一张图片的特征。
4. 实验与结果：作者自己根据先前的方法用 MS COCO生成了一些训练的数据集；用户自己合成的数据集进行了测试，CAISA 数据集，以及MFC2018这三个数据集进行评估，评价的指标采用了 IoU，NMM，以及MCC来评估定位表现，而检测表现则是使用了Precision，Recall，以及F1.在ablation上，作者主要考虑了用分开的特征提取和相关性匹配以及用户统一的管道，然后用大小不等的数据集来分析了模型针对尺寸变换的鲁棒性。

## 框架

![image-20231112103226759](https://s2.loli.net/2023/11/12/p1rRSHbhw6gjtsK.png)

![image-20231115090958880](https://s2.loli.net/2023/11/15/Ptfya9YSvzCcuNQ.png)

![image-20231115091032027](https://s2.loli.net/2023/11/15/QBzxanhwVAypkRd.png)

## 结果

![image-20231115090655196](https://s2.loli.net/2023/11/15/5vQuzeH3M1SFwP4.png)

![image-20231115090715877](https://s2.loli.net/2023/11/15/vboGI3fLZCpSBrt.png)