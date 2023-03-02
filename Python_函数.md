# Python_函数

**==还未完成==**

用于打包代码。

- 可以最大程度地实现代码重用，减少冗余的代码
- 可以将不同功能的代码段进行封装、分解，从而降低结构的复杂度，提高代码的可读性

## 一、函数基本性质

### 1.创建和调用函数 def

格式如下：

```python
# 创建
>>> def myfunc():
...     pass  # 空语句，做占位符
...

# 调用
>>> myfunc()
>>>
```



---

### 2.函数参数

包含形参和实参

形式参数是函数定义的时候写的参数名字（比如下面例子中的 name 和 times）；实际参数是在调用函数的时候传递进去的值（比如下面例子中的 "Python" 和 5）。

```python
>>> def myfunc(name, times):
...     for i in range(times):
...         print(f"I love {name}.")
...
>>> myfunc("Python", 5)
I love Python.
I love Python.
I love Python.
I love Python.
I love Python.
```



---

### 3.函数返回值

```python
>>> def div(x, y):
...     z = x / y
...     return z
...
>>> div(4, 2)
2.0
# 若无return语句，则返回None
```



## 二、参数

### 1.位置参数

在通常的情况下，实参是按照形参定义的顺序进行传递的：由于在定义函数的时候，就已经把参数的名字和位置确定了下来，将 Python 中这类位置固定的参数称之为位置参数。

```python
>>> def myfunc(s, vt, o):
...    return "".join((o, vt, s))
...
>>> myfunc("Python", "爱", "我")
'我爱Python'
>>> myfunc("我", "爱", "Python")
'Python爱我'
```

### 2.关键字参数

```python
>>> myfunc(o="我", vt="爱", s="Python")
'我爱Python'
```

同时使用位置参数和关键字参数时，位置参数必须是在关键字参数之前。

```python
>>> myfunc(o="我", "爱", "Python")
SyntaxError: positional argument follows keyword argument
```

### 3.默认参数

```python
>>> def myfunc(s, vt, o="我"):
...     return "".join((o, vt, s))
...
>>> myfunc("Python", "爱")
'我爱Python'
# 若指定了该参数值，则默认的值就会被覆盖
>>> myfunc("你", "爱", "Python")
'你爱Python'
# 注：若要使用默认参数，则应该把它们摆在最后
```



### 4.收集参数

定义阶段* & **

收集参数，指只指定一个参数，然后允许调用函数时传入任意数量的参数。用于解决定义一个函数的时候，需要传入的参数的个数是不确定的，按照一般的写法可能需要定义很多个相同的函数然后指定不同的参数个数的复杂情况。

```python
# 定义收集参数,即在形参的前面加上星号（*）来表示
>>> def myfunc(*args):
...     print("有%d个参数。" % len(args))
...     print("第2个参数是：%s" % args[1])
...
>>> myfunc("我", "百度")
有2个参数。
第2个参数是：百度
>>> myfunc(1, 2, 3, 4, 5)
有5个参数。
第二个参数是：2
# 若在收集参数后面还需指定其它参数，则在调用函数的时候应使用关键参数来指定后面的参数
>>> def myfunc(*args, a, b):
...     print(args, a, b)
... 
>>> myfunc(1, 2, 3, a=4, b=5)
(1, 2, 3) 4 5
# 收集参数可以将参数们打包为字典，做法是使用连续的两个星号（**）
>>> def myfunc(**kwargs):
...     print(kwargs)
... 
>>> myfunc(a=1, b=2, c=3) # 传递时使用关键字参数
{'a': 1, 'b': 2, 'c': 3}
# 混合使用的举例
>>> def myfunc(a, *b, **c):
...     print(a, b, c)
... 
>>> myfunc(1, 2, 3, 4, x=5, y=6)
1 (2, 3, 4) {'x': 5, 'y': 6}
```



### 5.解包参数

调用阶段* & **

在形参上使用称之为参数的打包，在实参上的使用，则起到了相反的效果，即为解包参数。

```python
>>> args = (1, 2, 3, 4)
>>> def myfunc(a, b, c, d):
...     print(a, b, c, d)
... 
>>> myfunc(*args)
1 2 3 4

>>> args = {'a':1, 'b':2, 'c':3, 'd':4}
>>> myfunc(**args)
1 2 3 4
```

## 三、作用域

### 1.局部作用域

变量定义的位置是在函数里面，那么它的作用域就仅限于函数中，我们将它称为局部变量，作用域仅限于该函数。

### 2.全局作用域

在任何函数的外部去定义一个变量，那么它的作用域就是全局的，我们也将其称为全局变量。

## 四、嵌套函数

```python
>>> def funA():
...     x = 520
...     def funB():
...         x = 880
...         print("In funB, x =", x)
...     print("In funA, x =", x)
# 注：外部函数 funA() 里嵌套了一个内部函数 funB()，该内部函数是无法被直接调用的，想要调用 funB()，必须得通过 funA()。
>>> funB()
Traceback (most recent call last):
  File "<pyshell#23>", line 1, in <module>
    funB()
NameError: name 'funB' is not defined
>>> funA()
In funB, x = 880
In funA, x = 520
```



## 五、global 语句，nonlocal 语句

使用global 语句可破除限制在函数内部修改全局变量的值。

```python
>>> x = 880
>>> def myfunc():
...     global x
...     x = 520
...     print(x)
... 
>>> myfunc()
520
>>> print(x)
520
```

使用nonlocal 语句可破除限制在嵌套函数的内部修改外部函数变量的值。

```python
>>> def funA():
...     x = 520
...     def funB():
...         nonlocal x
...         x = 880
...         print("In funB, x =", x)
...     funB()
...     print("In funA, x =", x)
... 
>>> funA()
In funB, x = 880
In funA, x = 880
```



## 六、闭包

可称之为工厂函数，由于参数不同，得到不同的 “生产线”。

```python
>>> def power(exp):
...     def exp_of(base):
...         return base ** exp
...     return exp_of
... 
>>> square = power(2)
>>> cube = power(3)
>>> square
<function power.<locals>.exp_of at 0x000001CF6A1FAF70>
>>> square(2)
4
>>> square(5)
25
>>> cube(2)
8
>>> cube(5)
125
```

