title: Python集成Splinter
date: 2015-12-13 17:47:07
tags: [Python, Splinter, 爬虫]
categories: 数据可视化开发
---
在学习Selenium的时候又发现这一款大杀器，比起Selenium代码更加简洁，操作起来也更方便。

Splinter是一个基于Python语言的测试网络应用的工具，简化了搜索元素、表单动作和其他的浏览器动作。

特性：

- 具有简单的API
- 多个webdriver（chrome webdriver, firefox webdriver, phantomjs webdriver, zopetestbrowser, remote webdriver）
- css和xpath选择器
- 支持iframe和alert
- 可执行javascript
- 支持ajax

[Splinter Quick Tutorial](http://splinter.readthedocs.org/en/latest/tutorial.html)

官网示例：
```python
from splinter import Browser

browser = Browser()
browser.visit('http://google.com')
browser.fill('q', 'splinter - python acceptance testing for web applications')
browser.find_by_name('btnG').click()

if browser.is_text_present('splinter.readthedocs.org'):
    print "Yes, the official website was found!"
else:
    print "No, it wasn't found... We need to improve our SEO techniques"

browser.quit()
```

度娘版：
```python
from splinter import Browser
with Browser() as browser:
    browser.visit(http://www.baidu.com)
    browser.find_by_name('wd').fill('splinter')
    browser.find_by_id('su').click()
    if browser.is_text_present('splinter.readthedocs.org'):
        print "Yes, the official website was found!"
    else:
        print "No, it wasn't found... We need to improve our SEO techniques"
```