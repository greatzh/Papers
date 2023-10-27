# CA-IFL

![image-20230709161518052](https://s2.loli.net/2023/07/09/mbMBa76d3N8WzAw.png)

> Wang, M., Fu, X., Liu, J., & Zha, Z.-J. (2022). JPEG Compression-aware Image Forgery Localization. Proceedings of the 30th ACM International Conference on Multimedia, 5871–5879. https://doi.org/10.1145/3503161.3547749

作者提出的问题是现有的方法在应对被JPEG压缩后的图片检测性能表现急剧下降，于是作者提出**基于小波压缩的特征学习**，通过小波集成对比学习来学习不同压缩等级的特征表示；再通过一个JPEG压缩感知的网络，来处理不同压缩等级的篡改图像，

![image-20230709175754558](https://s2.loli.net/2023/07/09/VPAXN85tQHsUku1.png)

![image-20230709175816340](https://s2.loli.net/2023/07/09/DoPhnWGtQVc5rjC.png)