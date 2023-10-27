# ERMPC

![image-20230704154205953](https://s2.loli.net/2023/07/04/UvLZ4f78zQspcYV.png)

> Li, D., Zhu, J., Wang, M., Liu, J., Cao, C., & Zha, Z.-J. (2023). Edge-aware Regional Message Passing Controller for Image Forgery Localization. IEEE/CVF Conference on Computer Vision and Pattern Recognition (CVPR), 8222–8232.

作者提到由于已有的深度学习的方法在真实区域和伪造区域上，存在着严重的特征耦合问题，feature coupling；于是提出一个两步的边缘感知区域信息传递控制策略来解决这个问题， two step Edge-aware Regional Message Passing Control strategy。第一步就是通过上下文增强图，Context Enhanced Graph，CEG，和，threshold-adaptive differentiable binarization edge algorithm, 阈值适应性的可微调二值化边缘算法，来充分利用边缘信息。第二步就是根据可学习的边缘的指导，一个区域的信息传递用来阻挡真实和篡改区域之间的信息传递。作者也称自己是第一个将图论应用到篡改检测里面的方法，Graph based，边缘引导的图注意力模型。

## Method

![emprc-framework](https://s2.loli.net/2023/07/04/jkL1RimUIXFgsEt.png)

方法的重点是Regional Message Passing Controler，区域信息传递控制，的提出，用来防止真实和伪造区域的特征耦合，实现的方式就是一个动态图，和重构邻接矩阵的节点，来得到refined feature。



![ceg](https://s2.loli.net/2023/07/04/541rTdSRL23yjQJ.png)

而这个区域信息非常重要的就是边缘信息，所以为了获取边缘信息，作者设计了一个Edge Reconstruction ER模块，包括一个CEG和一个阈值适应性的可微调二值化边缘算法，算法的目的是为了提供可学习的边缘信息。