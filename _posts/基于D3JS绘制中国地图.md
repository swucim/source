title: 基于D3JS绘制中国地图
date: 2015-12-27 15:02:45
tags: [D3, JavaScript]
categories: JavaScript可视化
---
参照网上给出的一些教程，仿照D3JS官网上的[美国地图](http://bl.ocks.org/NPashaP/a74faf20b492ad377312)制作了一个中国版的地图，效果如下：

<iframe src="/html/ChinaMap.html" width="100%" height="100%" seamless="seamless"></iframe>

制作过程并不复杂，代码也很好理解，有几点值得记录一下：

- 替换js代码中的地理信息包可以以此类推制作出其他各种地图等不规则图形；
- 真实的业务数据要放在json或gexf数据文件里面方便引用；
- 如果像我一样是用hexo发布到网上的话切记js文件和html文件不要放到根目录下面的source目录下，而是要放到主题文件夹下面的source文件夹中，不然解析文件会出各种问题，巨坑！
- [这里](http://www.ourd3js.com/wordpress/?cat=80)有更多的关于使用D3制作地图的方法和教程(博主看到记得给我广告费)。

[完整代码](https://github.com/swucim/D3/tree/master/ChinaMap)