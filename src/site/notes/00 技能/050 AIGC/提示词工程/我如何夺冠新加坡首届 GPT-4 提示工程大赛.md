---
{"dg-publish":true,"permalink":"/00 技能/050 AIGC/提示词工程/我如何夺冠新加坡首届 GPT-4 提示工程大赛/","tags":["ai","提问","提示工程"]}
---




- https://towardsdatascience.com/how-i-won-singapores-gpt-4-prompt-engineering-competition-34c195a93d41

{ .block-language-dataview}
翻译链接：[我如何夺冠新加坡首届 GPT-4 提示工程大赛 [译] | 宝玉的分享 (baoyu.io)](https://baoyu.io/translations/prompt-engineering/how-i-won-singapores-gpt-4-prompt-engineering-competition)


原文：[How I Won Singapore’s GPT-4 Prompt Engineering Competition](https://towardsdatascience.com/how-i-won-singapores-gpt-4-prompt-engineering-competition-34c195a93d41)

作者：

Sheila Teo

深度探索我在驾驭大语言模型（LLMs）中学到的策略

![庆祝这一里程碑 — 真正的胜利在于宝贵的学习经历！](https://baoyu.io/images/prompt-engineering/how-i-won-singapores-gpt-4-prompt-engineering-competition/1_RAI4cBXe1_zaxVykHz79oA.webp)

庆祝这一里程碑 — 真正的胜利在于宝贵的学习经历！

上个月，我非常荣幸地在新加坡政府科技局（GovTech）组织的首届 GPT-4 提示工程大赛中脱颖而出，这场比赛吸引了超过 400 名杰出的参与者。

提示工程是一门将艺术与科学巧妙融合的学科 — 它不仅关乎技术的理解，更涉及创造力和战略思考。这里分享的是我在实践中学到的一些提示工程策略，这些策略能够精准地驱动任何大语言模型为你服务，甚至做得更多！

> **作者的话：** 在写作本文时，我特意避开了那些已经广泛讨论和记录的常规提示工程技巧。相反，我更希望分享一些我在实验中获得的新洞见，以及我个人在理解和应用这些技巧时的独到见解。希望你能从中获得乐趣！

**本文涵盖以下主题，其中** 🔵 **代表初学者友好的技巧，而** 🔴 **代表高级策略：**

1. 🔵 [**借助 CO-STAR 框架构建高效的提示**](https://towardsdatascience.com/how-i-won-singapores-gpt-4-prompt-engineering-competition-34c195a93d41#10b2)
    
2. 🔵 [**利用分隔符来分节构建提示**](https://towardsdatascience.com/how-i-won-singapores-gpt-4-prompt-engineering-competition-34c195a93d41#8f6a)
    
3. 🔴 [**设计含有 LLM 保护机制的系统级提示**](https://towardsdatascience.com/how-i-won-singapores-gpt-4-prompt-engineering-competition-34c195a93d41#1cfa)
    
4. 🔴 [**仅依靠大语言模型分析数据集，无需插件或代码**](https://towardsdatascience.com/how-i-won-singapores-gpt-4-prompt-engineering-competition-34c195a93d41#183c)  — **实际案例分析 Kaggle 的真实数据集**
    

## [](https://baoyu.io/translations/prompt-engineering/how-i-won-singapores-gpt-4-prompt-engineering-competition#1--%E5%80%9F%E5%8A%A9-co-star-%E6%A1%86%E6%9E%B6%E6%9E%84%E5%BB%BA%E9%AB%98%E6%95%88%E7%9A%84%E6%8F%90%E7%A4%BA)1. 🔵 借助 CO-STAR 框架构建高效的提示

在使用大语言模型时，有效的提示构建至关重要。CO-STAR 框架，由新加坡政府科技局数据科学与 AI 团队创立，是一个实用的提示构建工具。它考虑了所有影响大语言模型响应效果和相关性的关键因素，帮助你获得更优的反馈。

![CO-STAR 框架 — 作者提供的图像](https://baoyu.io/images/prompt-engineering/how-i-won-singapores-gpt-4-prompt-engineering-competition/1__20YO3p4S4a4BKBtFGwwuA.webp)

CO-STAR 框架 — 作者提供的图像

### [](https://baoyu.io/translations/prompt-engineering/how-i-won-singapores-gpt-4-prompt-engineering-competition#%E5%A6%82%E4%BD%95%E5%BA%94%E7%94%A8-co-star-%E6%A1%86%E6%9E%B6)如何应用 CO-STAR 框架：

- **(C) 上下文：为任务提供背景信息** 通过为大语言模型（LLM）提供详细的背景信息，可以帮助它精确理解讨论的具体场景，确保提供的反馈具有相关性。
    
- **(O) 目标：明确你要求大语言模型完成的任务** 清晰地界定任务目标，可以使大语言模型更专注地调整其回应，以实现这一具体目标。
    
- **(S) 风格：明确你期望的写作风格** 你可以指定一个特定的著名人物或某个行业专家的写作风格，如商业分析师或 CEO。这将**指导**大语言模型以一种符合你需求的方式和词汇选择进行回应。
    
- **(T) 语气：设置回应的情感调** 设定适当的语气，确保大语言模型的回应能够与预期的情感或情绪背景相协调。可能的语气包括正式、幽默、富有同情心等。
    
- **(A) 受众：识别目标受众** 针对特定受众定制大语言模型的回应，无论是领域内的专家、初学者还是儿童，都能确保内容在特定上下文中适当且容易理解。
    
- **(R) 响应：规定输出的格式** 确定输出格式是为了确保大语言模型按照你的具体需求进行输出，便于执行下游任务。常见的格式包括列表、JSON 格式的数据、专业报告等。对于大部分需要程序化处理大语言模型输出的应用来说，JSON 格式是理想的选择。
    

## [](https://baoyu.io/translations/prompt-engineering/how-i-won-singapores-gpt-4-prompt-engineering-competition#co-star-%E6%A1%86%E6%9E%B6%E7%9A%84%E5%AE%9E%E7%94%A8%E7%A4%BA%E4%BE%8B)CO-STAR 框架的实用示例

这里有一个 CO-STAR 框架为何有用的现实案例。假设你担任社交媒体经理，需要草拟一条 Facebook 帖子，用以推广公司的新产品。

未使用 CO-STAR 的快速提示可能是这样的：

> 为我的公司 Alpha 的新产品 Beta——一款新型超快速吹风机，撰写一条 Facebook 帖子。

这是 GPT-4 的回答：

> 介绍 Alpha 公司革命性的 Beta 吹风机！告别长时间、无聊的吹发过程！Alpha 公司自豪地推出 Beta，这是我们在护发技术上的最新创新——超快干燥：Beta 设计旨在让你的吹发时间减半，得益于其先进的强力马达。快速准备，享受更多你所爱的时间！立即购买：[产品页面链接]

这一输出虽足够，但显得过于泛化，缺乏必要的细节和针对性吸引力，未能真正触及公司目标受众的心。

下面是一个应用 CO-STAR 模板的示例，它提醒我们在制定提示时，要考虑到任务的其它方面，特别是之前快速提示中缺少的`风格`、`语调`和`受众`：

> # CONTEXT（上下文） #  
> 我想推广公司的新产品。我的公司名为 Alpha，新产品名为 Beta，是一款新型超快速吹风机。
> 
> # OBJECTIVE（目标） #  
> 帮我创建一条 Facebook 帖子，目的是吸引人们点击产品链接进行购买。
> 
> # STYLE（风格） #  
> 参照 Dyson 等成功公司的宣传风格，它们在推广类似产品时的文案风格。
> 
> # TONE（语调） #  
> 说服性
> 
> # AUDIENCE（受众） #  
> 我们公司在 Facebook 上的主要受众是老年人。请针对这一群体在选择护发产品时的典型关注点来定制帖子。
> 
> # RESPONSE（响应） #  
> 保持 Facebook 帖子简洁而深具影响力。

通过运用 CO-STAR 框架，GPT-4 的响应变得更具针对性和效果：

> 用 Alpha Beta——超快速吹风机，体验轻松的优雅生活，它是为具有洞察力的一代人设计的。
> 
> 与 Alpha Beta 一起，重新找回简单而高效的护发乐趣。我们的最新创新不仅是一款吹风机；它还承诺为那些懂得欣赏生活美好事物的人提供快速、柔和且可靠的发型打理。
> 
> - 易用且直观：向复杂的设备说再见。Alpha Beta 专为舒适和简便而设计，非常适合那些喜欢简洁、无麻烦操作的人。- 节省时间的技术：我们知道您的时间非常宝贵。因此，Alpha Beta 显著缩短吹发时间，让您有更多时间享受生活。
> 
> 每天都是与 Alpha Beta 相伴的美好发型日。立即体验优雅与简约的完美结合。
> 
> [您的产品链接在此]

CO-STAR 框架指引您以有组织的方式提供所有关键任务信息，确保响应完全针对您的需求并进行优化。

## [](https://baoyu.io/translations/prompt-engineering/how-i-won-singapores-gpt-4-prompt-engineering-competition#2--%E4%BD%BF%E7%94%A8%E5%88%86%E9%9A%94%E7%AC%A6%E8%BF%9B%E8%A1%8C%E6%96%87%E6%9C%AC%E5%88%86%E6%AE%B5)2. 🔵 使用分隔符进行文本分段

![](https://baoyu.io/images/prompt-engineering/how-i-won-singapores-gpt-4-prompt-engineering-competition/1_Lzklp7X7btTm7DjZXDLzww.webp)

分隔符是特殊的符号，它们帮助大语言模型 (LLM) 辨识提示中哪些部分应当被视为一个完整的意义单元。这非常关键，因为你的提示是作为一个长的 Token 序列一次性传给模型的。通过设置分隔符，可以为这些 Token 序列提供结构，使特定部分得到不同的处理。

需要注意的是，对于简单的任务，分隔符对大语言模型的回应质量可能无显著影响。但是，任务越复杂，合理使用分隔符进行文本分段对模型的反应影响越明显。

### [](https://baoyu.io/translations/prompt-engineering/how-i-won-singapores-gpt-4-prompt-engineering-competition#%E5%88%86%E9%9A%94%E7%AC%A6%E7%9A%84%E4%BD%9C%E7%94%A8)分隔符的作用

分隔符可以是任何不常见组合的特殊字符序列，如：

- ###
- ===
- >>>

选择哪种特殊字符并不重要，关键是这些字符足够独特，使得模型能将其识别为分隔符，而非常规标点符号。

这里是一个分隔符使用的示例：

> 请在 <<<CONVERSATIONS>>> 中对每段对话的情绪进行分类，标为‘正面’或‘负面’。仅提供情绪分类结果，不需任何引言。
> 
> ### [](https://baoyu.io/translations/prompt-engineering/how-i-won-singapores-gpt-4-prompt-engineering-competition#)
> 
> 对话示例
> 
> [Agent]: 早上好，今天我能为您做些什么？  
> [Customer]: 这个产品真差劲，一点都不符合广告宣传！  
> [Customer]: 我非常不满，要求全额退款。
> 
> [Agent]: 早安，我今天怎么为您服务？ [Customer]: 嗨，我只想说我真的很喜欢你们的产品。它超出了我的预期！
> 
> ### [](https://baoyu.io/translations/prompt-engineering/how-i-won-singapores-gpt-4-prompt-engineering-competition#-1)
> 
> 输出示例
> 
> 负面
> 
> 正面
> 
> ### [](https://baoyu.io/translations/prompt-engineering/how-i-won-singapores-gpt-4-prompt-engineering-competition#-2)
> 
> <<<  
> [Agent]: 您好！欢迎使用我们的客服。今天有什么可以帮到您的？  
> [Customer]: 嗨，我只想让你知道我收到了订单，它非常棒！  
> [Agent]: 那太好了！我们很高兴您对购买感到满意。还有其他需要帮助的吗？  
> [Customer]: 不，就这些了。只是想表达一下我的好评。感谢您的优质服务！
> 
> [Agent]: 您好，感谢您联系我们。今天有什么可以帮助您的？  
> [Customer]: 我对最近的购买非常不满。这完全不是我所期待的。  
> [Agent]: 我很抱歉听到您有这样的体验。您能否提供更多细节，以便我为您提供帮助？  
> [Customer]: 产品质量不佳，而且送达晚了。我对这次购买感到非常不满。  
> >>>

在上述示例中，使用 `###` 分隔符来分隔不同的部分，通过大写的章节标题如 `对话示例` 和 `输出示例` 进行区分。引言部分说明了要对 `<<<CONVERSATIONS>>>` 中的对话进行情绪分类，而这些对话在提示的底部给出，没有任何解释文本，但分隔符的存在让模型明白这些对话需要被分类。

GPT-4 的输出正如请求的那样，仅给出情绪分类：

> 正面
> 
> 负面

### [](https://baoyu.io/translations/prompt-engineering/how-i-won-singapores-gpt-4-prompt-engineering-competition#%E5%B0%86%E5%88%86%E9%9A%94%E7%AC%A6%E7%94%A8%E4%BD%9C-xml-%E6%A0%87%E7%AD%BE)将分隔符用作 XML 标签

使用 XML 标签作为分隔符是一种方法。XML 标签是被尖括号包围的，包括开启标签和结束标签。例如，`<tag>`和`</tag>`。这种方法非常有效，因为大语言模型已经接受了大量包含 XML 格式的网页内容的训练，因此能够理解其结构。

以下是利用 XML 标签作为分隔符对同一提示进行结构化的例子：

> 分类以下对话的情感，分为正面和负面两类，根据给出的例子进行分类。请直接给出情感分类结果，不需要添加任何引导性文本。
> 
> <classes>  
> 正面  
> 负面  
> </classes>
> 
> <example-conversations>  
> [Agent]: 早上好，今天我能如何帮助您？  
> [Customer]: 这个产品太糟糕了，一点都不像广告上说的那样！  
> [Customer]: 我非常失望，希望全额退款。
> 
> [Agent]: 早上好，今天我能怎么帮您？  
> [Customer]: 嗨，我只是想说我真的对你们的产品印象深刻。它超出了我的期望！  
> </example-conversations>
> 
> <example-classes>  
> 负面  
> 正面  
> </example-classes>
> 
> <conversations>  
> [Agent]: 你好！欢迎来到我们的支持。今天我能怎么帮您？  
> [Customer]: 嗨，我只是想让你知道我收到我的订单了，它太棒了！  
> [Agent]: 听到这个真好！我们很高兴你对购买感到满意。还有其他我能帮忙的吗？  
> [Customer]: 不，就这些。只是想给一些正面的反馈。谢谢你们的优质服务！
> 
> [Agent]: 你好，感谢你的联系。今天我能怎么帮您？  
> [Customer]: 我对我最近的购买非常失望。这完全不是我所期待的。  
> [Agent]: 很遗憾听到这些。您能提供更多细节以便我帮助您吗？  
> [Customer]: 产品质量差，而且到货晚。我对这次经历非常不满。  
> </conversations>

在指令中使用的名词与 XML 标签的名词一致，如 `conversations`、`classes` 和 `examples`，因此使用的 XML 标签分别是 `<conversations>`、`<classes>`、`<example-conversations>` 和 `<example-classes>`。这确保了模型能够清晰地理解指令与使用的标签之间的关系。

通过这种结构化的分隔符使用方式，可以确保 GPT-4 精确地按照您的期望响应：

> 正面
> 
> 负面

## [](https://baoyu.io/translations/prompt-engineering/how-i-won-singapores-gpt-4-prompt-engineering-competition#3--%E5%88%A9%E7%94%A8%E5%A4%A7%E8%AF%AD%E8%A8%80%E6%A8%A1%E5%9E%8B-llm-%E7%9A%84%E7%B3%BB%E7%BB%9F%E6%8F%90%E7%A4%BA%E5%88%9B%E5%BB%BA%E6%9C%BA%E5%88%B6)3. 🔴 利用大语言模型 (LLM) 的系统提示创建机制

> _在开始前，我们需指出，本节内容仅适用于具备系统提示功能的大语言模型 (LLM)，与文章中其他适用于所有大语言模型的部分不同。显然，具有此功能的最知名的大语言模型是 ChatGPT，因此我们

将以 ChatGPT 为例进行说明。_

![](https://baoyu.io/images/prompt-engineering/how-i-won-singapores-gpt-4-prompt-engineering-competition/1_WLO3fEbiargL8GSbsYXC6w.webp)

### [](https://baoyu.io/translations/prompt-engineering/how-i-won-singapores-gpt-4-prompt-engineering-competition#%E5%85%B3%E4%BA%8E%E7%B3%BB%E7%BB%9F%E6%8F%90%E7%A4%BA%E7%9A%84%E6%9C%AF%E8%AF%AD%E8%A7%A3%E9%87%8A)关于系统提示的术语解释

首先，我们来厘清几个术语：在讨论 ChatGPT 时，这三个术语“系统提示”、“系统消息”和“自定义指令”几乎可以互换使用。这种用法让许多人（包括我自己）感到混淆，因此 OpenAI 发表了一篇[文章](https://help.openai.com/en/articles/8234522-chat-completions-api-system-message-vs-custom-instructions-in-ui)，专门解释了这些术语。简要总结如下：

- “系统提示”和“系统消息”是通过 Chat Completions API 编程方式交互时使用的术语。
- 而“自定义指令”则是在通过 [https://chat.openai.com/](https://chat.openai.com/) 的用户界面与 ChatGPT 交互时使用的术语。

![](https://baoyu.io/images/prompt-engineering/how-i-won-singapores-gpt-4-prompt-engineering-competition/1_gW-q7MI5fNG1fe-QhCCKBw@2x.webp)

图片来自 [Enterprise DNA Blog](https://blog.enterprisedna.co/chatgpt-custom-instructions/)

尽管这三个术语表达的是相同的概念，但不必因术语的使用而感到困扰。下面我们将统一使用“系统提示”这一术语。现在，让我们一探究竟！

### [](https://baoyu.io/translations/prompt-engineering/how-i-won-singapores-gpt-4-prompt-engineering-competition#%E4%BB%80%E4%B9%88%E6%98%AF%E7%B3%BB%E7%BB%9F%E6%8F%90%E7%A4%BA)什么是系统提示？

> 系统提示是您向大语言模型提供的关于其应如何响应的额外指示。这被视为一种额外的提示，因为它超出了您对大语言模型的常规用户提示。

在对话中，每当您提出一个新的提示时，系统提示就像是一个过滤器，大语言模型会在回应您的新提示之前自动应用这一过滤器。这意味着在对话中每次大语言模型给出回应时，都会考虑到这些系统提示。

系统提示一般包括以下几个部分：

- **任务定义**：确保大语言模型（LLM）在整个对话中清楚自己的任务。
- **输出格式**：指导 LLM 如何格式化其回答。
- **操作边界**：明确 LLM 不应采取的行为。这些边界是 LLM 治理中新兴的一个方面，旨在界定 LLM 的操作范围。

例如，系统提示可能是这样的：

> 您需要用这段文本来回答问题：[插入文本]。请按照`{"问题": "答案"}` 的格式来回答。如果文本信息不足以回答问题，请以"NA"作答。您只能解答与[指定范围]相关的问题。请避免回答任何与年龄、性别及宗教等人口统计信息相关的问题。

每一部分对应的内容如下图所示：

![系统提示解析 - 图片由作者提供](https://baoyu.io/images/prompt-engineering/how-i-won-singapores-gpt-4-prompt-engineering-competition/1_GtzzxPCqK4rsLxIpC5QHJQ.webp)

系统提示解析 - 图片由作者提供

### [](https://baoyu.io/translations/prompt-engineering/how-i-won-singapores-gpt-4-prompt-engineering-competition#%E9%82%A3%E4%B9%88%E7%94%A8%E6%88%B7%E6%8F%90%E7%A4%BA%E4%B8%AD%E5%BA%94%E8%AF%A5%E5%8C%85%E6%8B%AC%E4%BB%80%E4%B9%88%E5%86%85%E5%AE%B9)那么用户提示中应该包括什么内容？

系统提示已经概括了任务的总体要求。在上述示例中，任务被定义为仅使用特定文本进行问题解答，同时指导 LLM 按照`{"问题"："答案"}`的格式进行回答。

> 您需要用这段文本来回答问题：[插入文本]。请按照`{"问题": "答案"}`的格式来回答。

这种情况下，每个用户提示就是您想用该文本回答的具体问题。例如，用户提示可能是`"这篇文本主要讲了什么？"`，LLM 的回答将是`{"这篇文本主要讲了什么？":"文本主要讲述了......"}`。

但我们可以将这种任务进一步推广。通常，与只询问一个文本相比，你可能会有多个文本需要询问。这时，我们可以将系统提示的首句从

> 您需要用这段文本来回答问题：[插入文本]。

改为

> 您需要使用提供的文本来回答问题。

如此，每个用户提示将包括要问答的文本和问题，例如：

> <text> [插入文本] </text>
> 
> <question> [插入问题] </question>

此处，我们使用 XML 标签来分隔信息，以便以结构化方式向 LLM 提供所需的两个信息。XML 标签中的名词，`text` 和 `question`，与系统提示中的名词相对应，以便 LLM 理解这些标签是如何与指令相关联的。

总之，系统提示应提供整体任务指令，而每个用户提示则需要提供执行该任务所需的具体细节。在这个例子中，这些细节就是文本和问题。

### [](https://baoyu.io/translations/prompt-engineering/how-i-won-singapores-gpt-4-prompt-engineering-competition#%E9%A2%9D%E5%A4%96%E5%86%85%E5%AE%B9%E4%B8%BA-llm-%E8%AE%BE%E5%AE%9A%E5%8A%A8%E6%80%81%E8%A7%84%E5%88%99)额外内容：为 LLM 设定动态规则

在之前的讨论中，我们通过系统提示来设定规则，这些规则一经设定，将在整个对话中保持不变。但如果你想在对话的不同阶段实施不同的规则，应该怎么做呢？

对于直接使用 ChatGPT 用户界面的用户来说，目前还没有直接的方法可以实现这一点。然而，如果你通过编程方式与 ChatGPT 互动，那么情况就大不相同了！随着对开发有效 LLM 规则的关注不断增加，一些允许你通过编程方式设定更为详细和动态的规则的开源软件包也应运而生。

特别推荐的一个是由 NVIDIA 团队开发的[NeMo Guardrails](https://github.com/NVIDIA/NeMo-Guardrails)。这个工具允许你配置用户与 LLM 之间的预期对话流程，并在对话的不同环节设定不同的规则，实现规则的动态调整。这无疑是探索对话动态管理的一个很好的资源，值得一试！

## [](https://baoyu.io/translations/prompt-engineering/how-i-won-singapores-gpt-4-prompt-engineering-competition#4--%E4%BB%85%E7%94%A8%E5%A4%A7%E8%AF%AD%E8%A8%80%E6%A8%A1%E5%9E%8B-llm-%E5%88%86%E6%9E%90%E6%95%B0%E6%8D%AE%E9%9B%86%E4%B8%8D%E5%80%9F%E5%8A%A9%E6%8F%92%E4%BB%B6%E6%88%96%E7%BC%96%E7%A0%81)4. 🔴 仅用大语言模型 (LLM) 分析数据集，不借助插件或编码

![](https://baoyu.io/images/prompt-engineering/how-i-won-singapores-gpt-4-prompt-engineering-competition/1_uUfKhUoxA8ZaS4Ww5TzAug.webp)

你可能已经听说过 OpenAI 在 ChatGPT 的 GPT-4 中为付费账户提供的高级数据分析插件。它让用户可以上传数据集到 ChatGPT 并直接在数据集上执行编码，实现精准的数据分析。

但是，你知道吗？并不总是需要依赖这类插件来有效地使用大语言模型 (LLM) 分析数据集。我们首先来探讨一下仅利用 LLM 进行数据分析的优势与限制。

### [](https://baoyu.io/translations/prompt-engineering/how-i-won-singapores-gpt-4-prompt-engineering-competition#llm-%E5%9C%A8%E5%93%AA%E4%BA%9B%E6%95%B0%E6%8D%AE%E9%9B%86%E5%88%86%E6%9E%90%E7%B1%BB%E5%9E%8B%E4%B8%8A%E4%B8%8D%E6%93%85%E9%95%BF)LLM 在哪些数据集分析类型上_不_擅长

正如你可能已经知道的，LLMs 在执行精确的数学计算方面有所限制，这让它们不适合需要精确量化分析的任务，比如：

- **描述性统计（Descriptive Statistics）：** 通过如均值或方差等措施定量总结数值列。
- **相关性分析（Correlation Analysis）：** 获取列间的精确相关系数。
- **统计分析（Statistical Analysis）：** 例如进行假设检验，判断数据点组间是否存在统计显著的差异。
- **机器学习（Machine Learning）：** 在数据集上执行预测模型，如使用线性回归、梯度增强树或神经网络。

正是为了执行这些量化任务，OpenAI 推出了高级数据分析插件，以便通过编程语言在数据集上运行代码。

**那么，为什么还有人想仅用 LLMs 来分析数据集而不用这些插件呢？**

### [](https://baoyu.io/translations/prompt-engineering/how-i-won-singapores-gpt-4-prompt-engineering-competition#llm-%E6%93%85%E9%95%BF%E7%9A%84%E6%95%B0%E6%8D%AE%E9%9B%86%E5%88%86%E6%9E%90%E7%B1%BB%E5%9E%8B)LLM 擅长的数据集分析类型

LLMs 在识别模式和趋势方面表现出色。这得益于它们在庞大且多样化的数据上接受的广泛训练，能够洞察到复杂的模式，这些模式可能不是一眼就能看出来的。

这使它们非常适合执行基于模式查找的任务，例如：

- **异常检测：** 基于一个或多个列值，识别偏离常态的异常数据点。
- **聚类：** 将具有相似特征的数据点按列分组。
- **跨列关系：** 识别各列之间的联合趋势。
- **文本分析（适用于文本列）：** 根据主题或情感进行分类。
- **趋势分析（针对有时间维度的数据集）：** 识别列中的模式、季节性变化或趋势。

对于这些基于模式的任务，单独使用 LLMs 可能实际上会在更短的时间内比使用编程代码产生更好的结果！接下来，我们将通过一个例子来详细说明这一点。

### [](https://baoyu.io/translations/prompt-engineering/how-i-won-singapores-gpt-4-prompt-engineering-competition#%E4%BB%85%E4%BD%BF%E7%94%A8-llm-%E5%88%86%E6%9E%90-kaggle-%E6%95%B0%E6%8D%AE%E9%9B%86)仅使用 LLM 分析 Kaggle 数据集

我们将使用一个流行的实际[Kaggle 数据集](https://www.kaggle.com/datasets/imakash3011/customer-personality-analysis)，该数据集专为客户个性分析而设计，帮助公司对客户基础进行细分，从而更好地了解客户。

为了之后验证 LLM 分析的方便，我们将这个数据集缩减至 50 行，并仅保留最相关的几列。缩减后的数据集如下所示，每一行代表一位客户，各列展示了客户的相关信息：

![数据集前三行 —— 图片由作者提供](https://baoyu.io/images/prompt-engineering/how-i-won-singapores-gpt-4-prompt-engineering-competition/1_7WRn3k5heJmD8DWAHHwM5A.webp)

数据集前三行 —— 图片由作者提供

设想你是公司营销团队的一员，你的任务是利用这份客户信息数据集来指导营销活动。这是一个分两步的任务：首先，利用数据集生成有意义的客户细分；其次，针对每个细分提出最佳的市场营销策略。这是一个实际的商业问题，其中第一步的模式识别能力是 LLM 可以大显身手的地方。

我们将按以下方式设计任务提示，采用四种提示工程技术（[更多详情](https://towardsdatascience.com/how-i-won-singapores-gpt-4-prompt-engineering-competition-34c195a93d41#544b)）：

1. 将复杂任务分解成简单步骤；
2. 引用每个步骤的中间输出；
3. 格式化 LLM 的回答；
4. 将指令与数据集分离。

> **_系统提示：_**  
> 我希望你扮演数据科学家的角色来分析数据集。不要编造数据集中不存在的信息。对于我提出的每个分析要求，提供确切且确定的答案，不要提供代码或指导在其他平台上进行分析的方法。
> 
> **_提示：_**  
> # CONTEXT #  
> 我销售葡萄酒。我手头有一个客户信息数据集：[出生年份，婚姻状况，收入，子女数量，上次购买至今天数，消费金额]。
> 
> #############
> 
> # OBJECTIVE #  
> 我希望你利用这个数据集将我的客户分组，并为每个群组制定营销策略。遵循以下分步骤，且不使用代码：
> 
> 1. CLUSTERS: 根据数据集的列将客户分组，确保同一群组内的客户在列值上相似，不同群组的客户在列值上明显不同。确保每一行数据只属于一个群组。
> 
> 对于每个发现的群组，  
> 2. CLUSTER_INFORMATION: 根据数据集的列来描述群组。  
> 3. CLUSTER_NAME: 根据[CLUSTER_INFORMATION]解读得出该客户群组的简称。  
> 4. MARKETING_IDEAS: 提出针对该客户群组的市场营销策略。  
> 5. RATIONALE: 解释为什么[MARKETING_IDEAS]对这个客户群组有效且相关。
> 
> #############
> 
> # STYLE #  
> 商业分析报告
> 
> #############
> 
> # TONE #  
> 专业、技术性
> 
> #############
> 
> # AUDIENCE #  
> 我的商业伙伴们。让他们相信你的营销策略是深思熟虑的，并且有充分的数据支持。
> 
> #############
> 
> # RESPONSE: MARKDOWN REPORT #  
> <对[CLUSTERS]中的每一个群组> — 客户群组：[CLUSTER_NAME] — 群组档案：[CLUSTER_INFORMATION] — 营销策略：[MARKETING_IDEAS] — 理由：[RATIONALE]
> 
> <附录>  
> 提供一个表格，列出每个群组中的行号，以支持你的分析。表头如下：[[CLUSTER_NAME], 行号列表]。
> 
> #############
> 
> # START ANALYSIS #  
> 如果你已经明白，请向我索要我的数据集。

下面是 GPT-4 的回复，我们将继续将数据集以 CSV 字符串的形式传递给它。

![](https://baoyu.io/images/prompt-engineering/how-i-won-singapores-gpt-4-prompt-engineering-competition/1_sn6omL9-NITqwVEviMEKug.webp)

随后，GPT-4 按照我们要求的标记符报告格式回复了分析结果：

![](https://baoyu.io/images/prompt-engineering/how-i-won-singapores-gpt-4-prompt-engineering-competition/1_vwSrP7cmlYcxBdbtfOQUhw.webp)

![](https://baoyu.io/images/prompt-engineering/how-i-won-singapores-gpt-4-prompt-engineering-competition/1_NS46eluVmA515GuP6p3k_Q.webp)

![](https://baoyu.io/images/prompt-engineering/how-i-won-singapores-gpt-4-prompt-engineering-competition/1_3RYAZQXRkbidn0iSoCJxnw.webp)

### [](https://baoyu.io/translations/prompt-engineering/how-i-won-singapores-gpt-4-prompt-engineering-competition#%E9%AA%8C%E8%AF%81%E5%A4%A7%E8%AF%AD%E8%A8%80%E6%A8%A1%E5%9E%8B%E7%9A%84%E5%88%86%E6%9E%90%E8%83%BD%E5%8A%9B)验证大语言模型的分析能力

为了简洁，我们选择两个由大语言模型生成的客户群体进行验证——“年轻家庭”和“挑剔的爱好者”。

**年轻家庭** - 大语言模型生成的描述：出生于 1980 年后，已婚或同居，中等偏低的收入，育有孩子，常做小额消费。 - 此群体包括的数据行：3、4、7、10、16、20 - 深入查看这些数据行的详细信息，结果显示：

![](https://baoyu.io/images/prompt-engineering/how-i-won-singapores-gpt-4-prompt-engineering-competition/1_n5vX8URk1PKCiVYNd_amXg.webp)

年轻家庭的完整数据 — 作者图片

这些数据完美对应大语言模型确定的用户描述。该模型甚至能够识别包含空值的数据行，而无需我们预先处理！

**挑剔的爱好者** - 大语言模型生成的描述：年龄跨度广泛，不限婚姻状况，高收入，孩子情况不一，高消费水平。 - 此群体包括的数据行：2、5、18、29、34、36 - 深入查看这些数据行的详细信息，结果显示：

![](https://baoyu.io/images/prompt-engineering/how-i-won-singapores-gpt-4-prompt-engineering-competition/1_j1Se_C5CbxxZKZlhOz1l3Q.webp)

挑剔的爱好者的完整数据 — 作者图片

这些数据再次精准匹配大语言模型确定的用户描述！

本例展示了大语言模型在识别模式、解读及简化多维数据集以提炼出有意义的洞见方面的强大能力，确保其分析结果扎根于数据的真实情况。

### [](https://baoyu.io/translations/prompt-engineering/how-i-won-singapores-gpt-4-prompt-engineering-competition#%E4%BD%BF%E7%94%A8-chatgpt-%E7%9A%84%E9%AB%98%E7%BA%A7%E6%95%B0%E6%8D%AE%E5%88%86%E6%9E%90%E6%8F%92%E4%BB%B6%E4%BC%9A%E5%A6%82%E4%BD%95)使用 ChatGPT 的高级数据分析插件会如何？

为了全面考虑，我使用同一提示尝试了相同的任务，不过这次我让 ChatGPT 通过编程方式进行分析，启用了其高级数据分析插件。插件应用 K-均值等聚类算法直接对数据集进行处理，以便划分不同的客户群体，并据此制定营销策略。

尽管数据集仅含 50 行，多次尝试均显示错误信息且未产生任何结果：

![尝试 1 的错误和无输出 — 作者图片](https://baoyu.io/images/prompt-engineering/how-i-won-singapores-gpt-4-prompt-engineering-competition/1_ouYNaR56ptHhV9iUwF8ipg.webp)

尝试 1 的错误和无输出 — 作者图片

![尝试 2 的错误和无输出 — 作者图片](https://baoyu.io/images/prompt-engineering/how-i-won-singapores-gpt-4-prompt-engineering-competition/1__IexjpKEgRwnYzn7m7abHQ.webp)

尝试 2 的错误和无输出 — 作者图片

当前情况表明，虽然高级数据分析插件能够轻松完成一些简单任务，如统计描述或生成图表，但在执行需要较大计算量的高级任务时，有时可能因为计算限制或其他原因而发生错误，导致无法输出结果。

### [](https://baoyu.io/translations/prompt-engineering/how-i-won-singapores-gpt-4-prompt-engineering-competition#%E9%82%A3%E4%B9%88%E4%BD%95%E6%97%B6%E5%BA%94%E5%BD%93%E7%94%A8%E5%A4%A7%E8%AF%AD%E8%A8%80%E6%A8%A1%E5%9E%8B-llm-%E6%9D%A5%E5%88%86%E6%9E%90%E6%95%B0%E6%8D%AE%E9%9B%86)那么…何时应当用大语言模型 (LLM) 来分析数据集？

答案因分析的具体类型而异。

对于需要精确的数学运算或复杂的规则处理的任务，传统的编程方法依然更加适用。

而对于依赖模式识别的任务，传统的编程和算法处理可能更加困难且耗时。大语言模型在这类任务中表现优异，能提供包括分析附件在内的额外输出，并能生成 Markdown 格式的完整分析报告。

> 总的来说，是否采用大语言模型取决于任务本身的性质，需要平衡其在模式识别上的强项与传统编程技术提供的精确度和特定性。

### [](https://baoyu.io/translations/prompt-engineering/how-i-won-singapores-gpt-4-prompt-engineering-competition#%E5%9B%9E%E5%88%B0%E6%8F%90%E7%A4%BA%E5%B7%A5%E7%A8%8B%E7%8E%AF%E8%8A%82)回到提示工程环节！

在本节结束前，让我们重新审视用于生成此数据分析的提示，并详细解析关键的提示工程技巧：

> **_提示:_**  
> # CONTEXT #  
> 我经营葡萄酒生意。我手头有一份包含客户信息的数据集：[出生年份，婚姻状况，收入，子女数目，自上次购买至今天数，消费金额]。
> 
> #############
> 
> # OBJECTIVE #  
> 我希望你利用这份数据集将我的客户进行分组，随后为我提供针对每个群体的市场营销策略。请按以下步骤操作，且不要编写代码：
> 
> 1. CLUSTERS: 利用数据集中的列值对行数据进行聚类，确保同一聚类内的客户在列值上保持相似，而不同聚类的客户则明显不同。确保每一行数据只属于一个聚类。
> 
> 对于每个确定的聚类，  
> 2. CLUSTER_INFORMATION: 描述聚类的特征。  
> 3. CLUSTER_NAME: 根据[CLUSTER_INFORMATION]解读，为这个客户群体起一个简称。  
> 4. MARKETING_IDEAS: 提出针对此群体的营销策略。  
> 5. RATIONALE: 解释这些[MARKETING_IDEAS]为何对此群体有效。
> 
> #############
> 
> # STYLE #  
> 商业分析报告
> 
> #############
> 
> # TONE #  
> 专业，技术性
> 
> #############
> 
> # AUDIENCE #  
> 面向我的商业伙伴。让他们确信你的营销策略是经过深思熟虑的，并完全得到数据支持。
> 
> #############
> 
> # RESPONSE: MARKDOWN REPORT #  
> <对于[CLUSTERS]中的每个聚类>  
> — 客户群组：[CLUSTER_NAME]  
> — 简介：[CLUSTER_INFORMATION]  
> — 营销想法：[MARKETING_IDEAS]  
> — 理由：[RATIONALE]
> 
> <附录> 提供一个表格，记录每个聚类的行号，以佐证你的分析。表头如下：[[CLUSTER_NAME], 行号列表]。
> 
> #############
> 
> # START ANALYSIS #  
> 如果你已经理解，请向我请求我的数据集。

#### [](https://baoyu.io/translations/prompt-engineering/how-i-won-singapores-gpt-4-prompt-engineering-competition#%E6%8A%80%E5%B7%A7-1%E5%B0%86%E5%A4%8D%E6%9D%82%E4%BB%BB%E5%8A%A1%E7%AE%80%E5%8C%96%E6%88%90%E6%AD%A5%E9%AA%A4)技巧 1：将复杂任务简化成步骤

大语言模型（LLM）擅长处理简单的任务，对于复杂的任务则表现不佳。因此，在面对复杂任务时，把它分解成一步步简单的指令是至关重要的。这种方法的核心思想是，明确告知 LLM 你自己执行该任务时会采取的每一个步骤。

例如，具体步骤如下：

> 请按照这个步骤操作，不要使用编码：
> 
> 1. **数据聚类（CLUSTERS）**：利用数据集的各列特征，将数据行进行聚类，确保同一聚类中的客户在这些特征上相似，而不同聚类的客户则明显不同。每条数据只能属于一个聚类。
> 
> 对于每个聚类，  
> 2. **聚类描述（CLUSTER_INFORMATION）**：描述聚类的特点。  
> 3. **聚类命名（CLUSTER_NAME）**：根据聚类描述，为这个客户群体起一个简洁的名字。  
> 4. **营销策略（MARKETING_IDEAS）**：为这个客户群体制定营销策略。  
> 5. **策略解释（RATIONALE）**：说明为什么这些营销策略对这个客户群体有效。

这样的分步指导，比起直接要求 LLM“对客户进行分组并提出营销策略”的方式，能显著提高其输出的准确性。

#### [](https://baoyu.io/translations/prompt-engineering/how-i-won-singapores-gpt-4-prompt-engineering-competition#%E6%8A%80%E5%B7%A7-2%E6%A0%87%E8%AE%B0%E5%B9%B6%E5%BC%95%E7%94%A8%E4%B8%AD%E9%97%B4%E8%BE%93%E5%87%BA)技巧 2：标记并引用中间输出

在提供步骤时，我们会用大写字母标记每个步骤的输出，例如`数据聚类（CLUSTERS）`、`聚类描述（CLUSTER_INFORMATION）`、`聚类命名（CLUSTER_NAME）`、`营销策略（MARKETING_IDEAS）`和`策略解释（RATIONALE）`。这样做是为了区分指令中的变量名和其他文本，方便后续引用这些中间输出。

#### [](https://baoyu.io/translations/prompt-engineering/how-i-won-singapores-gpt-4-prompt-engineering-competition#%E6%8A%80%E5%B7%A7-3%E4%BC%98%E5%8C%96%E5%93%8D%E5%BA%94%E6%A0%BC%E5%BC%8F)技巧 3：优化响应格式

此处我们请求一个 Markdown 格式的报告，以增强响应的可读性和结构性。利用中间步骤的变量名，可以明确报告的构架。

> # 响应：Markdown 报告 #  
> <对每个数据聚类[数据聚类（CLUSTERS）]>  
> — 客户群体：[聚类命名（CLUSTER_NAME）]  
> — 群体特征：[聚类描述（CLUSTER_INFORMATION）]  
> — 营销策略：[营销策略（MARKETING_IDEAS）]  
> — 策略说明：[策略解释（RATIONALE）]
> 
> <附录> 提供一个表格，记录每个聚类包含的数据行号，以验证分析的准确性。表格标题为：[聚类命名（CLUSTER_NAME）, 行号列表]。

此外，你还可以让 ChatGPT 将报告以可下载文件形式提供，便于你在编写最终报告时参考使用。

![保存 GPT-4 的回答为文件](https://baoyu.io/images/prompt-engineering/how-i-won-singapores-gpt-4-prompt-engineering-competition/1_-rALQn7TirQZzxvGG0BT5w.webp)

保存 GPT-4 的回答为文件

#### [](https://baoyu.io/translations/prompt-engineering/how-i-won-singapores-gpt-4-prompt-engineering-competition#%E6%8A%80%E5%B7%A7-4%E5%B0%86%E4%BB%BB%E5%8A%A1%E6%8C%87%E4%BB%A4%E4%B8%8E%E6%95%B0%E6%8D%AE%E9%9B%86%E5%88%86%E7%A6%BB)技巧 4：将任务指令与数据集分离

在我们的首个提示中，你会发现我们并没有直接将数据集交给大语言模型（LLM）。反而，提示只给出了数据集分析的任务指令，并在底部添加了这样的话：

> # START ANALYSIS #  
> 如果你明白了，请向我请求数据集。

随后 ChatGPT 表示它已理解，并在下一个提示中，我们通过 CSV 字符串的形式将数据集传递给它：

![GPT-4 的反馈 — 作者提供的图像](https://baoyu.io/images/prompt-engineering/how-i-won-singapores-gpt-4-prompt-engineering-competition/1_sn6omL9-NITqwVEviMEKug.webp)

GPT-4 的反馈 — 作者提供的图像

**但为什么需要将指令与数据集分开处理呢？**

这样做可以帮助大语言模型更清晰地理解各自的内容，降低遗漏信息的风险，尤其是在指令较多且复杂的任务中。你可能遇到过这样的情况：在一个长的提示中提出的某个指令被“偶然遗忘”了——例如，你请求一个 100 字的回答，但大语言模型却给出了更长的段落。通过先接收指令，再处理这些指令所对应的数据集，大语言模型可以更好地消化它应该做的事情，然后再执行相关的数据操作。

值得注意的是，这种指令与数据集的分离只能在可以维护对话记忆的聊天型大语言模型中实现，而非那些没有这种记忆功能的完成型模型。

## [](https://baoyu.io/translations/prompt-engineering/how-i-won-singapores-gpt-4-prompt-engineering-competition#%E7%BB%93%E8%AF%AD)结语

在本文结束之前，我想分享一些关于这次非凡旅程的个人思考。

首先，我要衷心感谢 GovTech Singapore 精心策划这场精彩的比赛。如果你对 GovTech 如何组织这场独一无二的比赛感兴趣，可以阅读 Nicole Lee——比赛的主要组织者撰写的[这篇文章](https://go.gov.sg/how-govtech-designed-promptroyale2023)。

![决赛阶段的现场对决！](https://baoyu.io/images/prompt-engineering/how-i-won-singapores-gpt-4-prompt-engineering-competition/1_cESnPetMGa2ctf41QyN17A.webp)

决赛阶段的现场对决！

其次，我要向那些出色的竞争对手们致以最高的敬意，每个人都展现了特别的才能，让这场比赛既充满挑战又富有成效！我永远不会忘记决赛那一刻，我们在舞台上激烈竞争，现场观众的欢呼声——这是我将一直珍视的记忆。

对我而言，这不只是一场比赛；这是一次才华、创造力及学习精神的盛会。我对未来充满期待，并激动于即将到来的一切！

撰写本文让我感到非常愉快，如果你在阅读时也享受这份乐趣，希望你能花一点时间点赞并关注！

期待下一次的相遇！Sheila