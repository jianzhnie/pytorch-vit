<div align="center">
  <img width="600" src="media/logo.png" alt="awesome-vit">
  <br>
  <img src=https://cdn.rawgit.com/sindresorhus/awesome/d7305f38d29fed78fa85652e3a63e154dd8e8829/media/badge.svg>
</div>


--------------------------------------------------------------------------------
 English | [简体中文](README_zh-CN.md)



A curated list and survey of awesome Vision Transformers. 

You can use mind mapping software to open [the mind mapping source file](media/Vision-Transformer.xmind). You can also download [the mind mapping HD pictures](media/Vision-Transformer.png) if you just want to browse them.

## Contents

<!-- toc -->

- [Survey](#Survey)
  - [Image Classification](#Image-Classification)
    - [Attention-based](#Attention-based)
      - [Training Strategy](#Training-Strategy)
      - [Model Improvements](#Model-Improvements)
        - [Tokenization Module](#Tokenization-Module)
        - [Position Encoding Module](#Position-Encoding-Module)
        - [Attention Module](#Attention-Module)
        - [FFN Module](#FFN-Module)
        - [Normalization Module Location](#Normalization-Module-Location)
        - [Classification Prediction Head Module](#Classification-Prediction-Head-Module)
        - [Others](#Others)
    - [MLP-based](#MLP-based)
    - [ConvMixer-based](#ConvMixer-based)
    - [General Architecture Analysis](#General-Architecture-Analysis)
    - [Others](#Others)
  - [Object Detection](#Object-Detection)
  - [Semantic-Segmentation](#Semantic-Segmentation)

- [Papers](#Papers)
  - [Transformer Original Paper](#Transformer-Original-Paper)
  - [ViT Original Paper](#ViT-Original-Paper)
  - [Image Classification](#Image-Classification)
    - [2020](#2020)
    - [2021](#2021)
    - [2022](#2022)
  - [Object Detection](#Object-Detection)
  - [Semantic-Segmentation](#Semantic-Segmentation)

<!-- tocstop -->



## Survey

Only typical algorithms are listed in each category.



### Image Classification

Chinese Blogs

- [Vision Transformer 必读系列之图像分类综述(一)：概述](https://zhuanlan.zhihu.com/p/459828118)



#### Attention-based

![image](https://user-images.githubusercontent.com/17425982/150277299-3656d399-962c-4029-9dde-a2c64283de79.png)

##### Training Strategy

![image](https://user-images.githubusercontent.com/17425982/150277367-9a206b4b-69b3-43e1-b7e6-156d68e34234.png)

- [**DeiT**] Training data-efficient image transformers & distillation through attention (ICML 2021-2020.12) [[Paper](https://arxiv.org/abs/2012.12877)]
- [**Token Labeling**] All Tokens Matter: Token Labeling for Training Better Vision Transformers (2021.4) [[Paper](https://arxiv.org/abs/2104.10858)]



##### Model Improvements



###### Tokenization Module

--------------------------------------------------------------------------------

![image](https://user-images.githubusercontent.com/17425982/150276835-5c2558e9-9825-41cf-aa7c-766ed4bb2f8f.png)

Image to Token：

- **Non-overlapping Patch Embedding**
  
  -  [**ViT**] An Image is Worth 16x16 Words: Transformers for Image Recognition at Scale (ICLR 2021-2020.10) [[Paper](https://arxiv.org/abs/2010.11929)]
  - [**TNT**] Transformer in Transformer (NeurIPS 2021-2021.3) [[Paper](https://arxiv.org/abs/2103.00112)]
  - [**Swin Transformer**] Swin Transformer: Hierarchical Vision Transformer using Shifted Windows (ICCV2021-2021.3) [[Paper](https://arxiv.org/abs/2103.14030)]
  
- **Overlapping Patch Embedding**

  - [**T2T-ViT**] Tokens-to-Token ViT: Training Vision Transformers from Scratch on ImageNet (2021.1) [[Paper](https://arxiv.org/abs/2101.11986)]

  - [**ResT**] ResT: An Efficient Transformer for Visual Recognition (2021.5) [[Paper](https://arxiv.org/abs/2105.13677)]

  - [**PVTv2**] PVTv2: Improved Baselines with Pyramid Vision Transformer (2021.6) [[Paper](https://arxiv.org/abs/2106.13797)]

  - [**ViTAE**] ViTAE: Vision Transformer Advanced by Exploring Intrinsic Inductive Bias (2021.6) [[Paper](https://arxiv.org/abs/2106.03348)]

  - [**PS-ViT**] Vision Transformer with Progressive Sampling (2021.8) [[Paper](https://arxiv.org/abs/2108.01684)]

    

Token to Token：

- **Fixed sampling window tokenization**
  -  [**ViT**] An Image is Worth 16x16 Words: Transformers for Image Recognition at Scale (ICLR 2021-2020.10) [[Paper](https://arxiv.org/abs/2010.11929)]
  - [**Swin Transformer**] Swin Transformer: Hierarchical Vision Transformer using Shifted Windows (ICCV2021-2021.3) [[Paper](https://arxiv.org/abs/2103.14030)]
- **Dynamic sampling tokenization**
  - [**PS-ViT**] Vision Transformer with Progressive Sampling (2021.8) [[Paper](https://arxiv.org/abs/2108.01684)]
  - [**TokenLearner**] TokenLearner: What Can 8 Learned Tokens Do for Images and Videos? (2021.6) [[Paper](https://arxiv.org/abs/2106.11297)]



###### Position Encoding Module

--------------------------------------------------------------------------------

![image](https://user-images.githubusercontent.com/17425982/150276469-b756df37-b727-46ef-8e69-039d0a291729.png)

Explicit position encoding：

- Absolute position encoding
  - [**Transformer**] Attention is All You Need] (NIPS 2017-2017.06) [[Paper](https://arxiv.org/abs/1706.03762)]
  - [**ViT**] An Image is Worth 16x16 Words: Transformers for Image Recognition at Scale (ICLR 2021-2020.10) [[Paper](https://arxiv.org/abs/2010.11929)]
  - [**PVT**] Pyramid Vision Transformer: A Versatile Backbone for Dense Prediction without Convolutions (2021.2) [[Paper](https://arxiv.org/abs/2102.12122)]
- Relative position encoding
  - [**Swin Transformer**] Swin Transformer: Hierarchical Vision Transformer using Shifted Windows (ICCV2021-2021.3) [[Paper](https://arxiv.org/abs/2103.14030)]
  - [**Swin Transformer V2**] Swin Transformer V2: Scaling Up Capacity and Resolution (2021.11) [[Paper](https://arxiv.org/abs/2111.09883)]
  - [**Imporved MViT**] Improved Multiscale Vision Transformers for Classification and Detection (2021.12) [[Paper](https://arxiv.org/abs/2112.01526)]



Implicit position encoding：

- [**CPVT**] Conditional Positional Encodings for Vision Transformers (2021.2) [[Paper](https://arxiv.org/abs/2102.10882)]
- [**CSWin Transformer**] CSWin Transformer: A General Vision Transformer Backbone with Cross-Shaped Windows (2021.07) [[Paper](https://arxiv.org/abs/2107.00652)]
- [**PVTv2**] PVTv2: Improved Baselines with Pyramid Vision Transformer (2021.6) [[Paper](https://arxiv.org/abs/2106.13797)]
- [**ResT**] ResT: An Efficient Transformer for Visual Recognition (2021.5) [[Paper](https://arxiv.org/abs/2105.13677)]



###### Attention Module

--------------------------------------------------------------------------------

![image](https://user-images.githubusercontent.com/17425982/150276274-9e7463cc-f7b2-4914-9ebf-f32012782ca9.png)

Include only global attention：

- Multi-Head attention module

  - [**ViT**] An Image is Worth 16x16 Words: Transformers for Image Recognition at Scale (ICLR 2021-2020.10) [[Paper](https://arxiv.org/abs/2010.11929)]

- Reduce global attention computation

  - [**PVT**] Pyramid Vision Transformer: A Versatile Backbone for Dense Prediction without Convolutions (2021.2) [[Paper](https://arxiv.org/abs/2102.12122)]

  - [**PVTv2**] PVTv2: Improved Baselines with Pyramid Vision Transformer (2021.6) [[Paper](https://arxiv.org/abs/2106.13797)]
  - [**Twins**] Twins: Revisiting the Design of Spatial Attention in Vision Transformers (2021.4) [[Paper](https://arxiv.org/abs/2104.13840)]
  - [**P2T**] P2T: Pyramid Pooling Transformer for Scene Understanding (2021.6) [[Paper](https://arxiv.org/abs/2106.12011v3)]
  - [**ResT**] ResT: An Efficient Transformer for Visual Recognition (2021.5) [[Paper](https://arxiv.org/abs/2105.13677)]
  - [**MViT**] Multiscale Vision Transformers (2021.4) [[Paper](https://arxiv.org/abs/2104.11227)]
  - [**Imporved MViT**] Improved Multiscale Vision Transformers for Classification and Detection (2021.12) [[Paper](https://arxiv.org/abs/2112.01526)]

- Generalized linear attention

  - [**T2T-ViT**] Tokens-to-Token ViT: Training Vision Transformers from Scratch on ImageNet (2021.1) [[Paper](https://arxiv.org/abs/2101.11986)]



Introduce extra local attention：

- Local window mode
  - [**Swin Transformer**] Swin Transformer: Hierarchical Vision Transformer using Shifted Windows (ICCV2021-2021.3) [[Paper](https://arxiv.org/abs/2103.14030)]
  - [**Swin Transformer V2**] Swin Transformer V2: Scaling Up Capacity and Resolution (2021.11) [[Paper](https://arxiv.org/abs/2111.09883)]
  - [**Imporved MViT**] Improved Multiscale Vision Transformers for Classification and Detection (2021.12) [[Paper](https://arxiv.org/abs/2112.01526)]
  - [**Twins**] Twins: Revisiting the Design of Spatial Attention in Vision Transformers (2021.4) [[Paper](https://arxiv.org/abs/2104.13840)]
  - [**GG-Transformer**] Glance-and-Gaze Vision Transformer (2021.6) [[Paper](https://arxiv.org/abs/2106.02277)]
  - [**Shuffle Transformer**] Shuffle Transformer: Rethinking Spatial Shuffle for Vision Transformer (2021.6) [[Paper](https://arxiv.org/abs/2106.03650)]
  - [**MSG-Transformer**] MSG-Transformer: Exchanging Local Spatial Information by Manipulating Messenger Tokens (2021.5) [[Paper](https://arxiv.org/abs/2105.15168)]
  - [**CSWin Transformer**] CSWin Transformer: A General Vision Transformer Backbone with Cross-Shaped Windows (2021.07) [[Paper](https://arxiv.org/abs/2107.00652)]

- Introduce convolutional local inductive bias
  - [**ViTAE**] ViTAE: Vision Transformer Advanced by Exploring Intrinsic Inductive Bias (2021.6) [[Paper](https://arxiv.org/abs/2106.03348)]
  - [**ELSA**] ELSA: Enhanced Local Self-Attention for Vision Transformer (2021.12) [[Paper](https://arxiv.org/abs/2112.12786)]
- Sparse attention
  - [**Sparse Transformer**] Sparse Transformer: Concentrated Attention Through Explicit Selection [[Paper](https://openreview.net/pdf?id=Hye87grYDH)]



###### FFN Module

--------------------------------------------------------------------------------

![image](https://user-images.githubusercontent.com/17425982/150272284-8ed5b2be-fbe0-4c3c-9885-0577f47f310c.png)

Improve performance with Conv's local information extraction capability：

- [**LocalViT**] LocalViT: Bringing Locality to Vision Transformers (2021.4) [[Paper](https://arxiv.org/abs/2104.05707)]
- [**CeiT**] Incorporating Convolution Designs into Visual Transformers (2021.3) [[Paper](https://arxiv.org/abs/2103.11816)]



###### Normalization Module Location

--------------------------------------------------------------------------------

![image](https://user-images.githubusercontent.com/17425982/150266034-792b8987-2654-49df-9410-043c40d320f8.png)

- Pre Normalization
  - [**ViT**] An Image is Worth 16x16 Words: Transformers for Image Recognition at Scale (ICLR 2021-2020.10) [[Paper](https://arxiv.org/abs/2010.11929)]
  - [**Swin Transformer**] Swin Transformer: Hierarchical Vision Transformer using Shifted Windows (ICCV2021-2021.3) [[Paper](https://arxiv.org/abs/2103.14030)]

- Post Normalization
  - [**Swin Transformer V2**] Swin Transformer V2: Scaling Up Capacity and Resolution (2021.11) [[Paper](https://arxiv.org/abs/2111.09883)]



###### Classification Prediction Head Module

--------------------------------------------------------------------------------

![image](https://user-images.githubusercontent.com/17425982/150265671-ed284f48-8004-4e42-a9a9-f72d115026ce.png)

- Class Tokens
  - [**ViT**] An Image is Worth 16x16 Words: Transformers for Image Recognition at Scale (ICLR 2021-2020.10) [[Paper](https://arxiv.org/abs/2010.11929)]
  - [**CeiT**] Incorporating Convolution Designs into Visual Transformers (2021.3) [[Paper](https://arxiv.org/abs/2103.11816)]

- Avgerage Pooling
  - [**Swin Transformer**] Swin Transformer: Hierarchical Vision Transformer using Shifted Windows (ICCV2021-2021.3) [[Paper](https://arxiv.org/abs/2103.14030)]
  - [**CPVT**] Conditional Positional Encodings for Vision Transformers (2021.2) [[Paper](https://arxiv.org/abs/2102.10882)]
  - [**ResT**] ResT: An Efficient Transformer for Visual Recognition (2021.5) [[Paper](https://arxiv.org/abs/2105.13677)]



###### Others

--------------------------------------------------------------------------------

![image](https://user-images.githubusercontent.com/17425982/150269740-11f77408-76dc-4a63-b813-b34505e627a5.png)

**(1) How to output multi-scale feature map**

- Patch merging
  - [**PVT**] Pyramid Vision Transformer: A Versatile Backbone for Dense Prediction without Convolutions (2021.2) [[Paper](https://arxiv.org/abs/2102.12122)]
  - [**Twins**] Twins: Revisiting the Design of Spatial Attention in Vision Transformers (2021.4) [[Paper](https://arxiv.org/abs/2104.13840)]
  - [**Swin Transformer**] Swin Transformer: Hierarchical Vision Transformer using Shifted Windows (ICCV2021-2021.3) [[Paper](https://arxiv.org/abs/2103.14030)]
  - [**ResT**] ResT: An Efficient Transformer for Visual Recognition (2021.5) [[Paper](https://arxiv.org/abs/2105.13677)]
  - [**CSWin Transformer**] CSWin Transformer: A General Vision Transformer Backbone with Cross-Shaped Windows (2021.07) [[Paper](https://arxiv.org/abs/2107.00652)]
  - [**MetaFormer**] MetaFormer is Actually What You Need for Vision (2021.11) [[Paper](https://arxiv.org/abs/2111.11418)]

- Pooling attention 

  - [**MViT**] Multiscale Vision Transformers (2021.4) [[Paper](https://arxiv.org/abs/2104.11227)][**Imporved MViT**] 

  - [**Imporved MViT**] Improved Multiscale Vision Transformers for Classification and Detection (2021.12) [[Paper](https://arxiv.org/abs/2112.01526)]

- Dilation convolution
  - [**ViTAE**] ViTAE: Vision Transformer Advanced by Exploring Intrinsic Inductive Bias (2021.6) [[Paper](https://arxiv.org/abs/2106.03348)]



**(2) How to train a deeper Transformer**

- [**Cait**] Going deeper with Image Transformers (2021.3) [[Paper](https://arxiv.org/abs/2103.17239)]
- [**DeepViT**] DeepViT: Towards Deeper Vision Transformer (2021.3) [[Paper](https://arxiv.org/abs/2103.11886)]



#### MLP-based

![image](https://user-images.githubusercontent.com/17425982/150264115-71f2b7c3-5e22-44b7-a7d2-f54de6b38734.png)

- [**MLP-Mixer**] MLP-Mixer: An all-MLP Architecture for Vision (2021.5) [[Paper](https://arxiv.org/abs/2105.01601)]

- [**ResMLP**] ResMLP: Feedforward networks for image classification with data-efficient training (CVPR2021-2021.5) [[Paper](https://arxiv.org/abs/2105.03404)]

- [**gMLP**] Pay Attention to MLPs (2021.5) [[Paper](https://arxiv.org/abs/2105.08050)]

- [**CycleMLP**] CycleMLP: A MLP-like Architecture for Dense Prediction (2021.7) [[Paper](https://arxiv.org/abs/2107.10224)]

  

#### ConvMixer-based

- [**ConvMixer**] Patches Are All You Need [[Paper](https://openreview.net/pdf?id=TVHS5Y4dNvM)]

  

#### General Architecture Analysis

![image](https://user-images.githubusercontent.com/17425982/150263392-656e406b-0e28-4810-a3bd-a3aec6bfee8d.png)

- Demystifying Local Vision Transformer: Sparse Connectivity, Weight Sharing, and Dynamic Weight (2021.6) [[Paper](https://arxiv.org/abs/2106.04263)]
- A Battle of Network Structures: An Empirical Study of CNN, Transformer, and MLP (2021.8) [[Paper](https://arxiv.org/abs/2108.13002)]
- [**MetaFormer**] MetaFormer is Actually What You Need for Vision (2021.11) [[Paper](https://arxiv.org/abs/2111.11418)]
- [**ConvNeXt**] A ConvNet for the 2020s (2022.01) [[Paper](https://arxiv.org/abs/2201.03545)]



#### Others



### Object Detection



### Semantic Segmentation

**[⬆ back to top](#Contents)**



## Papers



### Transformer Original Paper

- [**Transformer**] Attention is All You Need] (NIPS 2017-2017.06) [[Paper](https://arxiv.org/abs/1706.03762)]



### ViT Original Paper

- [**ViT**] An Image is Worth 16x16 Words: Transformers for Image Recognition at Scale (ICLR 2021-2020.10) [[Paper](https://arxiv.org/abs/2010.11929)]



### Image Classification



#### 2020

- [**DeiT**] Training data-efficient image transformers & distillation through attention (ICML 2021-2020.12) [[Paper](https://arxiv.org/abs/2012.12877)]
- [Sparse Transformer] Sparse Transformer: Concentrated Attention Through Explicit Selection [[Paper](https://openreview.net/pdf?id=Hye87grYDH)]



#### 2021

- [T2T-ViT] Tokens-to-Token ViT: Training Vision Transformers from Scratch on ImageNet (2021.1) [[Paper](https://arxiv.org/abs/2101.11986)]
- [**PVT**] Pyramid Vision Transformer: A Versatile Backbone for Dense Prediction without Convolutions (2021.2) [[Paper](https://arxiv.org/abs/2102.12122)]
- [**CPVT**] Conditional Positional Encodings for Vision Transformers (2021.2) [[Paper](https://arxiv.org/abs/2102.10882)]

- [TNT] Transformer in Transformer (NeurIPS 2021-2021.3) [[Paper](https://arxiv.org/abs/2103.00112)]
- [**Cait**] Going deeper with Image Transformers (2021.3) [[Paper](https://arxiv.org/abs/2103.17239)]
- [**DeepViT**] DeepViT: Towards Deeper Vision Transformer (2021.3) [[Paper](https://arxiv.org/abs/2103.11886)]

- [**Swin Transformer**] Swin Transformer: Hierarchical Vision Transformer using Shifted Windows (ICCV2021-2021.3) [[Paper](https://arxiv.org/abs/2103.14030)]
- [CeiT] Incorporating Convolution Designs into Visual Transformers (2021.3) [[Paper](https://arxiv.org/abs/2103.11816)]
- [LocalViT] LocalViT: Bringing Locality to Vision Transformers (2021.4) [[Paper](https://arxiv.org/abs/2104.05707)]
- [**MViT**] Multiscale Vision Transformers (2021.4) [[Paper](https://arxiv.org/abs/2104.11227)]
- [**Twins**] Twins: Revisiting the Design of Spatial Attention in Vision Transformers (2021.4) [[Paper](https://arxiv.org/abs/2104.13840)]

- [**Token Labeling**] All Tokens Matter: Token Labeling for Training Better Vision Transformers (2021.4) [[Paper](https://arxiv.org/abs/2104.10858)]
- [**ResT**] ResT: An Efficient Transformer for Visual Recognition (2021.5) [[Paper](https://arxiv.org/abs/2105.13677)]
- [**MLP-Mixer**] MLP-Mixer: An all-MLP Architecture for Vision (2021.5) [[Paper](https://arxiv.org/abs/2105.01601)]
- [**ResMLP**] ResMLP: Feedforward networks for image classification with data-efficient training (CVPR2021-2021.5) [[Paper](https://arxiv.org/abs/2105.03404)]
- [gMLP] Pay Attention to MLPs (2021.5) [[Paper](https://arxiv.org/abs/2105.08050)]
- [MSG-Transformer] MSG-Transformer: Exchanging Local Spatial Information by Manipulating Messenger Tokens (2021.5) [[Paper](https://arxiv.org/abs/2105.15168)]
- [**PVTv2**] PVTv2: Improved Baselines with Pyramid Vision Transformer (2021.6) [[Paper](https://arxiv.org/abs/2106.13797)]
- [TokenLearner] TokenLearner: What Can 8 Learned Tokens Do for Images and Videos? (2021.6) [[Paper](https://arxiv.org/abs/2106.11297)]
- **Demystifying Local Vision Transformer: Sparse Connectivity, Weight Sharing, and Dynamic Weight (2021.6)** [[Paper](https://arxiv.org/abs/2106.04263)]
- [P2T] P2T: Pyramid Pooling Transformer for Scene Understanding (2021.6) [[Paper](https://arxiv.org/abs/2106.12011v3)]
- [GG-Transformer] Glance-and-Gaze Vision Transformer (2021.6) [[Paper](https://arxiv.org/abs/2106.02277)]
- [Shuffle Transformer] Shuffle Transformer: Rethinking Spatial Shuffle for Vision Transformer (2021.6) [[Paper](https://arxiv.org/abs/2106.03650)]
- [**ViTAE**] ViTAE: Vision Transformer Advanced by Exploring Intrinsic Inductive Bias (2021.6) [[Paper](https://arxiv.org/abs/2106.03348)]
- [**CycleMLP**] CycleMLP: A MLP-like Architecture for Dense Prediction (2021.7) [[Paper](https://arxiv.org/abs/2107.10224)]
- [**CSWin Transformer**] CSWin Transformer: A General Vision Transformer Backbone with Cross-Shaped Windows (2021.07) [[Paper](https://arxiv.org/abs/2107.00652)]
- [**PS-ViT**] Vision Transformer with Progressive Sampling (2021.8) [[Paper](https://arxiv.org/abs/2108.01684)]
- **A Battle of Network Structures: An Empirical Study of CNN, Transformer, and MLP (2021.8)** [[Paper](https://arxiv.org/abs/2108.13002)]
- [**Swin Transformer V2**] Swin Transformer V2: Scaling Up Capacity and Resolution (2021.11) [[Paper](https://arxiv.org/abs/2111.09883)]
- [**MetaFormer**] MetaFormer is Actually What You Need for Vision (2021.11) [[Paper](https://arxiv.org/abs/2111.11418)]
- [**Imporved MViT**] Improved Multiscale Vision Transformers for Classification and Detection (2021.12) [[Paper](https://arxiv.org/abs/2112.01526)]
- [**ELSA**] ELSA: Enhanced Local Self-Attention for Vision Transformer (2021.12) [[Paper](https://arxiv.org/abs/2112.12786)]
- [**ConvMixer**] Patches Are All You Need [[Paper](https://openreview.net/pdf?id=TVHS5Y4dNvM)]



#### 2022

- [**ConvNeXt**] A ConvNet for the 2020s (2022.01) [[Paper](https://arxiv.org/abs/2201.03545)]



### Object Detection



### Semantic Segmentation

**[⬆ back to top](#Contents)**



Stay tuned and PRs are welcomed!

