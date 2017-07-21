## 规范的意义
虽然突破标准是一种革新，但更多的时候问题都是没有标准的一片混乱，也就谈不上突破。正确的编程风格，不但有助于提升软件产品的功能，还可以明显减少软件灾难的产生。

风格，亦被称作可读性，也就是指导**Python**编程的约定。使用术语 “风格” 有些用词不当，因为这些习惯远不止源代码文件格式化这么简单。

使代码易于管理的方法之一是加强代码一致性。让任何程序员都可以快速读懂你的代码这点非常重要。

保持统一编程风格并遵守约定意味着可以很容易根据 “模式匹配” 规则来推断各种标识符的含义。 创建通用、必需的习惯用语和模式可以使代码更容易理解。在一些情况下可能有充分的理由改变某些编程风格，但我们还是应该遵循一致性原则，尽量不这么做。

常见的规范约定包括：

- 代码的可读性至上
- 遵循正确的命名约定
- 确保代码有一定的可维护性
- 注释必须易于理解


## 何时打破规则
> A Foolish Consistency is the Hobgoblin of Little Minds。 
> 
> 呆板的坚持一致性傻的没边了!  -- Emerson

代码风格的一致性是重要的，在一个项目内的一致性更重要，在一个模块或函数内的一致性最重要。
但最重要的是：知道何时会不一致！
有时只是没有实施风格指导。当出现疑惑时，运用最佳判断，看看别的例子，然后决定怎样看起来更好。

打破一条既定规则的两个好理由:

- 当应用这个规则是将导致代码可读性下降，即便对某人来说，他已经习惯于按这条规则来阅读代码了
- 为了和周围的代码保持一致而打破规则 （也许是历史原因；虽然这也是个清除其它混乱的好机会）

## Python哲学
> 执行命令： python -c "import this”

- 优美胜于丑陋（Python 以编写优美的代码为目标）
- 明了胜于晦涩（优美的代码应当是明了的，命名规范，风格相似）
- 简洁胜于复杂（优美的代码应当是简洁的，不要有复杂的内部实现）
- 复杂胜于凌乱（如果复杂不可避免，那代码间也不能有难懂的关系，要保持接口简洁）
- 扁平胜于嵌套（优美的代码应当是扁平的，不能有太多的嵌套）
- 间隔胜于紧凑（优美的代码有适当的间隔，不要奢望一行代码解决问题）
- 可读性很重要（优美的代码是可读的）
- 即便假借特例的实用性之名，也不可违背这些规则（这些规则至高无上）
- 不要包容所有错误，除非你确定需要这样做（精准地捕获异常，不写 except:pass 风格的代码）
- 当存在多种可能，不要尝试去猜测，而是尽量找一种，最好是唯一一种明显的解决方案（如果不确定，就用穷举法）；虽然这并不容易，因为你不是 Python 之父（这里的 Dutch 是指 Guido ）
- 做也许好过不做，但不假思索就动手还不如不做（动手之前要细思量）
- 如果你无法向人描述你的方案，那肯定不是一个好方案；反之亦然（方案测评标准）
- 命名空间是一种绝妙的理念，我们应当多加利用（倡导与号召）

## 脚本格式
```
#!/usr/bin/env python
# coding=utf-8
"""
for demo
__created__ = '3/13/17'
__author__ = 'xxx'
"""
import os # python默认包

import numpy as np # 安装的依赖包

import mine_package # 自建包


def test():
    print("hello test")

```

上面是一个示例程序，一般情况下新建脚本除了代码正文，会有:

`#!/usr/bin/env python` 这行的作用主要是在linux/unix系统中，执行脚本写为 ./xxoo.py 时，可以自动寻找当前环境的python版本来解析，避免进入系统默认python。非必须。

`# coding=utf-8` 如果脚本中有非英文字符，必须；避免乱码发生。在 [文件与编码] 部分会介绍为什么要添加。

添加脚本的功能备注。

## Python编程风格

Python指导手册 
> http://docs.python-guide.org/en/latest/

Python官方规范：
> https://www.python.org/dev/peps/pep-0008/ 

Google的python代码规范（中文版）：
> http://zh-google-styleguide.readthedocs.org/en/latest/google-python-styleguide/

Github上的google各语言标准:
> https://github.com/zh-google-styleguide/zh-google-styleguide
http://zh-google-styleguide.readthedocs.org/en/latest/

Google给出的json标准
> https://github.com/darcyliu/google-styleguide/blob/master/JSONStyleGuide.md

编程实践，老生常谈的一些实践标准：
> http://www.vaikan.com/principles-of-good-programming/
>
> http://www.artima.com/weblogs/viewpost.jsp?thread=331531

