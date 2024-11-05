---
title: C#：面向对象初步
tags: []
id: '3277'
categories:
  - - 技术贴
date: 2022-03-18 20:06:58
---

上一篇技术贴中我们介绍了 C# 的开发环境搭建、程序基本结构、常用数据类型和流程控制等基本语法，本次我们将对 C# 面向对象编程做简要介绍。

面向对象是一种目前比较流行的编程方法，是一种程序设计的方法论。相对于面向过程的编程方法，面向对象更契合人类正常的思维方式，更适用于开发、维护复杂系统。在这种编程方法下，程序中的数据和数据操作函数是一个逻辑上的整体，这个整体被称为对象。下面我们围绕类这一核心，结合示例代码，帮助大家快速上手 C# 面向对象编程中的常用概念。

## 类的定义和使用

在 C# 中，类的定义以 class 关键字开始，后面为类的名称和大括号包裹的类的成员。类的成员可以分为三种类型，字段、属性和方法：

*   字段是类的数据成员，是用于存储类和类的示例相关数据的变量；
*   属性是代表类的一个实例或类中一个数据的函数成员。在 C# 中对类的属性的设定和获取一般是通过 set 和 get 访问器完成的；
*   方法即类的函数成员，是为类实现某一特定功能的函数。

除了极特殊情况外，C# 中类的成员均需要一个访问标志符，最常用的访问标志符有：

*   public： 限制最宽的修饰符，允许类内及类外的访问；
*   private：限制最严格的修饰符，只允许类内成员访问；
*   protected：与 private 类似，但允许派生的子类成员访问。

此外类中含有两类特殊的成员函数：构造函数和析构函数。构造函数在创建类的新对象时被执行，默认不执行任何操作，可以通过在类中声明与类名相同的成员函数但参数列表不同的多个重载构造函数来实现自己的需求。析构函数则在类的对象超出范围时执行，可以通过波浪线~加类名的成员函数来编写自己的析构函数，但是析构函数不能被继承或重载。

在 C# 中通过 new() 运算符实例化类的对象，通过 . 运算符访问类的成员，下面的代码演示了上述知识：

```csharp
namespace ClassDemo
{
    class Box
    {
        // 字段
        private double length;
        private double height;
        private double width;
        // 属性
        public double Length { get { return length; } set { length = value; } }
        public double Height { get { return height; } set { height = value; } }
        public double Width { get { return width; } set { width = value; } }
        // 构造函数
        public Box()
        {
            Console.WriteLine("Use Box()");
        }
        // 重载构造函数
        public Box(double l, double h, double w)
        {
            Console.WriteLine("Use Box(l,h,w)");
            Length = l;
            Height = h;
            Width = w;
        }
        // 方法
        public double Calculate()
        {
            return length * height * width;
        }

    }

    static class BoxRunner
    {
       public static void RunBox()
        {
            Box box1 = new Box(); // 实例化一个Box类对象
            // 访问类的属性成员
            box1.Length = 1; 
            box1.Height = 1;
            box1.Width = 1;
            Console.WriteLine("{0}\n------------------", box1.Calculate());
            // 调用不同的构造函数实例化Box类对象
            Box box2 = new Box(10, 10, 10);
            Console.WriteLine(box2.Calculate());
        }
    }
}
```

## 类的继承与派生

继承是面向对象编程中的一个重要概念，允许我们根据一个类（基类/父类）定义新的类（派生类/子类），这样有利于代码的维护和复用，也能大大减少开发时间。

继承的思想实现了「属于」关系，例如哺乳动物「属于」动物、学生「属于」人、鸡「属于」鸟类等。

C# 中一个类可以继承自一个基类和多个接口，对应语法很简单，只需要在定义类时在类名后加上 : <基类/接口名> 即可。请注意，基类中 public 和 protected 类型的成员才能被子类访问到。

## 抽象类、抽象方法和虚方法

抽象（abstract）和虚方法（virtual）都可以被用来实现所谓动态多态性。（静态多态性是通过运算符重载和上文利用构造函数介绍过的函数重载实现的）两者十分相似，但又有一些区别：

*   C# 中可在类名前加 abstract 关键字将类声明为抽象类，抽象类不能被实例化，只能被继承。
*   在方法名前加关键字 abstract 可将方法声明为抽象方法，抽象方法只能声明在抽象类中。在声明抽象方法的抽象类中不能有方法主体，继承了抽象类的子类必须实现所有基类中的抽象方法。
*   在方法名前加关键字 virtual 可将方法声明为虚方法，虚方法可以声明在任何类中，声明是必须给出方法主体。继承含虚方法的基类后重写虚方法不是必须的。
*   在子类中重写虚方法或抽象方法都需要在方法名前加 override 关键字以避免命名错误。

下面的代码演示了上述概念：

```csharp
namespace InheritanceDemo
{
    abstract class Bird // 抽象类
    {
        // 请注意：此处为了编码方便直接将字段设置为了public，实际操作中为了数据安全建议参考上段演示代码使用字段进行封装
        public int birdNum = 0;
        public int eggNum = 0;
        // 虚方法，基类中必须有实现
        public virtual void Lay()
        {
            Console.WriteLine("{0} bird laid {1} eggs", birdNum, eggNum);
        }
        // 抽象方法，基类中不能有实现
        abstract public void Sleep();

    }
    class Chicken : Bird  // 子类，继承自基类Bird
    {
        // 重写基类中的虚方法
        public override void Lay()
        {
            Console.WriteLine("{0} chickens laid {1} eggs", birdNum, eggNum);
        }
        // 重写基类中的抽象方法
        override public void Sleep()
        {
            Console.WriteLine("{0} chickens are sleeping", birdNum);
        }
    }

    static class InheritanceRunner
        {
            public static void RunInheritance()
            {
                Bird bird = new Bird(); // 错误：不能实例化抽象类
                Chicken chicken = new Chicken();
                chicken.eggNum = 128;
                chicken.birdNum = 256;
                chicken.Lay();
                chicken.Sleep();
            }
        }
}
```

## 静态类和静态方法

静态类使用关键字 static 修饰，内部只能包含同样使用 static 修饰的静态成员。对于静态的成员，可以直接通过类名访问。例如，参考上段参考代码，可以在 Main 函数中直接通过 InheritanceDemo.InheritanceRunner.RunInheritance(); 访问 InheritanceDemo 命名空间下 InheritanceRunner 类（静态）中的 RunInheritance() 方法（静态）。细节可以参考文末阅读原文链接中的示例代码文件。

## 还可以学什么

近期两篇技术贴大致介绍了 C# 中比较常用的基本概念，希望进一步系统学习可以考虑阅读官方文档，亦可以考虑通过 Revit 二次开发等实际操作熟练，在实践中对新概念单独查询搜索。

*   C# 文档：[https://docs.microsoft.com/zh-cn/dotnet/csharp/](https://docs.microsoft.com/zh-cn/dotnet/csharp/)
*   遇到问题可以考虑在 Stack Overflow 搜索或提问：[https://stackoverflow.com/](https://stackoverflow.com/)
*   如何优雅地使用 Stack Overflow：[https://www.zhihu.com/question/20824615](https://www.zhihu.com/question/20824615)