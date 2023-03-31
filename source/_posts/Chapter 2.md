---
title: Python：从入门到实践 第二章
date: 2023-03-27
updated: 2023-03-31
tags:
categories:
keywords:
description:
top_img:
comments:
cover:
toc:
toc_number:
toc_style_simple:
copyright:
copyright_author:
copyright_author_href:
copyright_url:
copyright_info:
mathjax:
katex:
aplayer:
highlight_shrink:
aside:
---

# 1.1 Jupyter notebook 的基础使用

```python
print("Hello jupyter notebook")
```

    Hello jupyter notebook

## 1.1.1 快捷键

```python
#esc:从编辑模式退回命令模式
#enter:从命令模式退回编辑模式
#在命令模式（esc）下：
        #按m切换为markdown单元格，y切换为代码单元格，a（above）/b（below）在上/下方创建新的代码块，h快捷键一览
        #dd（delete）删除，z撤销，x剪切，c复制，shift+v在上方黏贴，v在当前位置粘贴，L标记当前代码块行数
#shift+enter可以运行当前代码块并跳到下一代码块，alt+enter执行当前代码块并在下面新建一个代码块
```

## 1.1.2 markdown 的应用

```python
#引用#
#跳转至外部链接#
#插入图片#
```

> 我是引用，我前面有一条灰色竖杠

[我是外部链接点我上 b 站](http://bilibili.com)

![我是图片](https://img1.baidu.com/it/u=2735769730,1464143095&fm=253&fmt=auto&app=138&f=JPEG?w=352&h=499)

```python
#在markdown模式中通过$$符号实现数学公式的镶嵌，如下所示：
#其中的$公式$为插入公式的特殊写法，其中$公式$代表公式在一行内完成，$$公式$$则代表公式在两行完成
```

这是爱因斯坦质能转换方程$E=mc^2$，揭示了质量之间的关系

这是一元二次方程求解公式$$x = \frac {-b\pm \sqrt {b^2-4ac}}{2a}$$

# 1.2 VS Code 的常用快捷键

F1 输入 theme/主题可以打开主题设置，选择自己喜欢的主题

commond + d 选取下一个相同字符

option(alt) +左键在鼠标所在烂添加光标，以同时更改多行内容

commond + s 保存

commond + z 撤销

commond + c

commond + v

commond + f 查找 按左方小箭头可以替换内容，第一个按钮是单个替换，第二个是全部替换

左方搜素 🔍 图标为全局搜索，可以在多个文件中找东西

option(alt) + shift +上/下键 将所在行代码快速复制到上面或下面

查看—编辑器布局 可以更改外观，实现将上方代码直接复制到下方之类的功能 而且不用反复拉去进度条

首选项中有键盘快捷方式可以查看所有的快捷键

# 1.3 github 的 push 以及内容更新

如何更新 hexo 上面的内容：

```python
cd "博客目录"
hexo cl
hexo s
```

如何使用 git 把文件夹 push 到 github：

```python
cd "博客目录"
git init
touch README #新建readme文件
git checkout -b master #创建分支
git add .
git commit -m "my blog first commit"
git remote add origin "远端github仓库地址"
git branch -M main
git push -u origin main
```

如何更新 github 上面的内容：

```python
git add . #将修改的内容添加到git中
#也可以尝试 git add  “新文件名称”
git commit -m “update” #将文件提交到缓存区域
#这一步我暂时没做 git pull origin master 从本地仓库或本地分支获取并集成
ssh -T git@github.com #用ssh密钥连接github网站
git push -u origin main #提交更新版的文件、
```

# 2.1 变量 variable

## Values

A **value** is one of the fundamental things — like a number, or a string, or a boolean — that a program manipulates.

### _`Literals`_

- Numbers
  - integer, (1,2,3...)
  - float, (1.23, 4.56...)
  - complex number, (c = 1 + 2j...)
  - convert (int(), float(), str(), etc.)
- Strings
  - index
  - methods (upper, lower, split, strip, etc.) https://docs.python.org/2/library/string.html
- Boolean

### _`Variables`_

- The first character of the identifier must be a letter of the alphabet (upper or lowercase) or an under- score ('\_').
- The rest of the identifier name can consist of letters (upper or lowercase), underscores ('\_') or digits (0-9).
- Identifier names are case-sensitive. For example, **myname** and **myName** are not the same.

## 2.1.1 变量的命名规则与引用规则

```python
#变量命名包含字母，数字和下划线（没有空格）
#但是变量不能用数字开头或者只包含数字（9=xxx或1_message=xxx这种是不行的）
#变量最好不包括l，o这些容易混淆的字母（在词组里的话没事）
#不能用关键字和函数名命名（比如min，max等）
#注意前后使用的变量名一致
```

```python
#1_test="hello"(x)
#9="world"(x)
#print(f"{1_test} {9}")
```

```python
test="hello"#(✅)
_message="world"#(✅)
print(f"{test} {_message}")
```

    hello world

## 2.1.2 变量是盒子/标签（具有覆写性）

```python
message="try jupyter"#你可以称呼这里的message为object
print(message)
message="try python3"
print(message)
```

    try jupyter
    try python3

# 2.2 字符串 string

用“”或‘’扩起来的数据为 string

不固定“”或‘是为了表达的方便，例如：

```python
print("She is Joke's friend")
print('Bereth and Edelgard are "best friend"')
```

    She is Joke's friend
    Bereth and Edelgard are "best friend"

错误示范：

```python
'She is Joke's friend'
"Bereth and Edelgard are "best friend""
```

      Cell In[7], line 1
        'She is Joke's friend'
                             ^
    SyntaxError: unterminated string literal (detected at line 1)

## 2.2.1 使用方法 function 修改字符串

下方将介绍三种方法：

title() --- 首字母大写

upper() --- 全大写

lower() --- 全小写

```python
str1 = "hello world"
str2 = "TEST"
print(str1.title())
print(str1.upper())
print(str2.lower())
```

    Hello World
    HELLO WORLD
    test

## 2.2.2 在字符串中使用变量

```python
first_name = "ada"
last_name = "lovelace"
full_name = f"{first_name} {last_name}"#使用f""字符串，将变量放在{}中就可以使用了 3.6版本之前是format()方法
print(full_name)
```

    ada lovelace

## 2.2.3 使用制表符\t 与换行符\n

```python
print("Language:\n\tpython\n\tC++\n\tJavaScrpit")#\t的作用是缩进一格\n的作用是换行
```

    Language:
    	python
    	C++
    	JavaScrpit

## 2.2.4 删除字符串中的空白

下面将介绍三种方法：

rstrip() --- 删除右边的空白

lstrip() --- 删除左边的空白

strip() --- 删除所有空白

```python
favorite_language ="    My favorite language is python.    "
favorite_language.rstrip()
```

    '    My favorite language is python.'

```python
favorite_language.lstrip()
```

    'My favorite language is python.    '

```python
favorite_language.strip()
```

    'My favorite language is python.'

## 2.2.5 分割字符串中的内容

有的时候，我们会需要根据某一元素分割字符串中的制定内容，在这种情况下，我们可以使用 Split 这一方法 split()

如果我们没有指定()中的内容，那么 split 会默认删除空格，并分割其前后的内容，若有指定内容，则会删除指定内容，并分割其前后内容

```python
favorite_language ="    My favorite language is python.    "
print(favorite_language.split())
str = '你好超级小说在线读i love you超级小说在线读'
print(str.split('超级小说在线读'))
```

    ['My', 'favorite', 'language', 'is', 'python.']
    ['你好', 'i love you', '']

# 2.3 数 Numbers

不带小数点的数为整数 integer，带小数点的数为浮点数 float

基础运算方法:

加法：+ 减法：- 乘法：\* 除法：/ 乘方：\*\* 使用()可以指定运算顺序

```python
print(2+3)
```

    5

```python
print(3-2)
```

    1

```python
print(2*3)
```

    6

```python
print(4/2)#除法结果会获得浮点数
```

    2.0

```python
print(3**3)
```

    27

```python
print(1+2*3)
print((1+2)*3)
```

    7
    9

## 2.3.1 浮点数

浮点数的运算方式与整数相同，需要注意的是只要运算中带有浮点数，运算结果也会默认生成浮点数

```python
print(3.0**3)
print(3.0-1)
print(3.0+1)
```

    27.0
    2.0
    4.0

## 2.3.2 使用下划线更好地显示变量(只在编码中可见)

```python
universe_age = 14_000_000_000
print(universe_age)
```

    14000000000

## 2.3.3 同时给多个变量赋值

```python
#可以用,将变量隔开,实现多个变量赋值
x,y,z=1,2,3
print(x)
print(z)
```

    1
    3

## 2.3.4 常量

```python
#常量类似于变量，但其值在整个生命周期（程序）中保持不变。python没有内置的常量类型
#但程序员习惯将使用全大写命名的变量视作常量，因此可以通过这种方式指出该值应为常量
```

```python
MAX_CONNECTIONS = 5000
```

# 2.4 注释

在 python 中，注释用#表示，出现在#后的内容会被 python 解释器忽略

```python
#比如这样
print("Hello every one")
```

    Hello every one

## 2.5 一个彩蛋 hhh

python 代码指导原则（python 之禅）

```python
import this
```

## The Zen of Python, by Tim Peters

Beautiful is better than ugly.

Explicit is better than implicit.

Simple is better than complex.

Complex is better than complicated.

Flat is better than nested.

Sparse is better than dense.

Readability counts.

Special cases aren't special enough to break the rules.

Although practicality beats purity.

Errors should never pass silently.

Unless explicitly silenced.

In the face of ambiguity, refuse the temptation to guess.

There should be one-- and preferably only one --obvious way to do it.

Although that way may not be obvious at first unless you're Dutch.

Now is better than never.

Although never is often better than _right_ now.

If the implementation is hard to explain, it's a bad idea.

If the implementation is easy to explain, it may be a good idea.

Namespaces are one honking great idea -- let's do more of those!
