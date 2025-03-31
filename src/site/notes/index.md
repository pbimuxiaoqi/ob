---
{"dg-publish":true,"permalink":"/index/","tags":["gardenEntry","gardenEntry"]}
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

| File                                                                                                  | file.ctime          |
| ----------------------------------------------------------------------------------------------------- | ------------------- |
| [[Documents/I.P.A.R.A/学习领域/收集/知识解释\|知识解释]]                                                         | 2025年3月25日 11:24 AM |
| [[00 技能/010 Power BI/080 外部工具/0820 Tabular Editor/Tabular Editor添加svg 模板\|Tabular Editor添加svg 模板]] | 2024年9月25日 09:46 AM |
| [[00 技能/010 Power BI/085 Fabric/Power BI中的Copilot\|Power BI中的Copilot]]                             | 2024年9月9日 02:28 PM  |
| [[30 公众号/获取Power BI报表中书签的配置信息\|获取Power BI报表中书签的配置信息]]                                              | 2024年8月13日 09:19 AM |
| [[30 公众号/为什么应该学习使用AI？\|为什么应该学习使用AI？]]                                                              | 2024年8月10日 05:20 PM |
| [[00 技能/050 AIGC/提示词工程/构建高性能Prompt之路\|构建高性能Prompt之路]]                                              | 2024年8月9日 10:54 PM  |
| [[00 技能/050 AIGC/提示词工程/宝藏内容-沃顿商学院给教师和学生的提示词库\|宝藏内容-沃顿商学院给教师和学生的提示词库]]                              | 2024年8月6日 09:37 AM  |
| [[00 技能/050 AIGC/应用/学习导师，轻松制作学习计划\|学习导师，轻松制作学习计划]]                                                 | 2024年8月5日 06:13 PM  |
| [[00 技能/050 AIGC/提示词工程/00为什么要使用AI\|00为什么要使用AI]]                                                    | 2024年8月5日 04:37 PM  |
| [[00 技能/050 AIGC/应用/阅读助手\|阅读助手]]                                                                   | 2024年8月4日 11:40 PM  |

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
| [[00 技能/010 Power BI/010 DAX基础/0120 DAX 函数/DISTINCTCOUNT\|DISTINCTCOUNT]]               | \-                          | 标量     | 5      | 1    |
| [[00 技能/010 Power BI/010 DAX基础/0120 DAX 函数/DISTINCTCOUNTNOBLANK\|DISTINCTCOUNTNOBLANK]] | \-                          | \-     | 5      | 1    |
| [[00 技能/010 Power BI/010 DAX基础/0120 DAX 函数/ROUND\|ROUND]]                               | \-                          | 标量     | 5      | 1    |
| [[00 技能/010 Power BI/010 DAX基础/0120 DAX 函数/SUM\|SUM]]                                   | 将一列中的所有数字相加                 | 标量     | 5      | 1    |

{ .block-language-dataview}

---
## AIGC
- [[00 技能/050 AIGC/应用/Claude制作2048\|Claude制作2048]]
- [[00 技能/050 AIGC/应用/Claude制作井字棋\|Claude制作井字棋]]
- [[00 技能/050 AIGC/应用/Claude将文档制作成互动游戏\|Claude将文档制作成互动游戏]]
- [[00 技能/050 AIGC/应用/Coze反思模式更好的翻译助手\|Coze反思模式更好的翻译助手]]
- [[00 技能/050 AIGC/应用/Coze打造英语教练\|Coze打造英语教练]]
- [[00 技能/050 AIGC/应用/个性化角色回复\|个性化角色回复]]
- [[00 技能/050 AIGC/应用/阅读助手\|阅读助手]]
- [[00 技能/050 AIGC/应用/学习导师，轻松制作学习计划\|学习导师，轻松制作学习计划]]

{ .block-language-dataview}

```components
componentId: e99eb179-84cd-4b5a-b605-d290f14d67fe

```


## 说明

内容来源于个人学习笔记或收集的网上的比较好的文章，DAX相关学习内容主要来源于SQLBI，感谢意大利人博客，也感谢几个微软员工的博客，感谢所有成为我养料的网上资源 。

博客部署采用的是[digitalgarden](https://github.com/oleeskild/digitalgarden)，具体可参见[部署方案](https://dg-docs.ole.dev/advanced/hosting-alternatives/)

---

<a href="https://notbyai.fyi"><img src="https://s2.loli.net/2024/01/19/karKNFv5oMhewt7.png" alt="Written by Human, Not by AI"></a>

