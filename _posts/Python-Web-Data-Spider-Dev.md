title: Python爬虫开发中遇到的问题
date: 2015-12-02 10:50:05
categories: 数据可视化开发
tags: [Python, 爬虫]
---
#### python操作mysql中文显示乱码
1. Python文件设置编码 utf-8,文件前面加上:
```
 #encoding=utf-8
```
2. MySQL数据库charset=utf-8
3. Python连接MySQL是加上参数 charset=utf8
```
con = mdb.Connect('localhost','root','password','dbname',charset='utf8')
```
4. 设置Python的默认编码为 utf-8:
```
sys.setdefaultencoding(utf-8)
```

