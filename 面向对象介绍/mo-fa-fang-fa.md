在python中方法名如果是\_\_xxxx\_\_\(\)的，那么就有特殊的功能，因此叫做“**魔法**”方法

在Python中魔法方法总是被双下横线所包围，现在我们来看看第一个魔法方法

###\_\_init\_\_方法

通常来说，\_\_init\_\_方法我们会叫它初始化方法，又叫构造方法，在创建对象的时候，对象就会自动的去调用\_\_init\_\_方法，其实在我们实例化对象时是可以将参数传入进去，这些参数会自动传入\_\_init\_\_\(\)方法中，举个栗子。

```py
class car():
    def __init__(self,brand):
        self.brand = brand
    def which_car(self):
        print('这是我的%s' %self.brand)
```

运行结果:

```py
>>>a = car('宝马')
>>>a.which_car()
>>>这是我的宝马
```

`__init__()`方法，在创建一个对象时默认被调用，不需要手动调用

`__init__(self)`中，默认有1个参数名字为self，如果在创建对象时传递了2个实参，那么

`__init__(self)`中出了self作为第一个形参外还需要2个形参，例如`__init__(self,x,y)`

`__init__(self)`中的self参数，不需要开发者传递，python解释器会自动把当前的对象引用传递进去

我们在这里使用时需要注意，\_\_init\_\_方法的返回值一定是None，不能返回其他内容，也就是说，在\_\_init\_\_方法中，我们不能够做任何的返回操作。

所以我们一般在初始化的时候才重写\_\_init\_\_方法，但其实\_\_init\_\_方法并不是实例化对象是第一个被调用的方法。

###`__str__()`方法
才是第一个被调用的方法，new方法与其他方法又有些不同，new方法的第一个参数并不是传入self，而是我们的类cls，其他的参数会直接传递给\_\_init\_\_方法，通常来说我们极少去重写这个方法，但是如果我们需要继承一个不可变的类型的时候，才会使用到。  
看例子：

```py
#创建demo1类，继承于str
class demo1(str):
    def __new__(cls,args):
        #调用字符串方法，将所有的内容转换成小写
        args = args.casefold()
        return str.__new__(cls,args)

a = demo1('abcSSGDG')
print(a)
```

### `__str__()`方法 {#2-定义str方法}

```
class Car:

    def __init__(self, newWheelNum, newColor):
        self.wheelNum = newWheelNum
        self.color = newColor

    def __str__(self):
        msg = "嘿。。。我的颜色是" + self.color + "我有" + int(self.wheelNum) + "个轮胎..."
        return msg

    def move(self):
        print('车在跑，目标:夏威夷')


BMW = Car(4, "白色")
print(BMW)
```



#### 总结 {#总结}

* 在python中方法名如果是
  `__xxxx__()`
  的，那么就有特殊的功能，因此叫做“魔法”方法
* 当使用print输出对象的时候，只要自己定义了
  `__str__(self)`
  方法，那么就会打印从在这个方法中return的数据



