---
description: 'LoFTR: Detector-Free Local Matching with Transformers'
---

# LoFTR

> Jiaming Sun, Zehong Shen, Yuang Wang, Hujun Bao, and Xiaowei Zhou. 2021. LoFTR: Detector-Free Local Feature Matching with Transformers. _2021 Ieee Cvf Conf Comput Vis Pattern Recognit Cvpr_ 00, (2021), 8918–8927. DOI:https://doi.org/10.1109/cvpr46437.2021.00881



<figure><img src="https://s2.loli.net/2022/03/25/uh3J2RIxL9isO5H.gif" alt=""><figcaption></figcaption></figure>

不使用普遍的先从特征检测到特征表示，匹配这样的流程，而是提出了一个coarse to fine的像素级别，利用自注意力和交叉注意力机制的密集匹配（detector free）去获取特征表示。Transformer提供的全局感受野让dense methods在low-texture区域也有好的密集匹配效果，无论是在动态虚化，重复图形以及低纹理区域。

问题的提出：以前用特征提取的方法，减少了匹配的搜索空间，同时提取不料足够多的候选点因为poor texture, viewpoint change, illumination variation, and mortion blur. 同时低纹理区域的特征或者重复的，通常就占据了大部分视野。其他一些人的解决方法提出了像是像素级别的密集匹配，从密集匹配中选择置信度分数最高的匹配。但是从CNN中提取的特征有限制的感受野，而匹配也不仅仅是局部的邻近的，更多是全局的。能够关注到除了**salient objects**之外的区域！！

**KEY**：从transformer里面得到的位置编码以及感受野让特征表示更加context-dependent and position-dependent.(上下文和位置独立？？)

### 相关工作

#### **Detector based**

(SIFT, ORB) $$\to$$ (LIFT, MagicPoint)$$\to$$ SuperPoint$$\to$$ SuperGlue(使用GNN，其实大体上就是Transformer)$$\to$$from detector based to detector free's **LoFTR**,

有一个缺点就是前面说的没办法检测重复的，以及只看自己感兴趣的。

#### **Detector-free**

直接生成密集的密集描述符或者密集匹配（？？），

SIFT Flow $$\to$$ NCNet(利用4D卷积正则化损失) $$\to$$ Sparse NCNet $$\to$$ DRC-Net

### Methods

*   Local feature CNN

    使用FPN得到多个level的特征，coarse level feature and fine-level features，
*   coarse feature maps

    粗粒度的特征图经过位置编码之后，进入LoFTR模块获得位置和上下文依赖，其实就是利用LoFTR把特征转换成了更容易匹配时候使用的特征表示。

    **Transformer**：类似于信息检索，查询向量query Q 从值向量value V 中检索信息，根据 Q 的点积计算的注意力权重和每个值value V 对应的关键向量key K。直观上，注意力操作通过测量查询元素query与每个关键元素key之间的相似度来选择相关信息。 输出向量是由相似度得分加权的值向量value的总和。 结果，如果相似度高，则从值向量value中提取相关信息。 这个过程在图神经网络中也称为“消息传递”。

    但是由于直接使用原生的transformer,尽管已经用cnn做了特征提取，点积的计算复杂度还是二次方，在上下文的局部特征匹配中使用是不现实的，于是作者提出了使用**Linear Transformer**,降低复杂度到$$O(N)$$,用新的核函数（先做一个ELU？？）替代原来注意力层中的指数核。

    **Positional Encoding**: 使用了**DEtection TRansformer（DTER）**里面的位置编码，位置编码以正弦格式给出每个元素的唯一位置信息。转换后的特征将变得依赖于位置，这对于 LoFTR 在模糊区域中产生匹配的能力至关重要。

    **Self-attention and Cross-sttention Layers**:
*   diffenentiable matching module

    optimal transport(OT) layer or a dual-softmax operator.
*   coarse-to-fine module

    建立了在粗粒度上的match之后，然后这些match进一步refine到原图的解析度，

### GitHub

[https://github.com/zju3dv/LoFTR](https://github.com/zju3dv/LoFTR)
