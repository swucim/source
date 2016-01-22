title: QlikView11读书笔记 5
date: 2015-08-27 16:40:22
categories: QlikView11读书笔记
tags: QlikView
---
# 第五章 形成风格(Styling up)
 
- 设计风格是一个非常个性化的东西，不过也还是有一些通用的准则可以遵守，以便你的dashboard设计出来更加吸引人。
总的原则就是：尽量最小化非数据相关的部分。我们应该focus在显示数据，因此要尽可能减少非数据相关的对象如：边框、网格线、阴影、3D对象、光泽等等。（更多详情参考 Information Dahboard Design, writen by Stephen Few）
 
- 开发一个新的dashboard，首先要清楚的两个基本要素：
 1. 大部分用户在使用什么样的屏幕分辨率(如果非要在一个屏幕分辨率下放更多的对象，纵向滚动比横向滚动更易于接受)；
 2. dashboard的总体风格和布局方式。
- 一个layout example：
![](http://7xoxf6.com1.z0.glb.clouddn.com/qlikview11notes51.png)
##### QlikView Sheet对象
![](http://7xoxf6.com1.z0.glb.clouddn.com/qlikview11notes52.png) 
##### Chart类型
-  ![](http://7xoxf6.com1.z0.glb.clouddn.com/qlikview11notes53.png)
- 名称上比较容易搞混的是Table Box和Straight table, 前者是sheet object， 后者是一种图表类型，必须有dimension/expression。
 
- 移动对象： 按住Ctrl的同时按方向键移动对象每次移动一个像素，按住Ctrl+shift的同时按方向键，每次移动10个像素
 
- 复制对象：copy，clone = Ctrl + 拖动    linked copy = ctrl+shift +拖动
- **copy vs linked copy： 不同之处在于后者copy出来的对象其实都指向同一个对象ID，前者copy出来的对象有新的ID。**