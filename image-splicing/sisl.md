---
description: >-
  SISL:Self-Supervised Image Signature Learning for Splicing Detection and
  Localization
---

# SISL

> Susmit Agrawal, Prabhat Kumar, Siddharth Seth, Toufiq Parag, Maneesh Singh, and Venkatesh Babu. 2022. SISL:Self-Supervised Image Signature Learning for Splicing Detection & Localization. _2022 Ieee Cvf Conf Comput Vis Pattern Recognit Work Cvprw_ 00, (2022), 22–32. DOI:https://doi.org/10.1109/cvprw56347.2022.00012

## 论文摘要

现阶段的一些篡改检测的算法，都需要对图片进行大量的标注，包括一些图片的元数据，设备id等；同时，在社交媒体网络上的图片往往也会自动抹掉元数据；因此相关数据集的缺乏以及标注的繁琐，包括带标注数据训练带来的在real world的鲁棒性问题；作者提出了一个自监督的算法，不需要大量的GT或者图片的元数据，从图片的频率转换（FT，频率变换很大程度上舍弃了空间和语义信息，但是保留了检测源或村该特征所需要的重要信息。）里面进行训练，通过强制图像自一致性来学习新的特征（潜在表征 latent representation）表示形式以捕捉图像的特定的信号，来实现图像拼接篡改检测。

作者在介绍和相关工作里面阐述了图像处理的现状，图像取证的重要性；提到了最近的一些使用神经网络的方法需要大量数据集和标注数据，这种监督学习对篡改的多样性是不匹配的，很难保证在实际数据上的鲁棒性；同时提到了一些使用了FT信息的方法，通过生成模型的篡改图片，但没有报告人工篡改图片的性能。相关工作里面提到了 1. 利用CNN的图像篡改方法；2. 根据设备信息做检测；3. 频率域；4. 人工伪造图像及其检测，用GAN生成的图片容易检测等问题；5. 自监督学习

## 方法

给定一张图像的两个图像块（patches）的频率变换，通过从频率域上学习图像特定的签名，来识别篡改的痕迹，利用CNN和对比损失（来自SimCLR）去学习它们是否来自相同或者不同的图片，同时应用基于均值漂移的聚类算法和所学习到的潜在特征的余弦相似性将真实的和篡改的图像块进行分组，实现自我监督训练。

![image-20230309013836269](https://s2.loli.net/2023/03/09/QDsnb7NoMtZ3h6w.png)

如图所示，所提出的从图像块的RFFT信息进行训练的自监督网络，图像对$\{p_1^1,p_2^1\}$和$\{p_1^2,p_2^2\}$是分别来自图像$I^1$和$I^2$，将绿色和棕色分别叠加在他们各自的RFFT$\{f_1^1,f_2^1\}$和$\{f_1^2,f_2^2\}$上，以区分两个图像，相同颜色的不同阴影则是用来区别同一张图片的不同图像块。而对比损失，是根据骨干网络$g$和映射网络$h$所学习到的特征表示进行计算。

### Self-supervised Signature Learning

将图像块的离散傅里叶变换（Discrete Fourier Transform）信息作为CNN的输入，对图像的DFT的计算，利用的是PyTorch的real valued fast Fourier transform (RFFT) 实数快速傅里叶变换算法，它可以移除在实数输入的幂谱（power spectrum）的对称值。高频系数通常也要比低频系数小得多。

正如上面的框架图所显示的，作者将$p_j^i$来表示图片$I^k$的第$j$个patch，然后将$p_j^i$的RFFT信息$f_j^k$输入到CNN模型里面，计算RFFT的方法
$$
f_j^k(m,n)=\frac{1}{\sqrt{UV}}\sum^{U-1}_{u=0}\sum^{V-1}_{v=0}p_j^k(u,v)cos\{2\pi(\frac{mu}{U}+\frac{nu}{V})\} \\
m=0,1,...U-1,n=0,1,...,V-1,\\
where\quad U,V =dimensions\quad of\quad p_j^k
$$
RFFT的结果$f_j^k$就包含了每个像素位置$(m,n)$的不同基函数的系数，然后通过CNN的学习编码，将$f_j^k$信息进一步以$z_j^k$来表示，$z_j^k=h(g(f_j^k))$, 使的，来自同一张图片$k$的两个补丁块的$z_j^k$和$z_{j'}^k$相似度高，而来自不同的图片的相似度低。编码器$g$和投影器$h$代表的就是ResNet-18的主干和单个线性层。

基于此，训练的损失函数，也就定义为
$$
\phi^{kk'}_{jj'}=\frac{exp(sim(z^k_j,z^{k'}_{j'})/\tau)}{\sum^{B}_{\kappa}exp(sim(z^k_j,z^{k}_{j'})/\tau)} \\
L(\{f_j^k,f_{j'}^k\},y^{kk'})=-\sum^{B}_{k,k'=1}y^{kk'}log(\phi^{kk'}_{jj'})
$$
其中sim$(a,b)$表示的就是预先相似度，而$\tau$代表的是温度权重，每个从同一张图片计算得到的$\{f_j^k,f_{j'}^k\}$RFFTs对与指向向量$y^{kk'}$计算，当$k=k'$时，指向向量就为1，不相等就是0，损失函数就会鼓励来自同一张图像的隐特征表示$z_j^k$和$z_j^{k'}$相互相似，来自不同的就表示不同。

### Image Splicing Detection and Lacalization

训练之后，模型可以从图像块的RFFT信息上生成潜在特征表示，然后计算这些laten vectors之间的余弦相似度，可以计算得到每对图像块之间的相似性，最后，将这些相似性通过**均值漂移聚类**和**双线性上采样**的方法汇总到图像级别，生成一个响应热土，在这个响应热图钟，值为1的像素表示被篡改的区域。（从图像的局部块之间的相似性来计算像素级响应的方法）。根据得到的响应图，作者设计了两种方法，一种是**SpAvg**, 在空间上平均响应图，对平均后的响应图进行阈值处理来检测；一种是**PctArea**，通过创建一个二进制掩码图，对像素的百分比进行阈值处理，然后绘制拼接的区域。

## 实验

### 训练集

Dresden(16961 images), Vision (34427 images), Socrates (8742 images), FODB (23106 images), Kaggle (2750 images), 从这些数据集钟，对每张图片获得他们各自的任意的裁剪100个图像块来创建数据集，在训练的时候，随机选择256张图片，从同一张图片的100张预裁剪的图像块里面选择两个patches，来生成训练对的批次。

### 测试集

Columbia (363 images, 180 spliced), Carvalho/DSO (200 images, 100 spliced), Realistic Tampering (RT)/Korus (440 images, 220 spliced).

### 评估

作者提到了用一个固定的阈值来判断是否篡改在真实世界不理想，但是没有其他更实用的方法，所以在检测上对于所有的图片都用固定的**$\delta_b$**, 根据之前提到的对响应图的两种阈值处理方法，（**SpAvg**和**PctArea**），计算其AP；而对于所有有拼接篡改的图片使用固定的**$\delta_l$**来评估表现，计算他们的MCC(Matthew's coefficient)和IoU(Intersection over Union)。

### 结果

![image-20230309235945687](https://s2.loli.net/2023/03/10/NADwbeZiG7XgdmY.png)

在检测上的表现，作者选择了MantraNet，EXIF-SC, FG(Forensic Graph)这三个baseline进行比较，

![image-20230310000022689](https://s2.loli.net/2023/03/10/i73P9fBOFS6NmKZ.png)

在定位上的表现，

### 消融研究

1. 讨论了RFFT和RGB两种信息的作用，在融合了RFFT信息和RGB信息的模型里面，检测上面的表现，如下图所示，![image-20230310001513577](https://s2.loli.net/2023/03/10/LdgEGscmuUNaFXn.png)，融合了两个信息的模型表现的确好了一点，而关于定位上的表示，则比不上单独使用RFFT的模型。![image-20230310001712740](https://s2.loli.net/2023/03/10/tXcoCv61IrZnfuG.png)
2. 模型的变体，使用ResNet50，作者表示效果可能更好，但需要的成本模型大小会更大。

## 总结和展望

本文提出了一种有效的方法，利用图像的傅里叶变换（FT）自我监督地训练拼接检测/定位卷积神经网络。给定傅里叶变换，模型被设计为学习图像指纹，以识别来自不同图像的拼接区域。我们的实验表明，自我监督下训练的模型可以在不同基准测试上实现多个标准算法的准确性和速度。我们的发现不仅将在没有相机、图像元数据的情况下促进模型训练，而且可以扩展训练集以学习更强大的网络。我们希望我们的工作将鼓励进一步研究类似方向的鲁棒和可扩展的篡改检测技术。

无监督的篡改检测的确比较少见，数据集也够大，每张图片有100张预裁剪的patches，结果由于比较的方法较少，同时没有公开代码，网络结构上也比较简单，估计也是为了模型的大小，无监督的对比学习大概是一个方向。



