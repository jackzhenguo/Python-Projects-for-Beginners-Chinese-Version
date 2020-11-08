
--------

<center> CHALLENGE QUESTION</center>

以下代码的结果是什么？

```python
values = { 4:4, 8:8, "Q":10, "ACE":11 }
card = ("Q", "Hearts")
print("{ }".format(values[ card[ 0 ] ] ) )
```

----







## 面向对象编程


Object-oriented programming，简称OOP，译为面向对象编程。在耳熟能响的众多语言当中，JavaScript、Java和C++等一众语言均以面向对象编程特性著称。本周，我们将开始学习掌握OOP编程，学会OOP的Python代码实现，并理解OOP存在的意义与作用。


在学习面向对象的编程过程中，我们需要掌握对象（object）与类（class）这两个核心概念。对象（object）通过类（class）进行创建，换而言之，类（class）可以视为对象（object）的模板/蓝图（blueprint ）。

以战地4游戏为例，其中的人物、车辆和武器即可视为各种类型的对象（objects）。同时，游戏中各分组通常由多人组成，这些人物具有相似的特征，如体重、身高、发色等。为所有人物编写相同代码的做法显得效率低下，鉴于此，我们可以采取更为高效的方式：为所有人物构建一个统一的模板（blueprint），所有人物均通过该模板进行创建。该举措能够节约代码量，提升代码管理效率。这周末，我们将利用Python的面向对象编程创建21点游戏。



本章概述

- 了解面向对象编程的基础知识

- 掌握属性的定义与使用

- 掌握方法的定义与使用

- 理解继承的概念

- 实战：使用类定义开始21点游戏编程实现

  



## Monday: 类的构造与实例化

在Python中，所有的对象（object）均由类（class）创建生成。换而言之，用Python编写代码的过程就是围绕面向对象编程开展的，Python也被视为面向对象的编程语言。面向对象编程（OOP）存在的意义两点：（1）节约代码量；（2）实现对象的个性化特征。



###  对象概念解析

在现实生活中，你身边可能有沙发、椅子、电视、书等事物。在编程的世界里，这些均可视为对象。更为甚之，人也可视为对象。究其原因，所有的对象均可视为来自于某个特定的统一的模板（blueprint）。在Python语言中，这些模板被称为类（class)。以汽车为例，所有的汽车均具有轮子、颜色、制造、型号、年份、车牌号等特征。Python的面向对象编程要求我们将汽车类（class）加以抽象，构建包含轮子、颜色、制造、型号、年份、车牌号等特征的模板（blueprint）；同时，在通过类创建对象的阶段，需要使得不同的汽车对象（objects）有不同的颜色、型号等特征值。如图7-1所示，概括了以上内容的图形化展示。

<img src="C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20201107195945958.png" alt="image-20201107195945958" style="zoom: 67%;" />

Figure 7-1. 通过汽车类（class）创建三个不同的汽车对象 (object)



### 面向对象编程（OOP）过程解析

由前述内容可知，面向对象编程（OOP）包含两个重要环节：

- 定义类（class ）：创建某个类的统一模板（blueprint）
- 生成对象（object）：通过类创建对象，该过程称为实例化instantiate）。

 

### 自定义一个类

学习面向对象编程，首先需要关注如何自定义一个类。Python中使用`def`关键字定义类（class），并使用缩进（block）定义类的属性（attributes）与方法（methods）。



现阶段，不必过分纠结属性（attributes）与方法（methods）的具体实现内容，暂时使用pass占位即可。将类（class）的定义类比于之前的函数（function）定义，在此给出自定义类的代码实现示例：

```python
# 创建第1个类
class Car( ):
	pass
	# 暂时使用pass占位，候选添加代码实现内容
```

运行上述代码块且不报错，说明你已经成功创建了第1个自定义的类。同时，以上代码结构将陪伴你Python生涯，后续你将学习如何将pass改为你需要实现的内容。

>注：Python中所有的数据对象均由与之对象的类实例化而来，打印实数的类型即可的`<class ‘int’>`。



### 创建一个对象

学习面向对象编程，随后需要关注如何借助类（class）实例化生成一个对象(object)。在类名后面加上一个括号即可实例化当前类并生成一个对象，通过赋值语句即可为该类打上标签，使得对应变量指向该对象。相应的代码实现梳理如下：

```python
# 由class实例化一个对象
class Car( ): # parens are optional here
	pass
ford = Car( ) # 由Car类创建一个实例，并贴上标签ford 
print(ford)
```

运行以上代码，你将获得以下输出`<__main__.Car object at
0x0332DB>`。以上结果表明，我们生成了一个来自 `Car`类的对象，该对象在内存中的地址值为：0x0332DB (16进制表示的内存地址)

> 注：内容地址可能有差异



### 创建多个对象

面向对象编程允许你从同一个类（Class）实例化多个对象，这些个对象可以存储在单独的变量中，也可以存储在诸如list、tuple等我们所接触的数据集合中。以下代码展示了创建多个对象的示意过程：

```python
#从同一个对象中创建多个实例
class Car( ):
	pass
ford = Car( ) # 创建第1个实例对象	 
subaru = Car( ) #创建第2个实例对象
print( hash(ford) )
print( hash(subaru) ) # hash函数的输出值代表当前变量在内容的地址
```

运行以上代码，我们们可以实例化两个变量并输出各自在内存中的地址值。记住：`hash()`函数的输出结果代表当前变量在内容中的地址。注意到，两个地址数值取值不同，换而言之，我们由`Car`这个类创建了两个不同的对象。后续，你将发现不同的对象能够拥有各自的个性化特征，而这正是面向对象编程（OOP）的魅力所在。



### 小结

本节的基本内容梳理如下：

- 阐述了与OOP相关的基本概念，重点包括：类（class）、对象（object）、实例化（instantiate）
- 概述了类的定义格式、对象的实例化过程





-----

<center> MONDAY EXERCISES </center>

1、**Animals**：创建一个Animals类，并据此实例化两个对象，分别存储在变量lion和tiger中

2、代码纠错：以下代码正确与否？倘若有错误之处，请指明。

```python
class Bus:
    pass
    	
school_bus = Bus()
```



----











## Tuesday：属性

前一章节阐述了类（class）的定义与实例化（instantiate），在此基础上，我们将学习之前所提及的个体化特征的概念——属性(attribute)。从语法定义上而言，属性是定义在类（class）内部的变量，其作用在于存储与实例（或者类）相关的个体化特征。以Car这个类为例，属性的定义可以涉及颜色、车轮数、座位数、引擎大小等。



### 属性声明与访问





```python
# 定义类属性
class Car( ):
	sound = "beep" # all car objects will have this sound attribute and its' value
	color = "red" # all car objects will have this color attribute and its' value

ford = Car( )
print(ford.color) # known as 'dot syntax'
```

在面向对象编程中，属性可视为类（class)内定义的变量，用于储存





### 更改属性值



 

### 定义 `__init__( )` 方法

现阶段，我们实例化所得对象的属性均






### 关于`self`参数





### 借助`__init__( )`创建多个实例







### 类属性与实例属性



`Global Attributes vs. Instance Attributes`