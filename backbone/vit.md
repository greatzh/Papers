---
description: 'An Image is Worth 16x16 Words: Transformers for Image Recognition at Scale'
---

# ViT

_Alexey Dosovitskiy, Lucas Beyer, Alexander Kolesnikov, Dirk Weissenborn, Xiaohua Zhai, Thomas Unterthiner, Mostafa Dehghani, Matthias Minderer, Georg Heigold, Sylvain Gelly, Jakob Uszkoreit, and Neil Houlsby. 2020. An Image is Worth 16x16 Words: Transformers for Image Recognition at Scale. Arxiv (2020)._

<figure><img src="https://s2.loli.net/2022/04/05/9u7xBrQpFszTG63.png" alt=""><figcaption></figcaption></figure>

使用标准的transformer来完成cv任务，以固定大小的patch序列的方式来让计算机理解图片，与CNN相比，Transformer缺少了固有的归纳偏差不能在数据量不足的规模下做到很好的泛化。然而在大规模的数据集上预训练之后，Vision Transformer（**ViT**）在多个图像识别的基准上都表现优异，同时在大规模的数据集上训练之后，只需要很少的计算资源很快就可以在你需要分类的数据集上进行fine-tuned，并且达到比较好的效果。局限包括目前只在图像的分类上可能表现不错，但是其他计算机视觉任务，像是分割，检测，还有一些空间。还有自监督的与训练模型和大规模的监督预训练。

**归纳偏置**：类似于一种先验知识，一种提前做好的假设；对于CNN来说，一个是locality，因为CNN是以滑动窗口的形式在图片上进行卷积，所以假设相邻的区域有相邻的特征；另一个是平移等边性，translation equivalence，$$f(g(x))=g(f(x))$$，无论你先做卷积还是先平移，最后结果是不变的。但是对于**ViT**来说没有这种假设，但是大规模的数据训练胜过了inductive bias带来的效果。

### GitHub

[https://github.com/lucidrains/vit-pytorch](https://github.com/lucidrains/vit-pytorch)

[https://github.com/google-research/vision\_transformer](https://github.com/google-research/vision\_transformer)

[https://github.com/dk-liang/Awesome-Visual-Transformer](https://github.com/dk-liang/Awesome-Visual-Transformer)
