---
{"dg-publish":true,"permalink":"/085 Fabric/获取所有Fabric工作区中项目列表/","tags":["fabric"]}
---



```js
!pip install --upgrade semantic-link --q #upgrade to semantic-link v0.5

import sempy.fabric as fabric
import pandas as pd 

df = pd.concat([fabric.list_items(workspace=ws) for ws in fabric.list_workspaces().query('`Is On Dedicated Capacity` == True').Id], ignore_index=True)
df

```

![](https://s2.loli.net/2024/01/18/fVJUMkA5b3oauOF.png)
