# IF-OSN

![image-20230709181739556](https://s2.loli.net/2023/07/09/nKtT5Eb9RUeoPLk.png)

> Wu, H., Zhou, J., Tian, J., & Liu, J. (2022). Robust Image Forgery Detection Over Online Social Network Shared Images. IEEE/CVF Conference on Computer Vision and Pattern Recognition (CVPR), 13440–13449.

由于在社交网络上的对不同的不同损失情况，对一些篡改检测的方法带来了一些挑战，为了应对在线社交网络的图片压缩行为，作者提出的方法是一个噪声建模的方案，将模拟的噪声整合到一个训练框架中，整合的噪声有两个部分，第一部分是可预测的，像是JPEG压缩等带来的；第二部分是讨论不同的在线社交网络赋予的未知的噪声和在不同社交网络上训练测试带来的差异。但是第二部分的噪声无法从信号本身的角度建模处理，所以作者使用对抗噪声的概念来进行建模，其本质就是一些无法察觉的扰动对模型性能的影响。

![image-20230709181850189](https://s2.loli.net/2023/07/09/MDHBs2ZAcERXu7J.png)

![image-20230709213415691](https://s2.loli.net/2023/07/09/SUqalRE6TPFZwme.png)
