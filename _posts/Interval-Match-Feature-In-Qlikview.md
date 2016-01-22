title: "Interval Match Feature In Qlikview"
date: 2015-09-20 20:31:32
categories: 数据可视化开发
tags: [QlikView, 转载]
---
#### Introduction:
The **Interval Match** is one of the functions in Qlikview which can be used for discreet data to one or more dimensions that are changing over time**解决缓慢变化维的问题**. It is one of the powerful features that can be used for resolving with slowly changing dimensions by linking the specific key fields to the appropriate numeric intervals.
This can be used as prefix with Load or SQL Select Statements. This will help the use of avoiding joins, or case statements in the above mentioned scenarios thereby improving performance in large tables.
Explanation:
Explaining this great feature with a simple example.
Loading desired data in the table.
![](http://7xoxf6.com1.z0.glb.clouddn.com/devintervalmatch1.png)

The first table gives the information about the Grades for the particular range of marks. The second table gives the marks scored by different students (discrete values).
We’re going to load these two tables and linking the Grade field to Grade table.

![](http://7xoxf6.com1.z0.glb.clouddn.com/devintervalmatch2.png)

After loading the data, we can able to get the table as shown in the screenshot below.

![](http://7xoxf6.com1.z0.glb.clouddn.com/devintervalmatch3.png)

Further, if we add one more field ‘subject’ to Grades table, and one more field ‘sub’ to Marks table, the interval match should be used as below:

![](http://7xoxf6.com1.z0.glb.clouddn.com/devintervalmatch4.png)

Then result would be like this:

![](http://7xoxf6.com1.z0.glb.clouddn.com/devintervalmatch5.png)

#### Advantages:
Interval Match is used to match a date/timestamp in one table to an interval in another (defined by a numeric start date/timestamp and a numeric end date/timestamp).
<br>1. Memory: avoids having to load all possible dates/timestamps into a Fact table;
<br>2. Load Time: often not using Interval Match means that a join must be used instead which, especially on large data sets, may add seconds or even minutes to script reload times.