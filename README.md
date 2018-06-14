# SentenceSim
 中文短文句相似度的几种方法，主要包括基于知网的，onehot向量模型，基于word2vec，基于哈工大sdp及其融合算法,LSTM算法
 
 中文问句相似度计算在问答系统中有着极其重要的作用，在人工智能还未能实现自动答案产出的现阶段，利用已有的问题-答案集，通过短问句的相似度计算方法，发现和用户查询意图最近接的问句，是问答系统研究的一个重要方向。
## 当前版本
 v1.1
## 主要内容
 给出了基于知网、传统词向量、word2vec以及语义依存分析的短问句相似度算法，并根据实验结果分析了不同方法的优缺点。基于传统词向量的one-hot向量表示方法没有考虑问句中的语义信息，在计算效果上存在一定局限性，由于知网专业领域词汇的收录不全，也不能在此数据集上取得很好效果。通过word2vec方法训练中文wiki数据以及结合哈工大LTP平台的语义依存分析，以及结合专业领域的词汇表，能够取得不错的效果。使用Stanford LSTM开源代码，实现在中文文本上的相似读计算，取得比word2vec更好的效果
## 代码应用
 `Sensim.java` 是整个项目的入口，在main函数里面可以配置数据文件目录，以及词向量文件、sdp分析结果文件。
 ``` java
 DataSet.Init("corpus_utf8_del.txt");
 DataSet.InitWord2vec("vecmodel.bin");
 DataSet.InitSdp("sdpresy.txt");
 DataSet.Run("word2vec", 10);
 ```
 DataSet类可以通过Init函数配置数据文件的路径，InitWord2vec函数配置训练好的词向量文件路径，InitSdp函数配置sdp语法分析结果的文件路径。Run函数有两个参数，第一个是要使用的算法的名字：
 * hownet -> 应用知网
 * onehot -> onehot词向量表示
 * word2vec -> 应用word2vec训练的Wiki词向量
 * sdp -> 应用哈工大的sdp语法分析
 * word2vec-sdp -> 两种方法融合

第二个参数是确定候选集的大小，一般可取1,3,5,10

## 更新
* 2016/1/15 上传SentenceBaseWord2vec项目
* 2016/4/6 上传此项目，此项目后续更新
* 2016/4/20 增加LSTM代码

## 引用
1. [知网](http://www.keenage.com/html/c_index.html)

2. [https://github.com/daishengdong/WordSimilarity](https://github.com/daishengdong/WordSimilarity)

3. [Mikolov, T.; Chen, K.; Corrado, G.; and Dean, J. 2013a.Efficient estimation of word representations in vector space.Proceedings of ICLR.](http://arxiv.org/abs/1301.3781)

4. [http://www.ltp-cloud.com/](http://www.ltp-cloud.com/)

5. [http://www.52nlp.cn/中英文维基百科语料上的word2vec实验/comment-page-1](4. http://www.52nlp.cn/中英文维基百科语料上的word2vec实验/comment-page-1)

6. [https://github.com/stanfordnlp/treelstm](https://github.com/stanfordnlp/treelstm)

## Connect
ICA fssqawj fssqawj@gmail.com
