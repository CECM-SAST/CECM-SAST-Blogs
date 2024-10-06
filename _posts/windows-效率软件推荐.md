---
title: Windows 效率软件推荐
tags: []
id: '3453'
categories:
  - - 技术贴
date: 2022-05-31 10:36:22
---

### 引言

当下，疫情的发展难以预料，网课学习、无纸化学习的需求也越来越大。在此背景下，我们要如何提升在 Windows 环境学习下的效率呢？

从工具使用的角度来看，易用与高效是矛盾的，我们要提升效率，往往就需要付出较高的学习成本，甚至需要去挑战一些学习曲线陡峭的软件。而本贴旨在推荐一些 Windows 下学习成本较低的效率软件，使得同学们能够用最短的时间，达到提升效率的目的。

### AutoHotkey

#### 简介

> 软件官网：[AutoHotkey](https://www.autohotkey.com/)

AutoHotkey 是用于 Windows 系统的一个免费开源的脚本语言，可以方便快捷地获取鼠标的位置与状态、键盘输入的快捷键以及输入序列，进而可以简单地完成一些 Windows 下的自动化操作，比如定义全局快捷键或者在不同软件中设置快捷键的具体工作方式。

#### 下载与安装

在官网页面点击「Download」下载，随后运行安装包完成安装。

![image-20220527190945439](https://s2.loli.net/2022/05/31/kEleIsAcphyPQxq.png)  
  

#### 简单教程

AutoHotkey 本身只是一个脚本语言，需要自己编写脚本来实现自动化的功能。但是不需要担心，常用的指令能够很方便地实现，如果需要实现复杂的功能，官网上有完整的使用文档，中文社区中也提供很多已有的优秀脚本，甚至还有用 AutoHotkey 语言编写的 IDE。

> [AutoHotkey 中文社区](https://www.autoahk.com/)
> 
> [快速参考 AutoHotkey](https://wyagd001.github.io/zh-cn/docs/AutoHotkey.htm)

下面使用 AutoHotkey 编写一个简单的脚本并且运行，方便快速了解其使用方法。

1.  新建一个文本文件。
    
2.  重新命名这个文件（注意，文件名必须带有 .ahk 后缀，比如 MyScript.ahk）。
    
3.  双击文件，并且选用任何一个文本编辑器，即可编辑这个脚本（Visual Studio Code 中有 AutoHotkey 相关的插件，能够实现语法高亮等功能）。
    
4.  创建一个简单脚本，当按下快捷键后，输入一段文本。
    
    ```
    ^j:: Send, Hello, world!
    ```
    
    简单解释一下这段代码：
    
    *   `^j::` 是快捷键，`^` 代表按键 `Ctrl` ，`j` 代表按键 `J` ，在 `::` 左边的字符表示需要按下的快捷键。
    *   `Send` 表示发送按键，在 `,` 后面的内容将会被键入。
    *   所以这段代码表示当你按下快捷键 `Ctrl`+`J` ，将会键入 `Hello, world!` 。
    *   当然，你也可以将这段文本替换为学号、邮箱等需要经常输入的信息，来实现快捷键快速输入。
5.  保存文件。
    
6.  双击运行这个脚本。此时，在记事本或者可以输入文字的地方按下 `Ctrl`+`J` ，就能够看到这个脚本的效果。
    

如果你成功运行了上面的脚本，并且大致理解了脚本的内容，那么你就能仿照这个简单的脚本框架，使用简单的快捷键完成很多工作。

#### 应用场景

##### 通过快捷键输入特殊符号

在日常使用过程中，有些键盘上没有特殊符号需要经常输入，但是开启软键盘并且寻找符号又太困难。使用 AutoHotkey 就可以设置在按下快捷键后键入特殊符号。

以直角引号为例。下面的脚本，实现了在按下快捷键 `Alt`+`[` 后输入 "「"，在按下快捷键 `Alt`+`]` 后输入 "」"，在按下快捷键 `Alt`+`Shift`+`[` 后输入 "『"，在按下快捷键 `Alt`+`Shift`+`]` 后输入 "』"。

脚本中，`!` 代表按键 `Alt` ，`+` 代表按键 `Shift` 。

```
![:: Send 「
!]:: Send 」
!+[:: Send 『
!+]:: Send 』
```

需要注意的是，该脚本应该选择采用 `GB2312` 编码保存。

##### 开机时自动运行脚本

按下 `Win`+`r` ，输入 `shell:startup` ，进入启动项文件夹。

![image-20220528160059987](https://s2.loli.net/2022/05/31/VPvtYeb19gs5m2Q.png)  
  

将写好的脚本文件放入这个文件夹，即可实现开机时自动运行脚本。

![image-20220528160253999](https://s2.loli.net/2022/05/31/X5jIZskaqpe1nNf.png)  
  

### Snipaste

#### 简介

> 软件官网：[Snipaste - 截图+ 贴图](https://zh.snipaste.com/)

Snipaste 是 Windows 下的一个简单但是强大的截图软件。

我在 Windows 下也尝试过很多截图软件，但是最后还是选择了 Snipaste ，主要原因有二：

1.  软件实现了方便的贴图功能。
2.  软件操作简单快捷。

我将在教程与应用场景中具体介绍这个软件的优点。

#### 下载与安装

可以在官网下载安装包，自行安装。

![image-20220528170602155](https://s2.loli.net/2022/05/31/mzsxjfCWMtyQbD6.png)  
  

也可以直接通过微软应用商店安装。

![image-20220528170910817](https://s2.loli.net/2022/05/31/rMGcu2vnoAUKbLJ.png)  
  

#### 简单教程

安装并运行 Snipaste 后，按下 `F1` 键截图。

![image-20220528211439345](https://s2.loli.net/2022/05/31/g3SzKdyricV9tTb.png)  
  

在截图后的界面，可以方便实现绘制常用图形，标注箭头，使用画笔与荧光笔，插入文本，打马赛克等功能。

![image-20220528211459539](https://s2.loli.net/2022/05/31/GzkJhFmavL9ZsdT.png)  
  

在编辑完成之后，按下 `F3` ，将编辑后的截图作为窗口，置顶显示。

![image-20220528211513614](https://s2.loli.net/2022/05/31/ZE5ugT7Svy6eQ4K.png)  
  

另外，在贴图后，可以双击贴图关闭，可以按下 `Shift`+`F3` ，隐藏贴图。

在截图后，可以按下 `Ctrl`+`C` 将截图复制，按下 `Ctrl`+`S` 将截图保存，与常见软件的操作逻辑相同。

#### 应用场景

尽管 Snipaste 的截图与贴图功能看似并不复杂，但是在网课的学习环境中，善用贴图功能能够极高的提升我们的效率。

##### 避免频繁切换窗口

当你在听网课时，或者在电脑上完成作业时，使用 Snipaste 可以将有用的信息平铺在屏幕上，避免频繁地切换窗口，或者反复翻动课件寻找有用的信息。

![image-20220528222708672](https://s2.loli.net/2022/05/31/4GSTJNIAH9LvciW.png)  
  

##### 进行简单的图片编辑

当你需要进行一些简单的图片编辑工作时，不需要打开大体积的图片编辑软件，仅需要按下 `F1` ，就能快速完成。

![image-20220528220850535](https://s2.loli.net/2022/05/31/WCL7qAIvH2SO4Gf.png)  
  

### RunCat

#### 简介

> GitHub 地址：[A cute running cat animation on your windows taskbar. - GitHub](https://github.com/Kyome22/RunCat_for_windows)

RunCat 是一个 Windows 下的任务栏小工具，是一只能够用奔跑速度显示当前 CPU 利用率的小猫。

#### 下载

在 GitHub 的 Releases 页面下载软件的最新版本。

![image-20220528223239249](https://s2.loli.net/2022/05/31/anS9bAqxfYR5UEi.png)  
  

双击软件即可运行，无需安装。

#### 演示

可能显示 CPU 利用率的功能并不是对每个人都有用，但是谁又能拒绝一只在任务栏奔跑的小猫呢？

![runcat_demo](https://s2.loli.net/2022/05/31/nrLRiX1wCsM9meS.gif)  
  

### 结语

本次向大家推荐了一些能够在 Windows 下提升学习工作效率，而且学习门槛并不高的软件，希望能够对同学们在网课期间的学习有所帮助。

### 参考

> [AutoHotkey - 维基百科，自由的百科全书](https://zh.m.wikipedia.org/zh-hans/AutoHotkey)
> 
> [AutoHotkey 初学者向导](https://wyagd001.github.io/zh-cn/docs/Tutorial.htm)
> 
> [A cute running cat animation on your windows taskbar. - GitHub](https://github.com/Kyome22/RunCat_for_windows)