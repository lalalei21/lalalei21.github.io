---
title: Text Classification 文本分类论文
date: 2019-11-12 14:52:26
tags: [NLP, text classification]
comments: true
toc: true
reward: false
---
**文本分类**是**自然语言处理**中的一项基础任务，目的是将文本分配给指定标签中的一个或多个。
通过将近年来看过的顶会论文集中到一起，希望对以后的工作有一定的帮助。
参考链接：https://paperswithcode.com/task/text-classification
<!--more-->

## 论文总结

| 序号 | 论文标题                                                     | 发表机构    | 简单描述                                                     | 代码                                                         | 备注                                                  |
| ---- | ------------------------------------------------------------ | ----------- | ------------------------------------------------------------ | ------------------------------------------------------------ | ----------------------------------------------------- |
| 0    | **Text Classification Algorithms: A Survey**                 |             | 文本分类综述                                                 | [GitHub](https://github.com/kk7nc/Text_Classification)       | 1233467                                               |
| 1    | Convolutional Neural Networks for Sentence Classification    | ACL 2014    | TextCNN                                                      |                                                              |                                                       |
| 2    | A Convolutional Neural Network for Modelling Sentences       | ACL 2014    | DCNN                                                         |                                                              |                                                       |
| 3    | Recurrent convolutional neural networks for text classification | AAAI 2015   | RCNN                                                         |                                                              |                                                       |
| 4    | Hierarchical Attention Networks for Document Classification  | NAACL 2016  | HAN                                                          |                                                              |                                                       |
| 5    | Recurrent Neural Network for Text Classification with Multi-Task Learning | IJCAI 2016  | TextRNN                                                      |                                                              |                                                       |
| 6    | Deep Pyramid Convolutional Neural Networks for Text Categorization | ACL 2017    | DPCNN                                                        |                                                              |                                                       |
| 7    | Very deep convolutional networks for text classification     | EACL 2017   | VDCNN                                                        |                                                              |                                                       |
| 8    | Bag of Tricks for Efficient Text Classification              | EACL 2017   | FastText                                                     |                                                              |                                                       |
|      | A Structured Self-Attentive Sentence Embedding               | ICLR 2017   | Self-Attention                                               |                                                              |                                                       |
| 9    | Joint embedding of words and labels for text classification  | ACL 2018    | LEAM                                                         | [tensorflow](https://github.com/guoyinwang/LEAM)             |                                                       |
| 10   | Baseline Needs More Love-On Simple Word-Embedding-Based Models and Associated Pooling Mechanisms | ACL 2018    | SWEM                                                         | [tensorflow](https://github.com/dinghanshen/SWEM)            |                                                       |
| 11   | Sequence Generation Model for Multi-Label Classification     | COLING 2018 | SGM                                                          |                                                              |                                                       |
| 12   | Investigating Capsule Networks with Dynamic Routing for Text Classification | EMNLP 2018  | Capsule                                                      |                                                              | [理解胶囊网络](https://zhuanlan.zhihu.com/p/33955995) |
| 13   | Universal Language Model Fine-tuning for Text Classification | ACL 2018    | ULMFiT                                                       |                                                              |                                                       |
| 14   | Graph Convolutional Networks for Text Classification         | AAAI 2019   |                                                              |                                                              |                                                       |
| 15   | Adaptive Convolution for Text Classification                 | NAACL  2019 | 自适应卷积，根据不同输入（上一个卷积块的输出）动态生成filter。提出hash genetation。 | [pytorch](https://www.aclweb.org/anthology/attachments/N19-1256.Software.zip) |                                                       |
| 16   | Neural Attentive Bag-of-Entities Model for Text Classification |             | 利用实体信息                                                 |                                                              |                                                       |
|      | Topic Memory Networks for Short Text Classification          | EMNLP  2018 |                                                              |                                                              |                                                       |
|      | Simplifying Graph Convolutional Networks                     | ICML 2019   | GCN                                                          |                                                              |                                                       |
|      | Sentiment Classification using Document Embeddings trained with Cosine Similarity | ACL 2019    |                                                              |                                                              |                                                       |
|      | Improved neural network-based multi-label classification with better initialization leveraging label co- occurrence | NAACL 2016  |                                                              |                                                              |                                                       |
|      | Compositional coding capsule network with k-means routing for text classification |             |                                                              |                                                              |                                                       |
|      | Large-scale Multi-label Text Classification                  |             |                                                              |                                                              |                                                       |
|      | SEMI-SUPERVISED CLASSIFICATION WITH GRAPH CONVOLUTIONAL NETWORKS |             |                                                              |                                                              |                                                       |
|      |                                                              |             |                                                              |                                                              |                                                       |
|      |                                                              |             |                                                              |                                                              |                                                       |
|      |                                                              |             |                                                              |                                                              |                                                       |
|      |                                                              |             |                                                              |                                                              |                                                       |
&nbsp;
## 专利分类论文总结

参考链接：[知网](http://kns.cnki.net/kns/brief/Default_Result.aspx)、

| 论文标题                                         | 作者   | 时间 | 来源         | 简单描述                                                     | 备注 |
| ------------------------------------------------ | ------ | ---- | ------------ | ------------------------------------------------------------ | ---- |
| 基于深度学习的专利文本分析方法研究               | 王英瑜 | 2019 | 北京邮电大学 | topic model + cnn/rcnn                                       |      |
| 中文专利的自动分类                               | 牛世雄 | 2017 | 大连理工     | tf-idf特征提取，词向量+空间向量/词袋模型的文本表示，重点在于提出了新的文本表示方法 |      |
| 基于深度学习理论与方法的中文专利文本自动分类研究 | 马双刚 | 2016 | 江苏大学     | 分词+DAE自动编码器特征提取+SVM分类器                         |      |
|                                                  |        |      |              |                                                              |      |
|                                                  |        |      |              |                                                              |      |
|                                                  |        |      |              |                                                              |      |


&nbsp;
## 论文简述

#### Text Classification Algorithms: A Survey

大多数文本分类和文档分类系统可以分解为以下四个阶段：特征提取、降维、分类器选择和评估。

文本分类分为4个级别：文档级别、段落级别、句子级别、子句级别（算法获得句子内的子表达式的相关类别）

1. **Text Preprocessing** 数据预处理：消除噪音
分词、去除停用词、俚语和缩略词、关键标点符号和特殊字符、拼写检查、Stemming 词干提取等
2. **Feature Extraction** 特征抽取：信息特征化
   - **Weighted word** 加权词：
     - **TF/Bag of Words (BoW)**：最常用的，词袋，文本的主体被认为是一袋单词，单词列表按照个数被创建。忽略了语法和顺序，但是利用了计数特征。容易导致一些特别常用的词在文本表示中占主要地位。使用one-hot编码，由于词汇量可能达到数百万，导致矩阵十分稀疏。
     - **Term Frequency-Inverse Document Frequency (TF-IDF)**：tf 改进了召回率，idf 提高了准确率。克服了文档中常见术语的限制，但是无法考虑词之间的相似性。
   - **Word embedding** 词嵌入:
     - **Word2Vec**：CBOW-预测给定上下文的单词、Skip-gram model-预测给定单词的上下文，保持句子的句法和语义信息。缺点是没有充分利用语料信息。
     - **[Global Vectors](http://www.fanyeong.com/2018/02/19/glove-in-detail/#comments) ([GloVe](https://blog.csdn.net/mr_tyting/article/details/80180780))**：与word2vec相似。但是基于全局词频统计的词表征工具，它把单词表示成一个由实数组成的向量，捕捉到单词间的语义信息，如相似性、类比性，通过对向量的计算，如欧几里得距离和余弦相似度，可以计算两个单词的相似性。
     - **FastText**：类似于CBOW，两种模型都是基于Hierarchical Softmax，但引入了N-gram信息。适合大型数据+高效的训练速度，支持多语言表达，专注于文本分类。
     - **Context2vec**：从双向语言模型学习词向量。[**ELMo**](https://zhuanlan.zhihu.com/p/63115885)，相对于**GPT**和**Bert**，lstm特征抽取能力弱于transformer，双向拼接融合比一体化融合弱。
3. **Dimensionality Reduction** 降维：
   - **Component Analysis**：成分分析
     - **[PCA](https://zhuanlan.zhihu.com/p/32412043)**：主成分分析，最重要的降维方法之一。PCA作为降噪算法也是一个有价值的工具，可以帮助避免过拟合问题。
     - **[ICA]()**：独立成分分析
     - **LDA**：
     - **NMF**：
   - **Random Projection**：
   - **Autoencoder**：
     - CNN
     - RNN：
   - **T-distributed Stochastic Neighbor Embedding (t-SNE)**：
4. **Classification Techniques** 分类器：
   - **Rocchio Classification**：
   - **Boosting / Bagging**：投票分类技术。Boosting，弱学习算法
   - **Bagging**：
   - **Logistic Regression**：
   - **Naïve Bayes**：
   - **K-Nearest Neighbor (KNN)**：
   - **Support Vector Machine (SVM)**：
   - **Decision Tree**：
   - **Random Forest**：
   - **Conditional Random Field (CRF)**：
   - **Deep Learning**：
     RNN、CNN、DBN、HAN等，见其论文详解
   - **Semi-Supervised Learning**：
5. **Evaluation** 评价方法：







