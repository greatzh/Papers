---
description: >-
  Deep learning papers notes sharing, especially for image forgery detection and
  localization
---

# 😀 Overview

> Newly added papers will be organized at the top of every category now.

### Related

* [Datasets Resources](related/datasets.md)
* [Nice Expression](related/nice-expressions.md)
* [Research Methods](related/howtodoresearch.md) (_public information summery_)
* [Paper Resource Links](related/papersource.md)

### Basics

* [图像处理基础知识](basic-knowledge/image-processing.md)

### Backbone

**骨干网络**，多为图像分类的网络。

* [x] [Attention Is All You Need](backbone/transformer.md) (_NeurIPS '17_) **\[**[**Paper**](https://proceedings.neurips.cc/paper/7181-attention-is-all)**]** **\[**[**Code\_official**](https://github.com/tensorflow/tensor2tensor/blob/master/tensor2tensor/models/transformer.py)**]** **\[**[**Code\_community**](https://github.com/jadore801120/attention-is-all-you-need-pytorch)**]**
* [x] [EfficientNet: Rethinking Model Scaling for Convolutional Neural Networks](backbone/efficientnet.md) (_ICML '19_) **\[**[**Paper**](https://arxiv.org/abs/1905.11946)**]** **\[**[**Code**](https://github.com/tensorflow/tpu/tree/master/models/official/efficientnet)**]**
* [x] [An Image is Worth 16x16 Words: Transformers for Image Recognition at Scale](backbone/vit.md) (_ICLR '21_) **\[**[**Paper**](https://arxiv.org/abs/2010.11929)**]** **\[**[**Code**](https://github.com/google-research/vision\_transformer)**]**
* [x] [Multi-Dimensional Model Compression of Vision Transformer](backbone/multi-dimensional-compression-vit.md) (_ICME '22_) **\[**[**Paper**](https://arxiv.org/abs/2201.00043)**]**
* [x] Deep Residual Learning for Image Recognition (_CVPR '16_) **\[**[**Paper**](https://arxiv.org/abs/1512.03385)**]**
* [ ] Generative Adversarial Networks (_NeurIPS '14_) **\[**[**Paper**](https://papers.nips.cc/paper/2014/hash/5ca3e9b122f61f8f06494c97b1afccf3-Abstract.html)**]**
* [ ] Masked Auto-Encoders Meet Generative Adversarial Networks and Beyond (_CVPR '23_) **\[**[**Paper**](https://feizc.github.io/resume/ganmae.pdf)**]**
* [ ] A Kernel Perspective of Skip Connections in Convolutional Networks (_ICLR '23_) **\[**[**Paper**](https://arxiv.org/abs/2211.14810)**]**
* [ ] EfficientViT: Memory Efficient Vision Transformer with Cascaded Group Attention (_CVPR '23_) **\[**[**Paper**](https://arxiv.org/abs/2305.07027)**]** **\[**[**Code**](https://github.com/microsoft/Cream/tree/main/EfficientViT)**]** **\[**[**Note\_community**](https://blog.csdn.net/P\_LarT/article/details/130687567)**]**
* [ ] Vision Transformers Need Registers _(ICLR '24)_ **[[Paper](https://openreview.net/forum?id=2dnO3LLiJ1)]**

### Image Tampering

**图像篡改检测定位**

#### Image Editing

<details open>
<summary>2024</summary>

* [ ] Exploring Multi-Modal Fusion for Image Manipulation Detection and Localization _(MMM '24)_  [![arXiv](https://img.shields.io/badge/arXiv-b31b1b.svg)](https://arxiv.org/abs/2312.01790) [![GitHub](https://img.shields.io/github/stars/idt-iti/mmfusion-iml?style=flat)](https://github.com/idt-iti/mmfusion-iml)
* [ ] A New Benchmark and Model for Challenging Image Manipulation Detection _(AAAI '24)_ [![arXiv](https://img.shields.io/badge/arXiv-b31b1b.svg)](https://arxiv.org/abs/2311.14218)
* [ ] MGQFormer: Mask-Guided Query-Based Transformer for Image Manipulation Localization _(AAAI '24)_ [![arXiv](https://img.shields.io/badge/News-4096ff.svg)](https://dml.fudan.edu.cn/d1/65/c35285a643429/page.htm)
* [ ] Learning Discriminative Noise Guidance for Image Forgery Detection and Localization _(AAAI '24)_ 
* [ ] CatmullRom Splines-Based Regression for Image Forgery Localization _(AAAI '24)_ 
* [ ] UnionFormer: Unified-Learning Transformer with Multi-View Representation for Image Manipulation Detection and Localization _(CVPR '24)_  
* [ ] Towards Modern Image Manipulation Localization: A Large-Scale Dataset and Novel Methods _(CVPR '24)_  
* [ ] EditGuard: Versatile Image Watermarking for Tamper Localization and Copyright Protection _(CVPR '24)_   [![arXiv](https://img.shields.io/badge/arXiv-b31b1b.svg)](https://arxiv.org/abs/2312.08883) [![GitHub](https://img.shields.io/github/stars/xuanyuzhang21/EditGuard?style=flat)](https://github.com/xuanyuzhang21/EditGuard)
* [ ] DiffForensics: Leveraging Diffusion Prior to Image Forgery Detection and Localization _(CVPR '24)_ 
* [ ] IML-ViT: Image Manipulation Localization by Vision Transformer _(AAAI '24)_ [![arXiv](https://img.shields.io/badge/arXiv-b31b1b.svg)](https://arxiv.org/abs/2307.14863) [![GitHub](https://img.shields.io/github/stars/SunnyHaze/IML-ViT?style=flat)](https://github.com/SunnyHaze/IML-ViT)
* [ ] CIMGEN: Controlled Image Manipulation by Finetuning Pretrained Generative Models on Limited Data _(arXiv '24)_ [![arXiv](https://img.shields.io/badge/arXiv-b31b1b.svg)](https://arxiv.org/abs/2401.13006)

</details>

<details open>
<summary>2023</summary>

* [ ] PL-GNet: Pixel Level Global Network for detection and localization of image forgeries _(IMAGE '23)_ **[[Paper](https://www.sciencedirect.com/science/article/pii/S092359652300111X)]** **[[Code](https://github.com/znshi/PL-GNet)]**
* [ ] Pixel-Inconsistency Modeling for Image Manipulation Localization _(arXiv '23)_ **[[Paper](https://arxiv.org/abs/2310.00234)]**
* [ ] Progressive Feedback-Enhanced Transformer for Image Forgery Localization _(arXiv '23)_ **[[Paper](https://arxiv.org/abs/2311.08910)]** **[[Code(N/A)](https://github.com/multimediaFor/ProFact)]**
* [ ] Secondary Labeling  A Novel Labeling Strategy for Image Manipulation Detection _(MM '23)_ **[[Paper](https://doi.org/10.1145/3581783.3613839)]**
* [ ] GP-Net: Image Manipulation Detection and Localization via Long-Range Modeling and Transformers (_Appl. Sci.  (IF: 2.8, not included in CCFs), MDPI, '23_) **\[[Paper](https://www.mdpi.com/2076-3417/13/21/12053)]**
* [ ] DS-Net: Dual supervision neural network for image manipulation localization _(IET-IPR '23)_ **[[Paper](https://ietresearch.onlinelibrary.wiley.com/doi/abs/10.1049/ipr2.12885)]**
* [ ] Learning to Immunize Images for Tamper Localization and Self Recovery _(TPAMI ‘23)_ **[[Paper](https://arxiv.org/pdf/2210.15902.pdf)]** 
* [ ] Semantic-agnostic progressive subtractive network for image manipulation detection and localization _(Neurocomputing '23)_ **[[Paper](https://doi.org/10.1016/j.neucom.2023.126263)]**
* [ ] Towards Effective Image Manipulation Detection with Proposal Contrastive Learning _(TCSVT '23)_ **[[Paper](https://arxiv.org/pdf/2210.08529.pdf)]** **[[Code](https://github.com/Sandy-Zeng/PCL)]**
* [ ] Effective image tampering localization with multi-scale ConvNeXt feature fusion (_JVCIR '23)_ **\[**[**Paper**](https://arxiv.org/abs/2208.13739)**]** **[[Code](https://github.com/multimediaFor/ConvNeXtFF)]**
* [ ] Evading Detection Actively: Toward Anti-Forensics against Forgery Localization (_arXiv '23_) **\[**[**Paper**](https://arxiv.org/abs/2310.10036)**]** **\[**[**Code**](https://github.com/tansq/SEAR)**]**
* [ ] [ReLoc: A Restoration-Assisted Framework for Robust Image Tampering Localization](image-forgery/2023/reloc.md) (_TIFS '23_) **\[**[**Paper**](https://arxiv.org/abs/2211.03930)**]** **\[**[**Code**](https://github.com/ZhuangPeiyu/ReLoc)**]**
* [ ] Image manipulation detection by multiple tampering traces and edge artifact enhancement (_PR '23_) **\[**[**Paper**](https://www.sciencedirect.com/science/article/pii/S0031320322005064)**]** (_EMT-Net_)
* [x] [CFL-Net: Image Forgery Localization Using Contrastive Learning](image-forgery/2023/cfl-net.md) (_WACV '23_) **\[**[**Paper**](https://arxiv.org/abs/2210.02182)**]** **\[**[**Code**](https://github.com/niloy193/CFLNet)**]**
* [x] [TruFor: Leveraging all-round clues for trustworthy image forgery detection and localization](image-forgery/2023/trufor.md) (_CVPR '23_) **\[**[**Paper**](https://arxiv.org/abs/2212.10957)**]** **\[**[**Project**](https://grip-unina.github.io/TruFor/)**]** **\[**[**Code**](https://github.com/grip-unina/TruFor)**]**
* [x] [TBFormer: Two-Branch Transformer for Image Forgery Localization](image-forgery/2023/tbformer.md) (_SPL '23_) **\[**[**Paper**](https://arxiv.org/abs/2302.13004)**]** **\[**[**Code**](https://github.com/free1dom1/tbformer)**]**
* [ ] [Detecting and Grounding Multi-Modal Media Manipulation](image-forgery/2023/dgm4.md) (_CVPR '23_) **\[**[**Paper**](https://arxiv.org/abs/2304.02556)**]** **\[**[**Code**](https://github.com/rshaojimmy/MultiModal-DeepFake)**]** **\[**[**Project**](https://rshaojimmy.github.io/Projects/MultiModal-DeepFake)**]**
* [x] [Hierarchical Fine-Grained Image Forgery Detection and Localization](image-forgery/2023/hifi\_ifdl.md) (_CVPR '23_) **\[**[**Paper**](https://arxiv.org/abs/2303.17111)**]** **\[**[**Code**](https://github.com/CHELSEA234/HiFi\_IFDL)**]**
* [ ] [Edge-aware Regional Message Passing Controller for Image Forgery Localization](image-forgery/2023/ermpc.md) (_CVPR '23_) **\[**[**Paper**](https://openaccess.thecvf.com/content/CVPR2023/papers/Li\_Edge-Aware\_Regional\_Message\_Passing\_Controller\_for\_Image\_Forgery\_Localization\_CVPR\_2023\_paper.pdf)**]** **\[**[**Video**](https://youtu.be/2pDR-hOFcQw)**]**
* [ ] AutoSplice: A Text-prompt Manipulated Image Dataset for Media Forensics (_CVPRW '23_) **\[**[**Paper**](https://arxiv.org/abs/2304.06870)**]** **\[**[**Dataset**](https://github.com/shanface33/autosplice\_dataset)**]**
* [ ] CTP-Net: Character Texture Perception Network for Document Image Forgery Localization (_arXiv '23_) **\[**[**Paper**](https://arxiv.org/abs/2308.02158v1)**]**
* [ ] TrainFors: A Large Benchmark Training Dataset for Image Manipulation Detection and Localization (_ICCV '23_) **\[**[**Paper**](https://arxiv.org/abs/2308.05264)**]** **\[**[**Code**](https://github.com/vimal-isi-edu/TrainFors)**]**
* [ ] Pre-training-free Image Manipulation Localization through Non-Mutually Exclusive Contrastive Learning (_ICCV '23_) **\[**[**Paper**](https://openaccess.thecvf.com/content/ICCV2023/html/Zhou\_Pre-Training-Free\_Image\_Manipulation\_Localization\_through\_Non-Mutually\_Exclusive\_Contrastive\_Learning\_ICCV\_2023\_paper.html)**]** **\[**[**Code**](https://github.com/Knightzjz/NCL-IML)**]**
* [ ] Towards Generic Image Manipulation Detection with Weakly-Supervised Self-Consistency Learning (_ICCV '23_) **\[**[**Paper**](https://openaccess.thecvf.com/content/ICCV2023/html/Zhai\_Towards\_Generic\_Image\_Manipulation\_Detection\_with\_Weakly-Supervised\_Self-Consistency\_Learning\_ICCV\_2023\_paper.html)**]** **\[**[**Code**](https://github.com/yhZhai/WSCL)**]** **\[**[**ResearchGate**](https://www.researchgate.net/publication/373686108\_Towards\_Generic\_Image\_Manipulation\_Detection\_with\_Weakly-Supervised\_Self-Consistency\_Learning)**]**
* [ ] SAFL-Net: Semantic-Agnostic Feature Learning Network with Auxiliary Plugins for Image Manipulation Detection (_ICCV '23_) **\[**[**Paper**](https://openaccess.thecvf.com/content/ICCV2023/html/Sun\_SAFL-Net\_Semantic-Agnostic\_Feature\_Learning\_Network\_with\_Auxiliary\_Plugins\_for\_Image\_ICCV\_2023\_paper.html)**]**
* [ ] Uncertainty-guided Learning for Improving Image Manipulation Detection (_ICCV '23_) **\[**[**Paper**](https://openaccess.thecvf.com/content/ICCV2023/html/Ji\_Uncertainty-guided\_Learning\_for\_Improving\_Image\_Manipulation\_Detection\_ICCV\_2023\_paper.html)**]**
* [ ] Rethinking Image Forgery Detection via Contrastive Learning and Unsupervised Clustering (_arXiv '23_) **\[**[**Paper**](https://arxiv.org/abs/2308.09307)**]** **\[**[**Code**](https://github.com/HighwayWu/FOCAL)**]**
* [ ] Pixel-Inconsistency Modeling for Image Manipulation Localization (_arXiv '23_) **\[**[**Paper**](https://arxiv.org/abs/2310.00234)**]**
* [ ] Perceptual MAE for Image Manipulation Localization: A High-level Vision Learner Focusing on Low-level Features (_arXiv '23_) **\[**[**Paper**](https://arxiv.org/abs/2310.06525)**]**
* [ ] [On the Security of the One-and-a-Half-Class Classifier for SPAM Feature-Based Image Forensics](image-forgery/2023/spam\_analysis.md) (_TIFS '23_) **(Traditional method, Analysis)** **\[**[**Paper**](https://ieeexplore.ieee.org/abstract/document/10098583/)**]**

</details>

<details open>
<summary>2022</summary>

* [ ] DS-UNet: A dual streams UNet for refined image forgery localization _(InfoS '22)_ **[[Paper](https://dl.acm.org/doi/abs/10.1016/j.ins.2022.08.005)]**
* [ ] MSMG-Net: Multi-scale Multi-grained Supervised Metworks for Multi-task Image Manipulation Detection and Localization (_ArXiv '22_) **\[**[**Paper**](https://arxiv.org/abs/2211.03140)**]**
* [ ] Towards JPEG-Resistant Image Forgery Detection and Localization Via Self-Supervised Domain Adaptation (_TPAMI '22_) **\[**[**Paper**](https://ieeexplore.ieee.org/document/9904872)**]**
* [ ] ESRNet: Efficient Search and Recognition Network for Image Manipulation Detection (_TOMCCAP '22_) **\[**[**Paper**](https://doi.org/10.1145/3506853)**]** **\[**[**Tool**](https://github.com/tampered816/rrr)**]**
* [ ] Learning to localize image forgery using end-to-end attention network (_Neurocomputing '22_) **\[**[**Paper**](https://www.sciencedirect.com/science/article/pii/S0925231222011274)**]** **\[**[**Code**](https://github.com/sadaf-ali/-Learning-to-Localize-Image-Forgery-Using-End-to-End-Attention-Network)**]**
* [ ] MVSS-Net: Multi-View Multi-Scale Supervised Networks for Image Manipulation Detection (_TPAMI '22_) **\[**[**Paper**](https://arxiv.org/abs/2112.08935)**]** **\[**[**Code**](https://github.com/dong03/MVSS-Net)**]**
* [ ] [Robust Image Forgery Detection Over Online Social Network Shared Images](image-forgery/2022/ifosn.md) (_CVPR '22_) **\[**[**Paper**](https://openaccess.thecvf.com/content/CVPR2022/papers/Wu\_Robust\_Image\_Forgery\_Detection\_Over\_Online\_Social\_Network\_Shared\_Images\_CVPR\_2022\_paper.pdf)**]** **\[**[**Code**](https://github.com/HighwayWu/ImageForensicsOSN)**]**
* [x] [ObjectFormer for Image Manipulation Detection and Localization](image-forgery/2022/objectformer.md) (_CVPR '22_) **\[**[**Paper**](https://arxiv.org/abs/2203.14681)**]**
* [ ] GCA-Net: Utilizing Gated Context Attention for Improving Image Forgery Localization and Detection (_CVPRW '22_) **\[**[**Paper**](https://arxiv.org/abs/2112.04298)**]**
* [ ] Non-Semantic Evaluation of Image Forensics Tools: Methodology and Database (_WACV '22_) **\[**[**Paper**](https://arxiv.org/abs/2105.02700)**]** **\[**[**Code**](https://github.com/qbammey/trace)**]**
* [ ] [JPEG Compression-aware Image Forgery Localization](image-forgery/2022/caifl.md) (_MM '22_) **\[**[**Paper**](https://dl.acm.org/doi/abs/10.1145/3503161.3547749)**]**
* [ ] [Image Manipulation Localization Using Multi-Scale Feature Fusion and Adaptive Edge Supervision](image-forgery/2022/msff.md) (_TMM '22_) **\[**[**Paper**](https://ieeexplore.ieee.org/document/9996125/)**]**
* [x] [PSCC-Net: Progressive Spatio-Channel Correlation Network for Image Manipulation Detection and Localization](image-forgery/2022/pscc-net.md) (_TCSVT '22_) **\[**[**Paper**](https://arxiv.org/abs/2103.10596)**]** **\[**[**Code**](https://github.com/proteus1991/PSCC-Net)**]**
* [x] [Self-Adversarial Training incorporating Forgery Attention for Image Forgery Localization](image-forgery/2022/satfl.md) (_TIFS '22_) **\[**[**Paper**](https://arxiv.org/abs/2107.02434)**]** **\[**[**Code**](https://github.com/tansq/SATFL)**]** (_LocateNet / SATFL_)
* [ ] M2TR: Multi-modal Multi-scale Transformers for Deepfake Detection (_ICMR '22_) **\[**[**Paper**](https://arxiv.org/abs/2104.09770)**]** **\[**[**Code**](https://github.com/wangjk666/M2TR-Multi-modal-Multi-scale-Transformers-for-Deepfake-Detection)**]**
* [ ] A Principled Design of Image Representation: Towards Forensic Tasks (_TPAMI '22_) **\[**[**Paper**](https://arxiv.org/abs/2203.00913)**]** **\[**[**Code**](https://github.com/ShurenQi/DIR)**]**
* [ ] [TBNet: A Two-stream Boundary-aware Network for Generic Image Manipulation Localization](image-forgery/2022/tbanet.md) (_KDE '22_) **\[**[**Paper**](https://arxiv.org/abs/2108.04508)**]**
* [ ] [Learning JPEG Compression Artifacts for Image Manipulation Detection and Localization](image-forgery/2022/catnetv2.md) (_IJCV '22_) **\[**[**Paper**](https://arxiv.org/abs/2108.12947)**]** **\[**[**Code**](https://github.com/mjkwon2021/CAT-Net)**]**
* [ ] Fighting Malicious Media Data: A Survey on Tampering Detection and Deepfake Detection (_arXiv '22_) (**Survey**) **\[**[**Paper**](https://arxiv.org/abs/2212.05667)**]**

</details>

<details>
<summary>2021</summary>

* [ ] MSTA-Net: Forgery Detection by Generating Manipulation Trace Based on Multi-Scale Self-Texture Attention (_TCSVT '21_) **\[**[**Paper**](https://ieeexplore.ieee.org/document/9643421)**]**
* [ ] Image Manipulation Detection by Multi-View Multi-Scale Supervision (_ICCV '21_) **\[**[**Paper**](https://arxiv.org/abs/2104.06832)**]** **\[**[**Code**](https://github.com/dong03/MVSS-Net)**]**
* [x] [TransForensics: Image Forgery Localization with Dense Self-Attention](image-forgery/2021/transforensics.md) (_ICCV '21_) **\[**[**Paper**](https://arxiv.org/abs/2108.03871)**]**
* [ ] Self-supervised Domain Adaptation for Forgery Localization of JPEG Compressed Images (_ICCV '21_) **\[**[**Paper**](https://openaccess.thecvf.com/content/ICCV2021/html/Rao\_Self-Supervised\_Domain\_Adaptation\_for\_Forgery\_Localization\_of\_JPEG\_Compressed\_Images\_ICCV\_2021\_paper.html)**]**
* [ ] Image Tampering Localization Using a Dense Fully Convolutional Network (_TIFS '21_) **\[**[**Paper**](https://ieeexplore.ieee.org/document/9393396)**]** **\[**[**Code**](https://github.com/ZhuangPeiyu/Dense-FCN-for-tampering-localization)**]** (_DenseFCN_)
* [ ] Image Manipulation Localization Using Attentional Cross-Domain CNN Features (_TNNLS '21_) **\[**[**Paper**](https://doi.org/10.1109/TNNLS.2021.3130168)**]**

</details>

<details>
<summary>2020 and before</summary>

* [ ] A Full-Image Full-Resolution End-to-EndTrainable CNN Framework for Image Forgery Detection (_IEEE Access '20_) \*\*\[[Paper](./)]
* [ ]  ![ConfnPubs](https://img.shields.io/badge/ICME-'20-ffc53d.svg)Constrained R-CNN: A general image manipulation detection model **\[**[**Paper**](https://arxiv.org/abs/1911.08217)**]** **\[**[**Code**](https://github.com/VedantWani/Constrained-R-CNN)**]**
* [ ] A CNNBased Camera Model Fingerprint (_TIFS '20_) \*\*\[[Paper](./)]
* [ ] An Adaptive Neural Network for Unsupervised Mosaic Consistency Analysis in Image Forensics (_CVPR '20_) **\[**[**Paper**](http://openaccess.thecvf.com/content\_CVPR\_2020/html/Bammey\_An\_Adaptive\_Neural\_Network\_for\_Unsupervised\_Mosaic\_Consistency\_Analysis\_in\_CVPR\_2020\_paper.html)**]** **\[**[**Code**](https://github.com/qbammey/adaptive\_cfa\_forensics)**]**
* [ ] A dense u-net with cross-layer intersection for detection and localization of image forgery (_ICASSP '20_) **\[**[**Paper**](https://ieeexplore.ieee.org/document/9054068)**]** **\[**[**Note\_unofficial**](https://blog.csdn.net/weixin\_45366180/article/details/128413821)**]**
* [x] [Generate, Segment, and Refine: Towards Generic Manipulation Segmentation](image-forgery/2020/gsrnet.md) (_AAAI '20_) **\[**[**Paper**](https://arxiv.org/abs/1811.09729)**]** **\[**[**Code**](https://github.com/pengzhou1108/GSRNet)**]** (_GSRNet_)
* [ ] SPAN: Spatial Pyramid Attention Network for Image Manipulation Localization (_ECCV '20_) **\[**[**Paper**](https://www.ecva.net/papers/eccv\_2020/papers\_ECCV/papers/123660307.pdf)**]** **\[**[**Code**](https://github.com/tsaishien-chen/SPAN)**]**  [![GitHub Page](https://img.shields.io/badge/Project-Page-159957.svg)](http://media.ee.ntu.edu.tw/research/SPAN/) 
* [ ] [Hybrid LSTM and Encoder-Decoder Architecture for Detection of Image Forgeries](image-forgery/2019/hled.md) (_TIP '19_) **\[**[**Paper**](https://arxiv.org/abs/1903.02495)**]** **\[**[**Code**](https://github.com/jawadbappy/forgery\_localization\_HLED)**]**
* [ ] ManTra-Net: Manipulation Tracing Network for Detection and Localization of Image Forgeries With Anomalous Features (_CVPR '19_) **\[**[**Paper**](https://ieeexplore.ieee.org/document/8953774)**]** **\[**[**Code**](https://github.com/ISICV/ManTraNet)**]**

</details>

#### CNN-synthesized

_Some of the above papers also contain methods to detect tampered images generated by GANs or DMs for synthetic images_

* [ ] Forgery-aware Adaptive Transformer for Generalizable Synthetic Image Detection _(CVPR '24)_ **[[Paper](https://arxiv.org/abs/2312.16649)]**
* [ ] Preserving Fairness Generalization in Deepfake Detection _(CVPR '24)_ **[[Paper](https://arxiv.org/abs/2402.17229)]** **[[Code](https://github.com/Purdue-M2/Fairness-Generalization)]**
* [ ] Leveraging Representations from Intermediate Encoder-blocks for Synthetic Image Detection _(arXiv '24)_ **[[Paper](https://arxiv.org/abs/2402.19091)]** **[[Code](https://github.com/mever-team/rine)]**
* [ ] Forgery-aware Adaptive Transformer for Generalizable Synthetic Image Detection _(arXiv '23)_ **[[Paper](https://arxiv.org/abs/2312.16649)]**
* [ ] AntifakePrompt: Prompt-Tuned Vision-Language Models are Fake Image Detectors (_arXiv '23_) **\[**[**Paper**](https://arxiv.org/abs/2310.17419)**]** **[[Code](https://github.com/nctu-eva-lab/AntifakePrompt)]**
* [ ] MaLP: Manipulation Localization Using a Proactive Scheme (_CVPR '23_) **\[**[**Paper**](https://arxiv.org/abs/2303.16976)**]** **\[**[**Code**](https://github.com/vishal3477/pro\_loc)**]**
* [ ] Discrepancy-Guided Reconstruction Learning for Image Forgery Detection (_IJCAI '23_) **\[**[**Paper**](https://arxiv.org/abs/2304.13349)**]** **\[**[**Code**](https://github.com/znshi/DisGRL)**]**
* [ ] Generalizable Synthetic Image Detection via Language-guided Contrastive Learning (_arXiv '23_) **\[**[**Paper**](https://arxiv.org/abs/2305.13800)**]** **\[**[**Code**](https://github.com/HighwayWu/LASTED)**]**
* [ ] Detect Any Deepfakes: Segment Anything Meets Face Forgery Detection and Localization (_arXiv '23_) **\[**[**Paper**](https://arxiv.org/abs/2306.17075)**]** **\[**[**Code**](https://github.com/laiyingxin2/DADF)**]**
* [ ] Discrepancy-Guided Reconstruction Learning for Image Forgery Detection (_arXiv '23_) **\[**[**Paper**](https://arxiv.org/abs/2304.13349)**]**
* [ ] Masked Relation Learning for DeepFake Detection (_TIFS '23_) **\[**[**Paper**](https://doi.org/10.1109/TIFS.2023.3249566)**]**

### Image Splicing

**图像的拼接篡改检测定位**

<details open>
<summary>2024</summary>

* [ ] Towards Effective Image Forensics via A Novel Computationally Efficient Framework and A New Image Splice Dataset _(arXiv '24)_ **[[Paper](https://arxiv.org/abs/2401.06998)]**

</details>

<details open>
<summary>2023</summary>

* [ ] GreatSplicing: A Semantically Rich Splicing Dataset _(arXiv '23)_ **[[Paper](https://arxiv.org/abs/2310.10070)]** **[[Dataset](http://www.greatsplicing.net/)]**
* [ ] Multi-scale attention context-aware network for detection and localization of image splicing: Efficient and robust identification network _(Appl. Intell. 23')_ **[[Paper](https://link.springer.com/article/10.1007/s10489-022-04421-3)]**
* [ ] A Multi-Stream Fusion Network for Image Splicing Localization _(MMM '23)_ **\[**[**Paper**](https://arxiv.org/abs/2212.01128)**]**
* [ ] Attacking Image Splicing Detection and Localization Algorithms Using Synthetic Traces _(TIFS '23)_ **\[**[**Paper**](https://arxiv.org/abs/2211.12314)**]** **[[IEEE Paper](https://doi.org/10.1109/TIFS.2023.3346312)]**
* [ ] Biomedical Image Splicing Detection using Uncertainty-Guided Refinement _(arXiv '23)_ **\[**[**Paper**](https://arxiv.org/abs/2309.16388)**]**
* [ ] A New Method to Detect Splicing Image Forgery Using Convolutional Neural Network (_Applied Science (IF: 2.8, not included in CCFs), MDPI, '23_) **\[**[**Paper**](https://www.mdpi.com/2076-3417/13/3/1272)**]**
* [ ] Multi-scale Target-Aware Framework for Constrained Image Splicing Detection and Localization (_MM '23_) **\[**[**Paper**](https://arxiv.org/abs/2308.09357)**]**

</details>

<details open>
<summary>2022</summary>

* [x] [Multi-Task SE-Network for Image Splicing Localization](image-splicing/multi-task-se-network.md) (_TCSVT '22_) **\[**[**Paper**](https://ieeexplore.ieee.org/document/9591639)**]** **\[**[**Code**](https://github.com/YulansZhang/Multi-task-SE-Network-for-Image-Splicing-Localization)**]**
* [x] [ET: Edge-Enhanced Transformer for Image Splicing Detection](image-splicing/et.md) (_SPL '22_) **\[**[**Paper**](https://ieeexplore.ieee.org/document/9769936)**]**
* [x] [Image splicing forgery detection by combining synthetic adversarial networks and hybrid dense U-net based on multiple spaces](image-splicing/san-and-hdu-net.md) (_IJIS '22_) **\[**[**Paper**](https://doi.org/10.1002/int.22939)**]** **\[**[**Code**](https://github.com/yelusaleng/SAN\_and\_HDU-Net)**]**
* [x] [SISL:Self-Supervised Image Signature Learning for Splicing Detection & Localization](image-splicing/sisl.md) (_CVPRW '22_) **\[**[**Paper**](https://arxiv.org/abs/2203.07824)**]**
* [ ] Deep Metric Color Embeddings for Splicing Localization in Severely Degraded Images (_TIFS '22_) **\[**[**Paper**](https://arxiv.org/abs/2206.10737)**]**
* [ ] Coarse-to-fine-grained method for image splicing region detection (_PR '22_) **\[**[**Paper**](https://doi.org/10.1016/j.patcog.2021.108347)**]**

</details>

<details>
<summary>2021</summary>

* [x] [CAT-Net: Compression Artifact Tracing Network for Detection and Localization of Image Splicing](image-splicing/cat-net.md) (_WACV '21_) **\[**[**Paper**](https://ieeexplore.ieee.org/document/9423390)**]** **\[**[**Code**](https://github.com/mjkwon2021/CAT-Net)**]**
* [ ] Image Splicing Detection, Localization and Attribution via JPEG Primary Quantization Matrix Estimation and Clustering (_TIFS '21_) **\[**[**Paper**](https://ieeexplore.ieee.org/document/9622213)**]** **\[**[**Code**](https://github.com/andreacos/CnnJpegPrimaryQuantizationEstimation)**]**
* [ ] Multiple Image Splicing Dataset (MISD): A Dataset for Multiple Splicing (_Data, MDPI '21_) **\[**[**Paper**](https://arxiv.org/abs/2108.09674)**]**
* [ ] Reality Transform Adversarial Generators for Image Splicing Forgery Detection and Localization (_ICCV '21_) **\[**[**Paper**](http://openaccess.thecvf.com/content/ICCV2021/html/Bi\_Reality\_Transform\_Adversarial\_Generators\_for\_Image\_Splicing\_Forgery\_Detection\_and\_ICCV\_2021\_paper.html)**]**
* [x] [Multi-Task Wavelet Corrected Network for Image Splicing Forgery Detection and Localization](image-splicing/mwc-net.md) (_ICME '21_) **\[**[**Paper**](https://ieeexplore.ieee.org/abstract/document/9428466/)**]**
* [ ] Detection and Localization of Multiple Image Splicing Using MobileNet V1 (_IEEE Access '21_) **\[**[**Paper**](https://arxiv.org/abs/2108.09674)**]**

</details>

<details>
<summary>2020 and before</summary>

* [ ] D-Unet: A Dual-encoder U-Net for Image Splicing Forgery Detection and Localization _(arXiv '20)_ **\[**[**Paper**](https://arxiv.org/abs/2012.01821)**]**
* [ ] Exposing splicing forgery in realistic scenes using deep fusion network (_InfoS '20_) **\[**[**Paper**](https://www.sciencedirect.com/science/article/pii/S0020025520302796)**]**
* [ ] Locating splicing forgery by adaptive-SVD noise estimation and vicinity noise descriptor (_Neurocomputing '20_) **\[**[**Paper**](https://www.sciencedirect.com/science/article/abs/pii/S0925231220300278)**]**
* [ ] Adversarial Learning for Constrained Image Splicing Detection and Localization Based on Atrous Convolution (_TIFS '19_) **\[**[**Paper**](https://ieeexplore.ieee.org/document/8658131)**]** **\[**[**Code**](https://github.com/yaqiliu-cs/CISDL-DMAC)**]**
* [ ] [RRU-Net: The Ringed Residual U-Net for Image Splicing Forgery Detection](image-splicing/rru-net.md) (_CVPRW' 19_) **\[**[**Paper**](http://openaccess.thecvf.com/content\_CVPRW\_2019/html/CV-COPS/Bi\_RRU-Net\_The\_Ringed\_Residual\_U-Net\_for\_Image\_Splicing\_Forgery\_Detection\_CVPRW\_2019\_paper.html?ref=https://githubhelp.com)**]** **\[**[**Code**](https://github.com/yelusaleng/RRU-Net)**]**
* [ ] Mixed adversarial generators for image splice detection (_NeuIPS '19_) **\[**[**Paper**](https://papers.nips.cc/paper/8315-the-point-where-reality-meets-fantasy-mixed-adversarial-generators-for-image-splice-detection)**]** **\[**[**Code**](https://github.com/vlkniaz/MAGritte)**]**
* [ ] Image Splicing Localization via Semi-global Network and Fully Connected Conditional Random Fields (_ECCV '18_)
* [ ] Image splicing localization using a multi-task fully convolutional network (mfcn) (_JVCIR '18_) **\[**[**Paper**](https://arxiv.org/abs/1709.02016)**]** **\[**[**Code**](https://github.com/namtpham/image\_tampering\_detection\_references.git)**]**
* [x] [Fighting Fake News: Image Splice Detection via Learned Self-Consistency](image-splicing/self-consistency.md) (_ECCV '18_) **\[**[**Paper**](https://openaccess.thecvf.com/content\_ECCV\_2018/html/Jacob\_Huh\_Fighting\_Fake\_News\_ECCV\_2018\_paper.html)**]** **\[**[**Code**](https://github.com/minyoungg/selfconsistency)**]**
* [ ] Deep Fusion Network for Splicing Forgery Localization (_ECCV '18_)
* [ ] Deep matching and validation network: An end-to-end solution to constrained image splicing localization and detection (_MM '17_) **\[**[**Paper**](https://arxiv.org/abs/1705.09765)**]**

</details>

### Image Harmonization

**图像协调化**

* [ ] Toward Realistic Image Compositing with Adversarial Learning (_CVPR '19_) **\[**[**Paper**](http://openaccess.thecvf.com/content\_CVPR\_2019/html/Chen\_Toward\_Realistic\_Image\_Compositing\_With\_Adversarial\_Learning\_CVPR\_2019\_paper.html)**]** **\[**[**Code\_unofficial**](https://github.com/SuhyeonHa/GCC-GANs)**]**
* [x] [Image Harmonization with Transformer](image-harmonization/ht-d-ht.md) (_ICCV '21_) **\[**[**Paper**](http://openaccess.thecvf.com/content/ICCV2021/html/Guo\_Image\_Harmonization\_With\_Transformer\_ICCV\_2021\_paper.html)**]**
* [ ] SSH: A Self-Supervised Framework for Image Harmonization (_ICCV '21_) **\[**[**Paper**](https://arxiv.org/abs/2108.06805)**]** **\[**[**Code**](https://github.com/VITA-Group/SSHarmonization)**]**
* [ ] Image Harmonization with Region-wise Contrastive Learning (_ArXiv '22_) **\[**[**Paper**](https://arxiv.org/abs/2205.14058)**]**
* [ ] [Harmonizer: Learning to Perform White-Box Image and Video Harmonization](image-harmonization/harmonizer.md) (_ECCV '22_) **\[**[**Paper**](https://arxiv.org/abs/2207.01322)**]** **\[**[**Code**](https://github.com/ZHKKKe/Harmonizer)**]**
* [ ] Spatial-Separated Curve Rendering Network for Efficient and High-Resolution Image Harmonization (_ECCV '22_) **\[**[**Paper**](https://arxiv.org/abs/2109.05750)**]** **\[**[**Code**](https://github.com/stefanLeong/S2CRNet)**]**
* [ ] High-Resolution Image Harmonization via Collaborative Dual Transformations (_CVPR '22_) **\[**[**Paper**](https://arxiv.org/abs/2109.06671)**]** **\[**[**Code\_unofficial**](https://github.com/SuhyeonHa/CDTNet-PyTorch)**]**
* [ ] [SCS-Co: Self-Consistent Style Contrastive Learning for Image Harmonization](image-harmonization/scs-co.md) (_CVPR '22_) **\[**[**Paper**](https://arxiv.org/abs/2204.13962)**]** **\[**[**Code**](https://github.com/YCHang686/SCS-Co-CVPR2022)**]**
* [ ] PCT-Net: Full Resolution Image Harmonization Using Pixel-Wise Color Transformations (_CVPR '23_)
* [ ] Semi-supervised Parametric Real-world Image Harmonization (_CVPR '23_) **\[**[**Paper**](https://arxiv.org/abs/2303.00157)**]** **\[**[**Code**](https://people.eecs.berkeley.edu/\~kewang/)**]** **\[**[**Project**](https://people.eecs.berkeley.edu/\~kewang/sprih/)**]**
* [ ] LEMaRT: Label-Efficient Masked Region Transform for Image Harmonization(_CVPR '23_) **\[**[**Paper**](https://arxiv.org/abs/2304.13166)**]**
* [ ] Burstormer: Burst Image Restoration and Enhancement Transformer (_CVPR '23_) **\[**[**Paper**](https://arxiv.org/abs/2304.01194)**] \[**[**Code**](https://github.com/akshaydudhane16/Burstormer.git)**]**

### Face Forgery

**人脸篡改**，篡改方法以及检测问题

* [ ] Exposing the Deception: Uncovering More Forgery Clues for Deepfake Detection _(AAAI '24)_ **[[Paper](https://arxiv.org/abs/2403.01786)]** **[[Code](https://github.com/QingyuLiu/Exposing-the-Deception)]**
* [ ] Contrastive Learning for DeepFake Classification and Localization via Multi-Label Ranking _(CVPR '24)_
* [ ] Transcending Forgery Specificity with Latent Space Augmentation for Generalizable Deepfake Detection _(CVPR '24)_ **[[Paper](https://arxiv.org/abs/2311.11278)]**
* [ ] Poisoned Forgery Face: Towards Backdoor Attacks on Face Forgery Detection _(ICLR '24)_ **[[Paper](https://openreview.net/pdf?id=8iTpB4RNvP)]** **[[Code](https://github.com/JWLiang007/PFF)]**
* [ ] Improving Fairness in Deepfake Detection _(WACV '24)_ **[[Paper](https://arxiv.org/abs/2306.16635)]** **[[Code](https://github.com/littlejuyan/DF_Fairness)]**
* [ ] Weakly-Supervised Deepfake Localization in Diffusion-Generated Images _(WACV '24)_ **[[Paper](https://arxiv.org/abs/2311.04584)]** **[[Code](https://github.com/bit-ml/dolos)]**
* [ ] Controllable Guide-Space for Generalizable Face Forgery Detection (_ICCV '23_) **\[**[**Paper**](https://arxiv.org/abs/2307.14039)**]**
* [ ] RAIRNet: Region-Aware Identity Rectification for Face Forgery Detection _(MM '23)_ **[[Paper](https://dl.acm.org/doi/10.1145/3581783.3612321)]**
* [ ] Not All Steps are Created Equal: Selective Diffusion Distillation for Image Manipulation (_ICCV '23_) **\[**[**Paper**](https://arxiv.org/abs/2307.08448)**]** **\[**[**Code**](https://github.com/EnVision-Research/Selective-Diffusion-Distillation)**]**
* [ ] UCF: Uncovering Common Features for Generalizable Deepfake Detection _(ICCV '23)_ **[[Paper](https://arxiv.org/abs/2304.13949)]**
* [ ] Learning Patch-Channel Correspondence for Interpretable Face Forgery Detection (_TIP '23_) **\[**[**Paper**](https://doi.org/10.1109/TIP.2023.3246793)**]** **\[**[**Code**](https://github.com/Jae35/IFFD)**]**
* [ ] Contrastive Multi-FaceForensics: An End-to-end Bi-grained Contrastive Learning Approach for Multi-face Forgery Detection _(arXiv '23')_ **\[**[**Paper**](https://arxiv.org/abs/2308.01520v1)**]**
* [ ] Two-in-one Knowledge Distillation for Efficient Facial Forgery Detection _(arXiv '23')_ **\[**[**Paper**](https://arxiv.org/abs/2302.10437)**]**
* [ ] AUNet: Learning Relations Between Action Units for Face Forgery Detection (_CVPR '23_) **\[**[**Paper**](http://openaccess.thecvf.com/content/CVPR2023/html/Bai\_AUNet\_Learning\_Relations\_Between\_Action\_Units\_for\_Face\_Forgery\_Detection\_CVPR\_2023\_paper.html)**]**
* [ ] AltFreezing for More General Face Forgery Detection (_CVPR '23_) **\[**[**Paper**](http://openaccess.thecvf.com/content/CVPR2023/html/Wang\_AltFreezing\_for\_More\_General\_Video\_Face\_Forgery\_Detection\_CVPR\_2023\_paper.html)**]** \*\*\[[Code](https://github.com/ZhendongWang6/AltFreezing)]88
* [ ] $F^2$Trans: High-Frequency Fine-Grained Transformer for Face Forgery Detection (_TIFS '23_) **\[**[**Paper**](https://ieeexplore.ieee.org/document/10004978)**]**
* [ ] On the Security of the One-and-a-Half-Class Classifier for SPAM Feature-Based Image Forensics (_TIFS '23_) **\[**[**Paper**](https://ieeexplore.ieee.org/document/10098583)**]**
* [ ] Multimodaltrace: Deepfake Detection Using Audiovisual Representation Learning (_CVPRW '23_) **\[**[**Paper**](https://openaccess.thecvf.com/content/CVPR2023W/WMF/html/Raza\_Multimodaltrace\_Deepfake\_Detection\_Using\_Audiovisual\_Representation\_Learning\_CVPRW\_2023\_paper.html)**]**
* [x] [MC-LCR: Multi-modal contrastive classification by locally correlated representations for effective face forgery detection](face-forgery/mc-lcr.md) (_KBS '22_) **\[**[**Paper**](https://arxiv.org/abs/2110.03290)**]**
* [x] [Multi-Scale Wavelet Transformer for Face Forgery Detection](face-forgery/multi-scale-wavelettransformer.md) (_ACCV '22_) **\[**[**Paper**](https://arxiv.org/abs/2210.03899)**]**
* [ ] Leveraging Real Talking Faces via Self-Supervision for Robust Forgery Detection (_CVPR '22_) **\[**[**Paper**](https://arxiv.org/abs/2201.07131)**]** **\[**[**Code**](https://github.com/ahaliassos/RealForensics)**]**
* [ ] SSTNet: Detecting Manipulated Faces Through Spatial, Steganalysis and Temporal Features (_ICASSP '20_) **\[**[**Paper**](https://ieeexplore.ieee.org/abstract/document/9053969/)**]**
* [x] Portrait shadow manipulation (_ACM MM / TOG '20_) **\[**[**Paper**](https://arxiv.org/abs/2005.08925)**]** **\[**[**Code**](https://github.com/google/portrait-shadow-manipulation)**]**

### Copy Move

**复制移动篡改定位**问题

* [ ] An effective image copy-move forgery detection using entropy image _(arXiv '23)_ **[[Paper](https://arxiv.org/abs/2312.11793)]**
* [ ] CMFDFormer: Transformer-based Copy-Move Forgery Detection with Continual Learning _(arXiv '23)_ **[[Paper](https://arxiv.org/abs/2311.13263)]**
* [ ] An approach for copy-move image multiple forgery detection based on an optimized pre-trained deep learning model _(KBS '23)_ **[[Paper](https://www.sciencedirect.com/science/article/pii/S0950705123002587)]**
* [ ] Image Copy-Move Forgery Detection via Deep Cross-Scale PatchMatch (_ICME '23_) **\[**[**Paper**](https://arxiv.org/abs/2308.04188)**]**
* [x] [BusterNet: Detecting Copy-Move Image Forgery with Source/Target Localization](copy-move/busternet.md) (_ECCV '18_) **\[**[**Paper**](http://openaccess.thecvf.com/content\_ECCV\_2018/html/Rex\_Yue\_Wu\_BusterNet\_Detecting\_Copy-Move\_ECCV\_2018\_paper.html)**]** **\[**[**Code**](https://github.com/isi-vista/BusterNet)**]**
* [x] [A Serial Image Copy-Move Forgery Localization Scheme With Source/Target Distinguishment](copy-move/cmsdnet.md) (_TMM '20_) **\[**[**Paper**](https://ieeexplore.ieee.org/abstract/document/9207851/)**]** **\[**[**Code**](https://github.com/imagecbj/A-serial-image-copy-move-forgery-localization-scheme-with-source-target-distinguishment)**]**
* [x] [DOA-GAN: Dual-Order Attentive Generative Adversarial Network for Image Copy-Move Forgery Detection and Localization](copy-move/doa-gan.md) (_CVPR '20_) **\[**[**Paper**](http://openaccess.thecvf.com/content\_CVPR\_2020/html/Islam\_DOA-GAN\_Dual-Order\_Attentive\_Generative\_Adversarial\_Network\_for\_Image\_Copy-Move\_Forgery\_CVPR\_2020\_paper.html)**]** **\[**[**Code**](https://github.com/asrafulashiq/doagan\_clean)**]**
* [x] [Two-Stage Copy-Move Forgery Detection with Self Deep Matching and Proposal SuperGlue](copy-move/selfdm-ps.md) (_TIP '22_) **\[**[**Paper**](https://arxiv.org/abs/2012.08697)**]**
* [ ] QDL-CMFD: A Quality-independent and deep Learning-based Copy-Move image forgery detection method (_Neurocomputing '22_) **\[**[**Paper**](https://www.sciencedirect.com/science/article/pii/S0925231222011031)**]** **\[**[**Code**](https://github.com/MehradAria/QDL-CMFD)**]**
* [ ] [Shrinking the Semantic Gap: Spatial Pooling of Local Moment Invariants for Copy-Move Forgery Detection](copy-move/word2phrasecmfd.md) _(TIFS '23)_ **\[**[**Paper**](https://arxiv.org/abs/2207.09135)**]** **\[**[**Code**](https://github.com/ChaoWang1016/word2phraseCMFD)**]**

### Tamper Text in Detection

图像中的**文本篡改检测**问题 (parts of)

- [ ] A Two-Stage Dual-Path Framework for Text Tampering Detection and Recognition _(arXiv '24)_ **[[Paper](https://arxiv.org/abs/2402.13545)]**
- [ ] Toward Real Text Manipulation Detection: New Dataset and New Solution _(arXiv '23)_ **[[Paper](https://arxiv.org/abs/2312.06934)]** **[[Code](https://github.com/DrLuo/RTM)]**
- [ ] Towards Robust Tampered Text Detection in Document Image: New dataset and New Solution (_CVPR '23_) **\[**[**Paper**](https://openaccess.thecvf.com/content/CVPR2023/papers/Qu_Towards_Robust_Tampered_Text_Detection_in_Document_Image_New_Dataset_CVPR_2023_paper.pdf)**]** **[[Code](https://github.com/qcf-568/DocTamper)]**
- [ ] Progressive Supervision for Tampering Localization in Document Images (_ICONIP '23_) **[[Paper](https://link.springer.com/chapter/10.1007/978-981-99-8184-7_11)]**
- [ ] SigScatNet: A Siamese + Scattering based Deep Learning Approach for Signature Forgery Detection and Similarity Assessment _(arXiv '23)_ **[[Paper](https://arxiv.org/pdf/2311.05579.pdf)]**
- [ ] Image Generation and Learning Strategy for Deep Document Forgery Detection _(arXiv '23)_ **[[Paper](https://arxiv.org/abs/2311.03650)]**
- [ ] Forgery-free signature verification with stroke-aware cycle-consistent generative adversarial network _(Neurocomputing '22)_ **[[Paper](https://doi.org/10.1016/j.neucom.2022.08.017)]** **[[Code](https://github.com/KAKAFEI123/Stroke-cCycleGAN)]**
- [ ] Document Forgery Detection in the Context of Double JPEG Compression _(ICPR '22)_ **[[Paper](https://link.springer.com/chapter/10.1007/978-3-031-37745-7_5)]**

### Low Level Vision

Related resources:

* [https://github.com/Kobaayyy/Awesome-ICCV2021-Low-Level-Vision](https://github.com/Kobaayyy/Awesome-ICCV2021-Low-Level-Vision)
* [https://github.com/lcybuzz/Low-Level-Vision-Paper-Record](https://github.com/lcybuzz/Low-Level-Vision-Paper-Record)

Low-level tasks include super-resolution, denoise, dehze, low-light enhancement, etc. High-level tasks include classification, detection, segmentation, etc. segmentation, and so on. However, the ones I have listed here are probably still mainly related to tampering detection.

> Testing the new layout of paper title.
>
> 📖Paper, 👨‍💻Code, 📦Dataset, 🔗Other links, 📜News,
>
> \*Equal contribution. #Corresponding author.

* [ ] (**EVP**) Explicit Visual Prompting for Low-Level Structure Segmentations (_CVPR '23_) [📖](https://arxiv.org/abs/2303.10883), [👨‍💻](https://github.com/NiFangBaAGe/Explicit-Visual-Prompt) (_including defocus blur, shadow, forgery, camouflaged dection_)

  > [Weihuang Liu](https://github.com/nifangbaage)<sup>1</sup>, [Xi Shen](https://xishen0220.github.io/)<sup>2</sup>, [Chi-Man Pun](https://www.cis.um.edu.mo/\~cmpun/)<sup>#,1</sup>, [Xiaodong Cun](https://vinthony.github.io/)<sup>#,2</sup>
  >
  > <sup>1</sup>University of Macau <sup>2</sup>Tencent AI Lab

* [ ] SYENet: A Simple Yet Effective Network for Multiple Low-Level Vision Tasks with Real-time Performance on Mobile Device (_ICCV '23_) [📖](https://arxiv.org/abs/2308.08137), [👨‍💻](https://github.com/sanechips-multimedia/syenet)

  > [Weiran Gou](https://github.com/WeiranGou)<sup>∗1,2</sup>, Ziyao Yi<sup>∗1,2</sup>, Yan Xiang<sup>1,2</sup>, Shaoqing Li<sup>1,2</sup>, Zibin Liu<sup>1,2</sup>, Dehui Kong<sup>1,2</sup>, Ke Xu<sup>#1,2</sup>
  >
  > <sup>1</sup>State Key Laboratory of Mobile Network and Mobile Multimedia Technology, <sup>2</sup>Sanechips Technology, Chengdu, China

* [ ] Q-Bench: A Benchmark for General-Purpose Foundation Models on Low-level Vision (_ICLR_ '24\_) [📖](https://arxiv.org/abs/2309.14181), [👨‍💻](https://github.com/VQAssessment/Q-Bench)

  > [Haoning Wu](https://teowu.github.io/)<sup>1\*</sup>, [Zicheng Zhang](https://github.com/zzc-1998)<sup>2\*</sup>, [Erli Zhang](https://github.com/ZhangErliCarl/)<sup>1\*</sup>, [Chaofeng Chen](https://chaofengc.github.io/)<sup>1</sup>, [Liang Liao](https://liaoliang92.github.io/)<sup>1</sup>, [Annan Wang](https://github.com/AnnanWangDaniel)<sup>1</sup>, [Chunyi Li](https://github.com/lcysyzxdxc)<sup>2</sup>, [Wenxiu Sun](https://wenxiusun.com/)<sup>3</sup>, [Qiong Yan](https://scholar.google.com/citations?user=uT9CtPYAAAAJ\&hl=en)<sup>3</sup>, [Guangtao Zhai](https://ee.sjtu.edu.cn/en/FacultyDetail.aspx?id=24\&infoid=153\&flag=153)<sup>2</sup>, [Weisi Lin](https://personal.ntu.edu.sg/wslin/Home.html)<sup>1#</sup>
  >
  > <sup>1</sup>Nanyang Technological University, <sup>2</sup>Shanghai Jiaotong University, <sup>3</sup>Sensetime Research

### Image Matching

**特征匹配**，图像匹配问题。

* [ ] FMRT: Learning Accurate Feature Matching with Reconciliatory Transformer(_arXiv '23_) **\[**[**Paper**](https://arxiv.org/abs/2310.13605)**]** 
* [x] [LoFTR: Detector-Free Local Matching with Transformers](image-matching/loftr.md) (_CVPR '21_) **\[**[**Paper**](https://arxiv.org/abs/2104.00680)**]** **\[**[**Code**](https://github.com/zju3dv/LoFTR)**]**
* [ ] PATS: Patch Area Transportation with Subdivision for Local Feature Matching (_CVPR '23_) **\[**[**Paper**](https://arxiv.org/abs/2303.07700)**]** **\[**[**Code**](https://github.com/zju3dv/pats)**]** **\[**[**Project**](https://zju3dv.github.io/pats/)**]**
* [ ] Adaptive Spot-Guided Transformer for Consistent Local Feature Matching (_CVPR '23_) **\[**[**Paper**](https://arxiv.org/abs/2303.16624)**]** **\[**[**Code**](https://github.com/ASTR2023/ASTR)**]** **\[**[**Project**](https://astr2023.github.io/)**]**
* [ ] ObjectMatch: Robust Registration using Canonical Object Correspondences (_CVPR '23_) **\[**[**Paper**](https://arxiv.org/abs/2212.01985)**]** **\[**[**Code**](https://github.com/cangumeli/ObjectMatch)**]** **\[**[**Project**](https://cangumeli.github.io/ObjectMatch/)**]**

### Object Detection

**目标检测**，包括伪装物体目标检测和突出目标检测，COD以及SOD。

* [ ] HEAP: Unsupervised Object Discovery and Localization with Contrastive Grouping *(AAAI '24)* **[[Paper](https://arxiv.org/abs/2312.17492)]**
* [ ] Endow SAM with Keen Eyes: Temporal-spatial Prompt Learning for Video Camouflaged Object Detection _(CVPR '24)_
* [ ] VSCode: General Visual Salient and Camouflaged Object Detection with 2D Prompt Learning _(CVPR '24)_ **[[Paper](https://arxiv.org/abs/2311.15011)]**
* [ ] Weakly Supervised Open-Vocabulary Object Detection _(AAAI '24)_ **[[Paper](https://arxiv.org/abs/2312.12437)]**
* [ ] OTA: Optimal Transport Assignment for Object Detection (_CVPR '21_) **\[**[**Paper**](https://arxiv.org/abs/2103.14259)**]** **\[**[**Code**](https://github.com/Megvii-BaseDetection/OTA)**]**
* [ ] Consistency-basd Active Learning for Object Detection (_CVPRW '22_) **\[**[**Paper**](http://128.84.21.203/abs/2103.10374)**]** **\[**[**Code**](https://github.com/we1pingyu/CALD)**]**
* [ ] [Zoom In and Out: A Mixed-scale Triplet Network for Camouflaged Object Detection](object-dection/zoomnet-cod.md) (_CVPR '22_) **\[**[**Paper**](https://arxiv.org/abs/2203.02688)**]** **\[**[**Code**](https://github.com/lartpang/ZoomNet)**]**
* [ ] Unsupervised Object Localization: Observing the Background to Discover Objects (_CVPR '23_) **\[**[**Paper**](https://arxiv.org/abs/2212.07834)**]** **\[**[**Code**](https://github.com/valeoai/FOUND)**]**
* [ ] Camouflaged Object Detection with Feature Decomposition and Edge Reconstruction (_CVPR '23_) **\[**[**Paper**](https://openreview.net/pdf?id=lin5jPqCQ6)**]** **\[**[**Code**](https://github.com/ChunmingHe/FEDER)**]**
* [ ] Feature Shrinkage Pyramid for Camouflaged Object Detection with Transformers (_CVPR '23_) **\[**[**Paper**](https://arxiv.org/abs/2303.14816)**]** **\[**[**Code**](https://github.com/ZhouHuang23/FSPNet)**]**
* [ ] Locate, Refine and Restore: A Progressive Enhancement Network for Camouflaged Object Detection (_IJCAI '23_) **\[**[**Paper**](https://www.ijcai.org/proceedings/2023/0124.pdf)**]**
* [ ] Spatial-Aware Token for Weakly Supervised Object Localization (_ICCV '23_) **\[**[**Paper**](https://arxiv.org/abs/2303.10438)**]** **\[**[**Code**](https://github.com/wpy1999/SAT)**]**
* [ ] Generative Prompt Model for Weakly Supervised Object Localization (_ICCV '23_) **\[**[**Paper**](https://arxiv.org/abs/2307.09756)**]** **\[**[**Code**](https://github.com/callsys/GenPromp)**]**
* [ ] Category-aware Allocation Transformer for Weakly Supervised Object Localization (_ICCV '23_) **\[**[**Paper**](https://openaccess.thecvf.com/content/ICCV2023/html/Chen\_Category-aware\_Allocation\_Transformer\_for\_Weakly\_Supervised\_Object\_Localization\_ICCV\_2023\_paper.html)**]**

### Semantic Segmentation

语义分割，将图片中完整语义（具有标签或者类别）的部分分割出来。不仅要进行目标检测检测到图像中的物体，还需要对每个像素分类。

* [ ] [Generative Semantic Segmentation](semantic-segmentation/gss.md) (_CVPR '23_) **\[**[**Paper**](https://arxiv.org/abs/2303.11316)**]** **\[**[**Code**](https://github.com/fudan-zvg/GSS)**]**
* [ ] EfficientViT: Lightweight Multi-Scale Attention for On-Device Semantic Segmentation **\[**[**Paper**](https://arxiv.org/abs/2205.14756)**]** **\[**[**Code**](https://github.com/mit-han-lab/efficientvit)**]**
* [ ] CAT-Seg: Cost Aggregation for Open-Vocabulary Semantic Segmentation **\[**[**Paper**](https://arxiv.org/abs/2303.11797)**]** **\[**[**Code**](https://github.com/KU-CVLAB/CAT-Seg)**]** **\[**[**Project**](https://ku-cvlab.github.io/CAT-Seg/)**]** **\[**[**Note\_community**](https://blog.csdn.net/P\_LarT/article/details/131083586)**]

### Anomaly Detection

异常检测，通常用于发现与正常模式或预期模式不符的图像与视频。

* [ ] Contextual Affinity Distillation for Image Anomaly Detection _(WACV '24)_  **[[Paper](https://arxiv.org/abs/2307.03101)]**
* [ ] PromptAD: Zero-Shot Anomaly Detection Using Text Prompts _(WACV '24)_  **[[Paper](https://openaccess.thecvf.com/content/WACV2024/html/Li_PromptAD_Zero-Shot_Anomaly_Detection_Using_Text_Prompts_WACV_2024_paper.html)]**
* [ ] Holistic Representation Learning for Multitask Trajectory Anomaly Detection _(WACV '24)_  **[[Paper](https://arxiv.org/abs/2311.01851)]** **[[Code](https://alexandrosstergiou.github.io/project_pages/TrajREC/index.html)]**

### Useful Links

1. CVPR 2024 Accepted Papers <https://cvpr2023.thecvf.com/Conferences/2024/AcceptedPapers>
2. ICLR 2024 Papers List <https://openreview.net/group?id=ICLR.cc/2024/Conference>
3. WACV 2024 Papers <https://openaccess.thecvf.com/WACV2024>
4. MM 2023 Proceedings <https://dl.acm.org/doi/proceedings/10.1145/3581783>
5. ICML 2023 https://dblp.org/db/conf/icml/icml2023.html
6. ICCV 2023 Paper List <https://huggingface.co/spaces/ICCV2023/ICCV2023-papers>
9. IJCAI 2023 Accepted Papers List <https://ijcai-23.org/main-track-accepted-papers/>
10. AAAI 2023 <https://dblp.org/db/conf/aaai/aaai2023.html>
11. ECCV 2022 Accepted papers <https://eccv2022.ecva.net/program/accepted-papers/>
12. SIGGRAPH _unofficial_ <https://kesen.realtimerendering.com/> eg SIGGRAPH 2023 <https://kesen.realtimerendering.com/sig2023.html>
13. TIFS <https://ieeexplore.ieee.org/xpl/RecentIssue.jsp?punumber=10206>
14. [More...](related/papersource.md)

### [Back to Home](https://zihol.gitbook.io/)
