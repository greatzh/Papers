# SAFIRE

SAFIRE: Segment Any Forged Image Region
Myung-Joon Kwon1\*, Wonjun Lee1\*, Seung-Hun Nam2, Minji Son1, Changick Kim1
1School of Electrical Engineering, Korea Advanced Institute of Science and Technology (KAIST)
2NAVER WEBTOON AI, Seongnam, South Korea
mjkwon2021@gmail.com, dpenguin@kaist.ac.kr, shnam1520@gmail.com, mjson0103@gmail.com, changick@kaist.ac.kr

> Kwon, M.-J., Lee, W., Nam, S.-H., Son, M., & Kim, C. (2024). SAFIRE: Segment Any Forged Image Region. In arXiv.

![image-20241225144330661](https://s2.loli.net/2024/12/25/3CxjGqVYeFszX4r.png)

作者将篡改图像按照源头进行分区这一更基础的方式来处理，而不是用二元分割的方式将真实区域标签0，篡改标签1。使用点提示 point prompt 的方法，图片上的每个点，都用于分割包括它自身的源区域，这样可以将图片分成多个不同源头的区域。如下图所示， SAFIRE 是将图片根据图片的来源进行分割，通过区域与区域的对比预训练来引导编码器可以高效地为源分区嵌入潜在的信号，通过训练以准确的预测源区域是否包含每个点，然后来判断一张图片是单独被拍摄的，还是 AI 生成的，或者是有其他图片参与进来的传统篡改。

![image-20241225150441928](https://s2.loli.net/2024/12/25/3EaNnHwYGTufC5p.png)

点提示的方法则是如下图所示，图片上的每一个点都分割了来自同一个源头的区域。关于 point prompt 的内容可以参考由 Meta AI 提出的 **SAM** 模型，与 SAM 不同的是，SAM 会分割点周围的任何有意义的部分，需要手动输入来指定点，且模糊处理真实值，而 SAFIRE 则是分割给定点的源区域，内部生成并使用点提示，有明确真实值。

![image-20241225222800704](https://s2.loli.net/2024/12/25/aSby7A2ViMgBNc1.png)