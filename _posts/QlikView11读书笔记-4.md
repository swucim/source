title: QlikView11读书笔记 4
date: 2015-08-25 16:29:21
categories: QlikView11读书笔记
tags: QlikView
---
# 第四章 数据模型
##### 维度模型 
- 由于实体关系模型在数据查询有着天然的不足，维度模型在构建数据仓库的时候成为了首选的数据模型结构。维度模型通常由事实表(fact table)和维度表(dimension table)两种类型的表组成，后者主要存储‘事实’类型的数据，如销售订单信息，而前者存储‘维度’信息，如订单所涉及到的买家卖家名称，地域，产品类别等固定的信息。进一步来讲，事实表和维度表的组织方式有以下几种
 1. 星形模型(star schema)：由1个事实表周围连上N多个维度表，维度表彼此之间没有任何连接；
 2. 雪花模型(snowflake schema)：1个事实表周围连上N个维度表，某些维度表继续扩展连接上其他维度表，如订单事实表连接到国家维度表，国家维度表继续扩展链接到地区、市维度表；
- 使用维度模型带来的好处是显而易见的：数据结构更易于理解，更节约内存空间，但也带来了复杂度的问题，并且，从查询时间上来说，所有的数据放在同一张表里面显然查询速度是最快的。那QlikView是如何取舍不同的数据模型的呢？这里有一张图表，从图表上可以看出，使用星形模型是比较平衡的最优选择。
![](http://7xoxf6.com1.z0.glb.clouddn.com/qlikview11notes41.png)
 
- Qualify: QlikView默认将含有相同字段名的表自动关联起来，那么如何两个含有相同字段名的表不自动关联呢？答案是使用'Qualify'关键字，同样地，取消不自动关联用'unqualify'.
 
##### 数据模型冲突，常见的数据模型冲突错误有两种：
1. 两张表存在不止一个相同的字段，这种情况被称为'synthetic keys';
![](http://7xoxf6.com1.z0.glb.clouddn.com/qlikview11notes42.png)
2. 数据模型中多个表之间构成数据关联回路，如：A通过字段1关联到表B，表B通过字段2关联到表C，表C又通过字段3关联到表A；
 
##### 解决模型冲突的方法：
![](http://7xoxf6.com1.z0.glb.clouddn.com/qlikview11notes43.png)
 
##### Table Preview
- 在Table Preview功能中，当鼠标悬停到表、字段上以后，会自动显示相关的信息，分别如下：
 1. 表信息：表名称、记录行数、字段数、key数量 （注意field字段和key的区别）
![](http://7xoxf6.com1.z0.glb.clouddn.com/qlikview11notes44.png)
 2. 字段信息：
 3. 字段名: [perfect key]每行有键值且唯一，并且subset ratio完整率100%
            [primary key]每行键值唯一但完整率不足100%
            [key] 两条都不满足
 4. 信息密度 information density: 每个字段所有非空记录所占比例
 5. subset ratio: 某字段在某个表中所有distinct value在所有表中可能的distinct value所占比例。
 6. tags: 其他信息标签。
![](http://7xoxf6.com1.z0.glb.clouddn.com/qlikview11notes45.png)