title: Gephi复杂网络分析平台
date: 2015-12-27 14:28:06
tags: [Gephi, Gexf]
categories: Others
---
[Gephi](http://gephi.org/)是一款开源的交互式的复杂网络分析平台，可以生成些比较漂亮的网络图。它支持Windows, Mac OS X以及Linux等环境。主要功能包括： 网络布局：提供了超过10种不同的布局算法 网络社区分析和分类 网络属性计算 动态网络分析。 Gephi被用于互联网，生物医学，交通网络分析等各个领域。

官方Tutorial [在此](https://gephi.org/users/tutorial-visualization/)。

[Gexf](http://www.gexf.net/format/)是一个Gephi相关开发者定义的开放文件格式,基于XML。本文是一个用python写的简单Demo，示例如何使用Python生成一个典型的gexf格式文件。

首先在使用之前需要安装pygexf这个库。
```python
pip install pygexf
```
python代码
```python
import sys,pprint
from gexf import Gexf


# test helloworld.gexf
gexf = Gexf("Gephi.org","A Web network")
graph=gexf.addGraph("directed","static","A Web network")

atr1 = graph.addNodeAttribute('url',type='string',defaultValue='none')
atr2 = graph.addNodeAttribute('indegree',type='float',defaultValue='1')
atr3 = graph.addNodeAttribute('frog',type='boolean',defaultValue='true')

tmp = graph.addNode("0","Gephi")
tmp.addAttribute(atr1,"http://gephi.org")
tmp.addAttribute(atr2,'1')

tmp = graph.addNode("1","Webatlas")
tmp.addAttribute(atr1,"http://webatlas.fr")
tmp.addAttribute(atr2,'2')

tmp = graph.addNode("2","RTGI")
tmp.addAttribute(atr1,"http://rtgi.fr")
tmp.addAttribute(atr2,'1')

tmp = graph.addNode("3","BarabasiLab")
tmp.addAttribute(atr1,"http://barabasilab.com")
tmp.addAttribute(atr2,'1')
tmp.addAttribute(atr3,'false')

graph.addEdge("0","0","1",weight='1')
graph.addEdge("1","0","2",weight='1')
graph.addEdge("2","1","0",weight='1')
graph.addEdge("3","2","1",weight='1')
graph.addEdge("4","0","3",weight='1')


output_file=open(".\data.gexf","w")
gexf.write(output_file)
```
最终生成的data.gexf文件
```xml
<?xml version='1.0' encoding='utf-8'?>
<gexf xmlns:viz="http://www.gexf.net/1.2draft/viz" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns="http://www.gephi.org/gexf/1.2draft" xmlns:ns0="xsi" version="1.2" ns0:schemaLocation="http://www.gephi.org/gexf/1.1draft http://gephi.org/gexf/1.2draft.xsd">
  <meta lastmodified="2015-08-24">
    <creator>Gephi.org</creator>
    <description>A Web network</description>
  </meta>
  <graph defaultedgetype="directed" label="A Web network" mode="static" timeformat="double">
    <attributes class="node" mode="static">
      <attribute id="0" title="url" type="string"/>
      <attribute id="1" title="indegree" type="float"/>
      <attribute id="2" title="frog" type="boolean">
        <default>true</default>
      </attribute>
    </attributes>
    <nodes>
      <node id="0" label="Gephi">
        <attvalues>
          <attvalue for="0" value="http://gephi.org"/>
          <attvalue for="1" value="1"/>
        </attvalues>
      </node>
      <node id="1" label="Webatlas">
        <attvalues>
          <attvalue for="0" value="http://webatlas.fr"/>
          <attvalue for="1" value="2"/>
        </attvalues>
      </node>
      <node id="2" label="RTGI">
        <attvalues>
          <attvalue for="0" value="http://rtgi.fr"/>
          <attvalue for="1" value="1"/>
        </attvalues>
      </node>
      <node id="3" label="BarabasiLab">
        <attvalues>
          <attvalue for="0" value="http://barabasilab.com"/>
          <attvalue for="1" value="1"/>
          <attvalue for="2" value="false"/>
        </attvalues>
      </node>
    </nodes>
    <edges>
      <edge id="0" source="0" target="1" weight="1"/>
      <edge id="1" source="0" target="2" weight="1"/>
      <edge id="2" source="1" target="0" weight="1"/>
      <edge id="3" source="2" target="1" weight="1"/>
      <edge id="4" source="0" target="3" weight="1"/>
    </edges>
  </graph>
</gexf>
```
导入到Gephi中：
![](http://7xoxf6.com1.z0.glb.clouddn.com/devgephi.png)