title: QlikView11读书笔记 6
date: 2015-08-28 16:40:31
categories: QlikView
tags: 读书笔记
toc: true
---
# 第六章 building dashboard 创建dashboard
##### DAR策略
- D: Dashboard users, 常见于企业中高层管理者，他们仅需要关注某些KPI指标的状态，需要能够快速的鸟瞰整体信息
- A: Analysis users, 常见于业务人员，需要真正去了解指标背后的数据细节，不仅知道发生了什么，还要知道为什么发生，需要为这种类型用户提供多种方式查询分析数据，做情景假设分析等
- R: Report users, 大部分情况下，这种用户仅需要一些以表格形式的静态数据， 实现方式上常用straight table或pivot table。
 


##### 常见图表类型及介绍：
- Bar chart: 条形图最普通，也最通用，可用于表现趋势、对比等多种场合。
- Line chart: 折线图，常用于表现变化趋势。
- Combo chart: 组合图，以上两者的结合。
- Pie chart: 饼图，用于表现部分与总体以及其它部分的对比关系。
- Scatter chart: 散点图，用于表现因变量（expression）随自变量（dimension）变化的变化趋势，或相关性分析；
- Guage chart: 仪表盘，适合百分比类型的KPI展现；
![](http://7xoxf6.com1.z0.glb.clouddn.com/qlikview11notes61.png)
- Radar chart: 雷达图， 用于表现周期性变化的数据指标；
![](http://7xoxf6.com1.z0.glb.clouddn.com/qlikview11notes62.png)
- Grid chart: 网格图，可包含3个不同的维度
![](http://7xoxf6.com1.z0.glb.clouddn.com/qlikview11notes63.png)
- Block chart: 另一种形式的pie chart
![](http://7xoxf6.com1.z0.glb.clouddn.com/qlikview11notes64.png)
- Funnel chart: 漏斗图，常见的用法是销售漏斗图
![](http://7xoxf6.com1.z0.glb.clouddn.com/qlikview11notes65.png)
- Mekko chart: 本质上是多了一个维度的条形图，多出来的维度表现条形图的宽度；
![](http://7xoxf6.com1.z0.glb.clouddn.com/qlikview11notes66.png)
- Straight table: regular table, 好处是可以用来做mini chart
![](http://7xoxf6.com1.z0.glb.clouddn.com/qlikview11notes67.png)
- Pivot table: 水晶透视表
 
- 最后，再上一张大杀器：
![](http://7xoxf6.com1.z0.glb.clouddn.com/qlikview11notes68.jpg)