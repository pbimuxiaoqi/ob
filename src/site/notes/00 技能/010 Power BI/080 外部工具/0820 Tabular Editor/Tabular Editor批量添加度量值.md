---
{"dg-publish":true,"permalink":"/00 技能/010 Power BI/080 外部工具/0820 Tabular Editor/Tabular Editor批量添加度量值/","tags":["tabular-editor","时间智能"]}
---



- https://github.com/TabularEditor/Scripts

{ .block-language-dataview}

## 批量度量
```js
/*
 * Title: Auto-generate SUM measures from columns
 * 
 * Author: Daniel Otykier, twitter.com/DOtykier
 * 
 * This script, when executed, will loop through the currently selected columns,
 * creating one SUM measure for each column and also hiding the column itself.
 */
 
// Loop through all currently selected columns:
foreach(var c in Selected.Columns)
{
    var newMeasure = c.Table.AddMeasure(
        "Sum of " + c.Name,                    // Name
        "SUM(" + c.DaxObjectFullName + ")",    // DAX expression
        c.DisplayFolder                        // Display Folder
    );
    
    // Set the format string on the new measure:
    newMeasure.FormatString = "0.00";

    // Provide some documentation:
    newMeasure.Description = "This measure is the sum of column " + c.DaxObjectFullName;

    // Hide the base column:
    c.IsHidden = true;
}
```

## 隐藏关系列

```js

foreach (var r in Model.Relationships)
{ // hide all columns on the many side of a join
    var c = r.FromColumn.Name;
    var t = r.FromTable.Name;
    Model.Tables[t].Columns[c].IsHidden = true;
}
```

## 移动度量到默认文件夹

```js
/*
 * Title: Move All Columns to a DisplayFolder  
 *
 * Author: Matt Allington, https://exceleratorbi.com.au  
 *
 *  move all columns into a display folder.  
 *  read why at https://exceleratorbi.com.au/column-sub-folders-better-than-measure-sub-folders/
 */


//Move all columns to display folder
foreach (var c in Model.AllColumns)
{
    c.DisplayFolder = "_Columns";
}
```

## 创建时间智能
```js
/*
 * Generate time intelligence measures based on calculation group items alredy created
 *
 * Author: Benoit Fedit, https://datakuity.com/ 
 *
 * You must have created the calculation group items beforehand (see link below)
 * https://docs.microsoft.com/en-us/analysis-services/tabular-models/calculation-groups?view=asallproducts-allversions
 * To add more measure simply copy/paste the YTD script and replace YTD by your calculation item name
 */


 // For each selected measure create MOM; MOM%, PM, PQ, MTD, QTD, YTD, PY, PY MTD, PY QTD, PY YTD, QOQ, QOQ%, YOY, YOY% measures
foreach(var m in Selected.Measures) {
    
    // MTD
    m.Table.AddMeasure(
    m.Name + " MTD",                                       // Name
    "Calculate(" + m.DaxObjectName + ", 'Time Intelligence'[Time Calculation]=\"MTD\")",    
    m.DisplayFolder                                        // Display Folder
    );
    
    // MOM
    m.Table.AddMeasure(
    m.Name + " MOM",                                       // Name
    "Calculate(" + m.DaxObjectName + ", 'Time Intelligence'[Time Calculation]=\"MOM\")",    
    m.DisplayFolder                                        // Display Folder
    );
    
    // MOM%
    m.Table.AddMeasure(
    m.Name + " MOM%",                                       // Name
    "Calculate(" + m.DaxObjectName + ", 'Time Intelligence'[Time Calculation]=\"MOM%\")",    
    m.DisplayFolder                                        // Display Folder
    ).FormatString = "0.0 %";
    
    // PM
    m.Table.AddMeasure(
    m.Name + " PM",                                       // Name
    "Calculate(" + m.DaxObjectName + ", 'Time Intelligence'[Time Calculation]=\"PM\")",    
    m.DisplayFolder                                        // Display Folder
    );
    
    // PQ
    m.Table.AddMeasure(
    m.Name + " PQ",                                       // Name
    "Calculate(" + m.DaxObjectName + ", 'Time Intelligence'[Time Calculation]=\"PQ\")",    
    m.DisplayFolder                                        // Display Folder
    );
    
    // QTD
    m.Table.AddMeasure(
    m.Name + " QTD",                                       // Name
    "Calculate(" + m.DaxObjectName + ", 'Time Intelligence'[Time Calculation]=\"QTD\")",    
    m.DisplayFolder                                        // Display Folder
    );
    
    // YTD
    m.Table.AddMeasure(
    m.Name + " YTD",                                       // Name
    "Calculate(" + m.DaxObjectName + ", 'Time Intelligence'[Time Calculation]=\"YTD\")",    
    m.DisplayFolder                                        // Display Folder
    );
    
    // PY
    m.Table.AddMeasure(
    m.Name + " PY",                                       // Name
    "Calculate(" + m.DaxObjectName + ", 'Time Intelligence'[Time Calculation]=\"PY\")",    
    m.DisplayFolder                                        // Display Folder
    );
    
    // PY MTD
    m.Table.AddMeasure(
    m.Name + " PY MTD",                                       // Name
    "Calculate(" + m.DaxObjectName + ", 'Time Intelligence'[Time Calculation]=\"PY MTD\")",    
    m.DisplayFolder                                        // Display Folder
    );
    
    // PY QTD
    m.Table.AddMeasure(
    m.Name + " PY QTD",                                       // Name
    "Calculate(" + m.DaxObjectName + ", 'Time Intelligence'[Time Calculation]=\"PY QTD\")",    
    m.DisplayFolder                                        // Display Folder
    );
    
    // PY YTD
    m.Table.AddMeasure(
    m.Name + " PY YTD",                                       // Name
    "Calculate(" + m.DaxObjectName + ", 'Time Intelligence'[Time Calculation]=\"PY YTD\")",    
    m.DisplayFolder                                        // Display Folder
    );
    
    // YOY
    m.Table.AddMeasure(
    m.Name + " YOY",                                       // Name
    "Calculate(" + m.DaxObjectName + ", 'Time Intelligence'[Time Calculation]=\"YOY\")",    
    m.DisplayFolder                                        // Display Folder
    );
    
    // QOQ
    m.Table.AddMeasure(
    m.Name + " QOQ",                                       // Name
    "Calculate(" + m.DaxObjectName + ", 'Time Intelligence'[Time Calculation]=\"QOQ\")",    
    m.DisplayFolder                                        // Display Folder
    );
        
    // YOY%
    m.Table.AddMeasure(
    m.Name + " YOY%",                                       // Name
    "Calculate(" + m.DaxObjectName + ", 'Time Intelligence'[Time Calculation]=\"YOY%\")",    
    m.DisplayFolder                                        // Display Folder
    ).FormatString = "0.0 %";
        
    // QOQ%
    m.Table.AddMeasure(
    m.Name + " QOQ%",                                       // Name
    "Calculate(" + m.DaxObjectName + ", 'Time Intelligence'[Time Calculation]=\"QOQ%\")",    
    m.DisplayFolder                                        // Display Folder
    ).FormatString = "0.0 %";
}
```

