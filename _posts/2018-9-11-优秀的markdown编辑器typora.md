---
layout: post
---

# 优秀的Markdown编辑器

## Typora 介绍

* Typora编辑器,是一个跨平台,所见即所得的md编辑器,最好的演示,在[Typora的官网](https://typora.io/), Typora独特的地方是,它能支持例如:公式,流程图,甘特图,表格等的插入完全用Markdown语法表示.你可以在[Support](https://support.typora.io/)页面找到一些例如:Quick Start,How To 等链接很有用
* 你在这里能够找到别人[录制的视频](https://youtu.be/nhgw2ceclVc?t=157),向你展示Typora的功能,如果你觉得很有意思,想尝试以下Markdown在这个[网站](https://support.typora.io/Markdown-Reference/)可以查到Markdown的语法规则,另外,本站的几乎所有的文章也是使用Markdown语法用Typora编写的
* 更有趣的是,Typora跟yalm语法结合的很好,我在用jekii部署博客的时候,往往需要在每篇博客头部,声明下面的这个部分,而Typora能够很优雅的帮助生成这个部分的代码

```yaml
---
layout: post
---
```



## Typora 支持 LaTeX

* 使用`$$+enter`快捷键就可以召唤出latex编辑器出来,而且会有预览r不知道行内怎么处理

$$
w_{1}+w_{2}=x
$$

* 这个[latex wikibook](https://en.wikibooks.org/wiki/LaTeX/Mathematics)网站,可以查看到许多公式的示例,相信很多时候,也许直接对照着使用就可以
* 在使用Typora如果你想使用内联公式,例如:使用`$x+x_2=y$`可以渲染出$x+x_2=y$效果,你需要使用inline latex特性,这个特性默认关闭,需要打开设置,你能在[这里](https://support.typora.io/Markdown-Reference/#inline-math)找到开启这个特性的参考,设置好之后,你就可以使用`${code}$`包装使用内联公式
* 当用Typora编写公式的时候,gitpage也许不能很好的支持渲染,你可以在head.html中添加mathjet的js代码,具体的你可以参考stackoverflow中的有关[gitpage支持latex的建议](https://stackoverflow.com/questions/26275645/how-to-supported-latex-in-github-pages/46765337#46765337)



## 一些写作规范

原文地址：[→阮一峰中文写作规范](https://github.com/ruanyf/document-style-guide)

以前从来去想一篇技术文章要怎么架构，总是随自己想到什么写什么，然后看到了阮一峰老师的总结，就把它改成了思维导图，以便记忆查询。

![中文技术文档写作规范](http://upload-images.jianshu.io/upload_images/1727565-a07e07f5691f0e14.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

[原图传送门](http://opohu5hxr.bkt.clouddn.com/%E4%B8%AD%E6%96%87%E6%8A%80%E6%9C%AF%E6%96%87%E6%A1%A3%E5%86%99%E4%BD%9C%E8%A7%84%E8%8C%83-20170427.png)

## 生成表格

| 你的技能    | 熟练度 |
| ----------- | ------ |
| Python      | 高     |
| Deeplearing | 中     |
| Java        | 中     |
| Spring Mvc  | 高     |



```flow
st=>start: Start|past:>http://www.google.com[blank]
e=>end: End|future:>http://www.google.com
op1=>operation: My Operation|past
op2=>operation: Stuff|current
sub1=>subroutine: My Subroutine
cond=>condition: Yes 
or No?|approved:>http://www.google.com
c2=>condition: Good idea
io=>inputoutput: catch something...|future

st(right)->op1(right)->cond
cond(yes, right)->c2
cond(no)->sub1(left)->op1
c2(yes)->io->e
c2(no)->op2->e
```



```flow
begein=>start: 开始 :>http:www.baidu.com
op=>operation: 操作 
over=>end: 结束
noover=>operation: 没结束
con=>condition: 是否满足

begein(right)->op(right)->con
con(yes,bottom)->over
con(no,right)->noover(right)->op
```



