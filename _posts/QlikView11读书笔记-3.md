title: QlikView11读书笔记 3
date: 2015-08-24 15:41:45
categories: QlikView11读书笔记
tags: QlikView
---
# 第三章 数据源
###### 总的说来，QlikView要抽取数据的数据来源分为五种类型：
1. 可以通过ODBC/OLE DB驱动访问的标准型的数据库系统，包含市场上大部分常见的的数据库系统软件，需注意ODBC和OLE DB两种配置方式的区别，以及64/32位版本问题；
2. 需要使用专有数据驱动或接口访问的数据系统，如必须用JDBC驱动访问的数据库、网络文件等；针对某些特定的数据系统，市场上有专门的数据接口(connector)软件或JDBC驱动程序，当然，大部分都是收费的。
3. 各种文件类型的数据文件，如EXCEL, CSV, TXT, XML等。
4. 除了以上三种，QlikView还支持自身的QVD、QVX文件加在数据，甚至可以通过二进制加载加载其他QVW文件的数据。
QVD(QlikView Data)： 只包含一张逻辑表，使用特殊算法压缩数据可达到90%，加载速度相比其他数据库可快10~100倍。使用qvd文件的另一个好处在于当需要多个qvw文件加载同一数据时，使用qvd文件可比直接从数据源加载大大加快速度以及节约硬件资源。同时配合使用qlikview publisher/server可以实现数据源增量加载自动更新等特性。
QVX(QlikView data eXchange)：和qvd类似，不同点在于qvx文件是由外部系统（如上面提到的第三方数据接口）产生，qvd只能由qlikview产生。使用qvx可以达到一定的优化效果，但相比qvd还是差了一些。
5. 第五种，LOAD INLINE