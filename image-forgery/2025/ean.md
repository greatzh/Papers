# EAN

![image-20250509113904190](https://s2.loli.net/2025/05/09/CstFb2YLOX8izw6.png)

> Chen, Y., Cheng, H., Wang, H., Liu, X., Chen, F., Li, F., Zhang, X., & Wang, M. (2025). EAN: Edge-Aware Network for Image Manipulation Localization. In IEEE Transactions on Circuits and Systems for Video Technology (Vol. 35, Issue 2, pp. 1591–1601). Institute of Electrical and Electronics Engineers (IEEE). https://doi.org/10.1109/TCSVT.2024.3473933

现有方法通过通过明显的边缘特征捕捉的边界伪影不能很好的处理细微的/隐藏的伪影，此外大模型强大的特征提取能力也会出现一些特征冗余妨碍准确的篡改伪影的识别，出现较高的误报率吧。作者为了解决这个问题，提出了一个边缘感知网络，将篡改定位问题看成一个分割问题，提出的边缘感知机制，能够通过相邻特征的交互来细化隐式和显式边缘特征；以及结合注意力机制的多特征融合等。其实就是一个 CNN 的编码器，获取 RGB 和 噪声特征，设计的边缘感知机制能够细化边缘特征的同时确保不会特征冗余，最后进行特征融合解码。

![image-20250509125720291](https://s2.loli.net/2025/05/09/xKL3AynZDb5m18u.png)

## 方法

![image-20250509125834571](https://s2.loli.net/2025/05/09/svCaOoAK6tpGyJB.png)