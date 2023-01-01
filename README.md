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

* [x] [Attention Is All You Need](backbone/transformer.md) <mark style="background-color:yellow;">(</mark>_<mark style="background-color:yellow;">NeurIPS '17</mark>_<mark style="background-color:yellow;">)</mark>
* [x] [EfficientNet: Rethinking Model Scaling for Convolutional Neural Networks](backbone/efficientnet.md) <mark style="background-color:yellow;">(</mark>_<mark style="background-color:yellow;">ICML '19</mark>_<mark style="background-color:yellow;">)</mark>
* [x] [An Image is Worth 16x16 Words: Transformers for Image Recognition at Scale](backbone/vit.md) <mark style="background-color:yellow;">(</mark>_<mark style="background-color:yellow;">ICLR '21</mark>_<mark style="background-color:yellow;">)</mark>
* [x] [Multi-Dimensional Model Compression of Vision Transformer](backbone/multi-dimensional-compression-vit.md) <mark style="background-color:yellow;">(</mark>_<mark style="background-color:yellow;">ICME '22</mark>_<mark style="background-color:yellow;">)</mark>
* [x] Deep Residual Learning for Image Recognition <mark style="background-color:yellow;">(</mark>_<mark style="background-color:yellow;">CVPR '16</mark>_<mark style="background-color:yellow;">)</mark>
* [ ] Generative Adversarial Networks <mark style="background-color:yellow;">(</mark>_<mark style="background-color:yellow;">NeurIPS '14</mark>_<mark style="background-color:yellow;">)</mark>

### Image Tampering

**图像篡改检测定位**

* [x] ****[ObjectFormer for Image Manipulation Detection and Localization](image-forgery/objectformer.md) <mark style="background-color:yellow;">(</mark>_<mark style="background-color:yellow;">CVPR '22</mark>_<mark style="background-color:yellow;">)</mark> **\[**[**Paper**](https://arxiv.org/abs/2203.14681)**]**&#x20;
* [x] [TransForensics: Image Forgery Localization with Dense Self-Attention](image-forgery/transforensics.md) <mark style="background-color:yellow;">(</mark>_<mark style="background-color:yellow;">ICCV '21</mark>_<mark style="background-color:yellow;">)</mark>
* [x] [Generate, Segment, and Refine: Towards Generic Manipulation Segmentation](image-forgery/gsrnet.md)  <mark style="background-color:yellow;">(</mark>_<mark style="background-color:yellow;">AAAI '20</mark>_<mark style="background-color:yellow;">)</mark> **\[**[**Paper**](https://arxiv.org/abs/1811.09729)**] \[**[**Code**](https://github.com/pengzhou1108/GSRNet)**]**
* [ ] M2TR: Multi-modal Multi-scale Transformers for Deepfake Detection <mark style="background-color:yellow;">(</mark>_<mark style="background-color:yellow;">ICMR '22</mark>_<mark style="background-color:yellow;">)</mark>
* [ ] PSCC-Net: Progressive Spatio-Channel Correlation Network for Image Manipulation Detection and Localization <mark style="background-color:yellow;">(</mark>_<mark style="background-color:yellow;">TCSVT '22</mark>_<mark style="background-color:yellow;">)</mark>
* [ ] Image manipulation detection by multiple tampering traces and edge artifact enhancement <mark style="background-color:yellow;">(</mark>_<mark style="background-color:yellow;">PR '23</mark>_<mark style="background-color:yellow;">)</mark>
* [ ] MSTA-Net: Forgery Detection by Generating Manipulation Trace Based on Multi-Scale Self-Texture Attention <mark style="background-color:yellow;">(</mark>_<mark style="background-color:yellow;">TCSVT '21</mark>_<mark style="background-color:yellow;">)</mark>
* [ ] Learning to localize image forgery using end-to-end attention network <mark style="background-color:yellow;">(</mark>_<mark style="background-color:yellow;">Neurocomputing '22</mark>_<mark style="background-color:yellow;">)</mark>
* [ ] MVSS-Net: Multi-View Multi-Scale Supervised Networks for Image Manipulation Detection <mark style="background-color:yellow;">(</mark>_<mark style="background-color:yellow;">TPAMI '22</mark>_<mark style="background-color:yellow;">)</mark>
* [ ] Self-supervised Domain Adaptation for Forgery Localization of JPEG Compressed Images <mark style="background-color:yellow;">(</mark>_<mark style="background-color:yellow;">ICCV '21</mark>_<mark style="background-color:yellow;">)</mark>
* [ ] Image Tampering Localization Using a Dense Fully Convolutional Network <mark style="background-color:yellow;">(</mark>_<mark style="background-color:yellow;">TIFS '21</mark>_<mark style="background-color:yellow;">)</mark>
* [ ] MSMG-Net: Multi-scale Multi-grained Supervised Metworks for Multi-task Image Manipulation Detection and Localization
* [ ] Towards JPEG-Resistant Image Forgery Detection and Localization Via Self-Supervised Domain Adaptation <mark style="background-color:yellow;">(</mark>_<mark style="background-color:yellow;">TPAMI '22</mark>_<mark style="background-color:yellow;">)</mark>
* [ ] ESRNet: Efficient Search and Recognition Network for Image Manipulation Detection <mark style="background-color:yellow;">(</mark>_<mark style="background-color:yellow;">TOMCCAP '22</mark>_<mark style="background-color:yellow;">)</mark>
* [ ] LSTM and encoder–decoder architecture for detection of image forgeries <mark style="background-color:yellow;">(</mark>_<mark style="background-color:yellow;">TIP '19</mark>_<mark style="background-color:yellow;">)</mark>
* [ ] ManTra-Net: Manipulation Tracing Network for Detection and Localization of Image Forgeries With Anomalous Features <mark style="background-color:yellow;">(</mark>_<mark style="background-color:yellow;">CVPR '19</mark>_<mark style="background-color:yellow;">)</mark>
* [ ] Robust Image Forgery Detection Over Online Social Network Shared Images <mark style="background-color:yellow;">(</mark>_<mark style="background-color:yellow;">CVPR '22</mark>_<mark style="background-color:yellow;">)</mark>
* [ ] GCA-Net: Utilizing Gated Context Attention for Improving Image Forgery Localization and Detection <mark style="background-color:yellow;">(</mark>_<mark style="background-color:yellow;">CVPRW '22</mark>_<mark style="background-color:yellow;">)</mark>
* [ ] Non-Semantic Evaluation of Image Forensics Tools: Methodology and Database <mark style="background-color:yellow;">(</mark>_<mark style="background-color:yellow;">WACV '22</mark>_<mark style="background-color:yellow;">)</mark>
* [ ] Image Manipulation Localization Using Multi-Scale Feature Fusion and Adaptive Edge Supervision (_<mark style="background-color:yellow;">TMM '22</mark>_)

### Image Splicing

**图像的拼接篡改检测定位**

* [x] [Multi-Task SE-Network for Image Splicing Localization](image-splicing/multi-task-se-network.md) <mark style="background-color:yellow;">(</mark>_<mark style="background-color:yellow;">TCSVT '21</mark>_<mark style="background-color:yellow;">)</mark>
* [x] [CAT-Net: Compression Artifact Tracing Network for Detection and Localization of Image Splicing](image-splicing/cat-net.md) <mark style="background-color:yellow;">(</mark>_<mark style="background-color:yellow;">WACV '21</mark>_<mark style="background-color:yellow;">)</mark>
* [x] [Fighting Fake News: Image Splice Detection via Learned Self-Consistency](image-splicing/self-consistency.md) <mark style="background-color:yellow;">(</mark>_<mark style="background-color:yellow;">ECCV '18</mark>_<mark style="background-color:yellow;">)</mark>
* [x] [Image splicing forgery detection by combining synthetic adversarial networks and hybrid dense U-net based on multiple spaces](image-splicing/san-and-hdu-net.md) <mark style="background-color:yellow;">(</mark>_<mark style="background-color:yellow;">IJIS '22</mark>_<mark style="background-color:yellow;">)</mark>
* [ ] [SISL:Self-Supervised Image Signature Learning for Splicing Detection & Localization](image-splicing/sisl.md) <mark style="background-color:yellow;">(</mark>_<mark style="background-color:yellow;">CVPRW '22</mark>_<mark style="background-color:yellow;">)</mark>
* [ ] Image Splicing Detection, Localization and Attribution via JPEG Primary Quantization Matrix Estimation and Clustering <mark style="background-color:yellow;">(</mark>_<mark style="background-color:yellow;">TIFS '21</mark>_<mark style="background-color:yellow;">)</mark>
* [ ] Adversarial Learning for Constrained Image Splicing Detection and Localization Based on Atrous Convolution <mark style="background-color:yellow;">(</mark>_<mark style="background-color:yellow;">TIFS '19</mark>_<mark style="background-color:yellow;">)</mark>
* [ ] Multiple Image Splicing Dataset (MISD): A Dataset for Multiple Splicing <mark style="background-color:yellow;">(</mark>_<mark style="background-color:yellow;">Data, MDPI '21</mark>_<mark style="background-color:yellow;">)</mark>
* [ ] ET: Edge-Enhanced Transformer for Image Splicing Detection <mark style="background-color:yellow;">(</mark>_<mark style="background-color:yellow;">SPL '22</mark>_<mark style="background-color:yellow;">)</mark>
* [ ] Reality Transform Adversarial Generators for Image Splicing Forgery Detection and Localization <mark style="background-color:yellow;">(I</mark>_<mark style="background-color:yellow;">CCV '21</mark>_<mark style="background-color:yellow;">)</mark>
* [ ] [RRU-Net: The Ringed Residual U-Net for Image Splicing Forgery Detection](https://github.com/yelusaleng/RRU-Net) <mark style="background-color:yellow;">(</mark>_<mark style="background-color:yellow;">CVPRW' 19</mark>_<mark style="background-color:yellow;">)</mark>
* [ ] Deep Metric Color Embeddings for Splicing Localization in Severely Degraded Images <mark style="background-color:yellow;">(</mark>_<mark style="background-color:yellow;">TIFS '22</mark>_<mark style="background-color:yellow;">)</mark>
* [ ] Multi-Task Wavelet Corrected Network for Image Splicing Forgery Detection and Localization <mark style="background-color:yellow;">(</mark>_<mark style="background-color:yellow;">ICME '21</mark>_<mark style="background-color:yellow;">)</mark>

### Image Harmonization

**图像协调化**

* [x] [Harmonizer: Learning to Perform White-Box Image and Video Harmonization](image-harmonization/harmonizer.md) <mark style="background-color:yellow;">(</mark>_<mark style="background-color:yellow;">ECCV '22</mark>_<mark style="background-color:yellow;">)</mark>
* [x] [Image Harmonization with Transformer](image-harmonization/ht-d-ht.md) <mark style="background-color:yellow;">(</mark>_<mark style="background-color:yellow;">ICCV '21</mark>_<mark style="background-color:yellow;">)</mark>
* [ ] Image Harmonization with Region-wise Contrastive Learning
* [ ] Spatial-Separated Curve Rendering Network for Efficient and High-Resolution Image Harmonization <mark style="background-color:yellow;">(</mark>_<mark style="background-color:yellow;">ECCV '22</mark>_<mark style="background-color:yellow;">)</mark>
* [ ] SSH: A Self-Supervised Framework for Image Harmonization <mark style="background-color:yellow;">(</mark>_<mark style="background-color:yellow;">ICCV '21</mark>_<mark style="background-color:yellow;">)</mark>
* [ ] Toward Realistic Image Compositing with Adversarial Learning <mark style="background-color:yellow;">(</mark>_<mark style="background-color:yellow;">CVPR '19</mark>_<mark style="background-color:yellow;">)</mark>
* [ ] High-Resolution Image Harmonization via Collaborative Dual Transformations <mark style="background-color:yellow;">(</mark>_<mark style="background-color:yellow;">CVPR '22</mark>_<mark style="background-color:yellow;">)</mark>
* [ ] SCS-Co: Self-Consistent Style Contrastive Learning for Image Harmonization <mark style="background-color:yellow;">(</mark>_<mark style="background-color:yellow;">CVPR '22</mark>_<mark style="background-color:yellow;">)</mark>&#x20;

### Face Forgery

**人脸篡改**，以及检测问题

* [x] [MC-LCR: Multi-modal contrastive classification by locally correlated representations for effective face forgery detection](face-forgery/mc-lcr.md) <mark style="background-color:yellow;">(</mark>_<mark style="background-color:yellow;">KBS '22</mark>_<mark style="background-color:yellow;">)</mark>
* [x] [Multi-Scale Wavelet Transformer for Face Forgery Detection](face-forgery/multi-scale-wavelettransformer.md) <mark style="background-color:yellow;">(</mark>_<mark style="background-color:yellow;">ACCV '22</mark>_<mark style="background-color:yellow;">)</mark>
* [ ] SSTNet: Detecting Manipulated Faces Through Spatial, Steganalysis and Temporal Features <mark style="background-color:yellow;">(</mark>_<mark style="background-color:yellow;">ICASSP '20</mark>_<mark style="background-color:yellow;">)</mark>
* [x] Portrait shadow manipulation <mark style="background-color:yellow;">(</mark>_<mark style="background-color:yellow;">ACM MM / TOG '20</mark>_<mark style="background-color:yellow;">)</mark>

### Copy Move

**复制移动篡改定位**问题

* [x] [DOA-GAN: Dual-Order Attentive Generative Adversarial Network for Image Copy-Move Forgery Detection and Localization](copy-move/doa-gan.md) <mark style="background-color:yellow;">(</mark>_<mark style="background-color:yellow;">CVPR' 20</mark>_<mark style="background-color:yellow;">)</mark>
* [x] [Two-Stage Copy-Move Forgery Detection with Self Deep Matching and Proposal SuperGlue](copy-move/selfdm-ps.md) <mark style="background-color:yellow;">(</mark>_<mark style="background-color:yellow;">TIP' 22</mark>_<mark style="background-color:yellow;">)</mark>
* [x] [A Serial Image Copy-Move Forgery Localization Scheme With Source/Target Distinguishment](copy-move/cmsdnet.md) <mark style="background-color:yellow;">(</mark>_<mark style="background-color:yellow;">TMM' 20</mark>_<mark style="background-color:yellow;">)</mark>
* [ ] QDL-CMFD: A Quality-independent and deep Learning-based Copy-Move image forgery detection method <mark style="background-color:yellow;">(</mark>_<mark style="background-color:yellow;">Neurocomputing '22</mark>_<mark style="background-color:yellow;">)</mark>
* [x] [BusterNet: Detecting Copy-Move Image Forgery with Source/Target Localization](copy-move/busternet.md) <mark style="background-color:yellow;">(</mark>_<mark style="background-color:yellow;">ECCV '18</mark>_<mark style="background-color:yellow;">)</mark>

### Image Matching

**特征匹配**，图像匹配问题。

* [x] [LoFTR: Detector-Free Local Matching with Transformers](image-matching/loftr.md) <mark style="background-color:yellow;">(</mark>_<mark style="background-color:yellow;">CVPR' 21</mark>_<mark style="background-color:yellow;">)</mark>

### Object Detection

**目标检测**，包括伪装物体目标检测和突出目标检测，COD以及SOD。

* [ ] [Zoom In and Out: A Mixed-scale Triplet Network for Camouflaged Object Detection](object-dection/zoomnet-cod.md) <mark style="background-color:yellow;">(</mark>_<mark style="background-color:yellow;">CVPR' 22</mark>_<mark style="background-color:yellow;">)</mark>
* [ ] OTA: Optimal Transport Assignment for Object Detection <mark style="background-color:yellow;">(</mark>_<mark style="background-color:yellow;">CVPR' 21</mark>_<mark style="background-color:yellow;">)</mark>
* [ ] Consistency-basd Active Learning for Object Detection <mark style="background-color:yellow;">(</mark>_<mark style="background-color:yellow;">CVPRW' 22</mark>_<mark style="background-color:yellow;">)</mark>\


### [Back to Home](https://zihol.gitbook.io/)
