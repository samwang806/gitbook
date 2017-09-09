我们先来看一下如果我们的函数里面有多个参数时，装饰器函数应该如何处理
```py
import time

def show_time(funs):
    def calc_time():
        start_time = time.time()
        funs()
        end_time = time.time()
        print('总共花费了：%f 秒' % (end_time - start_time))
    return calc_time


@show_time
def login(user,pwd):
    time.sleep(1)
    if user=='admin' and pwd=='admin123':
        print('登录成功')
    else:
        print('登录失败')


login('amdin','admin123')

```
运行结果：
```py
D:\Python35\python.exe D:/my_script/pyscript/day16.py
Traceback (most recent call last):
  File "D:/my_script/pyscript/day16.py", line 21, in <module>
    login('amdin','admin123')
TypeError: calc_time() takes 0 positional arguments but 2 were given
```
报错信息提示我们calc_time()报错了，这个时候我们看到，我们的calc_time()函数，他就是在调用我们的login函数，所以他会需要接受我们的这两个参数user,pwd,所以我们修改一下：

```py
import time

def show_time(funs):
    def calc_time(x,y):
        start_time = time.time()
        funs(x,y)
        end_time = time.time()
        print('总共花费了：%f 秒' % (end_time - start_time))
    return calc_time


@show_time
def login(user,pwd):
    time.sleep(1)
    if user=='admin' and pwd=='admin123':
        print('登录成功')
    else:
        print('登录失败')


login('admin','admin123')

```
运行结果：
```py
D:\Python35\python.exe D:/my_script/pyscript/day16.py
登录成功
总共花费了：1.000786 秒

Process finished with exit code 0
```
这个就是我们去使用，如果函数中有多个参数，我们的装饰器的中要如何修改。

现在我们除了这个计算时间的功能，我们还想加入一个打印日志的功能，怎么办？
很简单，直接在原来的装饰器函数中修改即可：
```py
import time

def show_time(funs):
    def calc_time(x,y):
        start_time = time.time()
        funs(x,y)
        end_time = time.time()
        print('总共花费了：%f 秒' % (end_time - start_time))
        print('在这里假装打印日志')
    return calc_time


@show_time
def login(user,pwd):
    time.sleep(1)
    if user=='admin' and pwd=='admin123':
        print('登录成功')
    else:
        print('登录失败')
login('admin','admin123')

```

这样我们就可以记录日志了。
那如果有些地方需要我们打印，有些地方不需要打印怎么办？
其实这个时候我们就可以在装饰器中增加参数了，用参数来标识是否需要打印日志。
参数加在哪里？
我们直接使用@show_time 其实就等于 show_time(login)，这里已经写死了，这种时候呢，我们可以换一种思路
```py
import time
def loger(flag):
    def show_time(funs):
        def calc_time(x,y):
            start_time = time.time()
            funs(x,y)
            end_time = time.time()
            print('总共花费了：%f 秒' % (end_time - start_time))
            if flag == 'y':
                print('在这里假装打印日志')
        return calc_time
    return show_time

@loger('y')
def login(user,pwd):
    time.sleep(1)
    if user=='admin' and pwd=='admin123':
        print('登录成功')
    else:
        print('登录失败')

@loger('')
def login2(user,pwd):
    time.sleep(1)
    if user=='admin' and pwd=='admin123':
        print('登录成功')
    else:
        print('登录失败')


login('admin','admin123')
print('-------------------')
login2('adm2in','admin123')


```
我们看一下，既然无法直接修改show_time()，那么我们就直接在show_time上在嵌套一层loger函数，给他一个参数flag，我们看到这个loger函数什么都没做，只是返回了一个show_time，这样我们在使用loger这个装饰器的时候，就可以根据自己的需求来了。
看运行结果：
```py
D:\Python35\python.exe D:/my_script/pyscript/day16.py
登录成功
总共花费了：1.000012 秒
在这里假装打印日志
-------------------
登录失败
总共花费了：1.000179 秒

Process finished with exit code 0
```