---
{"dg-publish":true,"permalink":"/00 技能/010 Power BI/020 可视化技巧/0210 可视化规范/收藏这5个网站，轻点鼠标制作漂亮的Power BI主题/","tags":["主题","资源导航"]}
---

Power BI开发人员经常遇到这样的情况：
- 被用户吐槽说页面不美观，但是项目却不给配UI
- 配了UI，UI并未做过Power BI的项目，设计了很复杂Power BI无法实现的效果图；
- UI设计了背景图，和图表颜色，间距，标题等等规范，因为图表太多，一个个操作很烦
无论上面哪种情况，一个好的主题都是必要的，通过切换主题可以快速配置规范化的图表设置，从面极大地减轻工作量。
# PowerBI.tips

[ PowerBI.tips](https://themes.powerbi.tips/themes/wireframes)这是我使用的第一个主题设计网站，如果开通会员的话还能实时预览主题的效果，免费版也足够用了。这里推荐先设置主题色，然后设置全局属性，这样一些通过的属性就不用每个图表里都设置一遍了。设置好主题后点击上方的下载按钮可下载json文件

![](https://s2.loli.net/2024/01/27/8IbmjA9NGV7QnBZ.png)

# Analyst Hub
[Analyst Hub](https://analysthub.enterprisedna.co/apps/power-bi-theme-generator) ，这是Enterprise DNA制作的一个功能性网站，里面还有一些其他的功能，比如代码格式化，色彩生成器等
![](https://s2.loli.net/2024/01/27/Acg5KUqrXvW3daP.png)


# themes.pbix
[ themes.pbix](https://themegenerator.point-gmbh.com/en/Home) ，这同样是个完全免费的主题生成网站，并且已经适配了最新的图表属性，只能说良心，这也是我用的最多的网站。
![](https://s2.loli.net/2024/01/27/XWGtUAML3NpKbCm.png)

# BIBB

[BIBB | Power BI Theme Generator](https://powerbithemegenerator.bibb.pro/)，这是我偶然间问GPT4的时候，GPT4告诉我的一个网站，嗯，只能说懒人必备，网站默认的主师已经设置了常用的属性，你需要做的只是修改下颜色。
![](https://s2.loli.net/2024/01/27/BywNeiWh8SpVZbL.png)
说到颜色，这个网站最让我喜欢的功能就是它可以直接应用[Color Palettes](https://coolors.co/palettes/trending)里的的配色，只需要复制Colors里的链接粘贴进来即可。
![](https://s2.loli.net/2024/01/27/vGBKTcO63h1LCyJ.png)

# Report theme JSON schema

其实无论上面哪个网站，都要使用微软的json schema，毕竟Power BI是微软家的，Power BI的主题的属性规范是微软定的。在新建的json文件中指定shhema的属于为某个版本的schema的链接即可，[Report Theme JSON Schema](https://github.com/microsoft/powerbi-desktop-samples/tree/main/Report%20Theme%20JSON%20Schema)
![](https://s2.loli.net/2024/01/27/xvOdAsciybLuXKD.png)
这样在编写文件的时候就有智能提示了，不过还是不建议通过此种方式编写主题文件。我一般只在需要批量修改主题中某个属性时借助于vs code来查找替换下
![](https://s2.loli.net/2024/01/27/cMLrxD6AFhloaWw.png)

对了，这里还要提下另一下[github仓库](https://github.com/MattRudy/PowerBI-ThemeTemplates),这里包含了自带图表的属性文件，不过该仓库很久不更新了，可能不包含最新的属性。
![](https://s2.loli.net/2024/01/27/gsrkDUqVHBXlyuh.png)

如果有国际版的账号，还可以在应用中搜索themes，这是由Curbal制作的一个应用，里面包含了每个图表的属性，可用于前期快速熟悉每个图表有哪些属性可设置。
![](https://s2.loli.net/2024/01/27/c6Uv38ZdRHh1pmj.png)

>[!tip]- 小技巧  
> 借助于Power BI主题，可以卡一些微软的bug，比如Power BI桌面端中图表没有的属性，或者突破软件中属性的界限，比如设置字体为微软雅黑，填充属性上限超过20px等

> 

# 更多

除了主题配置，还有很多不错的Power BI相关的资源站，可访问以下链接获取
https://zws.im/󠁴󠁡󠁺󠁰󠁱󠁰󠁷