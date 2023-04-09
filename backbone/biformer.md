# BiFormer

> BiFormer: Vision Transformer with Bi-Level Routing Attention

<img src="https://s2.loli.net/2023/04/01/dUeFPrIaXg8mZEK.png" alt="image-20230401160002020"  />

## 摘要

attention是[ViT](vit.md)里面起到重要作用的工具，用来捕获长距离依赖，（之前可能用RNN去处理长距离依赖）；但是注意力机制也带了很大的计算开销，需要占用大量内存来进行计算。一些方法也被提出来降低注意力机制的算力要求，主要是将和内容无关的稀疏性引入到注意力中，像一些局部稀疏化注意力机制的方法，axial stripes，dilated windows等。

和这些方法不同，作者提出的

## 介绍

### axial stripes

将注意力权重限制在沿着输入张量的不同轴向形成的条纹区域，这样可以减少注意力权重的数量，从而降低计算量。

### dilated Windows

通过使用dilated convolution 膨胀卷积来扩大注意力操作的视野，以减少注意力权重的数量和计算量，膨胀卷积