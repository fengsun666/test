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

### 3.字符串方法

#### 大小写

*capitalize()、casefold()、title()、swapcase()、upper()、lower()*

```python
>>> x = "I love FishC"
>>> x.capitalize()  # 字符串首字母大写，其他小写
'I love fishc'
>>> x.casefold()  # 所有字母均小写
'i love fishc'
>>> x.title()  # 单词首字母大写，其他小写
'I Love Fishc'
>>> x.swapcase()  # 大小写翻转
'i LOVE fISHc'
>>> x.upper()  # 全部大写
'I LOVE FISHC'
>>> x.lower()  # 全部小写（与casefold有区别）
'i love fishc'
```

#### 左中右对齐 

*center(width, fillchar=' ')、ljust(width, fillchar=' ')、rjust(width, fillchar=' ')、zfill(width)*

width：指定字符串宽度。若指定宽度小于源字符串宽度，原样输出。

fillchar：默认空格。

```python
>>> x = "有内鬼，停止交易！"
>>> x.center(5)
'有内鬼，停止交易！'
>>> x.center(15)  # 居中对齐
'   有内鬼，停止交易！   '
>>> x.ljust(15)  # 左对齐
'有内鬼，停止交易！      '
>>> x.rjust(15)  # 右对齐
'      有内鬼，停止交易！'
>>> x.zfill(15)  # 0填充左侧
'000000有内鬼，停止交易！'
>>> "520".zfill(5)
'00520'
>>> "-520".zfill(5)
'-0520'
>>> x.center(15, "淦")
'淦淦淦有内鬼，停止交易！淦淦淦'
>>> x.ljust(15, "淦")
'有内鬼，停止交易！淦淦淦淦淦淦'
>>> x.rjust(15, "淦")
'淦淦淦淦淦淦有内鬼，停止交易！'
```

#### 查找

*1.count(sub[, start[, end]])、2.find(sub[, start[, end]])、3.rfind(sub[, start[, end]])、4.index(sub[, start[, end]])、5.rindex(sub[, start[, end]])*

start:起始位置

end:结束位置

```python
>>> x = "上海自来水来自海上"
>>> x.count("海")
2
>>> x.count("海", 0, 5)
1
>>> x.find("海") # 从左往右找
1
>>> x.rfind("海") # 从右往左找
7
>>> x.find("龟") # 没有指定元素返回-1
-1
>>> x.index("龟") # 抛出异常错误
Traceback (most recent call last):
  File "<pyshell#6>", line 1, in <module>
    x.index("龟")
ValueError: substring not found
```

#### 替换

*1.expandtabs([tabsize=8])、2.replace(old, new, count=-1)、3.translate(table)*

tabsize:使用多少空格代替原来的tab

count:指替换次数。默认为-1，即替换全部。

制定表格：str.maketrans(x[, y[, z]]) 

```python
# code.expandtabs()
# code.replace( , , )
>>> table = str.maketrans("ABCDEFG", "1234567") # 将前字符串对应替换为后字符串
>>> "I love China".translate(table)
'I love 3hina'
>>> table = str.maketrans("ABCDEFG", "1234567", "lovena") # 第三个参数为忽略字符串
'I 3hi'
```

#### 判断

*1.startswith(prefix[, start[, end]])、2.endswith(suffix[, start[, end]])、3.istitle()、4.isupper()、5.islower()、6.isalpha()、7.isascii()、8.isspace()、9.isprintable()、10.isdecimal()、11.isdigit()、12.isnumeric()、13.isalnum()、14.isidentifier()*

*这 14 个方法都是应对各种情况的判断，所以返回的都是一个布尔类型的值 —— 要么是 True，要么是 False。*

start,end参数：规定起止位置

startswith(prefix[, start[, end]])：判断prefix参数指定的子字符串是否出现在字符串的起始位置

endswith(suffix[, start[, end]])： 结束位置。

istitle:判断一个字符串中的所有单词是否都是以大写字母开头，其余字母均为小写。

islower:判断一个字符串中的所有单词是否都是小写字母。

isupper:判断一个字符串中的所有单词是否都是大写字母。

isalpha:判断一个字符串中是否只是由字母组成。

isascii:判断一个字符串中是否只是由 ASCII 字符组成.

isspace:判断是否为一个空白字符串.

isprintable:是否所有字符都是可打印。

isdecimal:是否为数字  十进制

isdigit:是否为数字  十进制

isnumeric:是否为数字  十进制，罗马，中文，繁体

isalnum:只要isalpha,isdecimal,isdigit,isnumeric任一返回True,就返回True

isidentifier:判断一个字符串是否为 Python 的保留标识符。如"if","while'',"for"

```python
# startswith
>>> x = "I love Python"
>>> x.startswith("I")
True
>>> x.startswith("我")
False
# endswith
>>> x.endswith("Python")
True
>>> x.endswith("C")
False
# istitle
>>> x = "I Love Python"
>>> x.istitle()
True
```

#### 截取

*lstrip(chars=None)、rstrip(chars=None)、strip(chars=None)、removeprefix(prefix)、removesuffix(suffix)*

若无参数，则截取空格。

```python
>>> "    左侧不要留白".lstrip()
'左侧不要留白'
>>> "右侧不要留白    ".rstrip()
'右侧不要留白'
>>> "    左右不要留白    ".strip()
'左右不要留白'
```

截取具体的子字符串，则用removeprefix,removesuffix

```python
>>> "www.baidu.com".removeprefix("www.")
'baidu.com'
>>> "www.baidu.com".removesuffix(".com")
'www.baidu'
```

#### 拆分

*partition(sep)、rpartition(sep)、split(sep=None, maxsplit=-1)、rsplit(sep=None, maxsplit=-1)、splitlines(keepends=False)*

*partition(sep) 和 rpartition(sep) 方法的区别是前者是从左往右找分隔符，后者是从右往左找分隔符：*

```python
# 以上两种若无分隔符，原字符串放在第一个元素，其它两个元素为空字符串。
>>> "www.baidu.com".partition(".")
('www', '.', 'baidu.com')
>>> "baidu.com/python".partition("/")
('baidu.com', '/', 'python')
```

*split(sep=None, maxsplit=-1) 和 rsplit(sep=None, maxsplit=-1) 方法则是可以将字符串切成一块块：*

```python
>>> "苟日新，日日新，又日新".split("，")
['苟日新', '日日新', '又日新']
>>> "苟日新，日日新，又日新".rsplit("，")
['苟日新', '日日新', '又日新']
>>> "苟日新，日日新，又日新".split("，", 1)
['苟日新', '日日新，又日新']
>>> "苟日新，日日新，又日新".rsplit("，", 1)
['苟日新，日日新', '又日新']
```

*splitlines(keepends=False) 方法会将字符串进行按行分割，并将结果以列表的形式返回：*

```python
>>> "苟日新\n日日新\n又日新".splitlines()
['苟日新', '日日新', '又日新']
>>> "苟日新\r日日新\r又日新".splitlines()
['苟日新', '日日新', '又日新']
>>> "苟日新\r日日新\r\n又日新".splitlines()
['苟日新', '日日新', '又日新']
```

*keepends 参数用于指定结果是否包含换行符，True 是包含，默认 False 则表示是不包含：*

```python
>>> "苟日新\r日日新\r\n又日新".splitlines(True)
['苟日新\r', '日日新\r\n', '又日新']
```

#### 拼接

*join(iterable)*

iterable 参数指定插入的子字符串.

```python
>>> ".".join(["www", "baidu", "com"])
'www.baidu.com'
>>> "^".join(("bai", "d", 'u'))
'bai^d^u'
>>> "".join(("bai", "du"))
'baidu'
```

加法拼接与join拼接比较：字符串级数越高，加法拼接较join拼接更快

### 4.格式化字符串

格式化字符串就是使用一对花括号（{}）来表示替换字段，就在原字符串中先占一个坑的意思，然后真正的内容被放在了 format()方法的参数中。

```python
>>> "1+2={}, 2的平方是{}，3的立方是{}".format(1+2, 2*2, 3*3*3)
'1+2=3, 2的平方是4，3的立方是27'
```

```python
# 花括号写数字表示参数位置
>>> "{1}看到{0}就很激动！".format("Python", "我")
'我看到Python就很激动！'

# 同一索引值可被多次引用
>>> "{0}{0}{1}{1}".format("是", "非")
'是是非非'

# 关键字索引(可与位置索引混合使用)
>>> "我叫{name}，我爱{fav}。".format(name="a", fav="Pyhon")
'我叫a，我爱Pyhon。'

# 输出花括号
>>> "{}, {}, {}".format(1, "{}", 2)
'1, {}, 2'
>>> "{}, {{}}, {}".format(1, 2)
'1, {}, 2'
```

### 5.**字符串格式化语法**

```python
format_spec     ::=  [[fill]align][sign][#][0][width][grouping_option][.precision][type]
fill            ::=  <any character>
align           ::=  "<" | ">" | "=" | "^"
sign            ::=  "+" | "-" | " "
width           ::=  digit+
grouping_option ::=  "_" | ","
precision       ::=  digit+
type            ::=  "b" | "c" | "d" | "e" | "E" | "f" | "F" | "g" | "G" | "n" | "o" | "s" | "x" | "X" | "%"
```

####  对齐**[align]**

![对齐](https://xxx.ilovefishc.com/forum/202112/02/190356hkn3qxii66izqnx6.png.thumb.jpg)

```python
>>> "{:^}".format(250)
'250'
>>> "{:^10}".format(250)
'   250    '
>>> "{1:>10}{0:<10}".format(520, 250)
'       250520       '
>>> "{left:>10}{right:<10}".format(right=520, left=250)
'       250520       '
```

#### 填充**[fill]**

在数字前加'0'：

```python
#用法只对数字有效
>>> "{:010}".format(520)
'0000000520'
>>> "{:010}".format(-520)
'-000000520'
```

对齐+填充：

```python
>>> "{1:%>10}{0:%<10}".format(520, 250)
'%%%%%%%250520%%%%%%%'
>>> "{:0=10}".format(520)
'0000000520'
>>> "{:0=10}".format(-520)
'-000000520'
```

#### 符号**[sign]**

仅对数字类型有效

![sign](https://xxx.ilovefishc.com/forum/202112/18/181030vc1zkcrtzlc2lt23.png.thumb.jpg)

#### 精度**[.precision]**

精度（[.precision]）选项是一个十进制整数，对于不同类型的参数，它的效果是不一样的：



- 对于以 'f' 或 'F' 格式化的浮点数值来说，是限定小数点后显示多少个数位
- 对于以 'g' 或 'G' 格式化的浮点数值来说，是限定小数点前后共显示多少个数位
- 对于非数字类型来说，限定最大字段的大小（换句话说就是要使用多少个来自字段内容的字符）
- 对于整数来说，则不允许使用该选项值

#### 类型**[type]**

![type1](https://xxx.ilovefishc.com/forum/202112/18/181247n5a070nraocafwif.png.thumb.jpg)

![type2](https://xxx.ilovefishc.com/forum/202112/18/181350r5qxpq5umlpl5qwo.png.thumb.jpg)

#### f-字符串

便于字符操作，例：

```python
>>> f"1+2={1+2}, 2的平方是{2*2}，3的立方是{3*3*3}"
'1+2=3, 2的平方是4，3的立方是27'
>>> 
>>> "{:010}".format(-520)
>>> f"{-520:010}"
'-000000520'
>>> 
>>> "{:,}".format(123456789)
>>> f"{123456789:,}"
'123,456,789'
>>> 
>>> "{:.2f}".format(3.1415)
>>> f"{3.1415:.2f}"
'3.14'
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

