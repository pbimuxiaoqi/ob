---
{"dg-publish":true,"permalink":"/90 其他/如何更好地向AI提问/","tags":["ai"]}
---

- [[90 其他/如何更好地向AI提问\|如何更好地向AI提问]]: 
    - https://platform.openai.com/docs/guides/prompt-engineering
    - https://www.servicedeskinstitute.com/ai-powered-service-desk-we-tested-best-ai-prompt-frameworks
    - https://www.coursera.org/learn/prompt-engineering?trk_ref=articleProductCard


{ .block-language-dataview}


- 角色，给予它一个身份，比如SQL专家或者小学数学老师
- 背景，描述当下的问题，比如是寻求答案，还是征求意见，或者是推理
- 示例，给出具体的答案示例，从而约束答案
- 拆分问题，对于较为复杂的问题，可以拆分为多个小问题

# CO-START
![](https://s2.loli.net/2024/01/28/zY7lTUQrycVRDSm.png)
- C，上下文，提供任务的背景
- O，目标，定义要执行的任务
- S， 风格，以什么样的风格来回复，商业分析师，SQL专家等
- T， 语气， 回复时的态度，正式，幽默，善解人意等
- A， 受众，解释给谁，儿童，专家等
- R， 响应格式，按给定的格式输出，比如markdown表格

>[!tip]- 示例
>CONTEXT 
I want to advertise my company’s new product. My company’s name is Alpha and the product is called Beta, which is a new ultra-fast hairdryer.  
我想为我公司的新产品做广告。我公司的名字叫Alpha，产品叫Beta，是一种新型的超快速吹风机。
> OBJECTIVE   
Create a Facebook post for me, which aims to get people to click on the product link to purchase it.  
为我创建一个 Facebook 帖子，旨在让人们点击产品链接来购买。
>STYLE 
Follow the writing style of successful companies that advertise similar products, such as Dyson.  
遵循为类似产品做广告的成功公司（例如戴森）的写作风格。
> TONE   
>Persuasive 有说服力# AUDIENCE # ＃ 观众 ＃  
My company’s audience profile on Facebook is typically the older generation. Tailor your post to target what this audience typically looks out for in hair products.  
我公司在 Facebook 上的受众群体通常是老一代。根据受众通常对护发产品的需求来定制您的帖子。
>RESPONSE
The Facebook post, kept concise yet impactful.  
Facebook 上的帖子简洁而富有影响力。

# RTF
- R  角色
- T  任务
- F  输出格式
>[!tip]- 示例
>角色
>我想让你担任采访者。
>任务
>我希望您针对服务台分析师职位提出基于能力的面试问题。所有问题都应要求候选人展示对该行业的了解。
>格式
>将其显示为包含 5 个问题的列表。
# TAG
- T 任务
- A 行动
- G 目标
>[!tip]- 示例
>任务
>任务是评估团队成员的表现。
>行动
>作为服务台经理，您必须评估团队成员的优势和劣势，提供建设性的反馈并定义用于评估绩效的指标。
>目标
>最终目标是提高团队绩效，以便下一季度的平均用户满意度得分从 6 提高到 7.5。
# BAB
- B  以前
- A  以后
- B  过渡


# CARE
- C  背景
- A  行动
- R  结果
- E  期望
>[!tip]- 示例
>角色
>假设您是一名 IT 帮助台分析师，
>行动
>请解释故障排除流程并建议一组操作，
>背景
>这是针对因计算机速度缓慢而出现故障排除问题的客户。
>期望
>预期的结果是选择一套实用且有效的策略来快速解决该问题并获得高水平的客户满意度。
# RISE  

- R 角色
- I  输入
- S  步骤
- E  期望
>[!tip]- 示例

# APE
 - A 行动
 - P  目的
 - E  期望
>[!tip]- 示例
>行动
>您能否帮助我们为我们的新研究报告“IT 行业的工作生活”制定内容营销策略？
>目的
>我们的目标是激发对未来工作和技术趋势充满热情的 IT 专业人士目标受众的兴趣并提高认识。
>期望
>该策略应该吸引我们的受众并推动 pdf 下载量增加至少 25%。
# ERA

- E 期望
- R 角色
- A 行动
>[!tip]- 示例
>期望
>我们预计下一季度促销最终用户电子邮件活动的知识库访问量将增加 20%。
>角色
>假设您是知识经理，您的职责包括定义并成功执行知识使用电子邮件促销策略。
>行动
>为了实现这一目标，请提供主题行优化和细分的详细计划和策略。


# RASCFEF

- R 角色
- A 行动
- S  步骤
- C  背景
- E  示例
- F  格式


>[!tip]- 示例


# SPARK
- S 情况
- P 问题
- A 期望
- R 结果
- K 惊喜元素

>[!tip]- 示例


# GRADE

- G 目标
- R 请求
- A 行动
- D 详情
- E  示例

>[!tip]- 示例


