单**继承**

有些时候我们需要实现一些功能，但是呢我们之前已经写过相关的一些类，这个时候我们就可以使用到继承了，继承的语法很简单。

```py
class 类名(被继承的类):
    pass#pass为占位符,表示什么都不做
```

被继承的类我们称之为父类，继承者我们叫做子类，一个子类可以继承父类的全部属性和方法。举个栗子

```py
class dad():
    def say(self):
        print('我是爸爸')

class son(dad):
    pass

d = dad()
s = son()
d.say()
s.say()
```

运行结果：

```py
我是爸爸

我是爸爸
```

那这个时候我们看到，son\(\)继承了dad的所有的属性和方法，所以呢，他也有say方法，可以print出我是爸爸来，但是这个呢显示是不对的，儿子怎么能说出我是爸爸这种话呢？所以我们需要修改一下继承过来的方法，这个我们就叫做**方法的重写**

```py
class dad():
    def hello(self):
        print('你好')

    def say(self):
        print('我是爸爸')
class son(dad):
    def say(self):
        print('我是儿子')
d = dad()
s = son()
d.say()
s.say()
s.hello()
```

运行结果：

```py
D:\Python35\python.exe D:/my_script/pyscript/work33.py

我是爸爸

我是儿子

你好
```

这里我们看到，我们在son类下，重写了say方法，这样就会覆盖调继承过来的say方法。

