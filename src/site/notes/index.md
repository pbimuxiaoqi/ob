---
{"dg-publish":true,"permalink":"/index/","tags":["gardenEntry","gardenEntry","gardenEntry"]}
---

# Power BI木小桼  | [[010 DAX基础/0100 DAX 导航/1 函数导航\|DAX函数]]  |  [[090 其他/关于我\|关于我]] | 

## 工具  | [SQLBI](https://sqlbi.com/) |---| [[090 其他/Power BI资源推荐\|Power BI]] |---| [[090 其他/AI资源推荐\|AI]] |
---


>[!tip]- 三省  
> - [x] 早上吃啥
> - [x] 中午吃啥
> - [x] 晚上吃吗


---

#  最近文章

| File                                                     | created          |
| -------------------------------------------------------- | ---------------- |
| [[010 DAX基础/0110 DAX 基础知识/DAX数据类型\|DAX数据类型]]          | 2024-01-02 22:11 |
| [[020 可视化技巧/0210 可视化规范/颜色\|颜色]]                       | 2024-01-02 17:57 |
| [[090 其他/关于我\|关于我]]                                   | 2024-01-01 23:10 |
| [[090 其他/使用标注\|使用标注]]                                 | 2024-01-01 23:05 |
| [[090 其他/dataview基础\|dataview基础]]                     | 2024-01-01 23:00 |
| [[000 软件基础/0999 Power BI资源推荐\|0999 Power BI资源推荐]]     | 2023-09-04 01:32 |
| [[000 软件基础/0010 Power BI介绍\|0010 Power BI介绍]]         | 2023-09-04 01:30 |
| [[020 可视化技巧/0210 可视化规范/0204 IBCS图表规范\|0204 IBCS图表规范]] | 2023-09-07 00:23 |
| [[020 可视化技巧/0210 可视化规范/0201 可视化设计准则\|0201 可视化设计准则]]   | 2023-09-07 00:22 |
| [[020 可视化技巧/0200 可视化导航/0200 技巧导航\|0200 技巧导航]]         | 2023-09-07 00:23 |

{ .block-language-dataview}
---
#  重点函数

| File                                                                    | des                         | return | import | hard |
| ----------------------------------------------------------------------- | --------------------------- | ------ | ------ | ---- |
| [[010 DAX基础/0120 DAX 函数/FILTER\|FILTER]]                             | \-                          | 表      | 5      | 4    |
| [[010 DAX基础/0120 DAX 函数/AVERAGE\|AVERAGE]]                           | 返回列中所有数字的算术平均值，可以处理文本和非数字值。 | 标量     | 5      | 1    |
| [[010 DAX基础/0120 DAX 函数/COUNT\|COUNT]]                               | 统计指定列具有非空值的行数。              | 标量     | 5      | 1    |
| [[010 DAX基础/0120 DAX 函数/COUNTX\|COUNTX]]                             | 计算对表的每一行的表达式求值所产生的值的数量      | 标量     | 5      | 1    |
| [[010 DAX基础/0120 DAX 函数/DATEADD\|DATEADD]]                           | 按指定的时间间隔移动给定的日期集            | 表      | 5      | 1    |
| [[010 DAX基础/0120 DAX 函数/DISTINCTCOUNT\|DISTINCTCOUNT]]               | \-                          | 标量     | 5      | 1    |
| [[010 DAX基础/0120 DAX 函数/DISTINCTCOUNTNOBLANK\|DISTINCTCOUNTNOBLANK]] | \-                          | \-     | 5      | 1    |
| [[010 DAX基础/0120 DAX 函数/SUM\|SUM]]                                   | 将一列中的所有数字相加                 | 标量     | 5      | 1    |

{ .block-language-dataview}

---
## 标签云

```chartsview
#-----------------#
#- chart type    -#
#-----------------#
type: WordCloud

#-----------------#
#- chart data    -#
#-----------------#
data: | 
  dataviewjs: 
  return (() => {
    const tags = this.app.metadataCache.getTags();
   
    let dataArray = [];
    Object.keys(tags).forEach(key => dataArray.push ({tag: key.replace("#",""),count: tags[key]}));
    return dataArray;
   })();


#-----------------#
#- chart options -#
#-----------------#
options:
  wordField: "tag"
  weightField: "count"
  colorField: "tag"
style:
  backgroundColor: "translucent"

#-----------------------------------------------#
#--- 可选择多彩颜色(colorField) 或单色 (color) ---#
#---  colorField: "tag" ---#
#---  color: "#bb5548" ---#
#-----------------------------------------------#

  wordStyle:
    rotation: 0
```

---


