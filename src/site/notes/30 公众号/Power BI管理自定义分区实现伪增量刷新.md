---
{"dg-publish":true,"permalink":"/30 公众号/Power BI管理自定义分区实现伪增量刷新/","tags":["公众号","高级容量","分区"]}
---


- - https://www.antmanbi.com/post/create-partitions-in-ssas-with-tabular-editor
- https://www.tackytech.blog/how-to-automate-the-management-of-custom-partitions-for-power-bi-datasets


{ .block-language-dataview}


在上一篇文章[[30 公众号/Power BI实现Mysql增量刷新\|Power BI实现Mysql增量刷新]]中有介绍通过链接服务器的方式来实现其他数据库的增量刷新，技术方案是没问题的，但其实生产中一般不会用。链接服务器的前提是有sql server，如果已经有sql server了，数据再通过数据工厂或者其他ETL工具同步到sql server即可。

今天来介绍另外一种方案，其实在[[30 公众号/使用AI解决Doris性能不足问题\|使用AI解决Doris性能不足问题]]中早已介绍过，当时采用了两种方法，分页查询和自定义分区。因为当时是按年分区，所以手动在SSMS中进行了分区，但目前在做的项目需要到月度，这就不能手动了，即便可以首次加载全量数据不分区，后续新数据每月新建一个分区，这么懒的我也觉得麻烦，那可不可以交给代码来分区呢？

**这里要注意，该方法仅适用于高级容量工作区**。

# Tabular Editor中创建分区

要对Power BI语义模型中添加自定义分区，其实还是要操作表格对象模型(TOM)，[使用表格对象模型 (TOM) 对 Power BI 语义模型进行编程 | Microsoft Learn](https://learn.microsoft.com/zh-cn/analysis-services/tom/tom-pbi-datasets?view=asallproducts-allversions)。既然知道可以通过代码来实现，那就搜索一下，[使用表格编辑器在 SSAS 表格中创建分区 --- Create Partitions in SSAS Tabular with Tabular Editor (antmanbi.com)](https://www.antmanbi.com/post/create-partitions-in-ssas-with-tabular-editor)。代码看上去比微软的官方文档的例子更加简洁易懂....
构建自定义函数，为了简便，这里没有用年月参数，只是创建了一个月份的参数，然后修改了M表达式将其构造为一个自定义函数
![](https://s2.loli.net/2024/07/02/KSqWtgEyHc8UN4B.png)

接下来就是通过脚本调用这个自定义函数然后生成分区
```c#
Table sales = Model.Tables["aa"];
int[] months = { 1,2,3,5 };
foreach(int m in months)
{
      sales.AddMPartition(m.ToString(), "d(" + m + ")"); 
}
```
![](https://s2.loli.net/2024/07/02/jSPrxz61fEKV2Mn.png)
这里要注意原先的默认分区要删掉，不然会造成数据重复

# Python创建分区并刷新

毕竟没学过C#,哪怕可以让gpt来写，改起来也麻烦，那么是否可以使用pyhton呢？[[30 公众号/使用python连接Power BI语义模型\|使用python连接Power BI语义模型]] 中介绍过如何操作Power BI的语义模型，所以技术上应该是行的通的，那还试一下。

![](https://s2.loli.net/2024/07/02/mM8grObPLuSYTwp.png)
正常连接，接下来创建分区，如果是要自动创建分区，更好的是数据库中读取年月，然后用年月作为名称来创建分区，这里为了简单仍然是手动生成一个月份数列表
![](https://s2.loli.net/2024/07/02/ylXuazdSt2xjZWn.png)
可以正常创建并刷新分区，那么就可以写一个定时任务，后面只创建和刷新最新月份的分区数据。
再次感谢AI
![](https://s2.loli.net/2024/07/02/NdZucgOnRCt2FEU.png)


# # Azure中刷新 

问题又来了，如果要设置定时任务就还需要一台windows服务器，我是刚好有服务器，如果没服务器呢？既然核心的dll文件是微软的东东，那么应该也是可以在Azure中配置的，[如何自动管理 Power BI 语义模型（以前的数据集）的自定义分区。 --- how to automate the management of custom partitions for power bi semantic models (former datasets). (tackytech.blog)](https://www.tackytech.blog/how-to-automate-the-management-of-custom-partitions-for-power-bi-datasets/)
这里就不再演示了，感兴趣的可以动手试试。
![](https://s2.loli.net/2024/07/02/Yw7igRsLM6dNhbq.png)


# 总结

技术路线可以走通和生产环境是否可用是两个概念的，这里一定要清楚，本文讨论的主要是技术路线的可行性。另外再次提下，一定要学会使用AI，学会搜索。


# 完整代码

```python
import pandas as pd
from sys import path 
from Microsoft.AnalysisServices.Tabular import *

// 安装了Power BI默认都会有这个文件的
import clr
import pandas as pd
from sys import path 

folder = "C:/Windows/Microsoft.NET/assembly/GAC_MSIL" 
folder2 = "/Microsoft.AnalysisServices.Tabular/v4.0_15.0.0.0__89845dcd8080cc91/Microsoft.AnalysisServices.Tabular.dll" 
# folder2 = "C:/Program Files/Microsoft.NET/ADOMD.NET/160/Microsoft.AnalysisServices.Tabular.dll"
clr.AddReference(folder + folder2)

# 连接信息
server = "powerbi://api.powerbi.cn/v1.0/myorg/xxx"  # 工作区连接
username = "bi@powerbi.com"   # 账号
password = "password"  # 密码
datasource = "xxx"   # 语义模型名称
conn_string = "Provider=MSOLAP;Data Source={};User ID={};Password={};Persist Security Info=True;Impersonation Level=Impersonate".format(server, username, password)

# 连接服务
server = Server()
server.Connect(conn_string)
database = server.Databases.GetByName(datasource)
model = database.Model

months = { 1,2,3,8,9 }
sales = model.Tables["aa"]

// d是模型中存在的自定义函数
for m in months:
    p_name = str(m)
    exit_p = sales.Partitions.Find(p_name)
    if exit_p is None:
        p = Partition()
        p.Name = p_name
        p.Source = MPartitionSource()
        p.Source.Expression = f"d({m})"
        sales.Partitions.Add(p)
    else: 
        print(f"Partition already exists: {p_name}")
model.SaveChanges()

# 刷新分区
for m in months:
    p_name = str(m)
    exit_p = sales.Partitions.Find(p_name)
    
    if exit_p is not None:
        print(f"Refreshing partition: {p_name}")
        exit_p.RequestRefresh(RefreshType.Full)
    else:
        print(f"Partition not found: {p_name}")

# 执行刷新
model.SaveChanges()
# 断开连接
server.Disconnect()
```