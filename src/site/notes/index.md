---
{"dg-publish":true,"permalink":"/index/","tags":["gardenEntry","gardenEntry"]}
---

# Power BI木小桼  | [[00 技能/010 Power BI/010 DAX基础/0100 DAX 导航/1 函数导航\|DAX函数]]  |  [[90 其他/关于我\|关于我]] | 

## 工具  | [SQLBI](https://sqlbi.com/) |---| [[90 其他/Power BI资源推荐\|Power BI]] |---| [[90 其他/AI资源推荐\|AI]] |
---


>[!tip]- 人生三件事
> - [x] 发现天赋
> - [x] 培养天赋
> - [x] 奉献天赋

---

#  最近文章

| File                                                                                                          | created                               |
| ------------------------------------------------------------------------------------------------------------- | ------------------------------------- |
| [[00 技能/010 Power BI/070 REST API/增量刷新\|增量刷新]]                                                             | 2024-04-29 17:59                      |
| [[20 读书/10 书籍/优化DAX\|优化DAX]]                                                                               | \-                                    |
| [[40 资源/999 模板/book模板\|book模板]]                                                                            | <ul><li><b>{ date }</b>: \-</li></ul> |
| [[00 技能/010 Power BI/085 Fabric/通过API刷新报表中的partialBatch Commit Mode\|通过API刷新报表中的partialBatch Commit Mode]] | 2024-05-13 11:36                      |
| [[00 技能/010 Power BI/060 门户与权限管理/0601 门户设置\|0601 门户设置]]                                                    | 2024-05-06 14:16                      |
| [[00 技能/010 Power BI/040 DAX进阶/0410 高级原理/DAX引擎\|DAX引擎]]                                                    | 2023-09-10 17:37                      |
| [[90 其他/更好的向AI提问\|更好的向AI提问]]                                                                               | 2024-04-03 10:44                      |
| [[00 技能/010 Power BI/060 门户与权限管理/动态订阅\|动态订阅]]                                                              | 2024-01-19 19:39                      |
| [[00 技能/010 Power BI/060 门户与权限管理/Power BI 语义模型内存错误\|Power BI 语义模型内存错误]]                                    | 2024-04-29 09:55                      |
| [[90 其他/药品医院销售分析\|药品医院销售分析]]                                                                               | \-                                    |

{ .block-language-dataview}
---
#  重点函数

| File                                                                                       | des                         | return | import | hard |
| ------------------------------------------------------------------------------------------ | --------------------------- | ------ | ------ | ---- |
| [[00 技能/010 Power BI/010 DAX基础/0120 DAX 函数/FILTER\|FILTER]]                             | \-                          | 表      | 5      | 4    |
| [[00 技能/010 Power BI/010 DAX基础/0120 DAX 函数/AVERAGE\|AVERAGE]]                           | 返回列中所有数字的算术平均值，可以处理文本和非数字值。 | 标量     | 5      | 1    |
| [[00 技能/010 Power BI/010 DAX基础/0120 DAX 函数/COUNT\|COUNT]]                               | 统计指定列具有非空值的行数。              | 标量     | 5      | 1    |
| [[00 技能/010 Power BI/010 DAX基础/0120 DAX 函数/COUNTX\|COUNTX]]                             | 计算对表的每一行的表达式求值所产生的值的数量      | 标量     | 5      | 1    |
| [[00 技能/010 Power BI/010 DAX基础/0120 DAX 函数/DATEADD\|DATEADD]]                           | 按指定的时间间隔移动给定的日期集            | 表      | 5      | 1    |
| [[00 技能/010 Power BI/010 DAX基础/0120 DAX 函数/DISTINCTCOUNTNOBLANK\|DISTINCTCOUNTNOBLANK]] | \-                          | \-     | 5      | 1    |
| [[00 技能/010 Power BI/010 DAX基础/0120 DAX 函数/DISTINCTCOUNT\|DISTINCTCOUNT]]               | \-                          | 标量     | 5      | 1    |
| [[00 技能/010 Power BI/010 DAX基础/0120 DAX 函数/ROUND\|ROUND]]                               | \-                          | 标量     | 5      | 1    |
| [[00 技能/010 Power BI/010 DAX基础/0120 DAX 函数/SUM\|SUM]]                                   | 将一列中的所有数字相加                 | 标量     | 5      | 1    |

{ .block-language-dataview}

---



## 说明

内容来源于个人学习笔记或收集的网上的比较好的文章，DAX相关学习内容主要来源于SQLBI，感谢意大利人博客，也感谢几个微软员工的博客，感谢所有成为我养料的网上资源 。

博客部署采用的是[digitalgarden](https://github.com/oleeskild/digitalgarden)，具体可参见[部署方案](https://dg-docs.ole.dev/advanced/hosting-alternatives/)

---

<a href="https://notbyai.fyi"><img src="https://s2.loli.net/2024/01/19/karKNFv5oMhewt7.png" alt="Written by Human, Not by AI"></a>

