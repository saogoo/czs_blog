```python
print("Hello jupyter notebook")
```

    Hello jupyter notebook


# 1.1 Jupyter notebook 的基础使用

## 1.1.1 快捷键


```python
#esc:从编辑模式退回命令模式
#enter:从命令模式退回编辑模式
#在命令模式（esc）下：
        #按m切换为markdown单元格，y切换为代码单元格，a（above）/b（below）在上/下方创建新的代码块，h快捷键一览
        #dd（delete）删除，z撤销，x剪切，c复制，shift+v在上方黏贴，v在当前位置粘贴，L标记当前代码块行数
#shift+enter可以运行当前代码块并跳到下一代码块，alt+enter执行当前代码块并在下面新建一个代码块
```

## 1.1.2 markdown的应用


```python
#引用#
#跳转至外部链接#
#插入图片#
```

>我是引用，我前面有一条灰色竖杠

[我是外部链接点我上b站](www.bilibili.com)

![我是图片](https://img1.baidu.com/it/u=2735769730,1464143095&fm=253&fmt=auto&app=138&f=JPEG?w=352&h=499)


```python
#在markdown模式中通过$$符号实现数学公式的镶嵌，如下所示：
#其中的$公式$为插入公式的特殊写法，其中$公式$代表公式在一行内完成，$$公式$$则代表公式在两行完成
```

这是爱因斯坦质能转换方程$E=mc^2$，揭示了质量之间的关系

这是一元二次方程求解公式$$x = \frac {-b\pm \sqrt {b^2-4ac}}{2a}$$

# 2.1 变量

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
message="try jupyter"
print(message)
message="try python3"
print(message)
```

    try jupyter
    try python3


# 2.2 字符串


```python

```
