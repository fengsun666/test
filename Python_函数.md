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

### 5.解包参数



