# Python_1_12_字典

字典：唯一实现了映射关系的内置类型。

字典的关键符号是大括号（{}）和冒号（:）：这里就是两对映射关系，我们将冒号的左边称为字典的 “键”，右边称为字典的 “值”。在字典中，只要我们提供键，就可以获取其对应的值。方法跟序列类似，只不过这次在方括号中，咱们使用的是键，而非索引值：

例题：摩斯密码

```python
# 列表表示映射
# 摩斯密文表
c_table = [".-", "-...", "-.-.", "-..", ".", "..-.",
           "--.", "....", "..", ".---", "-.-", ".-..",
           "--", "-.", "---", ".--.", "--.-", ".-.",
           "...", "-", "..-", "...-", ".--", "-..-",
           "-.--", "--..", ".----", "..---", "...--", "....-",
           ".....", "-....", "--...", "---..", "----.", "-----"]
# 摩斯明文表
d_table = ["A", "B", "C", "D", "E", "F",
           "G", "H", "I", "J", "K", "L",
           "M", "N", "O", "P", "Q", "R",
           "S", "T", "U", "V", "W", "X",
           "Y", "Z", "1", "2", "3", "4",
           "5", "6", "7", "8", "9", "0"]
    
code = input("请输入摩斯密码：")
split_code = code.split(" ")
result = [d_table[c_table.index(each)] for each in split_code]
print(result)
```

```python
# 字典表示映射
c_table = {".-":"A", "-...":"B", "-.-.":"C", "-..":"D",
           ".":"E", "..-.":"F", "--.":"G", "....":"H",
           "..":"I", ".---":"J", "-.-":"K", ".-..":"L", 
           "--":"M", "-.":"N", "---":"O", ".--.":"P",
           "--.-":"Q", ".-.":"R", "...":"S", "-":"T",
           "..-":"U", "...-":"V", ".--":"W", "-..-":"X",
           "-.--":"Y", "--..":"Z", ".----":"1", "..---":"2",
           "...--":"3", "....-":"4", ".....":"5", "-....":"6",
           "--...":"7", "---..":"8", "----.":"9", "-----":"0"}
    
code = input("请输入摩斯密码：")
split_code = code.split(" ")
    
result = [c_table[each] for each in split_code]
print(result)
```



---

## 1.创建字典

法一：直接使用大括号和冒号的组合。

```python
>>> a = {"鸡":"你太美", "只因":"鸡"}
```

法二：使用 dict() 函数，每个参数就是一个键值对，键与值直接使用等号挂钩。

```python
>>> b = dict(鸡="你太美", 只因="鸡") # 键上无引号
```

法三：使用列表作为参数，列表中的每个元素是使用元组包裹起来的键值对。

```python
>>> c = dict([("鸡","你太美"), ("只因","鸡")])
```

法四：zip函数做dict函数参数

```python
>>> f = dict(zip(["鸡","只因","派神"], ["你太美","鸡","Python"]))
```

- 字典长度       len(d)

- 字典转化列表     list(d)  ==得到的是键的列表==        list(d.values()) ==得到的是值的列表==

- 字典逆向操作    list(reversed(d))  ==得到的是键的列表==    list(reversed(d.values())) ==得到的是值的列表== 

- 字典迭代器 iter() 

  ```python
  >>> e = iter(d)
  >>> next(e)
  'b'
  >>> next(e)
  'a'
  >>> next(e)
  'i'
  >>> next(e)
  'd'
  >>> next(e)
  'u'
  >>> next(e)
  'c'
  >>> next(e)
  Traceback (most recent call last):
    File "<pyshell#15>", line 1, in <module>
      next(e)
  StopIteration
  ```



---

## 2.字典处理

### 增 fromkeys(iterable[, value])

```python
>>> d = dict.fromkeys("baid", 250)
>>> d
{'b': 250, 'a': 250, 'i': 250, 'd': 250}
# 若不指定value参数，则默认为None

# 修改某个键的值，若无该键则增加一个新的键值对
>>> d['b'] = 70
>>> d
{'b': 70, 'a': None, 'i': None, 'd': None}
>>> d['u'] = 67
>>> d
{'b': 70, 'a': None, 'i': None, 'd': None, 'u': 67}
```

### 删 pop() popitem() del clear()

```python
>>> d.pop('i')
>>> d
{'b': None, 'a': None, 'd': None, 'u': 67}
# 若pop一个不存在的键，则抛出异常
```

```python
# Python3.7前为删除随机一个键值对，3.7后为删除最后一个键值对
>>> d.popitem()
('u', 67)
>>> d
{'b': None, 'a': None, 'd': None}
```

```python
# 删除指定元素
>>> del d['a']
>>> d
{'b': None, 'd': None}
# 删除整个字典（包括字典名）
>>> del d
>>> d
Traceback (most recent call last):
  File "<pyshell#14>", line 1, in <module>
    d
NameError: name 'd' is not defined
# 清空字典内容
>>> d = dict.fromkeys("baidu", 250)
>>> d
{'b': 250, 'a': 250, 'i': 250, 'd': 250, 'u': 250}
>>> d.clear()
>>> d
{}
```

### 改 update()

```python
# 改单个
>>> d = dict.fromkeys("baidu")
>>> d
{'b': None, 'a': None, 'i': None, 'd': None, 'u': None}
>>> d['i'] = 115
>>> d
{'b': None, 'a': None, 'i': 115, 'd': None, 'u': None}
# 改多个  update()
>>> d.update({'a':105, 'd':104})
>>> d
{'b': None, 'a': 105, 'i': 115, 'd': 104, 'u': None}
>>> d.update(b='70', u='67')
>>> d
{'b': '70', 'a': 105, 'i': 115, 'd': 104, 'u': '67'}
```

### 查 get()

```python
# 查指定键返回值，若无指定键则报错
>>> d['u']
67
# get()
>>> d.get('c', "这里没有c")
'这里没有c'
# 查指定键返回值，若无指定键则指定新值
>>> d.setdefault('u', "code")
67
>>> d
{'b': 70, 'a': 105, 'i': 115, 'd': 104, 'u': 67}
>>> d.setdefault('c', "code")
'code'
>>> d
{'b': 70, 'a': 105, 'i': 115, 'd': 104, 'u': 67, 'c': 'code'}
```

### 拷贝 copy()

语法：d.copy()     *浅拷贝*



---

## 3.视图对象

items()、keys() 和 values() 三个方法分别用于获取字典的键值对、键和值三者的视图对象。

```python
>>> d
{'b': 70, 'a': 105, 'i': 115, 'd': 104, 'u': 67, 'c': 'code'}
>>> items = d.items()
>>> keys = d.keys()
>>> values = d.values()
>>> items
dict_items([('b', 70), ('a', 105), ('i', 115), ('d', 104), ('u', 67), ('c', 'code')])
>>> keys
dict_keys(['b', 'a', 'i', 'd', 'u', 'c'])
>>> values
dict_values([70, 105, 115, 104, 67, 'code'])
>>> d.pop('c')
'code'
>>> items
dict_items([('b', 70), ('a', 105), ('i', 115), ('d', 104), ('u', 67)])
>>> keys
dict_keys(['b', 'a', 'i', 'd', 'u'])
>>> values
dict_values([70, 105, 115, 104, 67])
```

## 4.嵌套

普通嵌套

```python
>>> d = {"张三": {"语文":60, "数学":70, "英语":80}, "李四": {"语文":80, "数学":90, "英语":70}}
>>> d["张三"]["数学"]
70
```

嵌套列表

```python
>>> d = {"张三": [60, 70, 80], "李四": [80, 90, 70]}
>>> d["张三"][1]
70
```



---

## 5.字典推导式  

==还没掌握==

```python
>>> d = {'b':70, 'a':105, 'i':115, 'd':104, 'u':67}
>>> b = {v:k for k,v in d.items()}
>>> b
{70: 'b', 105: 'a', 115: 'i', 104: 'd', 67: 'u'}
>>> d
{'b': 70, 'a': 105, 'i': 115, 'd': 104, 'u': 67}

>>> c = {v:k for k,v in d.items() if v > 100}
>>> c
{105: 'a', 115: 'i', 104: 'd'}

>>> d = {x:ord(x) for x in "baidu"}
>>> d
{'b': 70, 'a': 105, 'i': 115, 'd': 104, 'u': 67}
```

