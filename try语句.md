**try**语句的用法用两种，一种是try-except，还有一种是try-finally

先来看看try-except语句

##try-except语句语法：

```py

try:
    检测范围
except:
    出现异常后的处理
```

我们先来看一看怎么使用，

```py
temp = input('不如来猜一下我现在心里想的数字呗')
guess = int(temp)
if guess == 6:
    pirnt('猜中了又如何，买得起宝马吗？')
else:
    print('猜错了，我想的是6')
print('游戏结束了，不玩了')
```

这个脚本呢，当用户输入的是正确的就不会有任何问题了，但只要用户输入的是一个非数字，那么这个代码就狗带了。你看

```py

不如来猜一下我现在心里想的数字呗 d
Traceback (most recent call last):
 File "D:/my_script/pyscript/work33.py", line 3, in <module>
 guess = int(temp)
ValueError: invalid literal for int() with base 10: 'd'
```

这里呢当我们输入的为字母d时，Python就跑出了一个ValueError的错误。
这里呢，我们知道当用户输入一个非数字类型的数据，就会抛出一个valueerror的错误，所以这里我们就使用valueError来接受这个异常信息。
```py
try:
    temp = input('不如来猜一下我现在心里想的数字呗')
    guess = int(temp)
    if guess == 6:
        pirnt('猜中了又如何，买得起宝马吗？')
    else:
        print('猜错了，我想的是6')
        print('游戏结束了，不玩了')
except ValueError as r:
    print('报错了，错误的原因是',r)
```
运行结果：
```py
不如来猜一下我现在心里想的数字呗asdf

报错了，错误的原因是 invalid literal for int() with base 10: 'asdf'

```
这里我们使用了ValueError来接受的用户的报错信息,并且将信息赋值个r将其打印了出来

##设置多个except

```py
try:
    a = 1+'a'
    int(a)
except TypeError as r:
    print('错错了，出错信息是,',r)
except ValueError as r:
    print('错错了，出错信息是,',r)
```
##一个except里处理多个异常
```py
try:
   a = 1+'a'
   int(a)
except (TypeError,ValueError) as r:
   print('错错了，出错信息是,',r)
```

##捕获所有异常
```py
try:
   a = 1+'a'
   int(a)
except:
   print('错错了')
```
如果无法确认是哪一个类型的报错，只是希望代码报错后，能够提示一个可以看得懂的提醒，那就这样做吧，但是并不推荐这样做

##try-finally语句
```py
try:
    检测范围
except:
    报错执行的代码
finally:
    无论如何都会去执行的代码
```
栗子一：
```py
try:
    a = 'a'+ 1
except:
    print('报错了')
finally:
    print('无论如何都去执行')
```
执行结果
```py
报错了

无论如何都去执行

```
栗子二:
```py
try:
    a = 2+ 1
except:
    print('报错了')
finally:
    print('无论如何都去执行')
```
执行结果：
```py
无论如何都去执行
```
