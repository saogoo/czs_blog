---
title: Python：从入门到实践 第三章
date: 2023-03-31
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

# 3.1 列表 List 是什么

```python
#列表List 中包含多个元素，用[]进行表示，用,分隔其中的元素，例子如下：
```

```python
bicycles = ['trek', 'cannondale', 'redline', 'specialized']
print(bicycles)
```

    ['trek', 'cannondale', 'redline', 'specialized']

## 3.1.1 如何访问列表中的元素

```python
#通过在list_name后面添加[]并输入索引数字来获得其中的元素，索引是一种搜素方法，需要注意的是，索引都是从0开始的
print(bicycles[0])
print(bicycles[2])
print(bicycles[4])
```

    trek
    redline



    ---------------------------------------------------------------------------

    IndexError                                Traceback (most recent call last)

    Cell In[8], line 4
          2 print(bicycles[0])
          3 print(bicycles[2])
    ----> 4 print(bicycles[4])


    IndexError: list index out of range

```python
#除了一个一个访问之外，我们还可以直接访问一定范围内的值
list_need = ["water","food","air", "space", "money"]
print(list_need[2:4])#在[:]中 冒号前的index指向的内容会被包含在内 冒号后的index指向的内容则不会被包含在内
print(list_need[2:])
print(list_need[:4])
```

    ['air', 'space']
    ['air', 'space', 'money']
    ['water', 'food', 'air', 'space']

```python
#使用titile还可以获得首字母大写格式的内容
print(bicycles[0].title())
```

    Trek

## 3.1.2 索引从 0 开始且可以指定负数

```python
print(bicycles[0])
print(bicycles[-1])#使用负数索引会从最后一个数开始往前索引
print(bicycles[-2])
```

    trek
    specialized
    redline

## 3.1.3 使用列表中的各个值

```python
#列表中的各个值可像变量一样使用。例如，拼接并使用列表中的值来创建消息。
#试着使用列表中的‘’trek‘来打印“My first bicycle was a Redline."
#如果你不知道redline这个值在列表中的哪里，那我们首先需要找到它：
bicycles.index('redline')#index有做索引的意思
#接着打出首字母大写格式的该单词（这里可以顺便回顾怎么打出全大写和全小写）
print(bicycles[2].title())
#最后使用f"{}"将我们需要的信息串联起来并进行打印：
message = f"My first bicycle was a {bicycles[2].title()}."
print(message)
```

    Redline
    My first bicycle was a Redline.

## 3.1.4 检索已知元素在列表中的位置

```python
list_need = ["water","food","air", "space", "money"]
list_need.index("food")
```

    1

```python
3.1.5
```

```python

```

## 练习

```python
#下方有一些练习题，尝试完成他们以更好地掌握所学内容
#3-1 姓名: 将一些朋友的姓名存储在一个列表中，并将其命名为names 。依次访问该列表中的每个元素，从而将每个朋友的姓名都打印出来。
name = ["Cecilia", "Aurelia", "Kynt", "Sand"]
#依次打印有几种方法，最快的是直接打印整个list
print(name)
#也可以使用f"{}"的方式，但是略显复杂
print(f"{name[0]} {name[1]} {name[2]} {name[3]}")

```

    ['Cecilia', 'Aurelia', 'Kynt', 'Sand']
    Cecilia Aurelia Kynt Sand

```python
#3-2 问候语: 继续使用练习3-1中的列表，但不打印每个朋友的姓名，而为每人打印一条消息。每条消息都包含相同的问候语，但抬头为相应朋友的姓名。
#这是一个很好的练习，我们可以使用for loop语句来快速地帮助我们完成这个任务，当然你也可以选择一条一条手动输入
#假设我们要输入的信息是“Nice to meet you, 'name'”，手动输入的方法为：
print(f"Nice to meet you, {name[0]}")
print(f"Nice to meet you, {name[1]}")
print(f"Nice to meet you, {name[2]}")
print(f"Nice to meet you, {name[3]}")
```

    Nice to meet you, Cecilia
    Nice to meet you, Aurelia
    Nice to meet you, Kynt
    Nice to meet you, Sand

```python
#3-2
#假设我们拥有许多人名，这将会十分费力，有没有更好的解决方法？答案之一或许是loop。
#关于for loop的具体使用方法后面的章节会出现，这里简单作为一个解题方法进行记录：
for i in range(len(name)):
    print(f"Nice to meet you, {name[i]}")
```

    Nice to meet you, Cecilia
    Nice to meet you, Aurelia
    Nice to meet you, Kynt
    Nice to meet you, Sand

```python
#3-3 自己的列表: 想想你喜欢的通勤方式，如骑摩托车或开汽车，并创建一个包含多种通勤方式的列表。
        #根据该列表打印一系列有关这些通勤方式的宣言，如“I would like to own a Honda motorcycle”。
vehicle =["car", "motorcycle","train"]
print(f"Today, I‘d like to go home by {vehicle[2]}")
```

    Today, I‘d like to go home by train

# 3.2 修改，添加和删除元素

## 3.2.1 修改列表元素

```python
motorcycles = ['honda', 'yamaha', 'suzuki']
print(motorcycles)
motorcycles[0] = 'ducati'
print(motorcycles)
```

    ['honda', 'yamaha', 'suzuki']
    ['ducati', 'yamaha', 'suzuki']

## 3.2.2 在列表中添加元素

### 1. 在列表末尾添加元素 append()

```python
#使用append()可以在列表末尾添加元素
motorcycles = ['honda', 'yamaha', 'suzuki']
print(motorcycles)
motorcycles.append('ducati')
print(motorcycles)
```

    ['honda', 'yamaha', 'suzuki']
    ['honda', 'yamaha', 'suzuki', 'ducati']

```python
#append 这一方法使得我们可以先创建空列表再实时添加需要的元素
motorcycles = []
motorcycles.append('honda')
motorcycles.append('yamaha')
motorcycles.append('suzuki')
print(motorcycles)
```

    ['honda', 'yamaha', 'suzuki']

### 2. 在列表中插入元素 insert()

```python
#使用 insert()可以在任意位置加入我们需要的元素，注意的是我们需要指定该元素的索引 index 和值 value，
#现在我们想要获得一个排列为['honda', 'yamaha', 'suzuki', 'ducati']的list,但我们只有motorcycles = ['honda', 'yamaha', 'ducati']这一list,解法如下：
motorcycles = ['honda', 'yamaha', 'ducati']
motorcycles.insert(2, 'suzuki')
print(motorcycles)
```

    ['honda', 'yamaha', 'suzuki', 'ducati']

## 3.2.3 从列表中删除元素 del 语句, remove(), pop()

有时候我们需要从列表中删除一个或多个元素，例如：将注销账号的用户移除列表，我们可以通过索引位置或者值来删除列表中的元素。注意使用 del 语句移除后的元素将无法使用：

```python
#用索引位置删除元素 del语句（del+name+position）
motorcycles = ['honda', 'yamaha', 'suzuki']
del motorcycles[1]
print(motorcycles)
#用值删除元素 remove()
motorcycles = ['honda','honda', 'yamaha', 'suzuki']
motorcycles.remove("honda")
print(motorcycles)
#注意  方法remove() 只删除第一个指定的值。如果要删除的值可能在列表中出现多次，就需要使用循环来判断是否删除了所有这样的值。
#我们将在后面的章节学习具体方法
```

    ['honda', 'suzuki']
    ['honda', 'yamaha', 'suzuki']

```python
#同时使用remove()方法 method 删除的元素是可以被再次使用的：
#(这个是书里的原话，我觉得不准确，因为实际上它是将那个移除的值存储到了新的变量中，然后再移除而不是和pop()一样在移除的同时赋值)
motorcycles = ['honda', 'yamaha', 'suzuki', 'ducati']
too_expensive = 'yamaha'
motorcycles.remove(too_expensive)
print("A " + too_expensive.title() + " is too expensive for me.")
```

    A Yamaha is too expensive for me.

方法 pop() 同样可以删除列表末尾的元素，并让你能够接着使用它:

```python
motorcycles = ['honda', 'yamaha', 'suzuki']
popped_motorcycle = motorcycles.pop() #我们从这个列表中弹出一个值，并将其存储到变量popped_motorcycle 中
print(motorcycles)#打印这个列表，确认从其中删除了一个值
print(popped_motorcycle)#打印弹出的值，以证明我们依然能够访问被删除的值
```

    ['honda', 'yamaha']
    suzuki

应用实例：

```python
motorcycles = ['honda', 'yamaha', 'suzuki']
last_owned = motorcycles.pop()
print("The last motorcycle I owned was a " + last_owned.title() + ".")#这里是另一种打印句子的方法(""+variable+"")
```

    The last motorcycle I owned was a Suzuki.

我们也可以使用 pop()并指出位置索引 index 的方式来弹出任意值：

```python
motorcycles = ['honda', 'yamaha', 'suzuki']
owned = motorcycles.pop(0)
print("The first motorcycle I owned was a " + owned.title() + ".")
```

    The first motorcycle I owned was a Honda.

## 练习

```python
#3-4 嘉宾名单 :如果你可以邀请任何人一起共进晚餐(无论是在世的还是故去的)，你会邀请哪些人?
        #请创建一个列表，其中包含至少3个你想邀请的人;然后，使用这个列表打印消息，邀请这些人来与你共进晚餐。
        #为了方便这里直接给出一个邀请名单invite=["Aurelia", "Kynt", "Sand", "Yinshi", "Byleth", "Edelgard"]
        #为了方便，我会使用手动方式打出一条邀请方式，然后用foor loop打出所有邀请内容
```

```python
invite=["Aurelia", "Kynt", "Sand",]
# 手动方式：
print("Hello "+invite[0]+", I'd like to invite you to have dinner with me.")
print("Hello "+invite[1]+", I'd like to invite you to have dinner with me.")
print("Hello "+invite[2]+", I'd like to invite you to have dinner with me.\n")
# for loop 语句：
for i in range(len(invite)):
    print("Hello "+invite[i]+", I'd like to invite you to have dinner with me.")
```

    Hello Aurelia, I'd like to invite you to have dinner with me.
    Hello Kynt, I'd like to invite you to have dinner with me.
    Hello Sand, I'd like to invite you to have dinner with me.

    Hello Aurelia, I'd like to invite you to have dinner with me.
    Hello Kynt, I'd like to invite you to have dinner with me.
    Hello Sand, I'd like to invite you to have dinner with me.

```python
#3-5 修改嘉宾名单 :你刚得知有位嘉宾无法赴约，因此需要另外邀请一位嘉宾。 以完成练习3-4时编写的程序为基础，在程序末尾添加一条print 语句，
        #指出哪位嘉宾无法赴约。 修改嘉宾名单，将无法赴约的嘉宾的姓名替换为新邀请的嘉宾的姓名。 再次打印一系列消息，向名单中的每位嘉宾发出邀请。
```

```python
invite=["Aurelia", "Kynt", "Sand"]#在这里重新输入list是为了防止多次运行该代码块时出现反复添加的情况
#我们可以使用del语句, remove()或者 pop()来去掉其中一位嘉宾，这里我先使用del语句，然后在3-7练习中使用 remove()和 pop()
del invite[-1]
print(invite)
#接着我们可以使用 insert()或者 append()来添加我们需要的嘉宾，这里我先使用 append()，然后在3-6练习中使用 insert()
invite.append("Byleth")
print(invite)
print()
#邀请的手动方法在上面一个练习3-4中已经展示，这里直接使用for loop
# for loop 语句：
for i in range(len(invite)):
    print("Hello "+invite[i]+", I'd like to invite you to have dinner with me.")
```

    ['Aurelia', 'Kynt']
    ['Aurelia', 'Kynt', 'Byleth']

    Hello Aurelia, I'd like to invite you to have dinner with me.
    Hello Kynt, I'd like to invite you to have dinner with me.
    Hello Byleth, I'd like to invite you to have dinner with me.

```python
#3-6 添加嘉宾 :你刚找到了一个更大的餐桌，可容纳更多的嘉宾。请想想你还想邀请哪三位嘉宾。 以完成练习3-4或练习3-5时编写的程序为基础，
        #在程序末尾添加一条print 语句，指出你找到了一个更大的餐桌。
        #使用insert() 将一位新嘉宾添加到名单开头。
        #使用insert() 将另一位新嘉宾添加到名单中间。
        #使用append() 将最后一位新嘉宾添加到名单末尾。
        #打印一系列消息，向名单中的每位嘉宾发出邀请。
```

```python
invite=['Aurelia', 'Kynt', 'Byleth']
print("Hello everyone I found a bigger table, so I think we can enjoy with more people now")
invite.insert(0, "Sand")#使用insert() 将一位新嘉宾添加到名单开头。
invite.insert(3, "Yinshi")#使用insert() 将另一位新嘉宾添加到名单中间。
invite.append("Edelgard")#使用append() 将最后一位新嘉宾添加到名单末尾。
print(invite)
#使用for loop打印一系列消息，向名单中的每位嘉宾发出邀请，手动方法参考3-5
for i in range(len(invite)):
    print("Hello "+invite[i]+", I'd like to invite you to have dinner with me.")
```

    Hello everyone I found a bigger table, so I think we can enjoy with more people now
    ['Sand', 'Aurelia', 'Kynt', 'Yinshi', 'Byleth', 'Edelgard']
    Hello Sand, I'd like to invite you to have dinner with me.
    Hello Aurelia, I'd like to invite you to have dinner with me.
    Hello Kynt, I'd like to invite you to have dinner with me.
    Hello Yinshi, I'd like to invite you to have dinner with me.
    Hello Byleth, I'd like to invite you to have dinner with me.
    Hello Edelgard, I'd like to invite you to have dinner with me.

```python
#3-7 缩减名单 :你刚得知新购买的餐桌无法及时送达，因此只能邀请两位嘉宾。 以完成练习3-6时编写的程序为基础，
        #在程序末尾添加一行代码，打印一条你只能邀请两位嘉宾共进晚餐的消息。
        #使用pop() 不断地删除名单中的嘉宾，直到只有两位嘉宾为止。每次从名单中弹出一位嘉宾时，
        #都打印一条消息，让该嘉宾知悉你很抱歉，无法邀请他来共进晚餐。
        #对于余下的两位嘉宾中的每一位，都打印一条消息，指出他依然在受邀人之列。
        #使用del 将最后两位嘉宾从名单中删除，让名单变成空的。打印该名单，核实程序结束时名单确实是空的。
```

```python
invite=['Sand', 'Aurelia', 'Kynt', 'Yinshi', 'Byleth', 'Edelgard']
print("Hello everyone, sorry, I just be notified that the bigger table could not be delivered in time.")
print("So I can only invite two people to have dinner with me")
#接下来我将使用手动方法来删除嘉宾并打印消息：
remove_1='Sand'
invite.remove(remove_1)
print("Hi "+ remove_1 +", I feel very sorry that I can't invite you to have dinner with me tonight. Hope we can have dinner next time.")
remove_2='Yinshi'
invite.remove(remove_2)
print("Hi "+ remove_2 +", I feel very sorry that I can't invite you to have dinner with me tonight. Hope we can have dinner next time.")
remove_3=invite.pop(2)
print("Hi "+ remove_3 +", I feel very sorry that I can't invite you to have dinner with me tonight. Hope we can have dinner next time.")
remove_4=invite.pop(2)
print("Hi "+ remove_4 +", I feel very sorry that I can't invite you to have dinner with me tonight. Hope we can have dinner next time.")
```

    Hello everyone, sorry, I just be notified that the bigger table could not be delivered in time.
    So I can only invite two people to have dinner with me
    Hi Sand, I feel very sorry that I can't invite you to have dinner with me tonight. Hope we can have dinner next time.
    Hi Yinshi, I feel very sorry that I can't invite you to have dinner with me tonight. Hope we can have dinner next time.
    Hi Byleth, I feel very sorry that I can't invite you to have dinner with me tonight. Hope we can have dinner next time.
    Hi Edelgard, I feel very sorry that I can't invite you to have dinner with me tonight. Hope we can have dinner next time.

```python
#使用for loop方法来删除嘉宾并打印消息：
invite=['Sand', 'Aurelia', 'Kynt', 'Yinshi', 'Byleth', 'Edelgard']
for i in range(len(invite)):
    remove=invite.pop(0)
    print ("Hi "+ remove +", I feel very sorry that I can't invite you to have dinner with me tonight. Hope we can have dinner next time.")
    if len(invite)==2:
        break
print(invite)
```

    Hi Sand, I feel very sorry that I can't invite you to have dinner with me tonight. Hope we can have dinner next time.
    Hi Aurelia, I feel very sorry that I can't invite you to have dinner with me tonight. Hope we can have dinner next time.
    Hi Kynt, I feel very sorry that I can't invite you to have dinner with me tonight. Hope we can have dinner next time.
    Hi Yinshi, I feel very sorry that I can't invite you to have dinner with me tonight. Hope we can have dinner next time.
    ['Byleth', 'Edelgard']

```python
invite=['Byleth', 'Edelgard']
#使用del 将最后两位嘉宾从名单中删除，让名单变成空的。
for i in range(len(invite)):
    del invite[0]
print(invite)
```

    []

# 3.3 组织列表

## 3.3.1 使用方法 sort() 对列表进行永久排序

按照字母顺序排列：

```python
cars = ['bmw', 'audi', 'toyota', 'subaru']
cars.sort()
print(cars)
```

    ['audi', 'bmw', 'subaru', 'toyota']

按照反字母顺序排列：

```python
cars = ['bmw', 'audi', 'toyota', 'subaru']
cars.sort(reverse=True)
print(cars)
```

    ['toyota', 'subaru', 'bmw', 'audi']

## 3.3.2 使用函数 sorted() 对列表进行临时排列

按照字母顺序排列：

```python
cars = ['bmw', 'audi', 'toyota', 'subaru']
print("\nHere is the sorted list:")
print(sorted(cars))
print("\nHere is the original list:")
print(cars)
```

    Here is the sorted list:
    ['audi', 'bmw', 'subaru', 'toyota']

    Here is the original list:
    ['bmw', 'audi', 'toyota', 'subaru']

按照反字母顺序排列：

```python
print(sorted(cars, reverse=True))
```

    ['toyota', 'subaru', 'bmw', 'audi']

## 3.3.3 倒着打印列表 reverse()永久修改

```python
#reverse() 只是反转列表元素的排列顺序:
cars = ['bmw', 'audi', 'toyota', 'subaru']
cars.reverse()
print(cars)
#可以对列表再次使用reverse() , 使其恢复到原来的排列顺序
```

    ['subaru', 'toyota', 'audi', 'bmw']

## 3.3.4 确定列表的长度 len()

```python
#在很多地方我们都会使用到len()这一函数 比如在for loop中确定输入的list的长度
cars = ['bmw', 'audi', 'toyota', 'subaru']
len(cars)
```

    4

## 练习

```python
#3-8 放眼世界 :想出至少5个你渴望去旅游的地方。 将这些地方存储在一个列表中，并确保其中的元素不是按字母顺序排列的。
        #1. 按原始排列顺序打印该列表。不要考虑输出是否整洁的问题，只管打印原始Python列表。
        #2. 使用sorted() 按字母顺序打印这个列表，同时不要修改它。 再次打印该列表，核实排列顺序未变。
        #3. 使用sorted() 按与字母顺序相反的顺序打印这个列表，同时不要修改它。 再次打印该列表，核实排列顺序未变。
        #4. 使用reverse() 修改列表元素的排列顺序。打印该列表，核实排列顺序确实变了。
        #5. 使用reverse() 再次修改列表元素的排列顺序。打印该列表，核实已恢复到原来的排列顺序。
        #6. 使用sort() 修改该列表，使其元素按字母顺序排列。打印该列表，核实排列顺序确实变了。
        #7. 使用sort() 修改该列表，使其元素按与字母顺序相反的顺序排列。打印该列表，核实排列顺序确实变了。
        #为了方便练习这里给出一个地名的列表 list_travel=[Iceland, London, Paris, Vatican, Arendelle]
```

```python
list_travel=['Iceland', 'London', 'Vatican', 'Paris', 'Arendelle']
print('task1:')
print(list_travel)

print('task2:')
print(sorted(list_travel))
print(list_travel)

print('task3:')
print(sorted(list_travel, reverse=True))
print(list_travel)

print('task4:')
list_travel.reverse()
print(list_travel)

print('task5:')
list_travel.reverse()
print(list_travel)

print('task6:')
list_travel.sort()
print(list_travel)

print('task7:')
list_travel.sort(reverse=True)
print(list_travel)
```

    task1:
    ['Iceland', 'London', 'Vatican', 'Paris', 'Arendelle']
    task2:
    ['Arendelle', 'Iceland', 'London', 'Paris', 'Vatican']
    ['Iceland', 'London', 'Vatican', 'Paris', 'Arendelle']
    task3:
    ['Vatican', 'Paris', 'London', 'Iceland', 'Arendelle']
    ['Iceland', 'London', 'Vatican', 'Paris', 'Arendelle']
    task4:
    ['Arendelle', 'Paris', 'Vatican', 'London', 'Iceland']
    task5:
    ['Iceland', 'London', 'Vatican', 'Paris', 'Arendelle']
    task6:
    ['Arendelle', 'Iceland', 'London', 'Paris', 'Vatican']
    task7:
    ['Vatican', 'Paris', 'London', 'Iceland', 'Arendelle']

```python
#3-9 晚餐嘉宾 :在完成练习3-4~练习3-7时编写的程序之一中，使用len() 打印一条消息，指出你邀请了多少位嘉宾来与你共进晚餐。
#这里给出一个嘉宾名单：invite=['Sand', 'Aurelia', 'Kynt', 'Yinshi', 'Byleth', 'Edelgard']
invite=['Sand', 'Aurelia', 'Kynt', 'Yinshi', 'Byleth', 'Edelgard']
n = len(invite)
print(f"I have invite {n} people to enjoy dinner tonight")
```

    I have invite 6 people to enjoy dinner tonight

```python
#3-10 尝试使用各个函数 :想想可存储到列表中的东西，如山岳、河流、国家、城市、语言或你喜欢的任何东西。
        #编写一个程序，在其中创建一个包含这些元素的列表，然后，对于本章介绍的每个函数，都至少使用一次来处理这个列表。
        #这里列出所有学到的内容方便自行尝试：（其中的Index, List, Value等首字母大写内容均为自由填写内容）
        #创建列表：List=[] 比如：list_need = ["water","food","air", "space", "money"]
        #检索列表中的元素：List[Index] --index start from 0, index can be negative 比如：list_need[2] 或者 list_need[-1]
        #                           List[Index:Index]
        #检索已知元素在列表中的位置：List.index("Value")
        #打印带变量的语句：print(f"{Variable} {Variable} xxx")
        #修改列表元素：List[Index] = 'Value'
        #添加列表元素：List.append('Value')
        #                     List.insert(Index, 'Value')
        #删除列表元素：del List[Index]
        #                     List.remove('Value')
        #                     List.pop(Index)
        #对列表进行永久排序：List.sort() / List.sort(reverse=True)
        #对列表进行临时排列：sorted(List) / sorted(List, reverse=True)
        #对列表进行永久反转：List.reverse()
        #确定列表的长度：len(List)
```

# 3.4 使用列表时避免索引错误

```python
list_need = ["water","food","air", "space", "money"]
#比如 list_need[5] 那么就会提示错误
#如何避免错误：1.确认list长度，2.确保输入的index小于list长度（注意是小于不是小于等于）
print(len(list_need))
print(list_need[4])
print(list_need[5])
```

    5
    money



    ---------------------------------------------------------------------------

    IndexError                                Traceback (most recent call last)

    Cell In[34], line 6
          4 print(len(list_need))
          5 print(list_need[4])
    ----> 6 print(list_need[5])


    IndexError: list index out of range

## 练习

```python
#3-11 有意引发错误 :如果你还没有在程序中遇到过索引错误，就尝试引发一个这种错误。在你的一个程序中，修改其中的索引，以引发索引错误。
        #关闭程序前，务必消除这个错误。
        #这里直接查看上面那个代码块就好了，那就是一个典型的索引错误
```
