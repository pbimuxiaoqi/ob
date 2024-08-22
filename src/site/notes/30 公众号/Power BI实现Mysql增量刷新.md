---
{"dg-publish":true,"permalink":"/30 公众号/Power BI实现Mysql增量刷新/","tags":["公众号","增量刷新","链接服务器"]}
---


- \-

{ .block-language-dataview}

随着公司全面推行大数据，我部门的数据终于也要进Doris了，对于早已用惯Azure sql的我来说，还是有那么一定的影响的。最大的影响就是mysql(Doris是基于mysql的)不支持查询折叠的，说人话就是不支持增量刷新。而目前的一个项目保守估计月更新就要几百万行，不支持增量，大数据团队又不可能因为我的拉数需求增加配置，而我也不可能每个月手动创建一个分区([[30 公众号/使用AI解决Doris性能不足问题\|使用AI解决Doris性能不足问题]]，这个文章中是按年分区。。。)

很遗憾，无论是Claude3.5，还是gpt4o都没有给我到相应的答案。
![](https://s2.loli.net/2024/06/30/Itcaur75CUPD8lB.png)

其实，如果是国际版，倒也是可以将数据加载到数据市场来实现任意数据源的增量刷新，但是，这个是环中国发布的功能。。。（[如何在任何数据源上使用增量刷新！– PBI 家伙 --- How to use Incremental Refresh on ANY data source! – PBI Guy (pbi-guy.com)](https://pbi-guy.com/2022/07/14/how-to-use-incremental-refresh-on-any-data-source/)）

那么，要怎么做呢？

只能换个思路让mysql支持查询折叠。嗯，啃官方文档去，还真找到了方法[创建链接服务器 - SQL Server | Microsoft Learn](https://learn.microsoft.com/zh-cn/sql/relational-databases/linked-servers/create-linked-servers-sql-server-database-engine?view=sql-server-ver16)
![](https://s2.loli.net/2024/06/30/FauBtVxrQvMXnk2.png)
官方文档太长，继续问AI要怎么通过链接服务器连接mysql
![](https://s2.loli.net/2024/06/30/YOVrRavfW2MJlyk.png)

## 通过odbc链接

1、安装mysql驱动 ，直接官方下载并安装即可[MySQL :: Download MySQL Connector/ODBC (Archived Versions)](https://downloads.mysql.com/archives/c-odbc/)
2、配置odbc源，这里要注意记下odbc源的名称，接下来要用到
![](https://s2.loli.net/2024/06/30/lSkpIrNiVtawcPW.png)

![](https://s2.loli.net/2024/06/30/aFJSjtCezRGc6nw.png)

3、打开SSMS新建链接服务器，这里要注意数据源是odbc的名称

![](https://s2.loli.net/2024/06/30/8Im9D6u5LMlhVWi.png)
接下来选择安全性，输入mysql服务器的账号密码
![](https://s2.loli.net/2024/06/30/SaMbKyAvu9nBTpk.png)

官方文档中还提到了了一些属性，这里也需要设置下
![](https://s2.loli.net/2024/06/30/CTeMkgodUWAXbEr.png)

![](https://s2.loli.net/2024/06/30/wcfje8PM7yHnF2o.png)



到这里，如果运气好的话，应该就可以结束了。无奈我是那个运气不好的人，遇到了字符不匹配的问题。
![](https://s2.loli.net/2024/06/30/ThFC1PkXzySquE2.png)

### 解决匹配问题
其实上面AI在回答我时已经提到了可能会遇到的问题
![](https://s2.loli.net/2024/06/30/7tcDjSUhC5IJQ1A.png)
可以继续问它解决方法，这次它用了可能的解决方法，越来越严谨了。因为我的的mysql驱动实际上还是去年安装的老版本，就重新安装了最新的驱动版本，很幸运的一次性解决了。。。
![](https://s2.loli.net/2024/06/30/PRjvXSKIYFCQZnz.png)

## 通过sql语句链接

官方文档中其实也有提到通过语句来创建链接服务器，其实要填写的内容和上面创建odbc基本上是一样的，
![](https://s2.loli.net/2024/06/30/2o8gcAPFjYMfWpI.png)


## Power BI配置增量Mysql刷新
这里其实我还又犯了一个小错误，当通过连接sql server后没看到链接服务器的名称，还以为哪里错了，
![](https://s2.loli.net/2024/06/30/1Socfg6AjNxQePY.png)

回到SSMS运行查询才注意到是在master下
![](https://s2.loli.net/2024/06/30/T67irEpQgW41Jv5.png)


具体配置增量刷新的步骤这里就不再赘述了，（[Power BI 中语义模型和实时数据的增量刷新 - Power BI | Microsoft Learn](https://learn.microsoft.com/zh-cn/power-bi/connect-data/incremental-refresh-overview)）
在配置增量刷新时可能会提醒不支持折叠查询，忽略即可。

![](https://s2.loli.net/2024/06/30/RDKpy6NsnXYPEr3.png)

发布到云端，配置好网关，刷新数据看一下，完美，已分好区。
![](https://s2.loli.net/2024/06/30/wOvHgCWkKNpeYI1.png)
