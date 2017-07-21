## Python 2 VS python 3

在教程部分说过，建议用 python3.6 为学习标准，**python2.7**之后支持**python3.x**的大部分语法，而需要注意的差别在这里会说明。

> 微软发布 [python-3-is-winning](https://blogs.msdn.microsoft.com/pythonengineering/2016/03/08/python-3-is-winning/): 
> 
> python3在2016年初已经慢慢超越python2获得更多的第三方库支持。

> http://py3readiness.org/ 
> 
> 前360个主流扩展包python3和2的支持对比。目前除了几个停止开发和系统运维模块，96%的模块都支持python3。

### python2和3的差别

链接地址列出了语法上的差别：

> [https://github.com/rasbt/python_reference/blob/master/tutorials/key_differences_between_python_2_and_3.ipynb](https://github.com/rasbt/python_reference/blob/master/tutorials/key_differences_between_python_2_and_3.ipynb)
>
> 中文翻译: [http://chenqx.github.io/2014/11/10/Key-differences-between-Python-2-7-x-and-Python-3-x/](http://chenqx.github.io/2014/11/10/Key-differences-between-Python-2-7-x-and-Python-3-x/)

### 实践技巧
在实践使用中，无论在2还是3，都要统一书写习惯包括：

1. print() 按函数方式来书写
2. 列表解析、集合解析 和 字典解析均可用
2. `except Exception as e` 代替 `except Exception, e` 的写法
3. 不要做不同类型数据的比较，比如拿列表和字符做比较： `print("[1, 2] > 'foo' = ", [1, 2] > 'foo')`；虽然在python2中一定会返回 False。
4. `from M import *` 尽一切可能不要使用；如果使用也只能放在顶部，在python3中不放在顶部会报错。

python2和3的这些差异中，真正需要注意的是：

1. 除法结果有差异：python2中 3/2 结果为1，python3中 3/2 为1.5；但作为习惯最好还是使用float(3)/2或者3/2.0，这样不用关心2或3的差异。
2. unicode编码优化，python3不需要再关心编码问题
3. python2中的xrange在python3中由range代替
4. python3不再支持语法糖 `[i+1 for i in 1,2,3,4]`，必须写成 `[i+1 for i in [1,2,3,4]]`，同时列表解析作用域闭合，变量i不会和函数作用域外的i互扰。

```
print('Python', python_version())
i = 1
print('before: i =', i)
print('comprehension:', [i for i in range(5)])
print('after: i =', i)
```

做到上面这几点，python2和python3日常使用，基本不会遇到使用习惯完全不同的地方。

### Python3新特性
- 新增nonlocal关键字
- 一切皆迭代器：range,itertools.izip,dict.itervalues等，优化性能
- 变量声明语法 Typehints
- 数字变量使用下划线， `1_000_000` 书写数字
- 异步生成器: 新的语法 async 和 await，asyncio模块
- 序列解包 a, *b = [1,2,3,4,5]

```
>>> a,b,*rest,c,d = range(1,8)
>>> rest
[3, 4, 5]
>>> a
1
```
	
- 统一所有类为新式类
- **添加矩阵乘法符号**

```
>>> import numpy as np
>>> a=np.array([[1,2,3],[123,5,61],[9,6,-3]])
>>> a@a
array([[ 274,   30,  116],
       [1287,  637,  491],
       [ 720,   30,  402]])
>>> a@a@a@a@a@a@a@a
array([[ 134837945986,   25136379570,   62890687970],
       [1347945735285,  292595126821,  616252333325],
       [ 320633136090,   54125094810,  151255191066]])
	
#python2中的矩阵乘法如下
>>> np.dot(a,a)
array([[ 274,   30,  116],
       [1287,  637,  491],
       [ 720,   30,  402]])
```
- 关键词唯一参数

```
# python2 示例
>>> def fun(a,b,key1=None,key2=None):
...     if key1 or key2:
...         print key1,key2
...     else:
...         print a,b
... 
>>> fun(1,2)
1 2
# 数值3 会被key1接收了，导致非预期的行为
>>> fun(1,2,3)
3 None
```
	
```
# python3 示例：
>>> def fun(value1,value2,*args, key1=None,key2=None):
...     if key1 or key2:
...         print (key1,key2)
...     else:
...         print (value1,value2,args)
... 
>>> 
>>> 
>>> fun(1,2)
1 2 ()
#*args接收多余的参数
>>> fun(1,2,3,4,5)
1 2 (3, 4, 5)
>>> fun(1,2,3,4,5,key1=6,key2=7)
6 7
```