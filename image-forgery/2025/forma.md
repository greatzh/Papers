# ForMa

![image-20250330092630491](https://s2.loli.net/2025/03/30/CzFTak3OGoYBtve.png)

> Guo, K., Cao, G., Lou, Z., Huang, X., & Liu, J. (2025). A Lightweight and Effective Image Tampering Localization Network with
>   Vision Mamba. In arXiv.

这篇短论文主要是利用了 [Mamba (ICLR '24) ](https://arxiv.org/pdf/2312.00752) 的变体 Vision Mamba [(VMamba, NeurIPS '24)](https://proceedings.neurips.cc/paper_files/paper/2024/file/baa2da9ae4bfed26520bb61d259a3653-Paper-Conference.pdf)，作者提到 CNN 局部感受野有限，Transformer 全局上下文建模算例复杂，而 ICLR 2024 提出的 Mamba 在当时就被提到有可能替代 Transformer，Mamba 是一种 State Space Mode 状态空间模型，比 Transformer 更高效的序列建模，线性复杂度，而 Transformer 为 O(N^2)。基于 VMamba，作者提出了一个轻量有效的 FORensic network based on vision MAmba (ForMa) 图像篡改取证网络。ForMa 利用 VMamba 作为编码器，提取多尺度，接着是一个由线性层构成的轻量解码器，它使用了像素重排来进一步降低计算成本。以及融合了使用噪声和噪声辅助解码来提取额外的篡改特征。

加上噪声特征似乎是基操了，如下图所示，除了获得由 VMamba 提取的视觉/RGB特征，还有由 Noiseprint++ 等传统检测方法提取的频率特征，作者也提到他们使用了多源的噪声融合，不使用单一的方法提取噪声。同时，不同的方法可能在不同的地方将 RGB 和 Frequency 特征融合，这篇短论文在解码器阶段，作为一个辅助的定位线索。

![image-20250330100119605](https://s2.loli.net/2025/03/30/dU37jOfBTpFerCX.png)

和 VMamba 框架一样

![image-20250330100308391](https://s2.loli.net/2025/03/30/A16GmcEO8YhdDaq.png)

## 结果

除了检测结果，作者还给出了计算复杂度的对比，在计算复杂度上，ForMa 表现最好；以及使用 OSNs 提出的社交网络篡改数据集来检测鲁棒性， ForMa 也是优于 CAT-Net 和 TruFor。

![image-20250330101540703](https://s2.loli.net/2025/03/30/hCSgqrxBFHGT4KZ.png)

Code is available at https://github.com/multimediaFor/ForMa