---
description: 'BusterNet: Detecting Copy-Move Image Forgery with Source/Target Localization'
---

# BusterNet

> Wu, Y., Abd-Almageed, W. & Natarajan, P. Computer Vision – ECCV 2018, 15th European Conference, Munich, Germany, September 8–14, 2018, Proceedings, Part VI. _Lect Notes Comput Sc_ 170–186 (2018) doi:10.1007/978-3-030-01231-1\_11.

<figure><img src="https://s2.loli.net/2022/04/26/Ny6dD4xfWJ7gZ5S.gif" alt=""><figcaption></figcaption></figure>

<figure><img src="https://s2.loli.net/2022/04/26/sQmheUDk14cEuiG.png" alt=""><figcaption></figcaption></figure>

首次提出了检测和定位的操作，作为一个新的feature，提供了可以生成大量数据集的方法，提出了使用深度神经网络的结构，构建端到端的模型，通过visual artifacts和visual similarities两个模块分别定位潜在的篡改区域和copy-move的区域。一个是Mani-net，一个是Simi-net，最后做一个Fusion。

### **传统方法有哪些不好**

* 分为三个步骤，首先是feature extraction，然后是feature matching，最后是post-processing，根据提取特征以及匹配特征的方法可以分为不同的种类，patch based，block based，key-point based.
* 分别有各自的缺点，block的计算量很大，关键点的计算量小了，但是容易在S和D同质的时候失败。（homogenous）
* 概括来说，就是每个模块之间是独立优化的，前面提取到的好的特征或许不能在下一个步骤中同样发挥好的效果，包含了一些启发式或手动调整的阈值，这样来减少错误的报告可能也不太好。

#### ## Details

* 端到端的结构可以不用手动的去调整参数，模块之间也有联系了。
*   **Manipulation Detection Branch(Mani-Net)**

    用VGG16首先提取特征，然后丢到Inception-based mask Deconvolution module。由于VGG16得到的解析度太小了，作者重新编码了特征，使用包括了BN-Inception和BilinearUpPool2D的Mask Decoder来生成新的tensor，整个这个过程也可以说是deconvolution。然后进行预测篡改的mask，作者用的是Binary Classifier，就是一个简单的二维卷积，然后一个sigmiod的激活函数。
*   **Similarity Detection Branch(Simi-Net)**

    通过一个Self-Correlation Module来计算特征的相似度，通过Percentile pooling（百分位汇集）来收集有用的信息。

    *   Self-Correlation:

        use the _Pearson correlation coefficient_ (皮尔逊相关系数\rho )来获取两个可能相似的特征patch之间的相似度高低。$$f_m^X[i] and f_m^X[j]$$

        $$\rho(i,j)=(\tilde{f}_m^X[i])^T \tilde{f}_m^X[j]/512$$

        $$\tilde{f}_m^X[i]=(f_m^X[i]-\mu_m^X[i])/\sigma_m^X[i]$$

        最后的final result就是

        $$S^X[i]=[\rho(i,0),...,\rho(i,j),...,\rho(i,255)]$$

        当皮尔逊系数$$\rho$$ 和$$f_m^X$$ 都有意义的时候，我们说如果$$f_m^X[i]$$ 是匹配的，当$$S^X[i][j]$$比剩下的分数大很多的时候。
    *   Percentile Pooling

        首先做一个分类，然后，

        $$S'^X[i]=sort(S^X[i])$$

        $$P^X[i][k]=S'^X[i][k'] where k'=round(p_k.(L-1)) and p_k\in[0,1]$$
*   **Fusion**

    concatenate这两个分支的特征，然后用BN-Inception融合，最后去预测用卷积神经网络。

#### Other

precision, recall, and $$F_1$$

TP, FP, FN, ROC， AUC，TPR，FPR，

有不同的计算协议，

作了一些鲁棒性的分析，检测是否能应对各种各样的后处理或者说攻击，直接两百张图片测试一下谁的更多。。。只要F\_1的分数高过0.5，就算一分。

只在最后评估了以下定位的准确率，

### Github

Keras + TF: [https://github.com/isi-vista/BusterNet](https://github.com/isi-vista/BusterNet)

PyTorch: [https://github.com/ntdat017/BusterNet\_pytorch](https://github.com/ntdat017/BusterNet\_pytorch)

### Other

[Improved BusterNet](cmsdnet.md)
