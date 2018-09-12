---
layout: post
---

# 优秀的markdown编辑器

* typora编辑器,是一个跨平台,所见即所得的md编辑器,你在这里能够找到别人[录制的视频](https://youtu.be/nhgw2ceclVc?t=157),向你展示typora的功能,如果你觉得很有意思,想尝试以下markdown在这个[网站](https://support.typora.io/Markdown-Reference/)可以查到markdown的语法规则,另外,本站的几乎所有的文章也是使用markdown语法用typora编写的
* 更有趣的是,typora跟yalm语法结合的很好,我在用jekii部署博客的时候,往往需要在每篇博客头部,声明下面的这个部分,而typora能够很优雅的帮助生成这个部分的代码

```yaml
---
layout: post
---
```



# typora 也是一个LaTeX的好工具

* 使用`$$+enter`快捷键就可以召唤出latex编辑器出来,而且会有预览r不知道行内怎么处理

$$
w_{1}+w_{2}=x
$$

* 这个[latex wikibook](https://en.wikibooks.org/wiki/LaTeX/Mathematics)网站,可以查看到许多公式的示例,相信很多时候,也许直接对照着使用就可以
* 在使用typora如果你想使用内联公式,例如:使用`$x+x_2=y$`可以渲染出$x+x_2=y$效果,你需要使用inline latex特性,这个特性默认关闭,需要打开设置,你能在[这里](https://support.typora.io/Markdown-Reference/#inline-math)找到开启这个特性的参考,设置好之后,你就可以使用`${code}$`包装使用内联公式
* 当用typora编写公式的时候,gitpage也许不能很好的支持渲染,你可以在head.html中添加mathjet的js代码,具体的你可以参考stackoverflow中的有关[gitpage支持latex的建议](https://stackoverflow.com/questions/26275645/how-to-supported-latex-in-github-pages/46765337#46765337)

