title: 利用notepad++打造Qlikview专属代码编辑器
date: 2015-10-21 17:16:44
categories: 资源工具汇总
tags: QlikView
---
notepad++是一款非常好的编辑器，除了已经内置的常见语言，利用它我们可以自定义其他语言，比如Qlikview脚本语言。

1. 如果还没有安装使用过notepad++，请先移步到这里下载安装 http://notepad-plus-plus.org/download/；
2. 下载Qlikview语言定义包 https://github.com/MattFryer/QlikView-Notepad-plus-plus/releases/latest 并解压到本地；
3. 将解压出来的"qlikview.xml"文件复制到notepad++安装目录下的 "Notepad++\plugins\APIs\"文件夹；
4. 将解压出来的"functionList.xml" 文件复制到当前用户的 "%UserProfile%\AppData\Roaming\Notepad++\"文件夹下；
5. 打开Notepad++并依次从菜单点开"Language -> Define your language",在新打开的界面上点击"import"，然后选择解压出来的"qlikview-lang-def.xml"文件并点击确定；
6. 重启Notepad++，然后再次从菜单点开"Language"，就应该可以看到"Qlikview"的语言选项了。

[原文地址](http://www.qlikviewaddict.com/p/qlikview-notepad.html)