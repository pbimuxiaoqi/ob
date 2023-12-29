---
{"dg-publish":true,"permalink":"/010 DAX基础/0120 DAX 函数/AVERAGE/","tags":["聚合","标量","dax函数"]}
---

- https://dax.guide/averagea/

{ .block-language-dataview}
返回列中所有数字的算术平均值，可以处理文本和非数字值。

## 语法

```DAX
AVERAGEA ( <ColumnName> )
```

| **参数** | **属性** | **描述**         |
| -------- | -------- | ---------------- |
| 列名     |          | 要计算平均值的列 |

## 返回值

#标量 一个货币类型或小数类型的值

## 备注
AVERAGEA 计算参数列中所有数字的平均值，但同时还会根据以下规则处理非数值类型的内容：  
- 计算结果为 TRUE 的值计为 1  
- 计算结果为 FALSE 的值计为 0  
- 包含非数字文本的值计为 0  
- 空文本 (“”) 计为 0  
如果不想在引用中包含逻辑值和数字的文本表示作为计算的一部分，请使用 [[010 DAX基础/0120 DAX 函数/AVERAGE\|AVERAGE]] 函数。如果没有要聚合的行，函数将返回空白。  
  
在 DAX 中对字符串类型的列使用 AVERAGEA 是没有用的，因为结果始终为 0，这个结果与 Excel 的 AVERAGEA 函数不同。为了计算字符串数据类型的列中包含的数字的平均值，使用 [[VALUE\|VALUE]] 和 [[010 DAX基础/0120 DAX 函数/AVERAGEX\|AVERAGEX]] 可以代替 AVERAGEA 将列转换为数字:  


## 示例
不考虑文本
```js
-- The AVERAGEA syntax does not consider the content
-- of a string column (as Excel does)
AVERAGEA(table[column])
```

将文本转换为数字
```js
-- The following AVERAGEX syntax works correctly
-- when table[column] is a string
AVERAGEX(
  table,
  VALUE(table[column])
)
```


## 相关函数

[[010 DAX基础/0120 DAX 函数/AVERAEA\|AVERAEA]]
[[010 DAX基础/0120 DAX 函数/AVERAGEX\|AVERAGEX]]