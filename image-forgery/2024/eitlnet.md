# EITLNet

![image-20241025100938723](https://s2.loli.net/2024/10/25/DjalEIcNUAwuKhm.png)

> Guo, K., Zhu, H., & Cao, G. (2024). Effective Image Tampering Localization Via Enhanced Transformer and Co-Attention Fusion. IEEE International Conference on Acoustics, Speech, and Signal Processing (ICASSP), abs/2309.09306, 4895–4899. https://doi.org/10.1109/ICASSP48485.2024.10446332

代码链接：https://github.com/multimediaFor/EITLNet

作者使用的依然是transformer的编码器结构，Segformer 的backbone，通过基于注意力的特征融合对transformer做了进一步增强。基于 Mix Transformer encoder Mit-B2，从 RGB 和 noise stream（先通过cw-hpf channel-wise high pass filter） 中提取的特征再增强之后，经过基于注意力的融合模块在多尺度进行特征的融合。与其他同类别的方法不同的是，作者指出其他结合两个特征的方法，大多在网络的前面或者后面，忽视了两个模态之间的交互，解码器中注意力模块也往往只在单一的尺度。作者设计了 FE feature enhancement 和 CAF coordinate attention-based fusion 两个模块，分别用来增强解码器的特征表示能力和在多尺度有效整合 RGB 和 noise 特征。

![image-20241025102852159](https://s2.loli.net/2024/10/25/LQHv9CcoeDaKuSG.png)

```python
class CoordAtt(nn.Module):
    def __init__(self, inp, oup,reduction=32):
        super(CoordAtt, self).__init__()
        self.pool_h = nn.AdaptiveAvgPool2d((None, 1))
        self.pool_w = nn.AdaptiveAvgPool2d((1, None))

        mip = max(8, inp // reduction)

        self.conv1 = nn.Conv2d(inp*2, mip, kernel_size=1, stride=1, padding=0)
        self.bn1 = nn.BatchNorm2d(mip)
        self.act = h_swish()

        self.conv_h = nn.Conv2d(mip, oup*2, kernel_size=1, stride=1, padding=0)
        self.conv_w = nn.Conv2d(mip, oup*2, kernel_size=1, stride=1, padding=0)


    def forward(self, x):
        identity = x

        n, c, h, w = x.size()
        x_h = self.pool_h(x)
        x_w = self.pool_w(x).permute(0, 1, 3, 2)

        y = torch.cat([x_h, x_w], dim=2)
        y = self.conv1(y)
        y = self.bn1(y)
        y = self.act(y)

        x_h, x_w = torch.split(y, [h, w], dim=2)
        x_w = x_w.permute(0, 1, 3, 2)

        a_h = self.conv_h(x_h).sigmoid()
        a_w = self.conv_w(x_w).sigmoid()

        out = identity * a_w * a_h

        return out
```

### Feature enhanced module





### Coordinate Attention-based Fusion Module





## 结果

![image-20241025103758595](https://s2.loli.net/2024/10/25/MYx9zPKHRshCQWk.png)

作者在 Columbia(2006) casiA-v1(2013) DSO(2013) NIST(2019) Coverage(2016) IMD(2020) 这些数据集上进行测试，与上述几个方法进行比较，都属于比较出色的表现。但这几个数据集都是比较老的数据集，不过除了Columbia 被打败了，其他的数据集的结果也确实还有很多提升的空间。我拿这个方法用在 CIMD 上提出的那个测试集去测试，发现结果也不如 CIMD 那篇论文报告的，不过那篇论文还没有公开代码。

而在ablation study上作者很好的证明了自己提出的两个模块，FE 和 CAF 是有作用的，虽然好像有没有 FE 提升不算特别明显。

除此之外，作者还针对鲁棒性评估做了一些实验，即将测试集的图片经过Facebook 微博 微信 WhatsApp四个社交媒体压缩后（压缩后的测试集是由此前的 OSN 工作提出），进一步评估其表现。

作者在介绍中表示一些非内容的篡改不影响语义信息，所以没有考虑jpeg 压缩、光照、高斯模糊等篡改操作。
