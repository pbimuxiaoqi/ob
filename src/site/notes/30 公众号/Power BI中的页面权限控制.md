---
{"dg-publish":true,"permalink":"/30 公众号/Power BI中的页面权限控制/","tags":["公众号","rls","页面权限"]}
---


- \-

{ .block-language-dataview}

最近一段时间遇到最多的问题无外乎两个，一个是想下载更多的数据，一个是想限制用户看到的数据。
但是，这两个其实是悖论的，只要允许数据下载，那就没办法控制数据的流通，没办法防止数据的泄露。所有的权限控制在允许数据下载的那一刻形同虚设。

那这里不再讨论技术之外的事情 ，来说下Power BI中的页面权限控制。Power BI中是不存在真正意义的页面权限控制的，我们只能通过隐藏页面和指标的形式来限制用户看到的数据。

## 导航页权限

新建一个主页，然后隐藏其他页面，再新建一张页面表，通过控制这张页面表来控制页面权限，这是大多数人的做法，这种做法是有严重的安全隐患的。
比如，下面这样，我新建了一表页面表。
![](https://s2.loli.net/2024/05/30/QGNDB6Lof4M3wVl.png)
然后，新建了两个角色，角色具有不同的页面权限，角色us只能看第2页，角色au可以看第1页
![](https://s2.loli.net/2024/05/30/rYCfhx4cJ1B6AL8.png)
发布到云端后，将角色us赋予了用户aa
![](https://s2.loli.net/2024/05/30/lBhPLaORG5wobze.png)

角色aa只能看到第2页，似乎是达到了我们预期的目的
![](https://s2.loli.net/2024/05/30/VoGKltaFDJjc5z1.png)
但是，当我把第1页的url发给aa，aa是可以看到第1页的。
![](https://s2.loli.net/2024/05/30/rQ76ikAu8Ih1asf.png)

## 字段参数权限

上面效果中，之所以aa拿到了第1页的访问链接，仍然看不了数据，是因为控制了该页使用的度量值的权限。我这里新建一个字段参数来存放需要控制权限的度量，并且隐藏了这些度量
![](https://s2.loli.net/2024/05/30/rDKImla95i7qvxj.png)

基础度量如下,
```js
Sales Amt = SUM( 'FactInternetSales'[SalesAmount] )

Sales Amt2 = [Sales Amt] * 1.2

Cost Amt = SUM( 'FactInternetSalesCost'[TotalProductCost] )
```

这里之所以要控制页面权限的重要原因，就是两个角色能够看到的指标数或计算逻辑不同。这里演示时，au可以看到Sales Amt和Cost Amt， 而角色us只能看到Sales Amt2
![](https://s2.loli.net/2024/05/30/W2Iy8wOS9ZrmxHM.png)

所以才呈现了，上面那样，aa拿到了页面的访问链接，但是因为没有指标的权限，所以看不到数据。


数据资产，是公司最重要的资产之一，一直以来我是极烈地反对允许数据下载的，只是。。。。。。