---
title: 层次文本分类论文（Hierarchical Text Classification）
date: 2019-11-12 14:52:26
tags:
  - NLP
categories:
  - 啦啦蕾的学习笔记～
  - 论文分享
  - 文本分类
---

**层次文本分类**是一种特殊的文本分类任务。它的分类标签具有树状层次结构。
### 存在问题
  - 使用分类标签结构信息。
  - 类别规模过大。
  - 类别对应的训练样本数目不足且不平衡。
<!--more-->                                    

### 论文集锦
| 序号 | 论文标题 | 发表机构 | 简单描述 | 代码 | 备注 |
| --- | --- | --- | --- | --- | --- |
| 00   | **A Survey of Hierarchical Classification**                  | 2011                      | 层次分类综述。flat、local（分三种）、big bang (global)       |                                                              |                                                              |
| 01   | Hierarchical Text Classification and Evaluation              | IEEE 2001                 | 定义了多级分类两种评价指标。基于类别相似度和相似距离。       |                                                              |                                                              |
| 02   | Label Embedding Trees for Large Multi-Class Tasks            | NIPS 2010 Bengio          | 没看明白。。。                                               |                                                              |                                                              |
| 03   | Hierarchical multi-label classification using local neural networks | 计算机与系统科学学报 2014 |                                                              |                                                              | [链接](https://www.sciencedirect.com/science/article/pii/S0022000013000718) |
| 1    | Hierarchical Deep Convolutional Neural Network for Large Scale Visual Recognition | IEEE 2015                 | 视觉识别任务，**HDCNNs**，将embedding deep CNNs引入到分类层次结构中 |                                                              |                                                              |
| 2    | **Initializing neural networks for hierarchical multi-label text classification** | BioNLP 2017               | 用训练数据中的标签共现来初始化最后的隐层参数。               |                                                              |                                                              |
| 3    | **HDLTex: Hierarchical Deep Learning for Text Classification** | ICMLA 2017                | 二级分类，一级训练完划分文档，二级再训练                     | [Keras](https://github.com/kk7nc/HDLTex)                     |                                                              |
| 4    | **Hierarchical Multi-Label Classification Networks**         | ICML 2018                 | **HMCN**。HMCN-F前馈、HMCN-R循环，融合全局和局部处理方式     |                                                              |                                                              |
| 5    | Large-Scale Hierarchical Text Classification with Recursively Regularized Deep Graph-CNN | WWW 2018                  | **DGCNN**。Recursive Regularization loss function            |                                                              |                                                              |
| 6    | An Analysis of Hierarchical Text Classification Using Word Embeddings | Information Sciences 2018 | 使用词嵌入（GloVe, word2vec, and fastText）+机器学习分类算法（fastText, XGBoost, SVM, and Keras’ CNN） |                                                              |                                                              |
| 7    | **A Hierarchical Neural Attention-based Text Classifier**    | EMNLP 2018                | encoder：bilstm编码word，decoder：每一级的label与隐层编码结果进行attention。 | [Pytorch](https://github.com/koustuvsinha/hier-class)        | [层次分类数据集](https://github.com/fatecbf/toutiao-multilevel-text-classfication-dataset/)<br>后续要看的参考文献3篇 |
| 8    | **Learning Hierarchical Category Structure for Multi-label Short Text Categorization** | EMNLP 2018                | **HFT-CNN**。Hierarchical Fine-tune CNN。**短文本分类**，类似**迁移学习**，基于每个父节点的local classification，父节点嵌入层和卷积层参数共享给子节点。打分机制：BSF和MSF。 | [Chainer](https://github.com/ShimShim46/HFT-CNN)             |                                                              |
| 9    | [Weakly-Supervised Hierarchical Text Classification](#Weakly-Supervised-Hierarchical-Text-Classification) | AAAI 2019                 | **WeSHClass**。1.提供少量类相关词或文档，使用语言模型生成伪数据。2.利用伪数据构建预训练局部分类器。3.融合所有局部分类器，生成全局分类器，在真实数据上迭代自训练。4.阻塞机制，防止强制性叶子节点预测。 | [GitHub](https://github.com/yumeng5/WeSHClass)               |                                                              |
| 10   | **Hierarchical Text Classification with Reinforced Label Assignment** | EMNLP 2019                | **HiLAP**。**将层次分类视为一个马尔可夫决策过程**，学习一个Label **Assignment** Policy决定当前实例放在哪个标签上，啥时候停止。 | [GitHub](https://github.com/morningmoni/HiLAP)               |                                                              |
| 11   | **NeuralClassifier: An Open-source Neural Hierarchical Multi-label Text Classification Toolkit** | ACL 2019                  | 腾讯的开源工具，pytorch，为了快速建立层次多标签分类神经网络模型。提供多种文本编码器，如fasttext、textcnn、textrnn等。 | [GitHub](https://github.com/Tencent/NeuralNLP-NeuralClassifier) | 后续要了解的：region embbedding                              |
| 12   | **Hierarchical Multi-label Classification of Text with Capsule Networks** | ACL 2019                  | 使用最简单的**胶囊网络**来进行层次分类。分类不一致策略。利用标签初始化权重。 | [GitHub](https://github.com/uhh-lt/BlurbGenreCollection-HMC) |                                                              |
| 13   | **Hierarchical Transfer Learning for Multi-label Text Classification** | ACL 2019                  | **HTrans**。利用**迁移学习**。给每个类别训练二分类器，父的参数给子类用，输出层训练，用高学习率；其他层参数保持，用低学习率；冻结嵌入层。训练优化类别权重。 |                                                              |                                                              |
|      |                                                              |                           |                                                              |                                                              |                                                              |

A structured self-attentive sentence embedding 

Generative and discriminative text classification with recurrent neural networks 

### 专利分类毕业论文

参考链接：[知网](http://kns.cnki.net/kns/brief/Default_Result.aspx)、

| 论文标题                                         | 作者   | 时间 | 来源         | 简单描述                                                     | 备注 |
| ------------------------------------------------ | ------ | ---- | ------------ | ------------------------------------------------------------ | ---- |
| 基于深度学习的专利文本分析方法研究               | 王英瑜 | 2019 | 北京邮电大学 | topic model + cnn/rcnn                                       |      |
| 中文专利的自动分类                               | 牛世雄 | 2017 | 大连理工     | tf-idf特征提取，词向量+空间向量/词袋模型的文本表示，重点在于提出了新的文本表示方法 |      |
| 基于深度学习理论与方法的中文专利文本自动分类研究 | 马双刚 | 2016 | 江苏大学     | 分词+DAE自动编码器特征提取+SVM分类器                         |      |

&nbsp;

#### Weakly-Supervised Hierarchical Text Classification

- 摘要

  层次文本分类目的是将文本分类到给定层次中，这是实际任务。存在问题：1. 依赖大量训练数据 2. 不容易确定合适的分类级别（非强制性叶子节点预测）。

  本文提出一种弱监督神经网络方法。1. 它不需要大量训练数据，只需要几个弱监督信号，如与类相关的文档或关键字。2. 以此生成伪数据进行局部模型预训练，3. 再对真实未标注数据自训练，迭代的精化模型。4. 最后通过阻塞机制确定文档的合适级别。

- 方法

  用户提供少量与叶子类相关的信号（词或文档），父类是叶子类的聚合。

  Class category tree: $T$	Text Collection: $D=\lbrace D_1,D_2,...,D_N\rbrace$

  Word-level supervision: $S$ 	Document-level supervision: $D^L$

  - **Pseudo Document Generation 伪数据生成**：
    - **Modeling Class Distribution 建模类分布**：
      将每个类建模为高维球形概率分布。训练<code>Skip-Gram</code>模型学习词向量，对所有词嵌入标准化，映射在一个单位球上。**对于每个类 $C_j \in T$，语义建模为movMF分布的混合（这一步不是很理解，公式太复杂）。**
      **关键字集合检索**：1. 提供词，在词向量空间中找到最接近这几个词平均向量的几个关键字；2. 提供文档，使用<code>TF-IDF</code>权值从$D^L_j$中提取代表性关键字。
      优点：与直接使用弱监督信号相比，此方法具有平滑效果，降低了模型对弱监督信号的敏感度。

    - **Language Model Based Document Generation**：使用<code>LSTM</code>语言模型生成伪数据。生成$C_j$的伪文档：从$C_j$的movMF分布中抽取一个向量，选择向量空间中最接近的词作为序列的起始词。
      优点：1. 由于初始词直接来自类分布，可以保证生成的文档与$C_j$相关。2. 通过混合分布建模，$C_j$ 的每个子类的语义信息都有机会被包含在伪文档中，从而使训练后的神经模型具有更好的泛化能力。

  - **Local Classifier Pre-Training**：
    使用**伪数据**，为每个父类构建**预训练局部分类模型**$M_p$。为了避免对伪数据过拟合，在真实数据上表现不好，使用**伪标签$l^*_{ij}$**来代替<code>one-hot</code>编码，使用超参数$\alpha$表示伪数据中的**噪声**。
    $$
    l^*_{ij} = \begin{cases}
    (1-\alpha)+\alpha/m,\quad D^*_i\ is\ generated\ from\ class\ j\\
        \alpha/m,\quad otherwise
      \end{cases}
    $$
    $m$是相对应的子类数目，使用<code>[KL divergence](https://www.jianshu.com/p/43318a3dc715) loss</code>作为预测值$Y$到$L^*$的损失函数。
    $$
    loss = KL(L^*||Y)=\sum_i\sum_jl^*_{ij}log\frac{l^*_{ij}}{y_{ij}}
    $$
  - Global Classifier Self-Training**：
  
    对每一层都需要输出所有类的概率分布。从根开始融合局部分类器，使用条件概率公式累乘，构建全局分类器$G_k$。
  
    优点：**Greedy top-down**方法会有错误传播，且错误无法更正。通过累乘给了低级别纠正高级别错误的机会。
  
    在**未标记真实数据**，使用$G_k$进行预测并迭代精调。模型输出$y_{ij}$，$f_j$是**soft frequency**，设置的伪标签$L^{**}$，最小化<code>[KL divergence](https://www.jianshu.com/p/43318a3dc715) loss</code>：
    $$
    l^{**}_{ij}=\frac{y^2_{ij}/f_j}{\sum_{y'}y^2_{ij'}/f_{j'}},\ f_j=\sum_iy_{ij}
    $$
    当语料库中少于$\delta$的文档类分配更改时停止迭代。
  
  - **Blocking Mechanism**：
  
    为了强制性叶子节点预测，使用**阻塞机制**。当被分类到中间节点$C_j$时，使用其局部分类器的输出$q$，判断此刻是否需阻塞，即它若与<code>one-hot</code>接近则表示它应分配给相应子类，若与一致分布接近则停止。
  
    用<code>normalized entropy</code>作为阻塞度量，$m$是子类数$\geq2$，$0\leq\gamma\leq1$，$\gamma=1$表示无阻塞全被分到叶子。此度量one-hot时为0，均匀分布时为1。
    $$
    -\ \frac{1}{log\ m}\sum_{i=1}^{m}q_i\ log\ q_i > \gamma
    $$

- 实验

  在[The New York Times(NYT)](http://developer.nytimes.com/) - 5/25、[arXiv](https://arxiv.org/) - 3/53、Yelp Review - 3/5 三个数据上实验。

  基线：Hier-Dataless、Hier-SVM、CNN、WeSTClass、**No-global**、**No-vMF**、**No-selftrain**。

- 想法

  本文构造伪数据的方法值得借鉴学习。

  但是存在一个问题，此文是基于给定的数据集上生成伪数据进行训练，若是新增一批同源测试集，模型需要重新训练吗，若不那么模型是否能在新数据集上表现良好。

