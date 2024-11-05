---
title: Python教程Ⅱ面向对象编程初步
tags: []
id: '2921'
categories:
  - - 技术贴
date: 2021-10-11 20:56:04
---

上次教程中，我们简要介绍了[Python安装与快速入门](https://thuce.top/2801.html)，本次教程将对Python数据类型、面向对象编程技术（OOP）初步、Python模块与包进行简要介绍，并向大家推荐Python后续学习资料。

## Python数据类型

上次介绍到Python内置数据类型有`bool`, `int`, `float`, `complex`, `str`，另外还有`list`, `tuple`, `set`, `dict`四类。其中，`bool`, `int`, `float` 及 `complex`与C语言中对应类型非常相似，所以本教程不再详述，而是将重点放在介绍`str`, `list`, `tuple`, `set`, `dict`五种数据类型上。由于操作函数方法较多，本篇教程无法完全涉及，大家可以参考教程后的参考链接继续深入学习。

### `str`类型

`str`类型即字符串类型，较C语言，Python中字符串支持许多编码格式，并且也有许多便利的运算方法。其中较常用的方法有`len`, `==`, `+`, `*`, `in`, `find`。

```python
s1 = 'hello, world'
print(s1 + s1)       # 字符串拼接
print(s1 * 100)      # 字符串重复
print(len(s1))       # 字符串长度
print('wo' in s1)    # True

s2 = 'goodbye'
print(s2 in s1)      # False
print(s1 == s2)      # False

## 以三个双引号或单引号开头的字符串可以折行
s3 = '''
hello, 
world!
'''
```

### `list`类型

`list`类型即列表类型，与C中的动态数组类似，但使用更为方便。常用的方法有`len`, `[]`, `append`, `insert`, `clear`, `pop`, `remove`, `sort`, `+`, `*`。

```python
items = ['Python', 'Java', 'Go', 'Kotlin']
items.append('Swift')  # ['Python', 'Java', 'Go', 'Kotlin', 'Swift']
items.insert(2, 'SQL') # ['Python', 'Java', 'SQL', 'Go', 'Kotlin', 'Swift']
items.remove('Java')   # ['Python', 'SQL', 'Go', 'Kotlin', 'Swift']
items.pop(0)           # ['SQL', 'Go', 'Kotlin', 'Swift']
items.pop(len(items) - 1) # ['SQL', 'Go', 'Kotlin']
items.clear()          # []
```

在使用列表重复(`*`)运算时，要注意可能出现的问题，例如：

```python
scores = [[0] * 3] * 5
print(scores)    # [[0, 0, 0], [0, 0, 0], [0, 0, 0], [0, 0, 0], [0, 0, 0]]
scores[0][0] = 95
print(scores)    # [[95, 0, 0], [95, 0, 0], [95, 0, 0], [95, 0, 0], [95, 0, 0]]
```

正确的做法应该是：

```python
scores = [[0] * 3 for _ in range(5)]
scores[0][0] = 95
print(scores)    # [[95, 0, 0], [0, 0, 0], [0, 0, 0], [0, 0, 0], [0, 0, 0]]
```

### `tuple`类型

`tuple`类型即元组类型，类似一个不能改变元素的列表。元组常用于函数多变量返回，变量打包、解包中。

```python
a = (1, 10, 100)    # 打包
i, j, k = a         # 解包
print(i, j, k)      # 1 10 100
```

同时，我们可以借助`*`，完成不定长元素的推测解包。需要注意，一个解包语句中只能出现一个`*`，否则会产生歧义，编译器将不能理解如何解包。

```python
a = 1, 10, 100, 1000
i, j, *k = a
print(i, j, k)          # 1 10 [100, 1000]
i, *j, k = a
print(i, j, k)          # 1 [10, 100] 1000
*i, j, k = a
print(i, j, k)          # [1, 10] 100 1000
*i, j = a
print(i, j)             # [1, 10, 100] 1000
i, *j = a
print(i, j)             # 1 [10, 100, 1000]
i, j, k, *l = a
print(i, j, k, l)       # 1 10 100 [1000]
i, j, k, l, *m = a
print(i, j, k, l, m)    # 1 10 100 1000 []
```

### `set`类型

`set`类型即集合类型，集合具有确定性、无序性和互异性，常用的有交并差及对称差。注意集合的运算使用的是Python中的位运算符。

```python
set1 = {1, 2, 3, 3, 3, 2}
print(set1)         # {1, 2, 3}
print(len(set1))    # 3

set1 = {1, 2, 3, 4, 5, 6, 7}
set2 = {2, 4, 6, 8, 10}
## 求交
print(set1 & set2)  # {2, 4, 6}
## 求并
print(set1  set2)  # {1, 2, 3, 4, 5, 6, 7, 8, 10}
## 求差
print(set1 - set2)  # {1, 3, 5, 7}
## 求对称差
print(set1 ^ set2)  # {1, 3, 5, 7, 8, 10}
```

### `dict`类型

`dict`类型即字典类型，通过键值对存储和访问数据。常用的有`items`, `keys`, `values`, `pop`等方法，类似列表生成式，也有字典生成式。

```python
person = {
    'name': 'CZG', 'age': 55
}
print(person['name'])     # CZG
print(person.keys())      # dict_keys(['name', 'age'])
print(person.items())     # dict_items([('name', 'CZG'), ('age', 55)])
print(person.pop('name')) # CZG
print(person)             # {'age': 55}

## 字典生成式示例
stocks = {
    'AAPL': 191.88, 'GOOG': 1186.96, 'IBM': 149.24,
    'ORCL': 48.44, 'ACN': 166.89, 'FB': 208.09, 'SYMC': 21.29
}
stocks2 = {key: value for key, value in stocks.items() if value > 100}
print(stocks2)  
# {'AAPL': 191.88, 'GOOG': 1186.96, 'IBM': 149.24, 'ACN': 166.89, 'FB': 208.09}
```

### 小结

以上几种数据类型构成了Python编程的基础，大家从这些数据类型的方法也能感受到Python语言的**简洁与易理解**。相比于C语言，Python更希望程序员写出**容易理解的代码**。

## 面向对象编程技术初步

面向对象是一种目前比较流行的编程方法，是一种程序设计的方法论。相对于面向过程的编程方法，面向对象更契合人类正常的思维方式，更适用于开发、维护复杂系统。在这种编程方法下，程序中的数据和数据操作函数是一个逻辑上的整体，这个整体被称为对象。引用一段对面向对象编程的精辟描述：

> 把一组数据和处理数据的方法组成**对象**，把行为相同的对象归纳为**类**，通过**封装**隐藏对象的内部细节，通过**继承**实现类的特化和泛化，通过**多态**实现基于对象类型的动态分派。

这句话并不那么好理解，接下来我们将进行一些解释。

在Python中，我们使用`class`关键字声明一个类，其语法结构为`class 类名:`，调用时，可以使用`.`运算符进行调用，具体参见下例：

```python
class Student:
    def study(self, course_name):
        print(f'学生正在学习{course_name}.')
    def play(self):
        print(f'学生正在玩游戏.')

stu1 = Student()
stu2 = Student()
# 通过“类.方法”调用方法，第一个参数是接收消息的对象，第二个参数是学习的课程名称
Student.study(stu1, 'Python程序设计')    # 学生正在学习Python程序设计.
# 通过“对象.方法”调用方法，点前面的对象就是接收消息的对象，只需要传入第二个参数
stu1.study('Python程序设计')             # 学生正在学习Python程序设计.
Student.play(stu2)    # 学生正在玩游戏.
stu2.play()           # 学生正在玩游戏. 
```

### Python魔术方法

提到类，就不得不先提一下Python的魔术方法。在Python中，所有以双下划线`__`包裹起来的方法，统称为魔术方法（Magic Method， 由于是双下划线，也可称dunder），它是一种特殊的方法，往往不会显式地调用。魔术方法在类或对象的某些事件触发后会自动运行，让类具有神奇的“魔力”。Python中的魔术方法很多，例如控制算术运算符的`__add__`, `__mul__`等，控制比较运算符的`__eq__`等，还有控制类型转换、属性操作、构造析构的魔术方法。这里对常用的`__init__`, `__repr__`稍作介绍。

### `__init__`初始化方法

`__init__`方法类似C++类中的构造函数。需要注意的是，`__init__`函数的第一个参数为实例本身，通常名字为`self`，通过`self`可以访问实例的属性。

```python
class Student:
    """学生"""
    def __init__(self, name, age):
        """初始化方法"""
        self.name = name
        self.age = age
    def study(self, course_name):
        """学习"""
        print(f'{self.name}正在学习{course_name}.')
    def play(self):
        """玩耍"""
        print(f'{self.name}正在玩游戏.')

stu1 = Student('程志刚', 21)
stu2 = Student('XX', 15)
stu1.study('Python程序设计')    
# 程志刚正在学习Python程序设计.
stu2.play()
# XX正在玩游戏.
```

### `__repr__`方法

`__repr__`方法可以改变`print`函数的行为。

```python
class Student:
    """学生"""
    def __init__(self, name, age):
        """初始化方法"""
        self.name = name
        self.age = age
    def __repr__(self):
        return f'{self.name}: {self.age}'

stu1 = Student('程志刚', 21)
print(stu1)        # 程志刚: 21
students = [
    stu1, 
    Student('张三', 16), 
    Student('李四', 25)
]
print(students)    
# [程志刚: 21, 张三: 16, 李四: 25]
```

### 封装

封装是为了便利代码的使用者，即程序员在编写类的过程中，隐藏一切可以隐藏的实现细节，只向外界暴露简单的调用接口。例如对于钟表类，可以定义`run`函数处理小时、分钟、秒的进位，使用者只需调用`run`即可。

```python
class Clock(object):
    """数字时钟"""

    def __init__(self, hour=0, minute=0, second=0):
        self.hour = hour
        self.min = minute
        self.sec = second

    def run(self):
        self.sec += 1
        if self.sec == 60:
            self.sec = 0
            self.min += 1
            if self.min == 60:
                self.min = 0
                self.hour += 1
                if self.hour == 24:
                    self.hour = 0

    def show(self):
        """显示时间"""
        return f'{self.hour:0>2d}:{self.min:0>2d}:{self.sec:0>2d}'

# 创建时钟对象
clock = Clock(23, 59, 58)
while True:
    # 给时钟对象发消息读取时间
    print(clock.show())
    # 休眠1秒钟
    time.sleep(1)
    # 给时钟对象发消息使其走字
    clock.run()
```

在本例中，将时钟的进位与显示封装起来，外部调用时，只需要调用相应函数即可。

### 继承

面向对象的编程语言支持在已有类的基础上创建新类，从而减少重复代码的编写。提供继承信息的类叫做父类（超类、基类），得到继承信息的类叫做子类（派生类、衍生类）。由于Python2.x版本的遗留问题，虽然Python3.x已经不必显式继承`object`类，但依然建议大家显式继承。继承的语法为`class 类名(父类名):`

```python
class Person(object):    # 此处显式继承了object类
    """人类"""
    def __init__(self, name, age):
        self.name = name
        self.age = age
    
    def eat(self):
        print(f'{self.name}正在吃饭.')
    
    def sleep(self):
        print(f'{self.name}正在睡觉.')

class Student(Person):
    """学生类"""
    
    def __init__(self, name, age):
        super().__init__(name, age)
    
    def study(self, course_name):
        print(f'{self.name}正在学习{course_name}.')

p = Person("CZG", 21)
p.eat()                    # CZG正在吃饭.
stu = Student("程志刚", 21)
stu.study("Pytorch")       # 程志刚正在学习Pytorch.
```

注意在本例中，重写了子类的`__init__`方法，如果不重写，将自动调用父类构造方法进行构造，如果重写，则默认不会调用，需要自己通过`super().__init__`调用父类构造方法。

## Python模块

为了编写可维护的代码，我们把很多函数分组，分别放到不同的文件里，这样，每个文件包含的代码就相对较少，很多编程语言都采用这种组织代码的方式。Python中每个文件就代表了一个模块（module）。使用模块可以大大提升代码可维护性，同时，也让编写代码不必从零开始。当一个模块编写完毕，就可以被其他地方引用。我们在编写程序的时候，也经常引用其它模块，包括Python内置的模块和来自第三方的模块。

当然，使用模块还可以避免函数名和变量名冲突。相同名字的函数、变量可以分别存在不同的模块中。在使用模块时，可以使用`import`关键字导入。

例如在同一文件夹下，分别有`module1.py`, `module2.py`, `test.py`三个文件。

`module1.py`文件内容：

```python
def foo():
    print('hello, world!')
```

`module2.py`文件内容

```python
def foo():
    print('goodbye, world!')
```

`test.py`文件内容

```python
import module1
import module2
# 用“模块名.函数名”的方式（完全限定名）调用函数
module1.foo()    # hello, world!
module2.foo()    # goodbye, world!
```

除了自己编写的模块外，Python本身还内置了许多模块，例如处理时间的`time`模块，处理文件系统的`os`模块等等。我们还可以自己安装第三方模块来进一步简化代码编写。例如`numpy`, `pandas`等就属于非常出名的第三方模块。

限于篇幅，此处不在详述如何使用conda，pip管理模块，大家可以参考https://www.jianshu.com/p/fe8cc7b6f558。

安装模块的常用命令：

```c
conda install <package-name>
pip install <package-name>

e.g. 

pip install numpy
conda install numpy
pip install scikit-learn
```

## 后续学习

以上是Python非常基础的语法，但Python核心语法不仅限于此。后续大家还可以学习Python标准库，文件读写，字符编码，正则表达式，面向对象进阶，函数式编程，各类包的使用（如numpy，pandas）以至机器学习……

在这里，笔者再推荐几个网站。

如果大家编程时，代码报错怎么办？

原文：[https://realpython.com/python-traceback/](https://realpython.com/python-traceback/)

译文：[https://blog.csdn.net/muzico425/article/details/99688343](https://blog.csdn.net/muzico425/article/details/99688343)

比较好的Python教程：

1.  [https://github.com/jackfrued/Python-100-Days](https://github.com/jackfrued/Python-100-Days)
    
2.  [https://github.com/jackfrued/Python-Core-50-Courses](https://github.com/jackfrued/Python-Core-50-Courses)
    
3.  [https://www.liaoxuefeng.com/wiki/1016959663602400](https://www.liaoxuefeng.com/wiki/1016959663602400)
    

官方文档：

[https://docs.python.org/zh-cn/3/](https://docs.python.org/zh-cn/3/)

Python语法速查：

1.  [https://www.pythoncheatsheet.org/](https://www.pythoncheatsheet.org/)
    
2.  [https://programming-idioms.org/cheatsheet/Python](https://programming-idioms.org/cheatsheet/Python)
    
3.  [https://programming-idioms.org/cheatsheet/C/Python](https://programming-idioms.org/cheatsheet/C/Python)
    

提问或搜索：

[https://stackoverflow.com/](https://stackoverflow.com/)

## 参考资料

本篇技术贴部分参考以下内容

\[1\] [https://github.com/jackfrued/Python-Core-50-Courses](https://github.com/jackfrued/Python-Core-50-Courses)

\[2\] [https://www.liaoxuefeng.com/wiki/1016959663602400](https://www.liaoxuefeng.com/wiki/1016959663602400)

\[3\] [https://docs.python.org/zh-cn/3/](https://docs.python.org/zh-cn/3/)

* * *

供稿 科协技术部 审核 顾燚 程志刚