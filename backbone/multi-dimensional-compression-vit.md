---
description: Multi-Dimensional Model Compression of Vision Transformer
---

# Multi-Dimensional Compression ViT

Z. Hou and S.-Y. Kung, “Multi-Dimensional Model Compression of Vision Transformer,” _2022 Ieee Int Conf Multimedia Expo Icme_, vol. 00, pp. 01–06, 2022, doi: 10.1109/icme52920.2022.9859786.

文章试图解决ViT模型需要的计算资源比较多，而之前pruning的方法大多在一个维度上面单独进行模型的剪枝，可能会出现过度减少的问题，导致模型并不是最优的，这次作者从**注意力头attention head**，**神经元neuron**，以及**序列sequence**三个维度上联合进行pruning。

具体多维的关键做法是，首先提出了一种通用的数据依赖标准（基于依赖的剪枝），这个标准基于**交叉方差算子Hilbert-Schimdt施密特范数**测量维度特征和模型输出预测之间的统计相关性。此外将多维压缩归纳为一个**优化**问题，即，寻求在目标计算成本下，最大化压缩模型的准确性的最佳剪枝策略。同时考虑到这个问题的**不可求导/微**，使用了**Gaussian process GP高斯过程**去搜索来估计不同剪枝策略的压缩模型的准确性。对于这个GP模型的fit，设计一个权重共享机制用于快速准确评估，而不用从头开始训练每个压缩模型。

$$C_{zy}:=\mathbb{E}_{zy}[(\Phi(z)-\mu_z)\otimes(\Psi(y)-\mu_y)]$$

Z表示特征的随机向量，Y表示模型的输出，\Phi或者\Psi是用来表示把特征映射到**reproducing kernel Hilbert space RKHS**上的kernel；然后用这个交叉协方差算子（希尔伯特-施密特范式）来测量他们之间的（非线性的）依赖性。（论文通过数学公式推导证明这个距离是可以用来表示这种依赖性的。）然后针对在neuron上，多头注意力机制上，以及sequence上进行的剪枝操作。紧接着是对准确度的计算，找到最适合的剪枝策略的参数，利用**Gaussian process search**，去找到准确值最大的时候的参数。同时采用了权重共享可以避免从一开始去训练和评估各个压缩后模型的表现。

$$
{min}_{W}\mathbb{E}_{(x,y)\sim D, w\sim U_T[L(y|x;W(w)]}
$$

D是数据集，U\_T是剪枝策略的受限均匀抽样分布。

### GitHub

[https://github.com/zejiangh/Multi-dimensional-vit-compression.git](https://github.com/zejiangh/Multi-dimensional-vit-compression.git)
