---
{"dg-publish":true,"permalink":"/30 公众号/获取Power BI报表中书签的配置信息/","tags":["公众号","元信息","dmv"]}
---


- \-

{ .block-language-dataview}

Power BI的书签功能用了，真的非常强大，但是维护起来也是真的头大，比如Power BI的官方团队的做的这个案例，只有一个页面，但是几十个书签。只想说：放手吧，阿祖......
![](https://s2.loli.net/2024/08/12/a5e4ilsv3TfFqWw.png)
那有没有一个工具可以直观地查看每个书签的内容呢？[[00 技能/010 Power BI/080 外部工具/Powerops Desktop\|Powerops Desktop]] 应该是目前查看元数据最好地一个工具，但是它有一个致命地缺点：收费。免费版体验很差，总是加载不出来。感兴趣的可自行下载（https://powerops.app/)
![](https://s2.loli.net/2024/08/12/HIyNzvUZmn5VPRF.png)

那，还有没有其他工具可以获取呢？另外既然这个工具可以获取到，首先可以肯定的一件事就是微软肯定是提供的有接口或者是有文件来存储这些数据。
查找官方文档，微软并没有提供相关的API,倒是Power BI Embedded有几个书签相关的方法，但并不是我想要的
![](https://s2.loli.net/2024/08/12/tjVWvauXd3hNopl.png)

那就只能是在Power BI文件中获取了，毕竟上面提到的那个外部工具需要提供的其实也是报表文件。这个就想到了[Field Finder Tool - (powerbi.tips)](https://powerbi.tips/product/field-finder-tool/)这是一个很久远的项目，可以查看报表的一些元数据。比如：页面布局，字段使用等。
![](https://s2.loli.net/2024/08/12/sXt8G3lTZbJciyR.png)

但是，其中并没有包含书签的相关信息，查看pq代码，可以看到本质上是解压报表文件，然后读取layout文件。
![](https://s2.loli.net/2024/08/12/h6qbvzwO8W5GJL2.png)
那就解析下这个文件看看，发现书签的信息应该是存放在config下面
![](https://s2.loli.net/2024/08/12/pArvbxyBPJWFc4H.png)

这就好办了，新建一个简单的页面，只有两个书签，然后把解析出来的config部分喂给gpt
![](https://s2.loli.net/2024/08/12/5pQ2oeybuRUnBLM.png)
gpt40给的答案如下，可以说非常正确了。
![](https://s2.loli.net/2024/08/12/8xDwbhyFQE1aOgY.png)

其实，还有更简单的方式获取这些信息，具体可以参考[Power BI Desktop 專案報表資料夾 - Power BI | Microsoft Learn](https://learn.microsoft.com/zh-tw/power-bi/developer/projects/projects-report#pbir-format)  文件的可读性更高。
![](https://s2.loli.net/2024/08/12/wMgxIheSAct8NXY.png)

到这里，其实有一个更大胆的想法，那就是用Power BI来复刻 Powerops的功能。而且前人已经做过很大一部分工作了，比如上面提到的Field Finder，还有当时介绍过的[[00 技能/010 Power BI/080 外部工具/0830 PBI Explorer/Model Documenter\|Model Documenter]]([Model Documenter](https://data-marc.com/model-documenter/)) 。这两者结合起来，再加上今天提到的书签的信息，基本上就包含了所有要用到的信息了。等哪天闲下来了，可以整合下。。。。
![](https://s2.loli.net/2024/08/12/RQeYMnKhb51wyzd.png)

