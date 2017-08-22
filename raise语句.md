一般来说我们的else语句，通常都是跟if语句来搭配使用的，在Python中else语句除了能够跟if语句搭配，同样可以跟for语句while语句进行搭配。**但else语句只在循环完成后才执行，也就是说，只要循环没有结束，或者跳出循环了，就不会去执行else的代码了。**

**跟while循环搭配**
```py
a = 5
while a >0:
    print(a)
    a -= 1
else:
    print('执行else')
```
执行结果
```py
5
4
3
2
1
执行else
```

再来看如果跳出循环后：
```py
a = 5
while a >0:
    print(a)
    a -= 1
    break
else:
    print('执行else')

```
执行结果:
```py
D:\Python35\python.exe D:/my_script/pyscript/work33.py
5
Process finished with exit code 0

```
同样的for语句的使用也是一样，这里就不在演示了。

**else语句跟try语句搭配**只要try语句的内容不报错，就会去执行else的内容,看例子

```py
try:
    a = 5
except:
    print(a)
else:
    print('执行了else的内容')

```

