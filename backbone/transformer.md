---
description: Attention Is All You Need
---

# Transformer

_Ashish Vaswani, Noam Shazeer, Niki Parmar, Jakob Uszkoreit, Llion Jones, Aidan N Gomez, Lukasz Kaiser, and Illia Polosukhin. 2017. Attention Is All You Need. Arxiv (2017)._

<figure><img src="https://s2.loli.net/2022/04/05/Qc3pnMHOglwE6ae.png" alt=""><figcaption></figcaption></figure>

### 概要

Transformer(变形金刚)，仅用注意力机制的编码器解码器模型，不依赖循环或者卷积神经网络，达到较高的并行度，在较短时间内实现更好的效果。注意力机制不像卷积一样需要经过多次卷积才能读到两个较远像素的特征，attention每一次能看到所有的像素，同时multi-head attention像卷积一样可以实现多输出通道，可以去识别不同的模式。

### **Batch Norm & Layer Norm**

Batch Norm: 在变长的应用中不常使用，每一列（特征）在一个minibatch里面，把它的方差调整到1，均值为0。通过将向量本身的均值减掉，再除以方差，在每一个小批量算出的均值和方差。

Layer Norm: 对每一行（样本），调整到方差为1，均值为0，即把数据转置放到Batch Norm得到的结果再转置。在时序的数据里面，样本的长度可能会发生变化，用Layer Norm算出的每个样本自己的均值和方差抖动相比Batch Norm更小，更稳定。

#### ## Attention

query和key-value pairs映射成输出，对于每一个value的权重，value对应的key和查询query的相似度（compatibility function）确定其权重。由于query的不一样，权重分配不一样，不同的相似函数导致不一样的注意力版本，导致输出不一样。

$$
Attention(Q,K,V)=softmax(\frac{QK^T}{\sqrt{d_k}})V
$$

两个向量，query和Key（列相同）做内积，如果两个向量Norm一样，两个向量内积的值，余弦值越大，相似度越高。

**additive attention** and **dot-attention**加性注意力和点乘注意力。

**Mask**防止看到以后的数据，对于之后计算的值换成非常大的负数，进入softmax指数运算的时候变成0。

#### **Scaled Dot-Product Attention**

query, key, values,

对于每一个values的权重，是value对应的key，以及query对应key的相似度（compatibility function），不同的相似函数导致不同的注意力机制版本。

（矩阵乘法是很容易并行的机制，顺序计算越少越好，越不用等，并行度越高）

#### **Multi-Head Attention**

$$
MultiHead(Q,K,V)=Concat(head_1,...,head_h)W^O \\where\;head_i=Attention(QW_i^Q,KW_i^K,VW_i^V)
$$

$$Q，V，K$$先进入到线性层，投影到比较低的维度，然后做一个Scaled Dot-Product Attention,做h次，h次学到不同的模式匹配，模拟在卷积里面多个输出通道。

假如长为n的句子输入，我们有n 个长为 d 的向量。three input as the Key, Value, Query, so that called the self attention, 输出就是value的加权和，权重就是来自于query和Key（来自于本身，以及跟其他向量的相似度）。编码器的输出作为value和key进入，解码器的输出作为query进入，根据在解码器输入的不一样，根据当前向量，在编码器里给感兴趣的东西更多的权重，即注意力机制(对输入做加权和，提取出有用的信息，进行aggregation汇聚)。

### **Position-wise Feed-Forward Networks**

就是一个全连接的前馈网络，MLP，对每个词作用一次MLP（FCN+activation function），因为前面的输入已经包含的序列信息，在最后的映射到更理想的语义空间的时候，可以单独进行。

### **Embedding**

#### **Positional Encoding**

Attention 没有时序信息，RNN是通过上一个时刻的输出作为下一个时刻的输入，Attenion是通过在输入里面加入时序信息，
