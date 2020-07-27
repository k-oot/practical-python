[Contents](../Contents.md) \| [Next (1.2 A First Program)](02_Hello_world.md)

# 1.1 Python

### Python是什么?

Python是一个解释型的高级编程语言。它通常被归类为["脚本语言"](https://en.wikipedia.org/wiki/Scripting_language)并且被认为与Perl，Tcl或者Ruby语言非常相似。Python的语法规则大体上是被C语言启发的。

Python是被Guido van Rossum在大约1990年发明的，该名是为了纪念Monty Python。

### 怎么获得Python?

[Python.org](https://www.python.org/)这是你将会获得Python的地方。为了完成该课程，你只需要简单地下载。我建议下载3.6或者更新的版本。在该教程中使用Python3.6作示例以及解答。

### 为什么Python被创造出来?

用Python作者的话来讲：

> 我创造Python最初的动机是想要为Amoeba[操作系统]项目创建一种高级语言。
> 我意识到用C来开发系统管理功能花了太长时间。
> 更进一步，在Bourne命令解析器(shell)下做这些事情会因为各种各样的原因失败。
> ...所以，需要一门语言来连接C与命令解析器之间的间隔。
> 
> - Guido van Rossum

### Python在我电脑的哪里?

尽管你可以在很多环境中运行Python，但Python通常被作为一个程序安装在你的机器上，通过终端（terminal)或者命令行（command shell)来运行。在终端中，你应该可以像这样输入`python` ：

```
bash $ python
Python 3.8.1 (default, Feb 20 2020, 09:29:22)
[Clang 10.0.0 (clang-1000.10.44.4)] on darwin
Type "help", "copyright", "credits" or "license" for more information.
>>> print("hello world")
hello world
>>>
```

如果你是使用命令解释器(shell)或者终端(terminal)的新手，你应该停在这里，先看看相关的简短教程，再返回这里。

即使在很多非命令行环境中你也可以编写Python代码，但是如果你可以在命令行中运行、调试以及与Python交互，你会成为一个更强的Python程序员。这是Python的原生环境。如果你可以在命令行中使用Python，那么你就可以在任何地方使用Python。

## 练习

### 练习 1.1: 把Python当作计算器

在你的机器上，启动python并且将它作为一个计算器来解决接下来的问题。

Lucky Larry以235.14美金每股的价格买了75股谷歌的股票。今天，谷歌每股股票价格为711.25美金。使用Python的交互模式作为计算器，计算如果他卖掉所有的谷歌股票能得到的利润。

```python
>>> (711.25 - 235.14) * 75
35708.25
>>>
```

进阶要点：使用下划线变量来使用之前计算的结果。例如，Larry在邪恶的中间商拿走20%之后还能得到多少利润？

```python
>>> _ * 0.80
28566.600000000002
>>>
```

### Exercise 1.2: 获得帮助

使用 `help()` 命令来获得关于 `abs()` 函数的帮助。然后使用
`help()` 来获得 `round()` 函数的帮助。不带参数地输入 `help()` 本身会进入交互的帮助查看器。
 
`help()` 值得注意的一点是它并不适用于Python的基础语句例如 `for`, `if`, `while`以及其它。（例如，如果你输入`help(for)`你会得到语法错误的提示）。你可以尝试将想要寻求帮助的部分加上引号，像是`help("for")` 。如果这也行不通了，你则应该转向互联网进行搜索。

进一步：访问<http://docs.python.org>，然后查找函数`abs()`的文档（提示：将会在library reference（库参考）下与build-in(内建）函数相关的部分找到。）

### 练习1.3: 剪切和复制

这个课程被构造为一系列网页，在该课程中你会被鼓励**通过自己动手**来尝试交互性的Python代码样例。如果你是第一次学习Python，这种“缓慢接触”是被鼓励的。通过缓慢接触，你对这门语言的的感觉将会更深刻，将语句键入，然后思考自己是在做什么，为什么这样做，会有什么效果（原文：thinking about what you are doing）。

如果你必须“剪切并复制”代码样例，选择`>>>`提示符之后的代码然后一直到第一行空白行或者下一个`>>>`提示符（这俩取最先出现的那个）。在浏览器中选择“复制”然后去Python界面选择“黏贴”从而将代码复制到Python命令解释器中。为了让代码跑起来，在你黏贴完毕之后，你可能需要点击“回车”。

请使用剪切复制来执行以下的Python语句：

```python
>>> 12 + 20
32
>>> (3 + 4
         + 5 + 6)
18
>>> for i in range(5):
        print(i)

0
1
2
3
4
>>>
```

警告：一次性黏贴多于一条Python命令（`>>>`后出现的语句）到Python命令解释器是不可能的。你一次只能黏贴一条命令。

现在你已经完成了上述任务，但要记住，如果你是缓慢地输入代码然后思考它，而不是剪切和复制，你将会从这门课程中学到更多。

### 练习 1.4: 我的巴士到哪了?

试点进阶的，输入这些语句来得到等在芝加哥的Clark street和Balmoral角落的人等待下一辆northbound CTA \#22巴士所需要的时间。

```python
>>> import urllib.request
>>> u = urllib.request.urlopen('http://ctabustracker.com/bustime/map/getStopPredictions.jsp?stop=14791&route=22')
>>> from xml.etree.ElementTree import parse
>>> doc = parse(u)
>>> for pt in doc.findall('.//pt'):
        print(pt.text)

6 MIN
18 MIN
28 MIN
>>>
```

是的，你刚刚下载了一个网页，解析了一个XML文件，还从中提取了一些有用的信息，通过大概6行代码。你访问的数据实际上是从<http://ctabustracker.com/bustime/home.jsp>网站中来的。再试一次，观察预测结果的变化。

注意：这个服务只报告30分钟内的到达时间。如果你在不同的时区，同时芝加哥是凌晨3点，那么你可能不会得到任何输出结果。使用上文中的追踪连接来检查这一点。

如果第一条import语句 `import urllib.request` 失败，那么你可能使用的是Python 2。对这门课程来说，你应该保证你使用的是Python 3.6或者更新。如果需要的话，去往 <https://www.python.org> 进行下载。

如果你的电脑工作环境（work environment）需要使用HTTP代理服务器，你可能需要设置 `HTTP_PROXY` 环境变量来使该部分运行成功。例如：

```python
>>> import os
>>> os.environ['HTTP_PROXY'] = 'http://yourproxy.server.com'
>>>
```

如果这不成功，不要担心。剩下的课程与解析XML没有任何关系。

[Contents](../Contents.md) \| [Next (1.2 A First Program)](02_Hello_world.md)

