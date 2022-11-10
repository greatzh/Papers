---
description: 'EfficientNet: Rethinking Model Scaling for Convolutional Neural Networks'
---

# EfficientNet

_Mingxing Tan and Quoc V Le. 2019. EfficientNet: Rethinking Model Scaling for Convolutional Neural Networks. Arxiv (2019). DOI:https://doi.org/10.48550/arxiv.1905.11946_

最主要的就是快，模型小，而且还维持了比较好的结果；不像一般的卷积不断去堆深度，广度，或者解析度之类的来消耗大量的计算资源达到更好的结果；而是对深度，广度，分辨率进行全部的协调，合成系数？平衡网络的宽度、深度和分辨率，让推理更快。最后就是提出了一个简单而高效的复合扩展方法 compound scaling method，再根据这个方法提出了一个模型，EfficientNet。

<figure><img src="https://s2.loli.net/2022/08/29/E5XhPnJc9y7QpAD.png" alt=""><figcaption></figcaption></figure>

### **提出的概念**

如上图中（e）所示，就是用一些固定的参数，同时对宽度，深度，解析度进行放大，这个固定的参数通过对原先的模型进行一个小的网格搜索来确定。

### **具体的方法**

首先定义一个卷积神经网络可以是：

$$
\mathcal{N}=\bigodot_{i=1...s}F^{L_i}_i(X_{<H_i,W_i,C_i>})
$$

然后目标是保持模型结构不变，调整网络每一层的长度和宽度以及解析度（向量的长宽），然后就是一个优化问题，通过最大化模型的准确率，找出对所有网络层进行缩放的这些参数。

$$
max_{d,w,r} \quad Accuracy(\mathcal{N}(depth,width,resolution)) \\ s.t. \quad \mathcal{N}(d,w,r)=\bigodot_{i=1...s}\hat{\mathcal{F}}^{d.\hat{L}_i}_i(X_{<r.\hat{H}_i,r.\hat{W}_i,w.\hat{C}_i>})
$$

深度：公认的就是越深提取到的特征就越多，但是容易出现梯度爆炸的问题，也有一些方法像skip connection，batch normalization

宽度：一般就是为了更小的模型。

分辨率：分辨率越高，特征越细节，精细度越高。

作者想要提出者方法是因为观察的问题：

1. 放大网络的$$d,w,r$$这三个参数去提高准确率，有时候会因为更大的模型而导致准确度下降。
2. 单独对这 $$d,w,r$$三个参数去改变，以及同时改变会有不同的结果。
3. 这些问题，发现前人已经有人做了，但是前人的方法是任意的对 $$d,w,r$$ 去改变。

所以提出了一种新的复合的方法，用一个复合系数 $$\phi$$统一对  $$d,w,r$$去进行均匀的缩放。具体的方法就是：

depth: d=$$\alpha^{\phi}$$

width: w=$$\beta^{\phi}$$

resolution: r=$$\gamma^{\phi}$$

$$
s.t. \alpha \cdot \beta^2 \cdot \gamma^2 \approx 2 \qquad $\alpha \ge 1, \beta \ge 1, \gamma \ge 1
$$

### GitHub

keras / TensorFlow + Keras: [https://github.com/qubvel/efficientnet](https://github.com/qubvel/efficientnet)

PyTorch: [https://github.com/lukemelas/EfficientNet-PyTorch](https://github.com/lukemelas/EfficientNet-PyTorch)
