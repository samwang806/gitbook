### lamdba匿名函数
```py
def ds(x):
    return 2*x+1
```
`ds(5)---->11`

我们来看一看lamdba的使用

`g = lamdba x : 2 * x + 1`

`g(5)`

在冒号的前面就是函数的参数，冒号的后面是函数的返回值，我们不需要给这个函数给命令，直接赋值变量调用就可以了。

```py
def add(x,y):
    return x+y
```
这种有多个参数的我们也可以使用lamdba使用

`g = lamdba x,y:x+y`

`g(5,7)`

