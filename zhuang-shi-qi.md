在看这篇文章之前，先需要知道闭包的作用。

假设我们现在已经实现了两个功能，

```py
def login():
    print('登录系统...')
    eat_time = random.randint(1,10)
    time.sleep(eat_time)


def logout():
    print('退出系统...')
    drink_time = random.randint(1,10)
    time.sleep(drink_time)
```

现在产品经理灵光一闪需要给登录和退出的功能加上一个计时器的功能，也就是说需要计算出这两个函数的所消耗的时间，那么没有办法只能修改我们的函数了。

Tips：

**random**模块

1. randint\(\)方法，它接受两个参数，并生成他们之间的随机整数

**time**模块

1. sleep\(\)方法，接受一个参数，有休眠的作用。

2. time\(\)方法，生成实时时间的方法。

这个时候我们需要注意，我们不能够在原来的函数上进行修改，因为原来的函数可能被其他的模块所调用或者所使用。

那经过一些列的巧妙的操作，我们大致上已经满足了产品的需求，代码如下：

```py
def show_time(funs):
    start_time = time.time()
    funs()
    end_time = time.time()
    print('总共花费了：%f 秒' % (end_time - start_time))

show_time(login)
show_time(logout)
```

Ps:注意变量名的命令规范性，不要随便取一些什么st,et,tt等等

看一下执行结果：

```py
登录系统...
总共花费了：8.000237 秒
退出系统...
总共花费了：7.000258 秒
```

我们看到执行结果，显示已经差不多满足了产品的要求了。

但是我们这样做还是有问题的，我们虽然实现了这样一个统计时间的功能，但是在执行的时候，我们却使她的功能调用方式已经发生了变化。原来我们使用这个函数是直接login\(\)，现在变成了show\_time\(login\)。我们还需要保证原来的调用方式不能变。

![](/assets/kick_face.png)

修改了一个通宵后：代码没看到的再去看看闭包

```py
def show_time(funs):
    def calc_time():
        start_time = time.time()
        funs()
        end_time = time.time()
        print('总共花费了：%f 秒' % (end_time - start_time))
    return calc_time

login = show_time(login)
logout = show_time(logout)
```

来看看执行结果：
```py
登录系统...
总共花费了：3.200237 秒
退出系统...
总共花费了：6.002258 秒
```



大功告成，总算满足了需求了。

然而python提供了一个更加简单的方式去进行调用

look look

```py
import time
import random

def show_time(funs):
    def calc_time():
        start_time = time.time()
        funs()
        end_time = time.time()
        print('总共花费了：%f 秒' % (end_time - start_time))
    return calc_time

@show_time    #login = show_time(login)
def login():
    print('登录系统...')
    eat_time = random.randint(1,10)
    time.sleep(eat_time)

@show_time     #logout = show_time(logout)
def logout():
    print('退出系统...')
    drink_time = random.randint(1,10)
    time.sleep(drink_time)


print('----------')
login()
logout()






```

注意函数的**@**的部分，我们只需要把之前写好的计时函数，在需要使用的函数\(login，logout\)上方写上@show\_time，就可以了，我们的调用就直接使用函数名即可，看下运行结果：

```py
----------
登录系统...
总共花费了：8.000237 秒
退出系统...
总共花费了：7.000258 秒
```

这个**@函数名**，就是我们的装饰器

简单的来说，装饰器本质就是一个Python函数，他可以让原有函数不需要做任何改变的前提下增加一些额外的功能，比如我们的计时、日志等等。她的返回值也是一个函数对象。

再简单一点：装饰器的就是为已经存在的对象添加额外的功能

