# 多继承 {#多继承}

## 1. 多继承 {#1-多继承}

![](/assets/moremorejichengde.png)

从图中能够看出，所谓多继承，即子类有多个父类，并且具有它们的特征

Python中多继承的格式如下:

```py
class A:
    def printA(self):
        print('----A----')

# 定义一个父类
class B:
    def printB(self):
        print('----B----')

# 定义一个子类，继承自A、B
class C(A,B):
    def printC(self):
        print('----C----')

obj_C = C()
obj_C.printA()
obj_C.printB()
```

运行结果:

```
----A----
----B----
```

#### 说明 {#说明}

* python中是可以多继承的
* 父类中的方法、属性，子类会继承

## 注意点 {#注意点}

* 想一想:
  > 如果在上面的多继承例子中，如果父类A和父类B中，有一个同名的方法，那么通过子类去调用的时候，调用哪个？

```py
class base(object):
    def test(self):
        print('----base test----')
class A(base):
    def test(self):
        print('----A test----')

# 定义一个父类
class B(base):
    def test(self):
        print('----B test----')

# 定义一个子类，继承自A、B
class C(A,B):
    pass


obj_C = C()
obj_C.test()

print(C.__mro__) #可以查看C类的对象搜索方法时的先后顺序
```



