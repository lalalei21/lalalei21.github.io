---
title: 层次文本分类论文（Hierarchical Text Classification）
date: 2019-11-12 14:52:26
tags: [NLP, text classification]
comments: true
toc: true
reward: false
---

**层次文本分类**是一种特殊的文本分类任务。它的分类标签具有树状层次结构。
### 存在问题
  - 使用分类标签结构信息。
  - 类别规模过大。
  - 类别对应的训练样本数目不足且不平衡。
<!--more-->                                    

### 论文集锦
| 序号 | 论文标题                                                     | 发表机构   | 简单描述                                                     | 代码                                                         | 备注                                                         |
| ---- | ------------------------------------------------------------ | ---------- | ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
| 0    | **A Survey of Hierarchical Classification**                  | 2011       | 定义多级分类的各种类型。flat、local（分三种）、big bang (global) |                                                              |                                                              |
| 1    | **HDLTex: Hierarchical Deep Learning for Text Classification** | ICMLA 2017 | 二级分类，一级训练完划分文档，二级再训练                     | [GitHub](https://github.com/kk7nc/HDLTex)                    |                                                              |
| 2    | **Hierarchical Multi-Label Classification Networks**         | ICML 2018  | **HMCN**。HMCN-F前馈、HMCN-R循环，融合全局和局部处理方式     |                                                              |                                                              |
| 3    | Hierarchical Deep Convolutional Neural Network for Large Scale Visual Recognition | IEEE 2015  | 视觉识别任务，**HDCNNs**，将embedding deep CNNs引入到分类层次结构中 |                                                              |                                                              |
| 4    | Large-Scale Hierarchical Text Classification with Recursively Regularized Deep Graph-CNN |            | **DGCNN**。Recursive Regularization loss function            |                                                              |                                                              |
| 5    | **Initializing neural networks for hierarchical multi-label text classification** | 2017       |                                                              |                                                              |                                                              |
| 6    | End to End Hierarchical Text Classification with Label Assignment Policy | ICLR 2018  | **HiLAP**。同一篇文章。                                      |                                                              |                                                              |
| 7    | Hierarchical Classification with Hierarchical Attention Networks |            | 就是在**HAN**结构上最后的输出上增加了分级结构，pooling一次分一级。 |                                                              |                                                              |
| 8    | Hierarchical Text Classification and Evaluation              |            | 定义了多级分类两种评价指标。基于类别相似度和相似距离。       |                                                              |                                                              |
| 9    | Weakly-Supervised Hierarchical Text Classification           | NAACL 2019 |                                                              |                                                              |                                                              |
| 11   | Hierarchical multi-label classification using local neural networks |            |                                                              |                                                              | [论文链接](https://www.sciencedirect.com/science/article/pii/S0022000013000718) |
| 1    | **A Hierarchical Neural Attention-based Text Classifier**    | EMNLP 2018 | encoder：bilstm编码word，decoder：每一级的label与隐层编码结果进行attention。 | [GitHub](https://github.com/koustuvsinha/hier-class)         | [多级分类数据集](https://github.com/fatecbf/toutiao-multilevel-text-classfication-dataset/)<br>后续要看的参考文献3篇 |
| 2    | **Learning Hierarchical Category Structure for Multi-label Short Text Categorization** | EMNLP 2018 | **HFT-CNN**。Hierarchical Fine-tune CNN。**短文本分类**，类似**迁移学习**，基于每个父节点的local classification，父节点嵌入层和卷积层参数共享给子节点。打分机制：BSF和MSF。 | [GitHub](https://github.com/ShimShim46/HFT-CNN)              |                                                              |
| 1    | **Hierarchical Text Classification with Reinforced Label Assignment** | EMNLP 2019 | **HiLAP**。**将多级分类视为一个马尔可夫决策过程**，学习一个Label **Assignment** Policy决定当前实例放在哪个标签上，啥时候停止。 | [GitHub](https://github.com/morningmoni/HiLAP)               |                                                              |
| 1    | **NeuralClassifier: An Open-source Neural Hierarchical Multi-label Text Classification Toolkit** | ACL 2019   | 腾讯的开源工具，pytorch，为了快速建立层次多标签分类神经网络模型。提供多种文本编码器，如fasttext、textcnn、textrnn等。 | [GitHub](https://github.com/Tencent/NeuralNLP-NeuralClassifier) | 后续要了解的：region embbedding                              |
| 2    | **Hierarchical Multi-label Classification of Text with Capsule Networks** | ACL 2019   | 使用最简单的**胶囊网络**来进行多级分类。分类不一致策略。利用标签初始化权重。 | [GitHub](https://github.com/uhh-lt/BlurbGenreCollection-HMC) |                                                              |
| 3    | **Hierarchical Transfer Learning for Multi-label Text Classification** | ACL 2019   | **HTrans**。利用**迁移学习**。给每个类别训练二分类器，父的参数给子类用，输出层训练，用高学习率；其他层参数保持，用低学习率；冻结嵌入层。训练优化类别权重。 |                                                              |                                                              |
|      |                                                              |            |                                                              |                                                              |                                                              |

Universal Language Model Fine-tuning for Text Classification

named-entity-recognition

Weakly-Supervised Hierarchical Text Classification

A structured self-attentive sentence embedding 

Generative and discriminative text classification with recurrent neural networks 