---
title: 技术贴  一篇使用Markdown编辑的Markdown教程
tags: []
id: '2000'
categories:
  - - 技术贴
date: 2020-12-06 21:17:00
---

Markdown作为一种重要的文本编辑工具，本文介绍了其功能与使用方法。

## Markdown是什么

> Markdown是一种轻量级标记语言，创始人为约翰·格鲁伯（英语：John Gruber）。 它允许人们使用易读易写的纯文本格式编写文档，然后转换成有效的XHTML（或者HTML）文档。这种语言吸收了很多在电子邮件中已有的纯文本标记的特性。

说人话版本：就是用一些简单的标记语法来代替排版，使我们能够专注于内容而不需要像常用的Word或Pages那样进行大量的排版、字体设置。

当前许多网站都广泛使用 Markdown 来撰写帮助文档或是用于论坛上发表消息。例如：GitHub、简书、T大树洞等。

## 使用什么工具

本帖将使用Typora编辑器来讲解Markdown的语法，这一编辑器支持 Windows 、MacOS、Linux等多个平台，且包含多种主题，编辑的同时可以直接渲染出效果，且支持导出HTML、PDF、Word、图片等多种类型文件。

Typora官网：[https://www.typora.io/](https://www.typora.io/)

## Markdown语法的简要规则

下面介绍的是Markdown语法中比较基础且常用的部分，在typora中大多可以通过快捷键或者右键菜单快速输入，所以无需担心遇到类似$\\LaTeX$那样陡峭的学习曲线，但是熟练掌握这些语法可以使码字体验更加流畅。

1.  **标题：**如果我们需要将一行文字定义成标题，只需要在文字前加`#`即可。注意在`#`和文字中间加一个空格，这是最标准的Markdown语法。通过连续的多个`#`我们可以定义多级标题。（最多支持到6级） [![DLGZ8g.png](https://s3.ax1x.com/2020/12/05/DLGZ8g.png)](https://imgchr.com/i/DLGZ8g)
    
    ```
    # 一级标题
    ## 二级标题
    ### 三级标题
    #### 四级标题
    ##### 五级标题
    ###### 六级标题
    ```
    
2.  **粗体与斜体：**两者语法比较类似，粗体是将文字用两个`*`包裹起来，而斜体只需要一个。在typora中我们可以用`ctrl`+`B`快速插入粗体，用`ctrl`+`i`插入斜体。 [![DLGkUf.png](https://s3.ax1x.com/2020/12/05/DLGkUf.png)](https://imgchr.com/i/DLGkUf)
    
    ```
    **这是一段粗体文本**
    *这是斜体*
    ```
    
3.  **引用：**如果我们需要引用一小段别处的句子，只需要在文本前加上>（大于号）即可。 [![DLGA58.png](https://s3.ax1x.com/2020/12/05/DLGA58.png)](https://imgchr.com/i/DLGA58)
    
    ```
     > 苟利国家生死以，岂因祸福避趋之。——林则徐
    ```
    
4.  **图片与链接：**链接的插入由两部分组成，其基本语法为`[显示的文字](URL)`。图片的插入和链接类似，只需要在代码前多加入一个英文感叹号`!`。在typora中两者均可以通过直接复制粘贴的方式快速输入。
    
    [![DLGe2Q.png](https://s3.ax1x.com/2020/12/05/DLGe2Q.png)](https://imgchr.com/i/DLGe2Q)
    
    ```
    [世一流](https://tsinghua.edu.cn)
    ![这里是图片加载失败时的替代文字](https://s1.ax1x.com/2020/10/25/BnpAxg.png)
    ```
    
5.  **表格：**在Markdown中输入表格相对比较复杂，这里不作展开说明，在typora中可以通过右键-插入-表格可视化的插入和编辑表格，此外[这个网站](https://www.tablesgenerator.com/markdown_tables)也提供在线的可视化编辑表格后生成Markdown供复制粘贴的服务。
    
6.  **无序列表和有序列表：**无序列表使用星号、加号或减号作为标记，选择自己喜爱的一种使用即可（不要混用，混用会被解释为不同的列表），有序列表则使用一般的数字和一个英文句号作为标记。不同的列表间可以嵌套。 [![DLGVPS.png](https://s3.ax1x.com/2020/12/05/DLGVPS.png)](https://imgchr.com/i/DLGVPS)
    
    ```
    * 这是一个无序列表
    + 这样也可以
    - 减号也行
    - 1. 还可以嵌套一个有序的
         1. 还可以嵌套很多层~~（禁止套娃）~~
    ```
    
7.  **代码及代码块：**`hello world!`
    
    ```
    hello world!
    如果您是一名程序员，您一定不需要阅读这份粗浅的教程qwq
    ```
    

如果看到了这里，恭喜你已经掌握了Markdown的基础语法，当然无论是typora编辑器还是Markdown本身都还有更多高阶玩法，可以在未来慢慢发掘~

## 公式输入专题

![](../../wp-content_uploads/2020/12/公式输入专题.png) 由于某些未知原因上面部分只能通过图片方式发出，图中涉及到的链接如下

*   识别工具[mathpix](https://mathpix.com/)
*   一份更详细的Markdown说明文档：[http://www.wowubuntu.com/markdown/index.html](http://www.wowubuntu.com/markdown/index.html)
*   数学公式参考：[https://www.luogu.com.cn/blog/IowaBattleship/latex-gong-shi-tai-quan](https://www.luogu.com.cn/blog/IowaBattleship/latex-gong-shi-tai-quan)