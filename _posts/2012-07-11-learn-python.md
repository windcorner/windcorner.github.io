---
layout: post
title: "Learning Python"
category: study
tags: [python]
description: |
  Python是一门优雅的语言，也是我最喜欢的语言，它的简洁高效的语法让你能专注于所解决的问题本身，Learning Python是学习Python最好的入门书籍之一。
---
{% include JB/setup %}

##第一部分 使用入门

###第1章 问答环节

####选择python的原因：

- 软件质量，具有脚本语言便于编写的优点，同时可读性强，以及对OOP的支持使他优于shell、perl等脚本语言，而且功能更强大。
- 开发效率高，python是比C/C++、java更高级的语言，他语法更简洁，使人们可以更加专注于需要解决的问题，而不是拘泥于编程语言本身。
- 可移植性强，如果说C/C++是一处编写处处编译，java是一处编译处处运行，那么python就是一处编写处处运行。
- 标准库的支持，python有许多内置标准扩以及第三方库，我选择python做图像处理很重要的原因就是<code>Python+NumPy+OpenCV</code>的组合比Matlab便于移植和工程应用，同时又比C/C++更易于编写，而且还免费。此外，python在第三方的支持下可以进行网站开发（Django）、数值计算（SciPy、NumPy）、游戏开发（PyOpenGL）、应用软件开发（PyQt、wxPython）等各个方面。
- 组件集成，原始的Python就是用C实现的，所以很容易实现和C/C++的相互调用。在Jython和IronPython的逐渐成熟，python和java以及.Net等框架之间的通信变得异常简单，所以python他不是一个人在战斗。
- 享受乐趣，python的简洁高效使得编程称为一种乐趣。

此外，python还有诸多的优点足够吸引你，比如python支持面向对象，却又不像java一样强制使用面向对象，这就意味着你可以像C一样去用它解决一些简单的注重于过程的问题，同时又可以像C++、java一样运用面向对象的方式解决一些大型的工程问题；由于python代码可以动态的修改，用户可以改进系统内部的python部分而不需要拥有或编译整个系统，所以python很容易实现定制；python区别于其他语言最明显的标志就是使用缩进而不是<code>{ }</code>来区分代码块，这也是很多人觉得python优雅的地方。

####关于脚本语言

很多人一提到脚本语言，第一感觉是干不了大事的语言，其实随着诸如python、ruby、javascript等一些脚本语言的迅速蹿红，这种观念很明显以及站不住脚了。维基百科对脚本语言的定义是“为了缩短传统的编写-编译-链接-运行（edit-compile-link-run）过程而创建的计算机编程语言”。python可以被认定是一种脚本语言，但是这取决于你要解决的问题，一般意义上讲，“脚本语言”更适合于描述python所支持的快速灵活的开发模式，而不是特定的应用领域。事实上，“脚本语言”和“程序语言”也是可以相互替代的，就像python超出了一般脚本语言的功能，而javascript也可以用来进行服务器端编程（Node.js）。

当然python也是有他固有的缺点的，可能执行速度慢慢是最重要的一条吧，python不能像C语言一样编译成底层的二进制代码（比如Intel芯片指令），而是转换成一种字节码的形式，之后再将字节码解释。不过速度慢的缺点也不是致命的，在硬件条件高速发展的今天，再加上云计算、虚拟化、超级计算机、分布式等技术的助力，计算机硬件环境已经提升到一个前所未有的高度，运算速度和程序员的解放之间的博弈似乎变得越来越明朗。

###第2章 Python如何运行程序

####解释器

解释器是代码与机器的计算机硬件之间的软件逻辑层。python的解释器主要完成字节码编译和程序执行：

- 字节码编译。程序执行时，解释器会将源代码编译成字节码，编译是简单的翻译过程，字节码是底层的、与平台无关的。字节码可以提高执行速度，但任然赶不上二进制码的执行速度，python编译过的字节码文件是以“.pyc”为后缀的，程序执行过后会存在于py文件同一目录下（如果程序对系统没有写入权，字节码将会生产于内存当中，程序执行结束时被简单的丢弃），程序未修改时，解释器会自动加载上次编译过的pyc文件，否则重新编译，当然单独的pyc文件也是可以被直接调用的。
- Python虚拟机（PVM）。编译后的字节码发送到PVM上执行，PVM是一个迭代运行指令的大循环，一个接一个的执行指令。

通过py2exe、PyInstaller、freeze等第三方工具，python可以生成真正的二进制文件，如windows下的exe文件。

###第3章 如何运行程序

python程序文件称之为模块，是python最大的程序结构，一个模块文件是一个独立的命名空间。Linux小的<code>#!/usr/local/bin/python</code>或<code>#!/usr/bin/env python</code>是为了指定脚本的执行程序。

导入操作只会执行一次，重新导入需要reload。

import和from的区别：import是将模块的整体导入，而from增加了额外的赋值操作，调用属性不用模块名称，但是from打破了命名空间的完备性，导入后程序中相同的变量会被覆盖。

<code>exec(open('spam.py').read())</code>相当于在调用的地方复制了模块，同样也会覆盖相同的变量名。

##第二部分 类型和运算

###第4章 介绍Python对象类型

python程序可以分解为模块、语句、表达式以及对象：

1. 程序由模块构成。
2. 模块包含语句。
3. 语句包含表达式。
4. 表达式建立并处理对象。

使用C/C++时很大的一部分工作都花费在用基本的数据类型和数据结构去构建表现层的组件，需要考虑内存分配、垃圾回收等乏味的工作，而且这是背离程序的真真目标的。python提供的强大的内置对象解决了这一问题，而且鼓励更多的使用内置对象，而不是自己实现的对象。

python的核心数据类型（内置对象）：数字、字符串、列表、字典、元组、文件、集合、其他类型（类型、None、布尔型）、编程单元类型（函数、模块、类）、与实现相关的类型（编译的代码堆栈跟踪）。

python中没有类型声明，运行的表达式的的语法决定了创建和使用对象的类型，一旦对象创建，就和对应的操作集合绑定了。python是动态类型（不需要声明，而是自动跟踪类型），同时也是强类型语言。

####数字

计算结果为全精度，相当于repr，print函数（在3.0以前为语句）可以打印出比较友好的结果，相当于str。

常用的数学工具包：math、random，以及第三方的NumPy等。

####字符串

字符串是单个字符的字符串的序列，可以进行下标、切片操作。但是字符串具有不可变性，即创建以后不能更改，不能对某一位置进行赋值。字符串除了一般序列的操作，还具有字符串特有的一些操作，如`find, replace, splite, upper, isalpha, restrip`等。此外还有一个格式化的高级操作：
{% highlight python %}
>>> '%s, eggs, and %s' % ('spam', 'SPAM!')
'spam, eggs, and SPAM!'
>>> '{0}, eggs, and {1}'.format('spam', 'SPAM!')
'spam, eggs, and SPAM!'
{% endhighlight %}

在python基本类型中，数字、字符串和元组是不可变的，列表和字典是可变的。

可用于多种类型的通用型操作都是以内置函数或者表达式的形式出现的（如`len(X), X[0]`），类型特定的操作一般是以方法调用的形式出现的（如`aString.upper()`）。

使用`dir`和`help`，可以获取对象的帮助信息，dir能给出所有的方法名，help函数可以获取方法的帮助信息。

三个单引号或双引号中可以包含多行字符，以r开头的字符串可以表示原始（raw）字符串常量（去掉反斜杠转义机制）：
{% highlight python %}
>>> msg='''aaaaaaaa
bbbbbbbb
cccccccc'''
>>> msg
'aaaaaaaa\nbbbbbbbb\ncccccccc'
>>> print(msg)
aaaaaaaa
bbbbbbbb
cccccccc
>>> r'C:\Program Files\ython'
'C:\\Program Files\\ython'
>>> r'C:\Program Files\Python'
'C:\\Program Files\\Python'
>>> R=r'C:\Program Files\Python'
>>> print(R)
C:\Program Files\Python
{% endhighlight %}

使用`re`模块可以支持正则表达式：
{% highlight python %}
>>> import re
>>> match=re.match('/(.*)/(.*)/(.*)', '/usr/home/spam')
>>> match.groups()
('usr', 'home', 'spam')
{% endhighlight %}

####列表

列表是任意对象的有序集合，没有固定大小，可以嵌套，可以改变，以及索引、切片等序列操作。类型特定的常用操作有：`append, pop, del, insert, remove, sort, reverse`等，这些方法都是直接对列表进行了改变。

列表递推式：
{% highlight python %}
>>> [i*10 for i in range(10) if i%2==0]
[0, 20, 40, 60, 80]
>>> [ord(x) for x in 'spam']
[115, 112, 97, 109]
{% endhighlight %}

解析语法创建生成器：
{% highlight python %}
>>> M=[[1,2,3],[4,5,6],[7,8,9]]
>>> G=(sum(row) for row in M)
>>> next(G)
6
>>> next(G)
15
{% endhighlight %}

####字典

字典是一种`key-value`型的映射，同样具有可变性，而且还支持边界以外的赋值，这与列表不同。
字典的常用操作有：映射、重放嵌套、键排序、if测试：
{% highlight python %}
>>> rec={'name': {'first': 'Bob', 'last': 'Smith'}, 'job': ['dev', 'mgr'], 'age': 40}
>>> rec
{'age': 40, 'job': ['dev', 'mgr'], 'name': {'last': 'Smith', 'first': 'Bob'}}
>>> rec['name']
{'last': 'Smith', 'first': 'Bob'}
>>> rec['job'].append('janitor')
>>> rec
{'age': 40, 'job': ['dev', 'mgr', 'janitor'], 'name': {'last': 'Smith', 'first': 'Bob'}}
>>> D={'a': 1, 'b': 2, 'c': 3}
>>> D
{'a': 1, 'c': 3, 'b': 2}
>>> Ks=list(D.keys())
>>> Ks
['a', 'c', 'b']
>>> Ks.sort()
>>> Ks
['a', 'b', 'c']
>>> for key in Ks:
     print(key, '=>', D[key])

    
('a', '=>', 1)
('b', '=>', 2)
('c', '=>', 3)
>>> 'e' in D
False
>>> value=D.get('x', 0)
>>> value
0
>>> value=D['b'] if 'b' in D else 0
>>> value
2
{% endhighlight %}

列表解析相关的函数如map和filter，通常运行得比for循环快。

####元组

元组类似于一个不可改变的列表，支持任意类型、任意嵌套以及常见的序列操作。元组提供了一种完整性的约束条件。

####文件

{% highlight python linenos %}
#基本文件操作
f=open(r'C:\Users\Calvin\vim\python\somefile.txt','w')
f.write('name: Calvin\n')
f.write('email: zhangsp@163.com\n')
f.write('tel: 13893819438\n')
f.close()
#文件模式默认为'r'，只读打开时可以忽略
text=open(r'C:\Users\Calvin\vim\python\somefile.txt').read()
print text
#使用fileinput
import fileinput
for line in fileinput.input(r'C:\Users\Calvin\vim\python\somefile.txt'):
     print line
#使用urllib
from urllib import urlopen
text=urlopen('file:C:\\Users\\Calvin\\vim\python\\somefile.txt')
print(text.read().split())
{% endhighlight %}

####集合

集合是唯一不可变的对象的无序集合（列表是有序的），支持一般的数学集合操作。
{% highlight python %}
>>> X=set('spam')
>>> Y={'m','o','n','t','y'}
>>> X,Y
(set(['a', 'p', 's', 'm']), set(['y', 'm', 't', 'o', 'n']))
>>> X&Y
set(['m'])
>>> X|Y
set(['a', 'm', 'o', 'n', 'p', 's', 't', 'y'])
>>> X-Y
set(['a', 'p', 's'])
{% endhighlight %}

检查对象类型的方法：
{% highlight python %}
>>> L=[1,2,3]
>>> if type(L)==type([]): print('YES')

YES
>>> if type(L)==list: print('YES')

YES
>>> if isinstance(L, list): print('YES')

YES
{% endhighlight %}

###第5章 数字

python的数字并不是真正的对象类型，而是一组类似类型的分类，整数允许无穷精度（当然只要你的内存允许）。数字类型包括整数、浮点数、十六进制（0x）、八进制（0o）、二进制（0b）、复数等，不同的数字类型出现时，python会自动启用对应的运算法则。

不同进制的常量在程序中都产生一个整数对象，内置对象`hes(I), oct(I), bin(I)`可以把一个整数转化成这三种进制表示的字符串。

产生复数对象的方式：
{% highlight python %}
>>> 1+2j
(1+2j)
>>> 1+2J
(1+2j)
>>> complex(1,2)
(1+2j)
{% endhighlight %}

处理数字对象的工具：

- 表达式操作符：`+, -, *, /, >>, **, &`等
- 内置数学函数：`pow, abs, round, int, hex, bin`等
- 公用模块：`random, math`

python表达式操作符及程序：

- `yield x`：生成器函数发送协议
- `lambda args: expression`：生成匿名函数
- `x if y else z`：三元选择表达式，python中没有`boolean_exp ? value1:value2`这样的三目运算符，也没有自增自减
- `x or y, x and y, not x `：逻辑或（x为假时才会计算y）、与（x为真时才会计算y）、非
- `x in y, x not in y; x is y, x is not y`：成员关系（可迭代对象、集合），对象实体测试（测试内存地址，严格意义上的相等）
- `x<y, x<=y, x>y, x>=y, x==y, x!=y`：大小比较，集合操作，比较操作符可以连续使用，如x<y<z等同于x<y and y<z
-`x|y, x^y, x&y`：逐位或、异或、与，集合并、对称差、交集
- `x<<y, x>>y`：左移、右移
- `x+y, x-y`：加减，集合合并、差集
- `x*y, x%y, x/y, x//y, -x, +x, ~x, x**y`：乘法/重复，余数/格式化，真除（结果依赖于对象类型）、floor除法（截断除法，忽略小数部分）、识别逐位求补（取反），幂运算，混合类型运算自动升级
- `x[i], x[i:j:k], x(...), x.attr, (...), [...], {...}`：索引，分片（等同于x[slice(i,j,k)]），调用，属性引用，元组，列表，字典/集合

python中的变量：

- 变量在第一次赋值是创建
- 变量在表达式中使用时被替换为实际值
- 变量在表达式中使用前必须赋值
- 变量不需要声明

数字格式的显示：
{% highlight python %}
>>> num=1/3.0
>>> num
0.3333333333333333
>>> print(num)
0.333333333333
>>> str(num),repr(num)
('0.333333333333', '0.3333333333333333')
>>> '%e' % num
'3.333333e-01'
>>> '%4.2f' % num
'0.33'
>>> '{0:4.2f}'.format(num)
'0.33'
>>> '{0:o},{1:x},{2:b}'.format(64,64,64)
'100,40,1000000'
>>> '%o, %x, %X' % (64,255, 255)
'100, ff, FF'
>>> int('64'),int('100',8),int('40',16),int('0x40',16),int('1000000',2),int('0b1000000',2)
(64, 64, 64, 64, 64, 64)
>>> eval('64'),eval('0o100'),eval('0x40'),eval('0b1000000')
(64, 64, 64, 64)
{% endhighlight %}

repr和str类似于默认的交互模式回显和打印的区别，两者都会把任意对象转换成字符串，repr会表现出对象的原始格式，str会显示相对于用户比较友好的格式，这是python比较人性化的地方。

浮点数在计算机中是近似的存储，所以浮点数运算缺乏精确性，比如：
{% highlight python %}
>>> 0.1+0.1+0.1-0.3
5.551115123125783e-17
{% endhighlight %}

提高进度的方法：

- 引入小数对象
- 使用分数类型

{% highlight python %}
>>> from decimal import Decimal as dec
>>> dec('0.1')+dec('0.1')+dec('0.1')-dec('0.3')
Decimal('0.0')
>>> from fractions import Fraction as fra
>>> fra(1,10)+fra(1,10)+fra(1,10)-fra(3,10)
Fraction(0, 1)
{% endhighlight %}

浮点数精度、小数、分数的一些基本操作：
{% highlight python %}
# 分数操作
from fractions import Fraction as fra
>>> x=fra(1,3)
>>> y=fra('.25')
>>> x+y
Fraction(7, 12)
>>> print(x+y)
7/12
# 临时精度设置
>>> import decimal
>>> decimal.Decimal('1.00')/decimal.Decimal('3.00')
Decimal('0.3333333333333333333333333333')
>>> with decimal.localcontext() as ctx:
     ctx.prec=2
     decimal.Decimal('1.00')/decimal.Decimal('3.00')

    
Decimal('0.33')
# 全局精度设置
>>> decimal.getcontext().prec=2
>>> pay=decimal.Decimal(str(1999+1.33))
>>> pay
Decimal('2000.33')
# 转换和混合类型
>>> (2.5).as_integer_ratio()
(5, 2)
>>> z=fra(*(2.5).as_integer_ratio())
>>> z
Fraction(5, 2)
>>> float(z)
2.5
>>> fra.from_float(2.5)
Fraction(5, 2)
>>> a=fra(137,349)
>>> a
Fraction(137, 349)
>>> a.limit_denominator(10)
Fraction(2, 5)
{% endhighlight %}

在python布尔类型（bool），其值True和False是预先定义的变量名，实际上是int类型的子类，他们的行为和1,0是一样的：
{% highlight python %}
>>> type(True)
<type 'bool'>
>>> isinstance(True,int)
True
>>> True==1
True
>>> True is 1
False
>>> True or False
True
>>> True+4
5
{% endhighlight %}

###第6章 动态类型简介

一个变量第一次赋值时就创建了它，之后的赋值会改变它的值或者类型，变量中永远也不会和具体的类型关联，变量原本是通用的，它只是在特定的时间简单的引用了一个特定的对象而已。当变量出现在表达式时，它会被替换为所引用的对象。类型属于对象，而不属于变量。

- 变量是一个系统表的元素，拥有指向对象连接的空间
- 对象时分配的一块内存，有足够的空间去表示他们所代表的值
- 引用是自动形成的从变量到对象的指针

每当一个变量被赋予一个新的对象，之前的那个对象占用的内存会被回收（前提是没有被其他的变量或者对象引用）。

**垃圾回收**：在内部，python对象有两个标准的头信息，一个**类型标志符**和一个**引用计数器**。类型标志符标示这个对象的类型，引用计数器记录当前指向该对象的引用的数目。一旦这个计数器被设置为0，这个对象的内存空间就会被回收。查询对象引用的次数可以用`sys.getrefcount(object)`。但是引用计数器有个缺陷，即不能释放出现循环引用的对象，但是python有一部分额外的功能（**循环检测器**）来及时的检测并回收带有循环引用的对象。

变量的赋值会产生共享引用，但是其中的一个变量改变引用后不会影响另一个对象的引用，相当于重新创建了一个新的对象。但是列表的共享引用，如果修改对象的某个元素，会在原处修改，要避免这种修改，需要拷贝对象，而不是直接赋值。
{% highlight python %}
>>> l1=[2,3,4]
>>> l2=l1
>>> l1[0]=24
>>> l1
[24, 3, 4]
>>> l2
[24, 3, 4]
>>> l1=l2[:]
>>> l1[0]=2
>>> l1
[2, 3, 4]
>>> l2
[24, 3, 4]
{% endhighlight %}

这种现象同样会发生在字典，以及class语句定义的对象中。

python为了提高程序执行速度，采用了对象缓存和复用的机制，而实际上这与代码是没有关系的，数字和字符串成是不可改变的，所以多少次引用都没有关系，我们只要知道所引用的对象不会被改变就行了。

###第7章 字符串

python中没有char类型，统一都用字符串，python的符串类型是一个不可变序列，而且字符串表示为一对引号（单双引号一样）中间的内容，文本块用三重引号（多用作注解，或在源文件中编写html，其实它还可以起到注释掉语句块的作用）。

原生（raw）字符以`r`开头，但是不能以奇数个`\`结尾，而且python会自动处理windows和linux下的文件路径。

想使用以后要加入的一些新功能可以用`__future__`模块，比如体验一新的`print`的用法：
{% highlight python %}
>>> from __future__ import print_function
>>> for x in s: print(x, end=" ")

s p a m
>>> 
{% endhighlight %}

字符转的下标实际上表示一个数字偏移量，最左边的元素偏移量为0，最右边的为-1，貌似不太合理，但他就是这个样子的。字符串的切片标准格式是`a[i:j:k]`，即开始、结束、步进，是包括i但是不包括j的一个区间，步进缺省时为1。

python中不同类型相加是错误的，如`"42"+1`，字符数字的相互转换用`int(), float(), str()`，`repr()`是代码的字符串，`str('spam'), repr('spam')`结果为`('spam', "'spam'")`，它俩的区别用内置函数`eval()`就可以看出来，`eval(str('spam'))`、`eval(repr('spam'))`前者是错误的。

字符和ASCII码之间的转化可以用`ord(), chr()`实现，字符串的格式化有三种方法：
{% highlight python %}
#基于元组
>>> 'This is %d %s bird!' % (1, 'dead')
'This is 1 dead bird!'
#基于字典
>>> 'This is %(n)d %(x)s bird!' % {'n':1, 'x':'dead'}
'This is 1 dead bird!'
#函数调用
>>> 'This is {0} {1} bird!'.format(1, 'dead')
'This is 1 dead bird!'
>>> 'This is {num} {adj} bird!'.format(num=1, adj='dead')
'This is 1 dead bird!'
>>> 'This is {num} {0} bird!'.format('dead',num=1)
'This is 1 dead bird!'
{% endhighlight %}

格式化的高级操作：可以指定对象的属性和字典的键，方括号可以指定序列的偏移量和字典的键，但是只有单个正的偏移量在格式化字符串中有效：
{% highlight python %}
#使用对象和字典键
>>> import sys
>>> 'My {1[spam]} runs {0.platform}'.format(sys, {'spam': 'laptop'})
'My laptop runs win32'
>>> 'My {config[spam]} runs {0.platform}'.format(sys, config={'spam': 'laptop'})
'My laptop runs win32'
#使用列表、元组、字典，一次传入多个值
>>> somelist=list('SPAM')
>>> somelist
['S', 'P', 'A', 'M']
>>> 'first={0[0]}, third={0[2]}'.format(somelist)
'first=S, third=A'
>>> 'first={0}, third={1}'.format(somelist[0], somelist[1])
'first=S, third=P'
>>> 'first={0}, third={1}'.format(somelist[0], somelist[-1])
'first=S, third=M'
>>> parts=somelist[0], somelist[-1], somelist[1:3]
>>> 'first={0}, last={1}, middle={2}'.format(*parts)
"first=S, last=M, middle=['P', 'A']"
>>> parts={'first':somelist[0], 'last':somelist[-1], 'middle':somelist[1:3]}
>>> 'first={first}, last={last}, middle={middle}'.format(**parts)
"first=S, last=M, middle=['P', 'A']"
{% endhighlight %}

具体格式化语法：`{fieldname!conversionflag:formatspec}`，conversionflag可以使r、s、a，分别代表对该值分别调用`repr, str, ascii`，formatspec的组成形式可以描述为：`[[fill]align][sign][#][0][width][.precision][typecode]`，指定字段宽度、对齐方式、补零、小数点精度、数据类型编码等。
{% highlight python %}
>>> '{0:10} = {1:10}'.format('spam', 123.4567)
'spam       =   123.4567'
>>> '{0:>10} = {1:<10}'.format('spam', 123.4567)
'      spam = 123.4567  '
>>> '%10s = %-10s' % ('spam', 123.4567)
'      spam = 123.4567  '
>>> import sys
>>> '{0.platform:>10} = {1[item]:<10}'.format(sys, dict(item='laptop'))
'     win32 = laptop    '
>>> '{0:e}, {0:.3e}, {0:g}'.format(3.1415926)
'3.141593e+00, 3.142e+00, 3.14159'
>>> '{0:e}, {0:.3e}, {0:g}, {0:06.2f}'.format(3.1415926)
'3.141593e+00, 3.142e+00, 3.14159, 003.14'
>>> '{0:X}, {0:o},{0:b}'.format(255)
'FF, 377,11111111'
>>> '0:{1}f'.format(1/3.0, 4)
'0:4f'
>>> '0:.{1}f'.format(1/3.0, 4)
'0:.4f'
>>> '{0:.{1}f}'.format(1/3.0, 4)
'0.3333'
>>> '%.*f' % (4, 1/3.0)
'0.3333'
>>> format(3.141569, '.2f')
'3.14'
{% endhighlight %}

同样分类的类型共享其操作集合：

- 数字（整数、浮点数、二进制、分数等）  --  支持加减乘除等
- 序列（字符串、列表、元组） --  支持索引、分片、合并等
- 映射（字典） --  支持键的索引
- 集合  --  数学集合的操作

可变类型和不可变类型：

- 不可变类型（数字、字符串、元组、不可变集合）  --  不支持原处修改，只能通过表达式创建新的对象
- 可变类型（列表、字典、可变集合） -- 支持原处直接修改 

###第8章 列表与字典

####列表

python列表的主要属性：

- 任意对象的有序集合
- 通过便宜读取
- 可变长度、异构以及任意嵌套
- 属于可变序列的分类
- 对象引用数组

常见列表操作：
{% highlight python %}
>>> list(map(ord,'spam'))
[115, 112, 97, 109]
>>> L=[0,1,2,3]
>>> S=list('spaam')
>>> L.append(4)
>>> L.extend([6,7])
>>> L.insert(5,5)
>>> L
[0, 1, 2, 3, 4, 5, 6, 7]
>>> L.index(3)
3
>>> S.count('a')
2
>>> S.sort()
>>> S
['a', 'a', 'm', 'p', 's']
>>> L.reverse()
>>> L
[7, 6, 5, 4, 3, 2, 1, 0]
>>> L.pop()
0
>>> L
[7, 6, 5, 4, 3, 2, 1]
>>> L.remove(7)
>>> L
[6, 5, 4, 3, 2, 1]
>>> S[0:1]=[]
>>> del S[-1]
>>> S
['a', 'm', 'p']
{% endhighlight %}

####字典

字典的主要属性：

- 通过键而不是偏移量来读取
- 任意对象的无需集合
- 可变长、异构、任意嵌套
- 属于可变映射类型
- 对象引用表（散列表）

常见字典操作：
{% highlight python %}
>>> D={'spam': 2, 'food': {'ham': 1, 'egg': 2}}
>>> S=dict(name='Bob', age=32)
>>> D.keys()
['food', 'spam']
>>> S.values()
[32, 'Bob']
>>> D.items()
[('food', {'egg': 2, 'ham': 1}), ('spam', 2)]
>>> D['food']['ham']
1
>>> D.get('food')
{'egg': 2, 'ham': 1}
>>> D=dict([('name', 'mel'), ('age', '32')])
>>> D
{'age': '32', 'name': 'mel'}
>>> dict.fromkeys(['a', 'b'], 0)
{'a': 0, 'b': 0}
>>> dict([('name', 'mel'), ('age', '32')])
{'age': '32', 'name': 'mel'}
>>> dict(zip(['a', 'b', 'c'], [1, 2, 3]))
{'a': 1, 'c': 3, 'b': 2}
>>> list(zip(['a', 'b', 'c'], [1, 2, 3]))
[('a', 1), ('b', 2), ('c', 3)]
>>> Matrix={}
>>> Matrix[(2,3,4)]=88
>>> Matrix[(7,8,9)]=99
>>> Matrix
{(2, 3, 4): 88, (7, 8, 9): 99}
>>> {k: v for (k, v) in zip(['a', 'b', 'c'], [1,2,3])}
{'a': 1, 'c': 3, 'b': 2}
{c: c*4 for c in 'SPAM'}
{'A': 'AAAA', 'P': 'PPPP', 'S': 'SSSS', 'M': 'MMMM'}
{% endhighlight %}

字典使用注意事项：

- 序列运算无序
- 对新索引赋值会添加项
- 键不一定总是字符串

###第9章 元组、文件及其他

####元组（tuple）

元组的基本属性：

- 任意对象的有序集合
- 通过偏移存取
- 属于不可变序列类型
- 固定长度、异构、任意嵌套
- 对象引用的数组

常见元组操作：
{% highlight python %}
>>> tuple('spam')
('s', 'p', 'a', 'm')
>>> T=tuple('spaam')
>>> T.index('a')
2
>>> T.count('a')
2
>>> (1,2)+(3,4)
(1, 2, 3, 4)
>>> (0,1)*3
(0, 1, 0, 1, 0, 1)
>>> #一个元素的元组需要加个逗号
>>> (1,)
(1,)
{% endhighlight %}

元组除过不可变性以外几乎与列表的操作一样。在不引起语法冲突的情况下，python允许忽略元组的圆括号，在单个元素的元组，函数调用及print语句中括号是不可少的。

####文件

文件的基本属性：

- 文件迭代器是最好的读取行工具
- 内容是字符串，不是对象
- close是通常选项
- 文件是缓冲的并且是可查找的

常见文件操作：
{% highlight python %}
>>> file=open(r'C:\Users\Calvin\somefile.txt', 'w')
>>> file.write('Monty Python\n')
>>> file.write('Hello World\n')
>>> file.flush()
>>> text=open(r'C:\Users\Calvin\somefile.txt', 'r')
>>> print text.read()
Monty Python
Hello World
>>> text=open(r'C:\Users\Calvin\somefile.txt', 'r')
>>> print text.read(5)
Monty
>>> text=open(r'C:\Users\Calvin\somefile.txt', 'r')
>>> print text.readline()
Monty Python

>>> print text.readline()
Hello World

>>> text=open(r'C:\Users\Calvin\somefile.txt', 'r')
>>> print text.readlines()
['Monty Python\n', 'Hello World\n']
>>> text.seek(0)
>>> print text.readline()
Monty Python
>>> D={'a': 1 ,'b': 2, 'c': 3}
>>> F=open(r'C:\Users\Calvin\somefile.txt', 'wb')
>>> import pickle
>>> pickle.dump(D, F)
>>> F.close()
>>> F=open(r'C:\Users\Calvin\somefile.txt', 'rb')
>>> E=pickle.load(F)
>>> E
{'a': 1, 'c': 3, 'b': 2}
>>> file=open(r'C:\Users\Calvin\text.txt', 'w')
>>> file.writelines("{'a':1,'b':2,'c':3}")
>>> file.close()
>>> text=open(r'C:\Users\Calvin\text.txt', 'r')
>>> eval(text.readline())
{'a': 1, 'c': 3, 'b': 2}
>>> F=open('C:\Users\Calvin\data.bin','wb')
>>> import struct
>>> data=struct.pack('>i4sh', 7, 'spam', 8)
>>> data
'\x00\x00\x00\x07spam\x00\x08'
>>> F.write(data)
>>> F.close()
>>> F=open('C:\Users\Calvin\data.bin','rb')
>>> data=F.read()
>>> data
'\x00\x00\x00\x07spam\x00\x08'
>>> values=struct.unpack('>i4sh', data)
>>> values
(7, 'spam', 8)
{% endhighlight %}

可以用两种方式解析和存储python对象，即`eval()`和`pickle`模块，eval是将字符串解析为python对象，pickle是用来更安全的解析python原生对象的工具。`struct`模块可以构造并解析打包的二进制数据。

列表的复制用`L[:]`，字典用`D.copy()`，copy只能复制顶层，处理含有嵌套的字典，可用`copy`模块下的`copy.deepcopy()`。

需要注意到的是重复、合并以及分片只是在复制操作数对象的顶层。
{% highlight python %}
>>> L=[3,4,5]
>>> X=L*4
>>> Y=[L]*4
>>> X
[3, 4, 5, 3, 4, 5, 3, 4, 5, 3, 4, 5]
>>> Y
[[3, 4, 5], [3, 4, 5], [3, 4, 5], [3, 4, 5]]
>>> L[1]=0
>>> X
[3, 4, 5, 3, 4, 5, 3, 4, 5, 3, 4, 5]
>>> Y
[[3, 0, 5], [3, 0, 5], [3, 0, 5], [3, 0, 5]]
{% endhighlight %}

如果一个复合对象包含指向自身的引用，就会出现**循环对象**，python中有循环检测机制，检测到循环会显示未`[...]`，而不会陷入无限循环。

##第三部分 语句和语法

###第10章 Python语句简介

python的语句

<table width="100%" border="1">
<tr><th>语句</th><th>角色</th><th>例子</th></tr>
<tr><td>赋值</td><td>创建引用值</td><td>a, b, c='good', 'bad', 'ugly</td></tr>
<tr><td>调用</td><td>执行函数</td><td>log.write('spam, bug')</td></tr>
<tr><td>打印</td><td>打印对象</td><td>print('the killer', joke)</td></tr>
<tr><td>if/elif/else</td><td>选择动作</td><td>if 'python' in text: print(text)</td></tr>
<tr><td>for/else</td><td>序列迭代</td><td>for x in mylist: print(x)</td></tr>
<tr><td>while/else</td><td>一般循环</td><td>while x>y : print('hello')</td></tr>
<tr><td>pass</td><td>空占位符</td><td>while True: pass</td></tr>
<tr><td>break</td><td>循环退出</td><td>while True: if exittest(): break</td></tr>
<tr><td>continue</td><td>循环继续</td><td>while True: if skiptest(): continue</td></tr>
<tr><td>def</td><td>函数和方法</td><td>def f(a, b=1, *c): print(a+b+c+sum(d))</td></tr>
<tr><td>return</td><td>函数结果</td><td>def f(a, b=1, *c): return a+b+c+sum(d)</td></tr>
<tr><td>yield</td><td>生成器函数</td><td>def gen(n): for i in n: yield i*2</td></tr>
<tr><td>global</td><td>命名空间</td><td>x='old';def function(): global x, y; x='new'</td></tr>
<tr><td>nonlocal</td><td>命名空间（3.0+）</td><td>def outer(): x='old'; def function(): nonlocal x; x='new'</td></tr>
<tr><td>import</td><td>模块访问</td><td>import sys</td></tr>
<tr><td>from</td><td>属性访问</td><td>from sys import stdin</td></tr>
<tr><td>class</td><td>创建对象</td><td>class Subclass(Superclass): staticData=[]; def method(self): pass</td></tr>
<tr><td>try/except/finally</td><td>捕捉异常</td><td>try: action(); except: print('action error')</td></tr>
<tr><td>raise</td><td>触发异常</td><td>raise EndSearch(localtion)</td></tr>
<tr><td>assert</td><td>调试检查</td><td>assert x>y, 'x is too small'</td></tr>
<tr><td>with/as</td><td>环境管理器（2.6）</td><td>with open('data') as myfile: process(myfile)</td></tr>
<tr><td>del</td><td>删除引用</td><td>del data[k]; del[i:j]; del obj.attr; del variable</td></tr>
</table>


python语句的特点：

- 多了冒号加缩进表示语句块
- 括号是可选的
- 语句截止不需要分号
- 缩进没有绝对的标准（一般是一个tab）
- 多条语句在一行时用分号隔开（唯一需要分号的地方）
- 一条语句可以横跨多行，只需要用括号括起来（`(), [], {}`）
- 符合语句的主体可以在首行的冒号之后（`if x>y: print(x)`），但只能是简单语句

简单的语句片段：
{% highlight python linenos %}
while True:
    reply=raw_input('Enter text:')
    if reply=='stop':
        break
    elif not reply.isdigit():
        print('Bad! '*3)
    else:
        print(int(reply)**2)
print('Bye!')
{% endhighlight %}

加入异常处理以后可以简化为：
{% highlight python linenos %}
while True:
    reply=raw_input('Enter text:')
    if reply=='stop':
        break
    try:
        num=int(reply)
    except:
        print('Bad! '*3)
    else:
        print(int(reply)**2)
print('Bye!')
{% endhighlight %}

###第11章 赋值、表达式和打印


<div class="alert alert-block alert-warn form-inline" style="text-align:center; vertical-align:middle; font-size: 16px; font-weight:300;">To be continue!</div>
