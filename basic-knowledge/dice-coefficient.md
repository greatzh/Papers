---
description: Dice 系数
---

# Dice coefficient

也是分割任务里面的一个评价标准，**Dice系数**，也是一种集合相似度度量指标，通常用于计算两个样本的相似度，值域\[0, 1], 分割结果最好的时候是1，最差的时候值为0。dice = 2\*Intersection / Union, 也就是2倍的交集除以并集，两倍预测正确的结果除以真实结果和预测结果的和，通常加smooth是为了防止除0情况的发生。

$$
s = \frac{2|X \cap Y|}{|X|+|Y|}=\frac{2\Theta_{TP}}{2\Theta_{TP}+\Theta_{FP}+\Theta_{FN}}=\frac{2\Theta_{TP}}{2\Theta_{TP}+\Theta_{AE}}
$$

$$X$$ 待评估图像（预测图像）

$$Y$$ 参考图像

$$\Theta_{TP}$$ 正阳性样本的数量，即是$$X$$ 和 $$Y$$ 都为真的位置的数量。

$$\Theta_{FP}$$ $$X$$中为真，但是$$Y$$中为假的位置的数量；即预测为正样本，但实际是负样本。

$$\Theta_{FN}$$ $$X$$中为假，而$$Y$$中为真的位置的数量；即预测为负样本，但事实上是正样本

$$\Theta_{AE}=\Theta_{FP}+\Theta{FN}$$ $$X$$和$$Y$$不一致的位置的数量。

## **Dice 变体**

### **Hard Dice score for binary segmentation**

即上面提到的。

### **Soft Dice score for binary segmentation**

### **Soft multi-class dice score**

### **Soft muti-class wassertstein dice score**

## **分割任务的其他评价指标**

### **PA**

图像共有k+1类，$$P_{ii}$$表示将第i类分成第i类的像素数量（即正确分类的像素数量）

$$
PA = \frac{\sum_{i=0}^kp_{ii}}{\sum_{i=0}^k\sum_{j=0}^kp_{ij}}
$$

### **MPA**

计算每类各自分类的准确率，再平均

$$
MPA = \frac{1}{k+1}\sum_{i=0}^k\frac{p_{ii}}{\sum_{j=0}^kp_{ij}}
$$

### **MIoU**

$$
MIoU=\frac{1}{k+1}\sum_{i=0}^k\frac{p_{ii}}{\sum_{j=0}^kp_{ij}+\sum_{j=0}^kp_{ji}-p_{ii}}
$$

### **FWIoU**

$$
FWIoU=\frac{1}{\sum_{i=0}^k\sum_{j=0}^kp_{ij}}\sum_{i=0}^k\frac{\sum_{j=0}^kp_{ij}p_{ii}}{\sum_{j=0}^kp_{ij}+\sum_{j=0}^kp_{ji}-p_{ii}}
$$

## **Cross entropy loss or Dice-coefficient loss**

在训练像素分割的神经网络时，如 FCN，如何选择交叉熵损失函数还是 Dice-coefficient 损失函数？

## 参考资料

1. [Dice Score](https://www.yuque.com/lart/idh721/gpix1i)
2. [Dice-coefficient loss function vs cross-entropy](https://stats.stackexchange.com/questions/321460/dice-coefficient-loss-function-vs-cross-entropy)
3. [医学图像分割之 Dice Loss](https://www.aiuai.cn/aifarm1159.html)
