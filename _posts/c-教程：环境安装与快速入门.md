---
title: C# 教程：环境安装与快速入门
tags: []
id: '3297'
categories:
  - - 技术贴
date: 2022-03-26 22:51:32
---

> C#（读作「See Sharp」）是由微软开发的一种面向对象且类型安全的新式编程语言，运行在 .NET 上，开发人员利用 C#能够生成在 .NET 中运行的多种安全可靠的应用程序。C# 源自 C 系列语言，因此有过基本程设基础的同学可以很快上手使用，有过 C++ 基础的同学可以更快地掌握面向对象部分。当然没有完全也不要紧，本篇技术贴将带你从环境安装开始快速入门 C#

## 环境安装和建立项目

对于 Windows 或 macOS，推荐使用 [Visual Studio](https://visualstudio.microsoft.com/zh-hans/)，目前对于个人用户这一强大的 IDE 是免费使用的，对于 Linux 用户，相信您一定不需要这份粗浅的教程可以考虑使用 [Mono](https://www.mono-project.com/download/stable/) 等。本文将以 Windows 平台为例进行演示。

下载 Visual Studio 后，启动下好的安装包，将会为你安装 Visual Studio Installer 方便管理，全流程都是提供简体中文描述的，比较容易理解，整体而言一路下一步即可，注意在如图所示的「工作负载」部分要勾选「.NET 桌面开发」即可。（当然即使忘记了后续也可以通过 Visual Studio Installer 补上，所以放轻松！）

![](../../wp-content_uploads/2022/03/1-1024x519.png)

安装过程由于需要现场下载几个 G 的内容，可能需要耗费一点时间，记得在这个过程中保持网络通畅。可以趁机冲一杯咖啡

安装好后让我们来创建第一个项目：启动 Visual Studio，选择右侧的「创建新项目」-「控制台应用」，给项目起一个好听的名称，选择一个合适的存储位置，点击创建，就可以等待 Visual Studio 为你建好一个全新的项目了。

## Hello, World! 与程序结构

如果你和笔者一样使用的是非常新版本的 Visual Studio（比如刚刚下载好的 Visual Studio 2022），在建立新项目之后大概率会见到一个总共两行还有一行是注释的 Hello World! 程序：

```C#
// See https://aka.ms/new-console-template for more information
Console.WriteLine("Hello, World!");
```

![](../../wp-content_uploads/2022/03/2-1024x655.png)

这是通过 C# 9.0 中新增的顶级语句特性实现的，暂时不在本文的讨论范围内，我们考虑一个标准的 Hello World! 程序：

```C#
using System;

namespace HelloWorld
{
    class Program
    {
        static void Main(string[] args)
        {
            Console.WriteLine("Hello World!");
        }
    }
}
```

用上述代码替换原先的极简版本，点击菜单栏下面的绿色箭头运行，当场可以得到输出了 Hello World! 的小黑框：

![](../../wp-content_uploads/2022/03/3-1024x545.png)

我们观察这个程序的各个部分可以得到典型 C# 程序的基本结构和一些需要注意的关键点：

*   第一行`using System;`使用了`using`关键字在程序中包含了`System`命名空间，一般 C# 程序通常会有多个`using`语句；
*   接下来是用`namespace`声明命名空间，一个`namespace`中通常会包含多个类（`class`），本例中定义了「HelloWorld」命名空间，并在其中包含了`Program`类；
*   与许多程序设计语言类似，C# 同样使用花括号对来包含代码块；
*   `class`关键字用来声明类，本例中声明了`Program`类，类中可以包括多个数据和方法，方法用于规定类的行为；
*   `static void Main(string[] args)`是`Program`类中包含的唯一一个方法，静态（`static`）方法`Main`是通常程序的入口点；
*   注意：与 C/C++ 的习惯不同，在 C# 中通常使用空返回值（`void`）的`Main`方法，且首字母`M`大写，在整个 C 系列语言中大小写都是敏感的；
*   `Console.WriteLine("Hello World!");`调用`System`命名空间中`Console`类的`WriteLine`方法向控制台输出了`Hello World!`，如果前文没有通过`using System;`包含命名空间则应当显式指定命名空间：`System.Console.WriteLine("Hello World!");`

## C# 的数据类型和变量

C# 是一种强类型语言，每个变量、常量和求值的表达式都有明确的类型，当在程序中声明变量或常量时必须指定其类型或使用`var`让编译器推断类型，且声明变量后，不能使用新类型重新声明该变量，并且不能分配与其声明的类型不兼容的值。

```C#
var x = 128;      // 使用 var 自动推断变量类型
double x = 98.5;  // 错误，不能重新声明 x
bool b = true;    // 正确的
x = b;            // 错误，不能将 bool 隐式转换成 int
```

请注意：和 C/C++ 不同，在 C# 中不能对`int` 和`bool`进行转换

C# 内置的类型可参考：[https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/builtin-types/built-in-types](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/builtin-types/built-in-types)

C# 可以进行类型转换，包含两种形式：

*   隐式类型转换：C# 默认以安全方式进行的转换，不会导致数据丢失，比如：从小的整数类型转换为大的，从派生类转换为基类；
*   显式类型转换：即强制类型转换，需要运算符，可能会造成数据丢失。

```C#
double d = 5673.74;
int i;
// 强制转换 double 为 int
i = (int)d; //i=5673
```

## C# 运算符

与许多编程语言类似，C# 也支持大部分常见运算符比如：

*   算术运算符：`+`、`-`、`*`、`/`、`%`、`++`、`--`
*   关系运算符：`==`、`!=`、`>`、`<`、`>=`、`<=`
*   逻辑运算符：`&&`、、`！`
*   其他：`sizeof()`返回数据类型的大小、`typeof()`返回 class 的类型、`is`判断对象是否为某一类型、`as`即使失败也不抛出异常的强制类型转换

## 流程控制

流程控制语句与 C/C++ 系列完全相同，比如选择结构：

```C#
int x = 200;
if(x >= 50)
{
    Console.WriteLine("if");
}
else
{
    Console.WriteLine("else");
}
// if
```

循环结构：

```C#
int sum = 0;
for(int i=1; i<=100; ++i)
{
    sum += i;
}
Console.WriteLine(sum); // 5050
while(sum > 0)
{
    sum -= 1;
}
Console.WriteLine(sum); // 0
```

## C# 面向对象编程、常用数据结构等

此部分将在下一次教程推出，敬请期待！

## 一些可能有用的参考

*   [https://visualstudio.microsoft.com/zh-hans/](https://visualstudio.microsoft.com/zh-hans/)
*   [https://www.mono-project.com/download/stable/](https://www.mono-project.com/download/stable/)
*   [https://docs.microsoft.com/zh-cn/dotnet/csharp/](https://docs.microsoft.com/zh-cn/dotnet/csharp/)
*   [https://www.w3cschool.cn/csharp/](https://www.w3cschool.cn/csharp/)