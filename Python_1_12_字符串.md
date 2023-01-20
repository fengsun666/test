# Python_1_12_字符串

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

---

