# 初链——打造承载未来商用去中心化应用的公链（二）
###### 作者：刘乐元
继上一篇综述之后，可能大家对区块链有一定的认识了，我继续研读了TrueChain的相关内容，今也通过新闻推送看到了区块链发展的相关新闻，可以说前途一片大好。今天这一篇文章主要来讲讲我所认为共识算法以及TrueChain的相关机制的东西，这一篇大部分都是干货，请做好接受准备。
## 1 共识算法
简单的概念说明我就不说了，网上一搜一大堆。我要强调的是共识机制是核心和重要的，所以TrueChain在共识机制的选择上下了很大的功夫，它采用的是将POW共识（工作量证明共识）和PBFT（拜占庭容错共识）混合的混合机制，在保证去中心化本质的基础上，实现高性能、高可靠性的公链开发，以承载规模化商用 Dapp 运行的目标。看了TrueChain的白皮书之后我发现TrueChain其实是一种改进版的PBFT，但是PBFT的缺陷是限制了加入的节点，然而POW是不限节点的所以相关的理论技术上的可行的，接下来我会详细讲讲这两个算法的详细知识。
### 1.1 PBFT共识（拜占庭容错共识）
在此之前，你们可以自行了解一下拜占庭将军问题，其实主要就是在战争当中如何把两支队伍在考虑叛徒的情况下获得通信，一致对抗敌人取得胜利的问题，有兴趣的可以具体了解，了解之后你就会知道PBFT共识的作用是什么。PBFT共识主要是通过多次网络请求确认，最终获得多数共识，其中确保一致性主要分为这三个步骤：预准备、准备和确认。具体流程如下图所示：

![avatar](https://github.com/truechain/wiki/blob/master/analysis/truechain-consensus-core/img/1.1.png)

具体步骤如下：
1. 请求：请求端发送请求到节点A
2. 预准备：服务端A收到请求后进行广播至B、C和宕机。
3. 准备：B、C收到后记录并再次广播。
4. 确认：A、B、C节点在准备阶段，若收到超过一定数量的相同请求，则进入确认阶段，广播确认请求。
5. 反馈：A、B、C节点在确认阶段，若收到超过一定数量的相同请求，则对请求端进行反馈。
以上就是PBFT共识确保一致性的过程，因为拜占庭容错能够容纳将近1/3的错误节点误差，所以很多的区块链都应用了该共识，当然我们TrueChain也应用了该共识。
### 1.2 POW共识（工作量证明共识）
其实说白了POW就是一种按劳分配，即证明了你的付出和你做的工作量你就能达到认可。打个比方人能流利的说英语（通过学习之后），那么那个人一定在这个技能上投入了足够的工作量，当然这是我简单通俗的理解，具体的概念性的东西可以上网搜索而知。但是pow到底能够做些什么，如何做的呢，这就是技术层面上的东西了。当然在TrueChain的白皮书和黄皮书当中做了仔细的解释。

其中他们的优缺点如下所示：

![avatar](https://github.com/truechain/wiki/blob/master/analysis/truechain-consensus-core/img/1.2.png)

## 2 TrueChain的混合共识机制
如TrueChain黄皮书所说，TrueChain考虑了一致性、活跃度、交易终结性和安全保障、轮值委员会成员的频率和物理时间戳限制等优化问题，最终决定采用混合共识机制，补偿了PBFT的存在可伸缩性和伪去中心化的问题又补偿了POW欠缺的速率等等问题，这无不证明是区块链在公链开发上的一个重大突破。在TrueChain的设计上采用了DailyBFT和混合委员会选举，选出来的委员会如果变现的好那么定期更换委员会的时候就可以不进行更换，如若不然。在具体的应用设计上TrueChain打破了物理时间的限制，他们试图通过合并一个被称为粘性时间戳的限制来减少这些问题，并且通过计算和数据分片确保投机事务的执行，这样在委员会选择过程和事务执行过程中起到了很好的帮助，其中在黄皮书中还提到了关于物理时间戳的额外验证的算法，如果感兴趣的同仁可以查看TrueChain进行了解。
## 3 说明
以上就是我对TrueChain混合共识算法的一些认识和交流。我相信不断的创新过程能碰撞出不同的科技成果，同样rueChain也在不断的更新和创造，我相信在未来公链开发的道路上，TrueChain会发挥最大的实力，在接下来的工作当中我会继续研究TrueChain的相关算法，并进行分享和分析。                                                                 
作者：刘乐元
