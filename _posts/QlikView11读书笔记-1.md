title: QlikView11读书笔记 1
date: 2015-08-17 15:41:45
categories: QlikView
tags: 读书笔记
---
# 第一章 初识QlikView
 
### 第一节 什么是Qlikview？
- QlikView是一个工具，一个商业智能分析（BusinessIntelligence，简称BI）的工具。

- QlikView是由QlikTech开发的。QlikTech 成立于1993，瑞典隆德。今天，她的研发中心仍然设在隆德，而美国及国际总部分别设在拉德诺郡和宾夕法尼亚州。QlikTech 在世界各地都设有办事处及合作伙伴。QlikTech的目的就是为企业提供一种获得保持企业生命力的信息的管道。QlikTech能够提供快捷、强效、低成本的数据分析及报表解决方案，能够提高整个企业的洞察力，并增强企业的决策能力。通过不断地创新技术和无与伦比的服务，将说明客户实现他们的愿望。

- 请看高德（Gartner）发布的2015年[BI产品和分析产品魔力象限图](http://www.qlik.com/us/explore/resources/analyst-reports/gartner-magic-quadrant-business-intelligence-bi-platform)，QlikView在这份报告图中排在第一象限，即领导者象限。

![](http://7xoxf6.com1.z0.glb.clouddn.com/qlikview11notes11.png)
 
- QlikView和传统BI产品有什么不一样？
相比于传统BI厂商（ORACLE, SAP, IBM, Microsoft）所提供的IT用户驱动的BI产品（BIEE, BW/BO, Cognos, SSIS/PS/AS）, QlikView能够为真正的业务用户提供自助式的使用体验，用户将可以更快速，更精准地创建所需要的动态的dashboard和report，并对数据进行即席分析, 业务用户对IT用户的依赖度大大降低。
 
- 除了使用对象的不同，真正使得QlikView区别于其他BI产品的特性有以下几点：
 1. ‘自动关联’的全新用户体验；传统BI产品在访问数据的时候必须按照预先定义好数据的存储路径才能访问到所需要的数据。Qlik改变了这一点，如下图中所示，用户可以从任意级别的数据访问到其他级别的数据，不需要遵循特定的访问路径，显然这更符合人类思维对事物的认识习惯。Qlik把这个技术称为‘业务发现’，以区别于传统的‘数据发现’。
![](http://7xoxf6.com1.z0.glb.clouddn.com/qlikview11notes12.png)
 2. 内存计算；QlikView区别于其他BI产品的核心在于他是基于内存计算，数据建模、存储全部在RAM中完成，自然意味着更快的处理速度，也带来更好的用户体验；
 3. 引用方式；传统BI产品是靠某个公司和企业的IT部门选型好以后，从整个公司到具体部门自上而下的方式来推广使用，而QlikView更多的是由某个部门开始使用，然后慢慢推广到整个部门，再到整个公司这样一种自下而上的引用方式。
 
### 第二节 初识QlikView
##### QlikView中所有数据的状态用三种颜色表示，分别是
- 绿色：当前选中的数据
- 白色：关联的可选数据
- 灰色：不关联的数据
 
##### Cyclic Groups：
- 预先定义好的一组dimension字段的list，实际开发中常用于在有限的空间内添加多个观察维度字段，类似于走马灯的效果；
 
##### DrillDown Groups:
- 同上，也需要开发者预先定义，但添加的维度字段有一定的逻辑层级关系要求，如年-月-日，或省-市-县等；
 
##### Containers:
- 在同一块区域可以切换显示不同的对象，也是节约空间的一种非常有用的sheet object.
 
### 第三节 QlikView背后的组件和技术
- QlikView数据流图
![](http://7xoxf6.com1.z0.glb.clouddn.com/qlikview11notes13.png)
- 更完整的QV架构图
![](http://7xoxf6.com1.z0.glb.clouddn.com/qlikview11notes14.png)
##### QlikView Publisher主要功能
- 所有程序文件数据加载、减少、文件分发、任务调度以及外部事件触发。
##### QlikView Server主要功能
- 文件存储、数据计算聚集。当publisher没有license的时候，server可以代替reload数据的功能。
##### QlikView Access Point
- 统一的文件访问portal。