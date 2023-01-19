# Python_1_12_其他

## 变量

### 1.创建变量

Python 的变量无需声明，只需要一次赋值，该变量就能够被成功创建。 //区别c语言

### 2.访问变量

使用变量名直接访问变量

### 3.变量名

变量名，通常是由字母、数字和下划线（_）构成，但不能以数字打头。

变量名是区分大小写的，Python 3 还支持中文字符作为变量名。



## 字符串

### 1.字符串类型

Python 字符串分为Single quotes、Double quotes 还有 Triple quoted 三种形式。

```python
#single quotes 单引号
>>>print('hello world')
hello world
```

```python
#double quotes 双引号
>>>print("hello world")
hello world
```

```python
#混用单双引号
>>>print("'hello world'")
'hello world'
>>>print('"hello world"')
"hello world"
```

```python
#triple quotes 三引号引用多行文本
>>> poetry = """
面朝大海，春暖花开

从明天起，做一个幸福的人
喂马、劈柴，周游世界
从明天起，关心粮食和蔬菜
我有一所房子，面朝大海，春暖花开

从明天起，和每一个亲人通信
告诉他们我的幸福
那幸福的闪电告诉我的
我将告诉每一个人

给每一条河每一座山取一个温暖的名字
陌生人，我也为你祝福
愿你有一个灿烂的前程
愿你有情人终成眷属
愿你在尘世获得幸福
我只愿面朝大海，春暖花开
"""
```

### 2.字符串加法和乘法（拼接和复制）

```python
#拼接
>>> '123' + '456789'
'123456789'
```

```python
#复制
>>> print("hello world\n" * 3)
hello world
hello world
hello world
```



## 转义字符

```python
\\ #反斜杠
\' #单引号
\" #双引号
\a #响铃
\b #退格符
\n #换行符
\t #水平制表符
\v #垂直制表符
\r #回车符
\f #换页符
\ooo #八进制数
\xhh #十六进制数
```



## 数字类型

Python 有三种不同的数字类型，分别是：整数、浮点数和复数。

### 1.整数

整数长度无限制的，有无限大的精度。

### 2.浮点数

小数以浮点数的形式呈现。

浮点数存储在计算机是存在误差，例如：

```python
>>> 0.1 + 0.2
0.30000000000000004
>>> 0.3 == 0.1 + 0.2
False
```

```python
#精确计算浮点数  decimal模块（十进制）
>>> import decimal
>>> a = decimal.Decimal('0.1')
>>> b = decimal.Decimal('0.2')
>>> print(a + b)
0.3
```

```python
#科学计数法（E记法）
>>> x = 0.00005
>>> x
5e-05
```

### 3.复数

```python
#包含一个实部和一个虚部
>>> 1 + 2j
(1+2j)
#x.real 访问该复数的实部，x.imag 访问其虚部
>>> x = 1 + 2j
>>> x.real
1.0
>>> x.imag
2.0
```

### 运算

```python
x + y
x - y
x * y
x / y
x // y #地板除 取比目标结果小的最大整数
x % y
-x
+x
abs(x) #返回绝对值 若复数则为复数的模
int(x) #转换成整数 若小数则截掉小数部分
float(x) #将指定的值转换成浮点数
complex(re, im) #将指定的值转换成复数
pow(x, y) #幂运算符
x ** y
```









