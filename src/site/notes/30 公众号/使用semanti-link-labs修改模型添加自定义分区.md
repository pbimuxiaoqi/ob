---
{"dg-publish":true,"permalink":"/30 公众号/使用semanti-link-labs修改模型添加自定义分区/","tags":["semantic_link","公众号","高级容量","分区"]}
---


- https://semantic-link-labs.readthedocs.io/en/stable/sempy_labs.tom.html#sempy_labs.tom.TOMWrapper.all_partitions

{ .block-language-dataview}


去年微软推出semanti-link预览版的时候就感叹确实比rest api好用，但还是限制太多，比如前面介绍修改模型添加自定义分区，就不支持([[30 公众号/Power BI管理自定义分区实现伪增量刷新\|Power BI管理自定义分区实现伪增量刷新]]）。

官方不给力，但是有民间大牛啊，[m-kovalsky](https://github.com/m-kovalsky)发布了一个名为“fabric_cat_tools”的 Python 库，包含120+的函数，并且已被微软收入，重命名为[semantic-link-labs )](https://github.com/microsoft/semantic-link-labs/tree/fb5595477f73e84c3c4c65d77415f9b788d77944) 正式成为[Semantic Link](https://learn.microsoft.com/en-us/python/api/semantic-link-sempy/sempy.fabric?view=semantic-link-python#sempy-fabric-evaluate-dax) 的官方扩展。[语义链接更新 2024 年 6 月 |Microsoft Fabric 博客 |Microsoft 结构 --- Semantic Link Updates June 2024  | Microsoft Fabric Blog | Microsoft Fabric](https://blog.fabric.microsoft.com/en-us/blog/semantic-link-updates-june-2024?ft=All)

接下来就来体验下这个功能强大的【真官方库】，这里要注意，这个库有个最大的限制就是**只支持Fabric容量工作区，是针对Fabric Notebook设计**

## 输出模型中的表
先来个简单的，查看下模型中的表
![](https://s2.loli.net/2024/07/07/m63PdYeRoUi9FJW.png)

## 添加自定义分区

搜索下官方文档，发现是有这样的函数的，只要套用就行了，
![](https://s2.loli.net/2024/07/07/YVPBh1nFdTWtkZf.png)
为了验证，先来看下目前已经存在的分区
![](https://s2.loli.net/2024/07/07/u7Dp2xCwzrSmoWA.png)
添加一个新的分区，注意这里的分区表达式是随便填的，只是为了演示创建效果
![](https://s2.loli.net/2024/07/07/2EjfsgYSwUkcQax.png)
再来查看下已有分区，可以看到分区已创建成功。
![](https://s2.loli.net/2024/07/07/eBLf8zWocg2Yy3H.png)

## 更多玩法

更多函数的功能可以查看官方文档，然后结合数据工厂就可以有更多的玩法，再次感叹Fabric什么时候才能国内上线啊。
![](https://s2.loli.net/2024/07/07/2ncgoLvH137RrsO.png)

