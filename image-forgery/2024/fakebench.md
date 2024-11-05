# FakeBench

![image-20241027170055242](https://s2.loli.net/2024/10/27/ioRJIBfF4H8Z9CV.png)

> Li, Y., Liu, X., Wang, X., Lee, B. S., Wang, S., Rocha, A., & Lin, W. (2024). FakeBench: Probing Explainable Fake Image Detection via Large Multimodal Models. In arXiv.

代码链接：https://github.com/Yixuan423/FakeBench

文章提到现在的篡改检测方法只给出一个mask，对大众来说其实并不友好，在图像取证工作上不够有说服力；同时大语言模型对图像文本的处理能力却无法应用到篡改检测这样的任务中，于是作者从人类感知的角度提出了 FakeBench 这一包含文本真实性描述的多模态数据集。FakeBench 使用了人类参与的评估标准，检测、推理、解释和细粒度伪造分析来检验大语言模型，来获得对图像篡改检测能力更加深入的理解。作者也在不同的14个大语言模型，例如 GPT-4V，Q-Instruct、Gemini Pro、LLaVA-v1.5、Qwen-VL等模型上进行了实验，以阐释这项研究把图像篡改检测从黑盒子向更透明的方向转变的范式。

主要贡献:

1. 针对可解释性的图像取证评估，探索LLM对于检测、推理、解释和细粒度篡改分析的数据集。
2. 提出了一个针对生成篡改图片的细粒度分类方法，
3. 在14个大语言模型上进行实验，得到了关于模型表现，提示词，调优等影响的结果。

![image-20241029220624557](https://s2.loli.net/2024/10/29/C629Sn5ywBNjIe4.png)

与其他数据集的对比，可以看到FakeBench更多的关注还是deepfake以及AIGC等方面的篡改。

![image-20241029220745686](https://s2.loli.net/2024/10/29/9Jgwateo4svWuFN.png)

这张图也显示了FakeBench里面的图片详情，它里面的图片都是使用 ProGAN，StyleGAN，DALL.E2，Midjournery 等GAN、DM或者专门的方法生成了，也包含了人像，艺术作品，风景，数字简笔画等类别。

在FakeBench里面除了图片，作者是分成了 FakeClaskk，FakeClue和FakeQA 三个部分，分别对应作者提到了白盒取证里面的检测，因果调查和细粒度分析三个部分。
