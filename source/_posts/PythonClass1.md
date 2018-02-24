---
title: Python类里面的初始化方法__init__
date: 2018-02-24 20:55:35
categories: Python
---
*python中的__init__(self)的意义*
***
Python中，__init__()方法是所谓的对象的“构造函数”，负责在对象初始化时进行一系列的构建操作

假设有如下类：
`class worker:`
    `pass`
在Python中，对某个类实例进行成员赋值，可以创建不存在的成员：
```
>>>a=worker()
>>>a.pay=55000
>>>a.name='Bob'
```
如果对于每一个worker类的实例对象，都要进行如此赋值的话，这个类会变得很难使用

另外，对于用于特殊场合的类，可能要求在对象创建时，进行连接数据库、连接FTP服务器、进行API验证等操作，这些初始化操作，都可以封装在__init__()方法中进行


__init__方法使用如下规则定义：
```
class ex:
    def __init__(self):
        pass
```
init__方法必须接受至少一个参数即self，Python中，self是指向该对象本身的一个引用，通过在类的内部使用self变量，类中的方法可以访问自己的成员变量，简单来说，self.varname的意义为”访问该对象的varname属性“

当然，__init__()中可以封装任意的程序逻辑，这是允许的，__init__()方法还接受任意多个其他参数，允许在初始化时提供一些数据，例如，对于刚刚的worker类，可以这样写：
```
class worker:
    def __init__(self,name,pay):
        self.name=name
        self.pay=pay
```
这样，在创建worker类的对象时，必须提供name和pay两个参数：
`>>>b=worker('Jim',5000)`
Python会自动调用worker.__init__()方法，并传递参数。


通常情况下，self形参由Python自动赋值，但是，在类继承中，并不是这样

例如，Python的HTML处理工具HTMLParser，是一个基于OOP模型的工具，要使用该工具，必须编写一个类，继承html.parser.HTMLParser类，并重载一系列方法，以定制自己的功能
```from html.parser.HTMLParser
 
class ex2(HTMLParser):
    def __init__(self):
        HTMLParser.__init__(self)
```
此处，需要调用了HTMLParser类的__init__方法，而且，此处手动给HTMLParser.__init__()方法的self形参赋值，事实上，如果不显式指定self形参的值，Python不会在此处自动为HTMLParser.__init__()方法的self形参进行赋值

如此设计的原因是，在子类中需要获得超类的成员和方法，而通过在子类的__init__方法中调用超类的__init__方法，并手动给它传递指向子类的self值，可以使超类的__init__方法将所初始化的变量设置成子类的变量，这样，就可以在子类中直接访问超类的变量了。

ps:具体为什么不在类中直接进行初始化,个人感觉一是__init__加载比较靠前,__new__之后马上就会__init__,二是感觉这样更加方便管理更加统一.

还有一个问题就是在类中用 类的名字.变量 和self.变量 不知道有什么区别但结果一样:
用qwer.name:
```
class qwer:
    name = 123
    def haha(self,haha):
        print('%d' % qwer.name)
np = qwer()
np.haha(236)
>>>123
```
用self.name:
```
class qwer:
    name = 123
    def haha(self,haha):
        print('%d' % self.name)
np = qwer()
np.haha(236)
>>>123
```
