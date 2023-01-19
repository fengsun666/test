# Python_1_12

## 缩进

### 1.推荐

```python
# 同开始分界符(左括号)对齐
foo = long_function_name(var_one, var_two,
                         var_three, var_four)

# 续行多缩进一级以同其他代码区别
def long_function_name(
        var_one, var_two, var_three,
        var_four):
    print(var_one)

# 悬挂缩进需要多缩进一级
foo = long_function_name(
    var_one, var_two,
    var_three, var_four)
```

### 2.反对

```python
# 采用垂直对齐时第一行不应该有参数
foo = long_function_name(var_one, var_two,
    var_three, var_four)

# 续行并没有被区分开，因此需要再缩进一级
def long_function_name(
    var_one, var_two, var_three,
    var_four):
    print(var_one)
```

### 3.if语句

```python
# 不采用额外缩进
if (this_is_one_thing and
    that_is_another_thing):
    do_something()

# 增加一行注释，在编辑器中显示时能有所区分
# supporting syntax highlighting.
if (this_is_one_thing and
    that_is_another_thing):
    # Since both conditions are true, we can frobnicate.
    do_something()

# 在条件语句的续行增加一级缩进
if (this_is_one_thing
        and that_is_another_thing):
    do_something()
```

### 4.括号

```python
my_list = [
    1, 2, 3,
    4, 5, 6,
    ]
result = some_function_that_takes_arguments(
    'a', 'b', 'c',
    'd', 'e', 'f',
    )
my_list = [
    1, 2, 3,
    4, 5, 6,
]
result = some_function_that_takes_arguments(
    'a', 'b', 'c',
    'd', 'e', 'f',
)
#以上两种表达等价
```

## 部分语法规则

### 1.tab与空格

推荐使用空格来进行缩进。

tab 应该只在现有代码已经使用 tab 进行缩进的情况下使用，以便和现有代码保持一致。

### 2.每行字符长度

将所有行都限制在 79 个字符长度以内。

推荐的换行方式是利用 Python 圆括号、方括号和花括号中的隐式续行（implied line continuation）。

很长的行可以通过在括号内换行来分成多行。

最好加上反斜杠来区别续行。

有时只能使用反斜杠。例如，较长的多个 with 语句不能采用隐式续行，只能接受反斜杠表示换行：

```python
with open('/path/to/some/file/you/want/to/read') as file_1, \
     open('/path/to/some/file/being/written', 'w') as file_2:
    file_2.write(file_1.read())
```

## 空行

使用 2 个空行来分隔最外层的函数（function）和类（class）定义。

使用 1 个空行来分隔类中的方法（method）定义。

可以使用额外的空行（尽量少）来分隔一组相关的函数。

## 导入import

1. 导入应该分行写，而不是都写在一行。

2. 导入应该写在代码文件开头，位于模块（module）注释和文档字符串之后，模块全局变量（globals）和常量（constants）声明之前。

   应该按照下面的顺序分组来写：

   - 标准库imports
   - 相关第三方imports
   - 本地应用/库的特定import

3. 从一个包括类的模块中导入一个类时,写为：

   ```python
   from...import...
   ```

## 字符串引用

表示字符串时，不管用单引号还是双引号都是一样的。

当字符串中包含单引号时，采用双引号来表示字符串，反之也是一样，这样可以避免使用反斜杠，代码也更易读。

## 注释

当注释和代码冲突时，优先考虑代码。当代码有改动时，一定要优先更改注释使其保持最新。

注释应该是完整的多个句子。

如果注释是一个短语或一个句子，其首字母应该大写。

除非开头是一个以小写字母开头的标识符（永远不要更改标识符的大小写）。

如果注释很短，结束的句号可以被忽略。

块注释通常由一段或几段完整的句子组成，每个句子都应该以句号结束。

你应该在句尾的句号后再加上 2 个空格。

### 1.行内注释

行内注释是和代码语句写在一行内的注释。

行内注释应该至少和代码语句之间有两个空格的间隔，并且以 # 和一个空格开始。

### 2.文档字符串

所有的公共模块，函数，类和方法都应该有文档字符串。

\1.对于非公共方法，文档字符串不是必要的，但你应该留有注释说明该方法的功能，该注释应当出现在 def 的下一行。

\2. PEP257 描述了好的文档字符应该遵循的规则。

其中最重要的是，多行文档字符串以单行 """ 结尾，不能有其他字符。\3. 对于仅有一行的文档字符串，结尾处的 """ 应该也写在这一行。

## 命名约定

### 1.避免

不要使用字符 ’l’（L 的小写的字母），’O’（o 大写的字母），或者 ’I’（i 的大写的字母）来作为单个字符的变量名。

在一些字体中，这些字符和数字 1 和 0 无法区别开来。

比如，当想使用 ’l’ 时，使用 ’L’ 代替。

### 2.包和模块命名

模块命名应精简，且为全小写。

若下划线能提高可读性，也可以在模块名中使用。

Python 包命名也应该精简，且为全小写，但不应使用下划线。

当使用 C 或 C++ 写的扩展模块有相应的 Python 模块提供更高级的接口时（比如，更加面向对象），C/C++ 模块名以下划线开头（例如， _sociket）。

### 

