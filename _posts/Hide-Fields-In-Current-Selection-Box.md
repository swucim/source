title: Hide Fields In Current Selection Box
date: 2015-09-27 20:23:49
categories: 数据可视化开发
tags: [QlikView, 转载]
---
#### Introduction:

When loading data from complex data sources there are fields in the data model that are required to be pulled in that you do not want to be visible to the end users. We may just want them to treat the fields like System Fields.

This can be achieved by a System Variable named “HidePrefix”. Using this we can make our own fields visible or not based on the same check box.

Let me explain this functionality with an example.

#### Explanation:

Decide the character which you would like to use as prefix fields you wish to hide. In this example, the character [~] is used to prefix.

1. set HidePrefix='~' ;



2. Loading a sample data in the qlikview to explain the functionality.

![](http://7xoxf6.com1.z0.glb.clouddn.com/devhide1.png)

3. Selecting the fields and having a “current selection” object to explain the example.

![](http://7xoxf6.com1.z0.glb.clouddn.com/devhide2.png)

4. Include a preload statement to include column to be prefixed as shown in the screenshot below.

![](http://7xoxf6.com1.z0.glb.clouddn.com/devhide3.png)

5. Now, reload the QVW to see the prefixed column. Once the prefixed column is visible in the qlikview, try selecting the field.

![](http://7xoxf6.com1.z0.glb.clouddn.com/devhide4.png)

6. The prefixed column selection will not be available in the Current Selection object in qlikview.