---
{"dg-publish":true,"permalink":"/index/","tags":["gardenEntry","gardenEntry"]}
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

| File                                                                       | created          |
| -------------------------------------------------------------------------- | ---------------- |
| [[090 其他/dataview学习\|dataview学习]]                                       | 2024-01-17 17:09 |
| [[020 可视化技巧/0210 可视化规范/使可访问性成为设计过程的一部分\|使可访问性成为设计过程的一部分]]               | 2024-01-17 15:12 |
| [[072 DMV/未命名\|未命名]]                                                    | \-               |
| [[085 Fabric/语义模型的OneLake集成\|语义模型的OneLake集成]]                           | 2024-01-16 18:25 |
| [[085 Fabric/DP-600 beta版已出，Fabric学习资源汇总\|DP-600 beta版已出，Fabric学习资源汇总]] | 2024-01-11 21:34 |
| [[090 其他/使用AI解决Doris性能不足问题\|使用AI解决Doris性能不足问题]]                         | 2024-01-06 23:18 |
| [[000 软件基础/数据刷新\|数据刷新]]                                                 | \-               |
| [[090 其他/E5开发者关闭双重验证\|E5开发者关闭双重验证]]                                     | 2024-01-04 16:12 |
| [[000 软件基础/Power BI快捷键\|Power BI快捷键]]                                   | 2024-01-03 09:36 |
| [[010 DAX基础/0110 DAX 基础知识/DAX数据类型\|DAX数据类型]]                            | 2024-01-02 22:11 |

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


