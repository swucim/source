title: 中国名医琅琊榜数据分析2-数据可视化的QlikView实现
date: 2015-12-09 17:00:28
tags: 可视化案例
categories: QlikView
---
## 写在前面
承接上文，本文继续对收集的中国名医琅琊榜数据进行建模并使用QlikView实现可视化的Dashboard。

QlikView是一款来自瑞典的BI工具，Gartner把它列在Leaders象限并称为Magic Product。 2009年Aberdeen年把它作为BI市场唯一的"Champion"。 QlikView引领了内存型BI产品的方向，也代表着下一代BI产品的方向。

很多时候在网页上爬取下来的数据有很多的‘脏数据’，即不符合要求的数据，需要对这些数据进行提纯处理，获得我们真正关心的数据。对应在BI的概念里面，我们把从数据从业务系统到数据仓库转移的这一过程称之为'ETL',即抽取、转换、加载的过程。然后再在数据仓库的基础上，对数据进行建模供后续的可视化分析、展示使用。本文所涉及到的数据量较小，无法真正体现出ETL和建模这两个过程，不过既然是个Demo，做到心里有数就行。

## 数据抽取

源数据表（对应BI项目里面的业务系统数据库表）
<br>![](http://7xoxf6.com1.z0.glb.clouddn.com/top10drtables.png)

QlikView内置了ODBC, OLE DB, Plain TEXT, CSV, Excel, XML等各种数据类型的驱动程序，我们选择ODBC的方式连接本地数据库，如果前面数据爬取保存结果是其他文件格式，也可以选择对应的驱动类型。

## 数据建模

数据建模是一个很重要的过程，模型的好坏决定了数据访问的速度，也决定了数据存储所需空间的大小。时间和空间，永远是辩证的两个因素，你可以选择牺牲数据存储方面的开销，将数据保存成一整张表，从而提高访问速度，也可以反其道而行。不过，在真正的项目里，我们一般都是选择两者均衡的星型模型。

![](http://7xoxf6.com1.z0.glb.clouddn.com/qlikview11notes41.png)

最终形成的数据模型如下图所示：
![](http://7xoxf6.com1.z0.glb.clouddn.com/top10drtop10dr_model.png)

## 数据可视化

制作Dashboard的过程比较简单，建议大家还是下载一个QlikView程序真正操作一下吧，这里贴几张图，后续再针对图中的数据做进一步说明。（待续）
![](http://7xoxf6.com1.z0.glb.clouddn.com/top10drdoctor1.png)

![](http://7xoxf6.com1.z0.glb.clouddn.com/top10drdoctor2.png)

![](http://7xoxf6.com1.z0.glb.clouddn.com/top10drdoctor3.png)

![](http://7xoxf6.com1.z0.glb.clouddn.com/top10drdoctor4.png)

