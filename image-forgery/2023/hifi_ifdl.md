# HIFI_IFDL

> Guo, X., Liu, X., Ren, Z., Grosz, S., Masi, I., & Liu, X. (2023). Hierarchical Fine-Grained Image Forgery Detection and Localization. IEEE/CVF Conference on Computer Vision and Pattern Recognition (CVPR).

*Hierarchical Fine-Grained Image Forgery Detection and Localization*

## 概要

作者提出了一种多层次细粒度的图像篡改检测和定位方法，它不仅仅针对传统的图像编辑技术带来的伪造，同时也对使用GAN或者Diffusion Model等方法的DeepFake篡改，都能起到作用，这是目前所提出的篡改检测的方法里面一个比较新的尝试。而为了实现能够同时用一套结构检测和定位两种大类型的伪造，作者重点介绍了用多个标签来表示图片的篡改类型，而篡改类型也以多个层次给出（四个），每一层对应篡改类型的每一个标签，同时层之间不是简单的铺平，作者也考虑到了之间的依赖关系，具体是像树的结构一样。作者表示对篡改类型的检测，是可以作为定位的先验知识，因为不同的篡改类型，往往会与它作用的伪造区域有关，所以对篡改类型进行分类是能起作用的。在本文中，作者对篡改类型的分类从第一层image-editing 和 CNN-synthesized两种大分类到第四层的具体某一种方法等多个标签类型。同时，针对要对两种伪造类型进行检测，作者设计了一个数据集，包含了传统篡改的和用deepfake进行篡改的大型数据集。

## 实现

### 篡改类型

首先，作者分析了不同的篡改类型与他们在图片里面的篡改区域的关系，如下图所示，不同的颜色代表不同的篡改类型，而y轴上代表的就是平均的篡改区域，泡泡的大小与伪造区域的方差成比例。而在用不同level的多标签来表示图片的篡改类型上，作者同样考虑到了不同层之间的依赖关系，这个依赖关系将有助于在最后一个level更准确的分类，而之前的粗粒度到细粒度的多层次分类大多是flat平坦的，各层之间是相互独立的结构。

![Distribution of forgery region depends on individual forgery methods](https://s2.loli.net/2023/04/30/KXomAUaMh6bEuLe.png)

![Forgery attribute of each manipulated image with multiple labels](https://s2.loli.net/2023/04/30/vhAmDEKtl74PujR.png)

作者设计了一个**多分支特征提取器**来学习图像不同解析度下的特征，得到每层的篡改类型分类结果，同时一个基于深度度量学习的目标函数用来生成篡改mask的**定位模块**和一个将定位得到的mask和输入的图片重叠得到的masked image再进行部分卷积学习IFDL的表示的**检测模块**，这三个部分共同组成了作者提出的**HiFi-Net**。为了能应对各种各样的篡改方法，作者也提出了一个数据集，这个数据集使用了多个篡改方法生成的篡改数据集，而每种伪造方法下的图片大概是10万张，在最后使用的数据集上，用来训练的图片是171万张，1.5万张的图片用来做validation，以及17.4万的图片用来做测试。

## 网络结构

![HiFi-Net Architechture](https://s2.loli.net/2023/05/05/MKTZ51zBvWbA6qV.png)

根据上面提到的HiFi-Net的三个部分，作者设计的框架如图所示，可以看到，同样也是从色彩域和频率域两个部分，在RGB域上，作者采用的是方法是和直接和[Iacopo Masi, et al, ECCV '20 ](https://arxiv.org/abs/2008.03412)一样的方法，即是在色彩域上使用普通的卷积，dense block等，然后在频率域上使用LoG(Laplacian of Gaussian) 高斯拉普拉斯算子来获取特征。

融合后的特征接下来去到设计的多分枝特征提取器，每一个分支是不同的解析度，如图所示，从下到上，Level 1到level 4，粗粒度到细粒度，而在最上面一个分支，即Level 4得到的特征图，将直接作为定位模块的先验知识。同时，在每一个分支，都会在最后输出对应的篡改类型，作者也解释了，篡改类型的分类，即了解不同的篡改放方法，是对定位有帮助的，因为不同的篡改方法，有着不同的伪造区域的分布，以及不同的样式。

而在定位模块上，可以看到则是将Level 4 的特征图作为输入，采用自注意力模块，将计算得到的空间注意力矩阵，转换到最后的全局特征图，再同[Iacopo Masi, et al, ECCV '20 ](https://arxiv.org/abs/2008.03412)一样，使用尺度学习目标函数，来产生一个更宽的边界，在真实的和篡改的像素之间；得到最后的mask。

![定位模块](https://s2.loli.net/2023/05/09/OiFZnMu7LR83zSY.png)

最后是分类模块，作者将定位模块取得的mask与输入图片再叠加，用作最后一个分支的分类输入，由于只有mask区域有RGB元素，所以先经过两次部分卷积，再和原分支的特征图结合用来进行篡改属性的分类。

## 实验与结果

在训练上，4个分支用4个损失函数进行优化，采用的损失函数是交叉熵距离，预测的类别和

### 数据集

![Detailed Datasets](https://s2.loli.net/2023/05/11/OcBKQzo7HCAJedf.png)

### Ablation

在这一部分，作者首先是对这三个分支的存在（约等于，通过控制Loss）以及作者使用的部分卷积进行了比较，如下图所示，讨论了包括分类Loss和定位Loss，以及只有定位，只有分类，或者只有最后一层（分支）的分类Loss，和没有多层次路径预测的分类Loss，以及最后的讨论了部分卷积的消融研究。

![Ablation study](https://s2.loli.net/2023/05/11/xr5mSuDa93ejX6A.png)

除此之外，作者还做了一些实验，用来验证篡改下面的Baseline是每次只在一个level上对属性进行分类，然后Multi-scale则是没有使用分层依赖的公式，就是四个分支之间没有通过公式联系起来，然后HiFinet就是最后的方法。通过渐进的方法来证明，其实作者提出的对篡改类型的分类是有效的。

![Forgery attribute classification result](https://s2.loli.net/2023/05/11/LwTCvP2XDUt9kAO.png)

### 结果

在传统图像编辑上的伪造检测上的结果对比：

![Result 1](https://s2.loli.net/2023/05/11/EfTbScoUFBxipr6.png)

在Diverse Fake Face Datasets，多种篡改人脸数据集上的结果，主要就是用styleGAN生成的了，

![Result 2](https://s2.loli.net/2023/05/11/TwDz2EjQ5uJgetL.png)

在作者自己的提出的数据集上的评估的结果，星号表示的是，在测试这个方法的时候，使用的是作者提供的预训练模型，而没有经过作者提出的数据集进行训练；不带星号就意味着有在作者提出的训练集上进行训练。

![Result 3](https://s2.loli.net/2023/05/11/KtxAYoR79LBgHGk.png)

所以无论是结果哪组结果，其实PSCC和作者的方法有得一拼，但是作者的结果大多已经到95%+的准确率。所以我可能觉得这个生成的数据集，是不是还是太容易被击败了，就是在数据集这个维度上比较的话，不比较方法，单从提出的数据集来说，我觉得应该要可以留下来给以后的方法作为一个benchmark一样，意思是，可能当前所有的方法都只能达到80%或者更低，同时，作者的方法又可以比其他方法更好，我以为这样才是证明了提出数据集有用，方法也好。

## 结论

这是一篇实验很充足的论文，论文为了验证自己提出来的多标签是有效的，以及涉及到对多标签的学习所用到的多层次细粒度结构，进行了大量的实验；同时我认为文章突出的一点在于，它将传统的image editing和现阶段的深度篡改，无论是人脸，是GAN生成还是Diffusion，都整合到用一个方法进行定位，为了实现这个目标，也是提出了一个庞大的数据集，而为了证明不是因为数据集的多样性带来的好结果，作者也用其他方法使用同样的数据集来进行训练，而结果同样比不上作者提出的HiFi-Net结构，来说明这个框架的创新性。

文章的出发点是，面对日益复杂的篡改方法（属性），一个“大一统”的检测定位方法的提出，显得非常有挑战；因此作者解决这个问题的方法就是去用多分支特征提取器分类不同的篡改类型，将分类结果作为一个先验知识，等等。

那作者说自己工作的限制是diffusion的inpainting篡改方法表现不好，再有就是数据集的问题，觉得应该再大一点。

所以，我觉得是不是用来做evaluation的数据集都太容易被defeat了，动不动就97%，是不是这些用来evaluation的数据集，要不就是太粗糙了，要不就是精细的已经太过时了，无论是针对传统的图像编辑技术，还是用深度学习生成的。

那针对这个方法，我觉得，好像没有讲清楚怎么把这个“篡改类型”分类后的多标签作为先验知识放到定位模块上来辅助得到更准确的mask；其他的是，如果这样真的有用，那再去优化这个网络是不是也可以。再有，这个定位模块感觉和整个网络剥离了一样。

我会怎么想现在deepfake这么火，怎么会还有人检测传统的图片编辑伪造呢；那可以问的就是，那现在AIGC这么火，为什么还在检测deepfake，当然deepfake在某称程度上大概和AIGC是重合的，还有一点是，在检测deepfake的算法里面，我们经常看到的数据集是什么，这是我在看Arxiv上面的一篇文章（[Discrepancy-Guided Reconstruction Learning for Image Forgery Detection](https://arxiv.org/abs/2304.13349)）里面的一张结果对比图，虽然论文的标题也是image forgery detection，但是比较的方法和对应的评估的数据集，可以看到其中[FF++HQ](https://arxiv.org/abs/1901.08971) ICCV 2019, [FF++LQ](https://arxiv.org/abs/1901.08971), [Celeb-DF](https://arxiv.org/abs/1909.12962) CVPR 2020, [WLD](https://arxiv.org/abs/2101.01456) MM 2020, [DFDC](https://arxiv.org/abs/2006.07397), 这四个数据集全部都是人脸，但是我们现实世界里面的篡改伪造绝对不是只在人脸上面进行伪造，包括像我最近看到的一篇论文，[Synthetic and Manipulated Overhead Imagery For Forensics Research](https://arxiv.org/abs/2305.05784), 这篇论文专门研究了俯瞰图片的篡改，篡改类型是inpainting，图像修复，image inpainting如下图所示。

![image-20230517204659840](https://s2.loli.net/2023/05/17/MBXfLHlxT7hESKw.png)

那除了人脸上的deepfake，现在我们有visual GPT，怎么去检测这些篡改，我的观点是，这些合成的图片，大多风格化比较严重，人眼一眼就能看出来图片是不是由AI生成的，他对社会的影响，远没有在文字上的篡改来的爆裂。就像下面一张，来自bing image creator官网的截图，这些由AI生成的图片一般不是用来取证的，作为证据的媒体，可能这方面的篡改，当然，他仍然在假信息传播上，是非常具有迷惑性的，所以我觉得这个问题还是需要去想想是否可以提炼出一个新的问题，新任务。

![image-20230519192110329](https://s2.loli.net/2023/05/19/uZphdPRJE9cm2KM.png)



![image-20230517203512325](https://s2.loli.net/2023/05/17/FXASovetxVpdnOM.png)

## GitHub

https://github.com/CHELSEA234/HiFi_IFDL
