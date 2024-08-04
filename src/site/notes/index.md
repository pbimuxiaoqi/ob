---
{"dg-publish":true,"permalink":"/index/","tags":["gardenEntry","gardenEntry","gardenEntry"]}
---

# Power BI木小桼  | [[00 技能/010 Power BI/010 DAX基础/0100 DAX 导航/1 函数导航\|DAX函数]]  |  [[90 其他/关于我\|关于我]] | 

## 工具  | [SQLBI](https://sqlbi.com/) |---| [[90 其他/Power BI资源推荐\|Power BI]] |---| [[40 资源/900 网址/网址导航\|工具站]] |
---


>[!tip]- 人生三件事
> - [x] 发现天赋
> - [x] 培养天赋
> - [x] 奉献天赋

---

#  最近文章

| File                                                                         | created          |
| ---------------------------------------------------------------------------- | ---------------- |
| [[00 技能/050 AIGC/应用/Claude将文档制作成互动游戏\|Claude将文档制作成互动游戏]]                  | 2024-08-04 22:24 |
| [[00 技能/050 AIGC/应用/个性化角色回复\|个性化角色回复]]                                    | 2024-08-04 22:14 |
| [[00 技能/050 AIGC/应用/Claude制作2048\|Claude制作2048]]                          | 2024-08-03 22:26 |
| [[00 技能/050 AIGC/应用/Claude制作井字棋\|Claude制作井字棋]]                            | 2024-08-03 22:26 |
| [[00 技能/050 AIGC/应用/Coze打造英语教练\|Coze打造英语教练]]                              | 2024-08-04 22:27 |
| [[00 技能/010 Power BI/080 外部工具/前后端分离\|前后端分离]]                              | 2024-07-30 16:51 |
| [[00 技能/010 Power BI/060 门户与权限管理/缩放工作区容量\|缩放工作区容量]]                       | 2024-07-15 10:00 |
| [[30 公众号/使用semanti-link-labs修改模型添加自定义分区\|使用semanti-link-labs修改模型添加自定义分区]] | 2024-07-06 23:09 |
| [[30 公众号/Power BI管理自定义分区实现伪增量刷新\|Power BI管理自定义分区实现伪增量刷新]]                 | 2024-07-02 13:40 |
| [[30 公众号/Power BI实现Mysql增量刷新\|Power BI实现Mysql增量刷新]]                       | 2024-06-30 09:51 |

{ .block-language-dataview}
---
#  重点函数

| File                                                                                       | des                         | return | import | hard |
| ------------------------------------------------------------------------------------------ | --------------------------- | ------ | ------ | ---- |
| [[00 技能/010 Power BI/010 DAX基础/0120 DAX 函数/FILTER\|FILTER]]                             | \-                          | 表      | 5      | 4    |
| [[00 技能/010 Power BI/010 DAX基础/0120 DAX 函数/AVERAGE\|AVERAGE]]                           | 返回列中所有数字的算术平均值，可以处理文本和非数字值。 | 标量     | 5      | 1    |
| [[00 技能/010 Power BI/010 DAX基础/0120 DAX 函数/COUNT\|COUNT]]                               | 统计指定列具有非空值的行数。              | 标量     | 5      | 1    |
| [[00 技能/010 Power BI/010 DAX基础/0120 DAX 函数/COUNTX\|COUNTX]]                             | 计算对表的每一行的表达式求值所产生的值的数量      | 标量     | 5      | 1    |
| [[00 技能/010 Power BI/010 DAX基础/0120 DAX 函数/DISTINCTCOUNT\|DISTINCTCOUNT]]               | \-                          | 标量     | 5      | 1    |
| [[00 技能/010 Power BI/010 DAX基础/0120 DAX 函数/DATEADD\|DATEADD]]                           | 按指定的时间间隔移动给定的日期集            | 表      | 5      | 1    |
| [[00 技能/010 Power BI/010 DAX基础/0120 DAX 函数/DISTINCTCOUNTNOBLANK\|DISTINCTCOUNTNOBLANK]] | \-                          | \-     | 5      | 1    |
| [[00 技能/010 Power BI/010 DAX基础/0120 DAX 函数/ROUND\|ROUND]]                               | \-                          | 标量     | 5      | 1    |
| [[00 技能/010 Power BI/010 DAX基础/0120 DAX 函数/SUM\|SUM]]                                   | 将一列中的所有数字相加                 | 标量     | 5      | 1    |

{ .block-language-dataview}

---
## AIGC
- [[00 技能/050 AIGC/应用/Coze人生模拟器\|Coze人生模拟器]]
- [[00 技能/050 AIGC/应用/Coze打造英语教练\|Coze打造英语教练]]
- [[00 技能/050 AIGC/应用/个性化角色回复\|个性化角色回复]]
- [[00 技能/050 AIGC/应用/Claude制作井字棋\|Claude制作井字棋]]
- [[00 技能/050 AIGC/应用/Claude制作2048\|Claude制作2048]]
- [[00 技能/050 AIGC/应用/Claude将文档制作成互动游戏\|Claude将文档制作成互动游戏]]

{ .block-language-dataview}


## 说明

内容来源于个人学习笔记或收集的网上的比较好的文章，DAX相关学习内容主要来源于SQLBI，感谢意大利人博客，也感谢几个微软员工的博客，感谢所有成为我养料的网上资源 。

博客部署采用的是[digitalgarden](https://github.com/oleeskild/digitalgarden)，具体可参见[部署方案](https://dg-docs.ole.dev/advanced/hosting-alternatives/)

---

<a href="https://notbyai.fyi"><img src="https://s2.loli.net/2024/01/19/karKNFv5oMhewt7.png" alt="Written by Human, Not by AI"></a>

