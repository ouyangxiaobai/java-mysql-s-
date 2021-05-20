# java mysql餐饮协同过滤系统+论文
下载地址：http://ym.maptoface.com/2021/05/20/java-mysql%e9%a4%90%e9%a5%ae%e5%8d%8f%e5%90%8c%e8%bf%87%e6%bb%a4%e7%b3%bb%e7%bb%9f%e8%ae%ba%e6%96%87/
项目介绍
java mysql餐饮协同过滤系统+论文

系统说明
目录

摘  要. 2

ABSTRACT 3

第一章 概述. 1

1.1        推荐系统开发背景. 1

1.2        开发目标. 2

1.3        本章小结. 3

第二章 推荐系统的开发分析. 3

2.1  推荐系统的定义. 3

2.2  推荐系统的体系结构. 4

2.3  推荐系统的评价. 4

2.4  本章小结. 4

第三章 系统相关技术研究. 5

3.1  协同过滤算法. 5

3.2  基于内容的推荐算法. 8

3.3  基于二部图的推荐算法. 9

3.4  混合推荐算法. 9

3.5  Spring boot框架. 10

3.6  MySQL数据库. 10

3.7  本章小结. 11

第四章  餐饮推荐系统的需求分析. 11

4.1  系统功能需求分析. 12

4.2  可行性分析. 12

4.3  本章小结. 13

第五章  数据库设计. 13

5.1  数据库设计原则. 13

5.2  数据库E-R图设计. 14

5.3  数据库表设计. 16

第六章  系统实现与测试. 19

6.1  后台管理. 19

6.2  商品管理以及产品列表. 19

6.3  前台管理. 20

6.4  系统测试. 20

6.4.1测试的目的与目标. 20

6.4.2测试方法. 21

6.4.2测试用例. 22

6.4.3测试结论. 23

第七章 总结. 24

参考文献. 1

致 谢. 2







 摘  要
随着电子商务的快速发展，大数据以及云计算时代的到来，协同过滤推荐系统成为了电子商务网站的核心技术之一。本文分析了个性化推荐的特点，发展。作为协同过滤推荐系统的核心----推荐算法，本文讲述了常见的几种算法（协同过滤，基于内容推荐，社会网络（二部分图）算法，混合算法），比较了这几种算法的优劣。最后根据餐饮的特点，提出了自己的一些关于推荐算法的想法。

主要采用spring boot框架，及JAVA语言，IDE开发环境，在设计过程中，充分保证了系统代码的良好可读性、实用性、易扩展性、通用性、便于后期维护、操作方便以及页面简洁等特点。



关键词：数据挖掘；推荐系统；个性化；协同过滤

                                    ABSTRACT
With the rapid development of e-commerce, the advent of the era of big data and cloud computing, personalized recommendation system has become one of the core technology of e-commerce sites. This paper analyses the characteristics of personalized recommendation, development. As the core of the personalized recommendation system, recommendation algorithm, this paper tells the story of several common algorithm (collaborative filtering and content-based recommendation, social network (2 parts) algorithm, the hybrid algorithm), comparing the several kinds of advantages and disadvantages of the algorithm. Finally according to the characteristics of the food and beverage, the author put forward some ideas about the recommendation algorithm.

It mainly adopts spring boot framework, Java language and IDE development environment. In the design process, it fully ensures the good readability, practicability, expansibility, generality, easy maintenance, easy operation and simple page of the system code.



Key words: data mining; Recommendation system; Personalized; Collaborative filtering



第一章 概述
1.1 推荐系统开发背景
我们已经进入了一个信息爆炸的时代，每时每刻都有海量信息产生，然而这些信息并不全是个人所关心的，用户从大量的信息中寻找对自己有用的信息也变得越来越困难。另一方面，信息的生产方也在绞尽脑汁的把用户感兴趣的信息送到用户面前，每个人的兴趣又不尽相同，所以可以实现千人千面的推荐系统应运而生。简单来说，推荐系统是根据用户的浏览习惯，确定用户的兴趣，通过发掘用户的行为，将合适的信息推荐给用户，满足用户的个性化需求，帮助用户找到对他胃口但是不易找到的信息或商品。推荐系统在互联网和传统行业中都有着大量的应用。在互联网行业，几乎所有的互联网平台都应用了推荐系统，如资讯新闻/影视剧/知识社区的内容推荐、电商平台的商品推荐等；在传统行业中，有些用于企业的营销环节，如银行的金融产品推荐、保险公司的保险产品推荐等。根据QM报告，以推荐系统技术为核心的短视频行业在2019年的用户规模已超8.2亿，市场规模达2千亿，由此可见这项技术在现代社会的经济价值。

当前通过互联网提供服务的平台越来越多，相应的提供的服务种类(购物，视频，新闻，音乐，婚恋，社交等)层出不穷，服务“标的物”的种类也越来越多样(亚马逊上有上百万的书)，这么多的“标的物”怎么让需要它的人找到它， 满足用户的各种需要， 就是摆在企业面前的难题。

同时，随着社会的发展，受教育程度的提升，每个人都有表现自我个性的欲望。随着互联网的发展，出现了非常多的可以表达自我个性的产品，如微信朋友圈，微博，抖音，快手等，每个人的个性喜好特长有了极大展示的空间。另外从进化论的角度来说，每个人都是一个差异化的个体，是生而不同的，生而具有不同的性格特征，个人的生活成长环境又有极大差异，导致个人的偏好口味千差万别。“长尾理论”也很好的解释了多样化物品中的非畅销品可以满足人们多样化的需求，这些需求加起来不一定比热门物品产生的销售额小。

随着社会的进步，物质生活条件的改善，大家不必再为生存下来而担忧，所以大家有越来越多的需求是非生存需求，比如看书，看电影，购物等，而这些非生存的需求往往在很多时候是不确定的， 是无意识的，自己不知道自己需要什么。生存需求对人而言显得非常强烈而明显，比如你快饿死了，你的第一需要肯定是食物。不同于生存需求，面对非生存需求，人们实际上更愿意接受被动推荐的好的物品， 比如给你推荐一部电影，如果符合你的口味，你可能会很喜欢。

总结上面提到的三点，当今时代可选择的商品和服务这么多，而不同人的兴趣偏好又是截然不同，并且在特定场景下，个人对自己的需求不是很明确。在这三个背景驱动下，推荐系统应运而生。个性化推荐系统是解决上述三个矛盾的最有效的方法和工具之一。

为了更好的为用户提供服务， 在为用户提供服务的同时赚取更多的利润，越来越多的公司通过采用个性化推荐技术，辅助用户更快地发现自己喜欢的东西 。公司根据用户在产品上的行为记录，结合用户自身和“标的物”的信息， 利用推荐技术(机器学习的一个分支)来为用户推荐可能感兴趣的物品。

适用场景：
毕业论文、课程设计、公司项目参考

运行截图
        

关注【程序代做 源码分享】公众号获取更多免费源码！！！
