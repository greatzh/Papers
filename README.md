---
description: Deep learning papers notes sharing
---

# 😀 Overview

### Related

* [Nice Expression](related/nice-expressions.md)

### Basics

* [图像处理基础知识](basic-knowledge/image-processing.md)

### Backbone

**骨干网络**，多为图像分类的网络。

* [x] [Attention Is All You Need](backbone/transformer.md) <mark style="background-color:yellow;">(</mark>_<mark style="background-color:yellow;">NeurIPS '17</mark>_<mark style="background-color:yellow;">)</mark> **[[Paper](https://proceedings.neurips.cc/paper/7181-attention-is-all)]** **[[Code_official](https://github.com/tensorflow/tensor2tensor/blob/master/tensor2tensor/models/transformer.py)]** **[[Code_community](https://github.com/jadore801120/attention-is-all-you-need-pytorch)]**
* [x] [EfficientNet: Rethinking Model Scaling for Convolutional Neural Networks](backbone/efficientnet.md) <mark style="background-color:yellow;">(</mark>_<mark style="background-color:yellow;">ICML '19</mark>_<mark style="background-color:yellow;">)</mark> **[[Paper](https://arxiv.org/abs/1905.11946)]** **[[Code](https://github.com/tensorflow/tpu/tree/master/models/official/efficientnet)]**
* [x] [An Image is Worth 16x16 Words: Transformers for Image Recognition at Scale](backbone/vit.md) <mark style="background-color:yellow;">(</mark>_<mark style="background-color:yellow;">ICLR '21</mark>_<mark style="background-color:yellow;">)</mark> **[[Paper](https://arxiv.org/abs/2010.11929)]** **[[Code](https://github.com/google-research/vision_transformer)]**
* [x] [Multi-Dimensional Model Compression of Vision Transformer](backbone/multi-dimensional-compression-vit.md) <mark style="background-color:yellow;">(</mark>_<mark style="background-color:yellow;">ICME '22</mark>_<mark style="background-color:yellow;">)</mark> **[[Paper](https://arxiv.org/abs/2201.00043)]**
* [x] Deep Residual Learning for Image Recognition <mark style="background-color:yellow;">(</mark>_<mark style="background-color:yellow;">CVPR '16</mark>_<mark style="background-color:yellow;">)</mark> **[[Paper](https://arxiv.org/abs/1512.03385)]**
* [ ] Generative Adversarial Networks <mark style="background-color:yellow;">(</mark>_<mark style="background-color:yellow;">NeurIPS '14</mark>_<mark style="background-color:yellow;">)</mark> **[[Paper](https://papers.nips.cc/paper/2014/hash/5ca3e9b122f61f8f06494c97b1afccf3-Abstract.html)]**

### Image Tampering

**图像篡改检测定位**

* [x] [ObjectFormer for Image Manipulation Detection and Localization](image-forgery/objectformer.md) <mark style="background-color:yellow;">(</mark>_<mark style="background-color:yellow;">CVPR '22</mark>_<mark style="background-color:yellow;">)</mark> **\[**[**Paper**](https://arxiv.org/abs/2203.14681)**]**&#x20;
* [x] [TransForensics: Image Forgery Localization with Dense Self-Attention](image-forgery/transforensics.md) <mark style="background-color:yellow;">(</mark>_<mark style="background-color:yellow;">ICCV '21</mark>_<mark style="background-color:yellow;">)</mark> **[[Paper](https://arxiv.org/abs/2108.03871)]**
* [x] [Generate, Segment, and Refine: Towards Generic Manipulation Segmentation](image-forgery/gsrnet.md)  <mark style="background-color:yellow;">(</mark>_<mark style="background-color:yellow;">AAAI '20</mark>_<mark style="background-color:yellow;">)</mark> **[[Paper](https://arxiv.org/abs/1811.09729)]** **[[Code](https://github.com/pengzhou1108/GSRNet)]**
* [x] [PSCC-Net: Progressive Spatio-Channel Correlation Network for Image Manipulation Detection and Localization](image-forgery/pscc-net.md) <mark style="background-color:yellow;">(</mark>_<mark style="background-color:yellow;">TCSVT '22</mark>_<mark style="background-color:yellow;">)</mark> **[[Paper](https://arxiv.org/abs/2103.10596)]** **[[Code](https://github.com/proteus1991/PSCC-Net)]**
* [ ] M2TR: Multi-modal Multi-scale Transformers for Deepfake Detection <mark style="background-color:yellow;">(</mark>_<mark style="background-color:yellow;">ICMR '22</mark>_<mark style="background-color:yellow;">)</mark> **[[Paper](https://arxiv.org/abs/2104.09770)]** **[[Code](https://github.com/wangjk666/M2TR-Multi-modal-Multi-scale-Transformers-for-Deepfake-Detection)]**
* [ ] Image manipulation detection by multiple tampering traces and edge artifact enhancement <mark style="background-color:yellow;">(</mark>_<mark style="background-color:yellow;">PR '23</mark>_<mark style="background-color:yellow;">)</mark> **[[Paper](https://www.sciencedirect.com/science/article/pii/S0031320322005064)]** 
* [ ] MSTA-Net: Forgery Detection by Generating Manipulation Trace Based on Multi-Scale Self-Texture Attention <mark style="background-color:yellow;">(</mark>_<mark style="background-color:yellow;">TCSVT '21</mark>_<mark style="background-color:yellow;">)</mark> **[[Paper](https://ieeexplore.ieee.org/document/9643421)]**
* [ ] Learning to localize image forgery using end-to-end attention network <mark style="background-color:yellow;">(</mark>_<mark style="background-color:yellow;">Neurocomputing '22</mark>_<mark style="background-color:yellow;">)</mark> **[[Paper](https://www.sciencedirect.com/science/article/pii/S0925231222011274)]** **[[Code](https://github.com/sadaf-ali/-Learning-to-Localize-Image-Forgery-Using-End-to-End-Attention-Network)]**
* [ ] MVSS-Net: Multi-View Multi-Scale Supervised Networks for Image Manipulation Detection <mark style="background-color:yellow;">(</mark>_<mark style="background-color:yellow;">TPAMI '22</mark>_<mark style="background-color:yellow;">)</mark> **[[Paper](https://arxiv.org/abs/2112.08935)]** **[[Code](https://github.com/dong03/MVSS-Net)]**
* [ ] Image Manipulation Detection by Multi-View Multi-Scale Supervision <mark style="background-color:yellow;">(</mark>_<mark style="background-color:yellow;">ICCV '21</mark>_<mark style="background-color:yellow;">)</mark>  **[[Paper](https://arxiv.org/abs/2104.06832)]** **[[Code](https://github.com/dong03/MVSS-Net)]**
* [ ] Self-supervised Domain Adaptation for Forgery Localization of JPEG Compressed Images <mark style="background-color:yellow;">(</mark>_<mark style="background-color:yellow;">ICCV '21</mark>_<mark style="background-color:yellow;">)</mark> **[[Paper](https://openaccess.thecvf.com/content/ICCV2021/html/Rao_Self-Supervised_Domain_Adaptation_for_Forgery_Localization_of_JPEG_Compressed_Images_ICCV_2021_paper.html)]** 
* [ ] Image Tampering Localization Using a Dense Fully Convolutional Network <mark style="background-color:yellow;">(</mark>_<mark style="background-color:yellow;">TIFS '21</mark>_<mark style="background-color:yellow;">)</mark> **[[Paper](https://ieeexplore.ieee.org/document/9393396)]** **[[Code](https://github.com/ZhuangPeiyu/Dense-FCN-for-tampering-localization)]**
* [ ] MSMG-Net: Multi-scale Multi-grained Supervised Metworks for Multi-task Image Manipulation Detection and Localization <mark style="background-color:yellow;">(</mark>_<mark style="background-color:yellow;">ArXiv '22</mark>_<mark style="background-color:yellow;">)</mark> **[[Paper](https://arxiv.org/abs/2211.03140)]**
* [ ] Towards JPEG-Resistant Image Forgery Detection and Localization Via Self-Supervised Domain Adaptation <mark style="background-color:yellow;">(</mark>_<mark style="background-color:yellow;">TPAMI '22</mark>_<mark style="background-color:yellow;">)</mark> **[[Paper](https://ieeexplore.ieee.org/document/9904872)]** 
* [ ] ESRNet: Efficient Search and Recognition Network for Image Manipulation Detection <mark style="background-color:yellow;">(</mark>_<mark style="background-color:yellow;">TOMCCAP '22</mark>_<mark style="background-color:yellow;">)</mark> **[[Paper](https://doi.org/10.1145/3506853)]** **[[Tool](https://github.com/tampered816/rrr)]**
* [ ] LSTM and encoder–decoder architecture for detection of image forgeries <mark style="background-color:yellow;">(</mark>_<mark style="background-color:yellow;">TIP '19</mark>_<mark style="background-color:yellow;">)</mark> **[[Paper](https://arxiv.org/abs/1903.02495)]** **[[Code](https://github.com/jawadbappy/forgery_localization_HLED)]**
* [ ] ManTra-Net: Manipulation Tracing Network for Detection and Localization of Image Forgeries With Anomalous Features <mark style="background-color:yellow;">(</mark>_<mark style="background-color:yellow;">CVPR '19</mark>_<mark style="background-color:yellow;">)</mark> **[[Paper](https://ieeexplore.ieee.org/document/8953774)]** **[[Code](https://github.com/ISICV/ManTraNet)]**
* [ ] Robust Image Forgery Detection Over Online Social Network Shared Images <mark style="background-color:yellow;">(</mark>_<mark style="background-color:yellow;">CVPR '22</mark>_<mark style="background-color:yellow;">)</mark> **[[Paper](https://openaccess.thecvf.com/content/CVPR2022/papers/Wu_Robust_Image_Forgery_Detection_Over_Online_Social_Network_Shared_Images_CVPR_2022_paper.pdf)]** **[[Code](https://github.com/HighwayWu/ImageForensicsOSN)]**
* [ ] GCA-Net: Utilizing Gated Context Attention for Improving Image Forgery Localization and Detection <mark style="background-color:yellow;">(</mark>_<mark style="background-color:yellow;">CVPRW '22</mark>_<mark style="background-color:yellow;">)</mark> **[[Paper](https://arxiv.org/abs/2112.04298)]** 
* [ ] Non-Semantic Evaluation of Image Forensics Tools: Methodology and Database <mark style="background-color:yellow;">(</mark>_<mark style="background-color:yellow;">WACV '22</mark>_<mark style="background-color:yellow;">)</mark> **[[Paper](https://arxiv.org/abs/2105.02700)]** **[[Code](https://github.com/qbammey/trace)]**
* [ ] Image Manipulation Localization Using Multi-Scale Feature Fusion and Adaptive Edge Supervision <mark style="background-color:yellow;">(_TMM '22_)</mark> **[[Paper](https://ieeexplore.ieee.org/document/9996125/)]** 
* [ ] [ReLoc: A Restoration-Assisted Framework for Robust Image Tampering Localization](image-forgery/reloc.md) <mark style="background-color:yellow;">(</mark>_<mark style="background-color:yellow;">ArXiv '22</mark>_<mark style="background-color:yellow;">)</mark> **[[Paper](https://arxiv.org/abs/2211.03930)]** **[[Code](https://github.com/ZhuangPeiyu/ReLoc)]**
* [ ] CFL-Net: Image Forgery Localization Using Contrastive Learning <mark style="background-color:yellow;">(</mark>_<mark style="background-color:yellow;">WACV '23</mark>_<mark style="background-color:yellow;">)</mark> **[[Paper](https://arxiv.org/abs/2210.02182)]** **[[Code](https://github.com/niloy193/CFLNet)]**
* [ ] TruFor: Leveraging all-round clues for trustworthy image forgery detection and localization <mark style="background-color:yellow;">(</mark>_<mark style="background-color:yellow;">ArXiv '22</mark>_<mark style="background-color:yellow;">)</mark> **[[Paper](https://arxiv.org/abs/2212.10957)]** **[[Project](https://grip-unina.github.io/TruFor/)]** **[[Code](https://github.com/grip-unina/TruFor)]**
* [ ] A Principled Design of Image Representation: Towards Forensic Tasks <mark style="background-color:yellow;">(</mark>_<mark style="background-color:yellow;">TPAMI '22</mark>_<mark style="background-color:yellow;">)</mark> **[[Paper](https://arxiv.org/abs/2203.00913)]** **[[Code](https://github.com/ShurenQi/DIR)]**

### Image Splicing

**图像的拼接篡改检测定位**

* [x] [Multi-Task SE-Network for Image Splicing Localization](image-splicing/multi-task-se-network.md) <mark style="background-color:yellow;">(</mark>_<mark style="background-color:yellow;">TCSVT '21</mark>_<mark style="background-color:yellow;">)</mark> **[[Paper](https://ieeexplore.ieee.org/document/9591639)]** **[[Code](https://github.com/YulansZhang/Multi-task-SE-Network-for-Image-Splicing-Localization)]**
* [x] [CAT-Net: Compression Artifact Tracing Network for Detection and Localization of Image Splicing](image-splicing/cat-net.md) <mark style="background-color:yellow;">(</mark>_<mark style="background-color:yellow;">WACV '21</mark>_<mark style="background-color:yellow;">)</mark> **[[Paper](https://ieeexplore.ieee.org/document/9423390)]** **[[Code](https://github.com/mjkwon2021/CAT-Net)]**
* [x] [Fighting Fake News: Image Splice Detection via Learned Self-Consistency](image-splicing/self-consistency.md) <mark style="background-color:yellow;">(</mark>_<mark style="background-color:yellow;">ECCV '18</mark>_<mark style="background-color:yellow;">)</mark> **[[Paper](https://openaccess.thecvf.com/content_ECCV_2018/html/Jacob_Huh_Fighting_Fake_News_ECCV_2018_paper.html)]** **[[Code](https://github.com/minyoungg/selfconsistency)]**
* [x] [Image splicing forgery detection by combining synthetic adversarial networks and hybrid dense U-net based on multiple spaces](image-splicing/san-and-hdu-net.md) <mark style="background-color:yellow;">(</mark>_<mark style="background-color:yellow;">IJIS '22</mark>_<mark style="background-color:yellow;">)</mark> **[[Paper](https://doi.org/10.1002/int.22939)]** **[[Code](https://github.com/yelusaleng/SAN_and_HDU-Net)]**
* [ ] [SISL:Self-Supervised Image Signature Learning for Splicing Detection & Localization](image-splicing/sisl.md) <mark style="background-color:yellow;">(</mark>_<mark style="background-color:yellow;">CVPRW '22</mark>_<mark style="background-color:yellow;">)</mark> **[[Paper](https://arxiv.org/abs/2203.07824)]**
* [ ] Image Splicing Detection, Localization and Attribution via JPEG Primary Quantization Matrix Estimation and Clustering <mark style="background-color:yellow;">(</mark>_<mark style="background-color:yellow;">TIFS '21</mark>_<mark style="background-color:yellow;">)</mark> **[[Paper](https://ieeexplore.ieee.org/document/9622213)]** 
* [ ] Adversarial Learning for Constrained Image Splicing Detection and Localization Based on Atrous Convolution <mark style="background-color:yellow;">(</mark>_<mark style="background-color:yellow;">TIFS '19</mark>_<mark style="background-color:yellow;">)</mark> **[[Paper](https://ieeexplore.ieee.org/document/8658131)]** **[[Code](https://github.com/yaqiliu-cs/CISDL-DMAC)]**
* [ ] Multiple Image Splicing Dataset (MISD): A Dataset for Multiple Splicing <mark style="background-color:yellow;">(</mark>_<mark style="background-color:yellow;">Data, MDPI '21</mark>_<mark style="background-color:yellow;">)</mark> **[[Paper](https://arxiv.org/abs/2108.09674)]** 
* [ ] ET: Edge-Enhanced Transformer for Image Splicing Detection <mark style="background-color:yellow;">(</mark>_<mark style="background-color:yellow;">SPL '22</mark>_<mark style="background-color:yellow;">)</mark> **[[Paper](https://ieeexplore.ieee.org/document/9769936)]**
* [ ] Reality Transform Adversarial Generators for Image Splicing Forgery Detection and Localization <mark style="background-color:yellow;">(I</mark>_<mark style="background-color:yellow;">CCV '21</mark>_<mark style="background-color:yellow;">)</mark> **[[Paper](http://openaccess.thecvf.com/content/ICCV2021/html/Bi_Reality_Transform_Adversarial_Generators_for_Image_Splicing_Forgery_Detection_and_ICCV_2021_paper.html)]** 
* [ ] [RRU-Net: The Ringed Residual U-Net for Image Splicing Forgery Detection](https://github.com/yelusaleng/RRU-Net) <mark style="background-color:yellow;">(</mark>_<mark style="background-color:yellow;">CVPRW' 19</mark>_<mark style="background-color:yellow;">)</mark> **[[Paper](http://openaccess.thecvf.com/content_CVPRW_2019/html/CV-COPS/Bi_RRU-Net_The_Ringed_Residual_U-Net_for_Image_Splicing_Forgery_Detection_CVPRW_2019_paper.html?ref=https://githubhelp.com)]** **[[Code](https://github.com/yelusaleng/RRU-Net)]**
* [ ] Deep Metric Color Embeddings for Splicing Localization in Severely Degraded Images <mark style="background-color:yellow;">(</mark>_<mark style="background-color:yellow;">TIFS '22</mark>_<mark style="background-color:yellow;">)</mark> **[[Paper](https://arxiv.org/abs/2206.10737)]**
* [ ] Multi-Task Wavelet Corrected Network for Image Splicing Forgery Detection and Localization <mark style="background-color:yellow;">(</mark>_<mark style="background-color:yellow;">ICME '21</mark>_<mark style="background-color:yellow;">)</mark> **[[Paper](https://ieeexplore.ieee.org/abstract/document/9428466/)]** 

### Image Harmonization

**图像协调化**

* [x] [Harmonizer: Learning to Perform White-Box Image and Video Harmonization](image-harmonization/harmonizer.md) <mark style="background-color:yellow;">(</mark>_<mark style="background-color:yellow;">ECCV '22</mark>_<mark style="background-color:yellow;">)</mark> **[[Paper](https://arxiv.org/abs/2207.01322)]** **[[Code](https://github.com/ZHKKKe/Harmonizer)]**
* [x] [Image Harmonization with Transformer](image-harmonization/ht-d-ht.md) <mark style="background-color:yellow;">(</mark>_<mark style="background-color:yellow;">ICCV '21</mark>_<mark style="background-color:yellow;">)</mark> **[[Paper](http://openaccess.thecvf.com/content/ICCV2021/html/Guo_Image_Harmonization_With_Transformer_ICCV_2021_paper.html)]** 
* [ ] Image Harmonization with Region-wise Contrastive Learning <mark style="background-color:yellow;">(</mark>_<mark style="background-color:yellow;">ArXiv '22</mark>_<mark style="background-color:yellow;">)</mark> **[[Paper](https://arxiv.org/abs/2205.14058)]**
* [ ] Spatial-Separated Curve Rendering Network for Efficient and High-Resolution Image Harmonization <mark style="background-color:yellow;">(</mark>_<mark style="background-color:yellow;">ECCV '22</mark>_<mark style="background-color:yellow;">)</mark> **[[Paper](https://arxiv.org/abs/2109.05750)]** **[[Code](https://github.com/stefanLeong/S2CRNet)]**
* [ ] SSH: A Self-Supervised Framework for Image Harmonization <mark style="background-color:yellow;">(</mark>_<mark style="background-color:yellow;">ICCV '21</mark>_<mark style="background-color:yellow;">)</mark> **[[Paper](https://arxiv.org/abs/2108.06805)]** **[[Code](https://github.com/VITA-Group/SSHarmonization)]**
* [ ] Toward Realistic Image Compositing with Adversarial Learning <mark style="background-color:yellow;">(</mark>_<mark style="background-color:yellow;">CVPR '19</mark>_<mark style="background-color:yellow;">)</mark> **[[Paper](http://openaccess.thecvf.com/content_CVPR_2019/html/Chen_Toward_Realistic_Image_Compositing_With_Adversarial_Learning_CVPR_2019_paper.html)]** **[[Code_unofficial](https://github.com/SuhyeonHa/GCC-GANs)]**
* [ ] High-Resolution Image Harmonization via Collaborative Dual Transformations <mark style="background-color:yellow;">(</mark>_<mark style="background-color:yellow;">CVPR '22</mark>_<mark style="background-color:yellow;">)</mark> **[[Paper](https://arxiv.org/abs/2109.06671)]** **[[Code_unofficial](https://github.com/SuhyeonHa/CDTNet-PyTorch)]**
* [ ] SCS-Co: Self-Consistent Style Contrastive Learning for Image Harmonization <mark style="background-color:yellow;">(</mark>_<mark style="background-color:yellow;">CVPR '22</mark>_<mark style="background-color:yellow;">)</mark> **[[Paper](https://arxiv.org/abs/2204.13962)]** **[[Code](https://github.com/YCHang686/SCS-Co-CVPR2022)]** &#x20;

### Face Forgery

**人脸篡改**，以及检测问题

* [x] [MC-LCR: Multi-modal contrastive classification by locally correlated representations for effective face forgery detection](face-forgery/mc-lcr.md) <mark style="background-color:yellow;">(</mark>_<mark style="background-color:yellow;">KBS '22</mark>_<mark style="background-color:yellow;">)</mark> **[[Paper](https://arxiv.org/abs/2110.03290)]** 
* [x] [Multi-Scale Wavelet Transformer for Face Forgery Detection](face-forgery/multi-scale-wavelettransformer.md) <mark style="background-color:yellow;">(</mark>_<mark style="background-color:yellow;">ACCV '22</mark>_<mark style="background-color:yellow;">)</mark> **[[Paper](https://arxiv.org/abs/2210.03899)]**
* [ ] SSTNet: Detecting Manipulated Faces Through Spatial, Steganalysis and Temporal Features <mark style="background-color:yellow;">(</mark>_<mark style="background-color:yellow;">ICASSP '20</mark>_<mark style="background-color:yellow;">)</mark> **[[Paper](https://ieeexplore.ieee.org/abstract/document/9053969/)]**
* [x] Portrait shadow manipulation <mark style="background-color:yellow;">(</mark>_<mark style="background-color:yellow;">ACM MM / TOG '20</mark>_<mark style="background-color:yellow;">)</mark> **[[Paper](https://arxiv.org/abs/2005.08925)]** **[[Code](https://github.com/google/portrait-shadow-manipulation)]**

### Copy Move

**复制移动篡改定位**问题

* [x] [DOA-GAN: Dual-Order Attentive Generative Adversarial Network for Image Copy-Move Forgery Detection and Localization](copy-move/doa-gan.md) <mark style="background-color:yellow;">(</mark>_<mark style="background-color:yellow;">CVPR' 20</mark>_<mark style="background-color:yellow;">)</mark> **[[Paper](http://openaccess.thecvf.com/content_CVPR_2020/html/Islam_DOA-GAN_Dual-Order_Attentive_Generative_Adversarial_Network_for_Image_Copy-Move_Forgery_CVPR_2020_paper.html)]** **[[Code](https://github.com/asrafulashiq/doagan_clean)]**
* [x] [Two-Stage Copy-Move Forgery Detection with Self Deep Matching and Proposal SuperGlue](copy-move/selfdm-ps.md) <mark style="background-color:yellow;">(</mark>_<mark style="background-color:yellow;">TIP' 22</mark>_<mark style="background-color:yellow;">)</mark> **[[Paper](https://arxiv.org/abs/2012.08697)]**
* [x] [A Serial Image Copy-Move Forgery Localization Scheme With Source/Target Distinguishment](copy-move/cmsdnet.md) <mark style="background-color:yellow;">(</mark>_<mark style="background-color:yellow;">TMM' 20</mark>_<mark style="background-color:yellow;">)</mark> **[[Paper](https://ieeexplore.ieee.org/abstract/document/9207851/)]** **[[Code](https://github.com/imagecbj/A-serial-image-copy-move-forgery-localization-scheme-with-source-target-distinguishment)]**
* [ ] QDL-CMFD: A Quality-independent and deep Learning-based Copy-Move image forgery detection method <mark style="background-color:yellow;">(</mark>_<mark style="background-color:yellow;">Neurocomputing '22</mark>_<mark style="background-color:yellow;">)</mark> **[[Paper](https://www.sciencedirect.com/science/article/pii/S0925231222011031)]** **[[Code](https://github.com/MehradAria/QDL-CMFD)]**
* [x] [BusterNet: Detecting Copy-Move Image Forgery with Source/Target Localization](copy-move/busternet.md) <mark style="background-color:yellow;">(</mark>_<mark style="background-color:yellow;">ECCV '18</mark>_<mark style="background-color:yellow;">)</mark> **[[Paper](http://openaccess.thecvf.com/content_ECCV_2018/html/Rex_Yue_Wu_BusterNet_Detecting_Copy-Move_ECCV_2018_paper.html)]** **[[Code](https://github.com/isi-vista/BusterNet)]**

### Image Matching

**特征匹配**，图像匹配问题。

* [x] [LoFTR: Detector-Free Local Matching with Transformers](image-matching/loftr.md) <mark style="background-color:yellow;">(</mark>_<mark style="background-color:yellow;">CVPR' 21</mark>_<mark style="background-color:yellow;">)</mark> **[[Paper](https://arxiv.org/abs/2104.00680)]** **[[Code](https://github.com/zju3dv/LoFTR)]**

### Object Detection

**目标检测**，包括伪装物体目标检测和突出目标检测，COD以及SOD。

* [ ] [Zoom In and Out: A Mixed-scale Triplet Network for Camouflaged Object Detection](object-dection/zoomnet-cod.md) <mark style="background-color:yellow;">(</mark>_<mark style="background-color:yellow;">CVPR' 22</mark>_<mark style="background-color:yellow;">)</mark> **[[Paper](https://arxiv.org/abs/2203.02688)]** **[[Code](https://github.com/lartpang/ZoomNet)]**
* [ ] OTA: Optimal Transport Assignment for Object Detection <mark style="background-color:yellow;">(</mark>_<mark style="background-color:yellow;">CVPR' 21</mark>_<mark style="background-color:yellow;">)</mark> **[[Paper](https://arxiv.org/abs/2103.14259)]** **[[Code](https://github.com/Megvii-BaseDetection/OTA)]**
* [ ] Consistency-basd Active Learning for Object Detection <mark style="background-color:yellow;">(</mark>_<mark style="background-color:yellow;">CVPRW' 22</mark>_<mark style="background-color:yellow;">)</mark> **[[Paper](http://128.84.21.203/abs/2103.10374)]** **[[Code](https://github.com/we1pingyu/CALD)]**


### [Back to Home](https://zihol.gitbook.io/)
