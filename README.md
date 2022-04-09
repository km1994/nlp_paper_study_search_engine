# 【关于 NLP】 那些你不知道的事 —— 搜索引擎篇

> 作者：杨夕
> 
> 介绍：研读顶会论文，复现论文相关代码
> 
> NLP 百面百搭 地址：https://github.com/km1994/NLP-Interview-Notes
> 
> **[手机版NLP百面百搭](https://mp.weixin.qq.com/s?__biz=MzAxMTU5Njg4NQ==&mid=100005719&idx=3&sn=5d8e62993e5ecd4582703684c0d12e44&chksm=1bbff26d2cc87b7bf2504a8a4cafc60919d722b6e9acbcee81a626924d80f53a49301df9bd97&scene=18#wechat_redirect)**
> 
> 推荐系统 百面百搭 地址：https://github.com/km1994/RES-Interview-Notes
> 
> **[手机版推荐系统百面百搭](https://mp.weixin.qq.com/s/b_KBT6rUw09cLGRHV_EUtw)**
> 
> 搜索引擎 百面百搭 地址：https://github.com/km1994/search-engine-Interview-Notes 【编写ing】
> 
> NLP论文学习笔记：https://github.com/km1994/nlp_paper_study
> 
> 推荐系统论文学习笔记：https://github.com/km1994/RS_paper_study
> 
> GCN 论文学习笔记：https://github.com/km1994/GCN_study
> 
> **推广搜 军火库**：https://github.com/km1994/recommendation_advertisement_search
![](other_study/resource/pic/微信截图_20210301212242.png)

> 手机版笔记，可以关注公众号 **【关于NLP那些你不知道的事】** 获取，并加入 【NLP && 推荐学习群】一起学习！！！

> 注：github 网页版 看起来不舒服，可以看 **[手机版NLP论文学习笔记](https://mp.weixin.qq.com/s?__biz=MzAxMTU5Njg4NQ==&mid=100005719&idx=1&sn=14d34d70a7e7cbf9700f804cca5be2d0&chksm=1bbff26d2cc87b7b9d2ed12c8d280cd737e270cd82c8850f7ca2ee44ec8883873ff5e9904e7e&scene=18#wechat_redirect)**


- [【关于 NLP】 那些你不知道的事 —— 搜索引擎篇](#关于-nlp-那些你不知道的事--搜索引擎篇)
  - [介绍](#介绍)
    - [NLP 学习篇](#nlp-学习篇)
      - [理论学习篇](#理论学习篇)
        - [【关于 搜索引擎】那些你不知道的事](#关于-搜索引擎那些你不知道的事)
  - [参考资料](#参考资料)

## 介绍

### NLP 学习篇

#### 理论学习篇

##### [【关于 搜索引擎】那些你不知道的事](https://github.com/km1994/nlp_paper_study_search_engine)

- [【关于 搜索引擎】 那些你不知道的事](https://github.com/km1994/nlp_paper_study_search_engine/)
  - [搜索系统的架构设计](#搜索系统的架构设计)
    - [搜索 QP（query理解）的架构设计](#搜索-qpquery理解的架构设计)
  - [搜索j介绍](#搜索j介绍)
    - [搜索排序 介绍](#搜索排序-介绍)
    - [Embedding 搜索](#embedding-搜索)
      - [动机](#动机)
      - [Embedding 搜索优点](#embedding-搜索优点)
      - [Embedding的学习形式](#embedding的学习形式)
      - [Embedding 搜索 所关心的问题](#embedding-搜索-所关心的问题)
      - [参考资料](#参考资料)
    - [Query纠错](#query纠错)
      - [Query纠错 之  原理](#query纠错-之--原理)
      - [Query纠错 之 文本错误类型](#query纠错-之-文本错误类型)
        - [动机](#动机-1)
        - [常见的错误类型](#常见的错误类型)
      - [Query纠错 之 纠错结果类型](#query纠错-之-纠错结果类型)
        - [动机](#动机-2)
        - [介绍](#介绍)
        - [纠错结果类型](#纠错结果类型)
  - [搜索引擎两大问题](#搜索引擎两大问题)
    - [问题一：召回](#问题一召回)
      - [什么是召回？](#什么是召回)
      - [基于关键词的召回方法](#基于关键词的召回方法)
        - [什么是 基于关键词的召回方法 ？](#什么是-基于关键词的召回方法-)
      - [基于关键词的召回方法存在哪些问题？](#基于关键词的召回方法存在哪些问题)
        - [Q1：索引粒度如何选择问题](#q1索引粒度如何选择问题)
        - [Q2：保证 召回 有相关文档数问题](#q2保证-召回-有相关文档数问题)
        - [Q3：召回 候选 query 多样性问题](#q3召回-候选-query-多样性问题)
        - [Q4：召回 候选 query 无语义效果问题](#q4召回-候选-query-无语义效果问题)
      - [基于语义的召回方法](#基于语义的召回方法)
        - [什么是 基于语义的召回方法？](#什么是-基于语义的召回方法)
        - [基于语义的召回方法 的思路](#基于语义的召回方法-的思路)
        - [基于语义的召回方法 存在问题](#基于语义的召回方法-存在问题)
      - [参考资料](#参考资料-1)
    - [问题二：相关性](#问题二相关性)
      - [什么是 相关性？](#什么是-相关性)
      - [相关性 存在哪些问题？](#相关性-存在哪些问题)
      - [相关性方法介绍](#相关性方法介绍)
        - [计算场景角度](#计算场景角度)
        - [计算方法角度](#计算方法角度)
      - [参考资料](#参考资料-2)
  - [搜索未来新趋势](#搜索未来新趋势)
    - [1. 多模态搜索](#1-多模态搜索)
    - [2. 更语义搜索](#2-更语义搜索)
    - [3。 多轮搜索](#3-多轮搜索)

- [【关于 GECToR】 那些你不知道的事](https://github.com/km1994/nlp_paper_study_search_engine/tree/master/search_engine/PLMbasedRankingInBaiduSearch/)
  - 论文：Pre-trained Language Model based Ranking in Baidu Search
  - 论文地址：https://arxiv.org/abs/2105.11108
  - 论文出处：KDD'21
  - 动机：
    - 作为搜索引擎的核心， Ranking System 在满足用户的信息需求方面起着至关重要的作用；
    - 基于 PLM 的 Neural Rankers 难以直接应用：
      - （1）推理时延高：大规模神经 PLM 的计算成本过高，尤其是对于网络文档中的长文本，禁止将它们部署在需要极低延迟的 Online Ranking System 中；
      - (2) 目标不一致问题：基于 PLM 的训练目标 与 临时检索场景目标 存在不一致问题；
      - (3) 兼容性问题：搜索引擎通常涉及 committee of ranking components，如何 让 Fine-tuning PLM 得到的 Ranking System 与其 兼容，存在问题；
  - 论文方法：在线搜索引擎系统中部署最先进的中文预训练语言模型（即 ERNIE）时，贡献了一系列成功应用的技术来解决这些暴露的问题。
    - 首先，阐述了一种新颖的做法，以经济高效地汇总 Web 文档，并使用廉价但功能强大的 Pyramid-ERNIE 架构将结果汇总内容与查询联系起来。
    - 然后，赋予了一种创新范式来精细地利用大规模嘈杂和有偏见的点击后行为数据进行面向相关的预训练。
    - 提出了一种 针对 在线排名系统 的 human-anchored 微调策略 ，旨在稳定各种在线组件的排名信号。
  - 实验结果：大量的离线和在线实验结果表明，所提出的技术显着提高了搜索引擎的性能。

- [【关于 PLM for Web-scale Retrieval in Baidu Search 】 那些你不知道的事](https://github.com/km1994/nlp_paper_study_search_engine/tree/master/search_engine/PLMforWeb-scaleRetrievalInBaiduSearch/)
  - 论文：Pre-trained Language Model for Web-scale Retrieval in Baidu Search 
  - 论文地址：https://arxiv.org/abs/2106.03373
  - 论文出处：KDD'21
  - 介绍： Retrieval 是网络搜索中的一个关键阶段，它从十亿规模的语料库中识别出一个与查询相关的候选集。在 retrieval 阶段发现更多语义相关的候选集 有助于 向最终用户展示更多高质量的结果。
  - 动机：
    - 【语义匹配】：**如何 解决 用户 query 多样化和口语化问题？**
    - 【冷启动问题】：**对于 大多数 第一次出现的 query 和 doc，如何让 Retrieval Models 捕获 其对应语义信息？**
    - 【工程实践】：**如何 将 Retrieval Models 应用于 Baidu Search？**
  - 论文方法：论文描述了作者在 Baidu Search 中开发和部署的 Retrieval Models 。
    - 该系统利用了最近最先进的中文预训练语言模型，即通过知识整合 (ERNIE) 的增强表示，它促进了系统的表达语义匹配。
    - 基于 ERNIE 的 Retrieval Models 拥有：
      - 1）expressive Transformer-based semantic encoders：能够 帮助 Retrieval 充分捕获 query 和 doc 对应语义信息；
      - 2）多阶段训练范式：ERNIE 预训练模型 分别采用 不同的语料数据 进行 多阶段训练，提高模型 泛化能力；
    - 系统工作流程：基于 ERNIE 的 Retrieval Models 结合 传统 Retrieval Models 和 Deep Retrieval Models，并 采用  lightweight post-retrieval filtering module 引入更多的统计特征（例如，点击率、停留时间），来对上述 Retrieval Models 的 检索结果 进行 统一过滤，；
    - 最终，该系统完全部署到生产环境中，并进行了严格的离线和在线实验。
  - 实验结果：
    - 该系统可以执行高质量的候选 retrieval ，特别是对于那些需求不常见的尾部查询。
    - 由预训练语言模型（即 ERNIE）推动的新 retrieval system 可以在很大程度上提高我们搜索引擎的可用性和适用性。


## 参考资料

1. [【ACL2020放榜!】事件抽取、关系抽取、NER、Few-Shot 相关论文整理](https://www.pianshen.com/article/14251297031/)
2. [第58届国际计算语言学协会会议（ACL 2020）有哪些值得关注的论文？](https://www.zhihu.com/question/385259014)
