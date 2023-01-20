# Python_1_12_其他

## 变量

### 1.创建变量

Python 的变量无需声明，只需要一次赋值，该变量就能够被成功创建。 //区别c语言

### 2.访问变量

使用变量名直接访问变量

### 3.变量名

变量名，通常是由字母、数字和下划线（_）构成，但不能以数字打头。

变量名是区分大小写的，Python 3 还支持中文字符作为变量名。



---



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

---



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

---



## 数据结构

### 1.列表List

类似c语言数组

```python
#创建列表（中括号，逗号隔开）
>>> rhyme = [1, 2, 3, 4, 5, "上山打老虎"]
>>> print(rhyme)
[1, 2, 3, 4, 5, '上山打老虎']

#访问列表
##按顺序访问（for循环）
>>> for each in rhyme:
...     print(each)
...
1
2
3
4
5
上山打老虎
##随机访问（下标索引）  正向：0 1 2 3 4 5 逆向：-6 -5 -4 -3 -2 -1
>>> rhyme[0]
1
>>> rhyme[2]
3
>>> rhyme[5]
'上山打老虎'
##访问范围  List.[某一位置:某一位置]
>>> rhyme[0:2]
1
2 
3
```

#### 列表处理1

##### 列表长度

len(List)

##### 增 *append*  *extend*  *insert*

单个：List .append("element")     

多个：List .extend([element 1，element 2...]) 

任意位置：insert(参数1，参数2)   参数1为插入的位置 参数2为插入的元素

切片语法：     ==还没掌握==

```python
>>> s = [1, 2, 3, 4, 5]
>>> # 下面的做法等同于 s.append(6)
>>> s[len(s):] = [6]
>>> s
[1, 2, 3, 4, 5, 6]
>>> # 下面的做法等同于 s.extend([7, 8, 9])
>>> s[len(s):] = [7, 8, 9]
>>> s
[1, 2, 3, 4, 5, 6, 7, 8, 9]
```

##### 删 *remove*  *pop*  *clear*

指定元素：List .remove("element")  注：若存在多个匹配元素，只删除第一个；若无匹配元素，则报错。

指定位置元素：List .pop(参数)，参数为元素的下标索引值  注：若无参数，则删最后一个

清空：List .clear()

##### 改

下标索引赋值

```python
>>> heros = ['蜘蛛侠', '绿巨人', '黑寡妇', '鹰眼', '灭霸', '雷神']
>>> heros[4] = "钢铁侠"
>>> heros
['蜘蛛侠', '绿巨人', '黑寡妇', '鹰眼', '钢铁侠', '雷神']
```

连续多个元素替换： 切片  ==还没掌握==

```python
>>> heros[3:] = ["武松", "林冲", "李逵"]
>>> heros
['蜘蛛侠', '绿巨人', '黑寡妇', '武松', '林冲', '李逵']
```

##### 排序与翻转 *sort*  *reverse*

```python
>>> nums = [3, 1, 9, 6, 8, 3, 5, 3]
>>> nums.sort()  # 升序排序
>>> nums
[1, 3, 3, 3, 5, 6, 8, 9]
>>> nums.reverse() # 逆序排序
>>> nums
[9, 8, 6, 5, 3, 3, 3, 1]

# 一步到位
>>> nums = [3, 1, 9, 6, 8, 3, 5, 3]
>>> nums.sort(reverse=True) #默认reverse=False 若reverse=True将对列表进行降序排序。
>>> nums
[9, 8, 6, 5, 3, 3, 3, 1]
```

语法：list .sort(reverse=True|False, key =myFunc)

| 参数    | 描述                                                         |
| :------ | :----------------------------------------------------------- |
| reverse | 可选。reverse=True 将对列表进行降序排序。默认是 reverse=False。 |
| key     | 可选。指定排序标准的函数。                                   |

##### 查 *count*  *index*

查元素个数：  List .count(element)

查元素下标索引值：  List .index(element)       List ,index(element, start, end)

查有无：in           if  "element" in List...

##### 拷贝 *copy*  *copy+deepcopy*

*浅拷贝*：浅拷贝可以用于处理一维列表，对于嵌套列表的拷贝，只能拷贝第一层数据，其余仅拷贝其引用。

New List = List .copy()

```python
# 切片法
>>> nums_copy2 = nums[:]
>>> nums_copy2
[3, 1, 9, 6, 8, 3, 5, 3]
```

实现逻辑：

![浅拷贝](https://xxx.ilovefishc.com/forum/202106/23/014911fkj8fkvdk1ok9989.png.thumb.jpg)

深拷贝：处理多维列表

```python
>>> x = [[1, 2, 3], [4, 5, 6], [7, 8, 9]]
>>> y = copy.deepcopy(x)
>>> x[1][1] = 0
>>> x
[[1, 2, 3], [4, 0, 6], [7, 8, 9]]
>>> y
[[1, 2, 3], [4, 5, 6], [7, 8, 9]]
```

实现逻辑：

![深拷贝](https://xxx.ilovefishc.com/forum/202106/23/014927ywiasuqoidbtylz9.png.thumb.jpg)

#### 列表处理2

##### 加法和乘法（拼接和重复）

```python
# 加法
>>> s = [1, 2, 3]
>>> t = [4, 5, 6]
>>> s + t
[1, 2, 3, 4, 5, 6]
# 乘法
>>> s * 3
[1, 2, 3, 1, 2, 3, 1, 2, 3]
```

##### 嵌套列表（多维列表）

```python
>>> matrix = [[1, 2, 3], [4, 5, 6], [7, 8, 9]]

>>> matrix = [[1, 2, 3],
              [4, 5, 6],
              [7, 8, 9]]
```

##### 访问嵌套列表

```python
# for循环法
>>> for i in matrix:
...     for each in i:
...         print(each)
...
1
2
3
4
5
6
7
8
9
# 下标索引
>>> matrix[0]
[1, 2, 3]
>>> matrix[1]
[4, 5, 6]
>>> matrix[2]
[7, 8, 9]
>>> matrix[0][0]
1
>>> matrix[1][1]
5
>>> matrix[2][2]
9
```

##### 创建和初始嵌套列表

```python
>>> A = [0] * 3
>>> for i in range(3): 
...     A[i] = [0] * 3
...
>>> A
[[0, 0, 0], [0, 0, 0], [0, 0, 0]]
```

range函数语法

*range(start, stop[, step])*  

start: 从start开始，默认为0

stop: 计数到 stop 结束，但不包括 stop。

step：步长，默认为1。





