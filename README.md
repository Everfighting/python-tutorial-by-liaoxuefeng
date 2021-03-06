##廖雪峰python教程笔记

- Python与其他语言区别
    - Python为高级语言
    - Python为解释型语言
    - 运行速度慢
    - 简单易学

- Python不能干的事
    - 操作系统需要用C语言
    - ios应用需要用Objective-C
    - Android需要用Java
    - 3D游戏最好用C或C++

- Python内置电池
    - Python提供了非常完善的基础代码库，
    - 覆盖了网络、文件、GUI、数据库、文本等大量内容。
    - 即各种库，内置库和第三方库。

- Python适合开发的应用
    - 网络应用，包括网站、后台服务等等；
    - 日常需要的小工具，包括系统管理员需要的脚本任务等等；
    - 把其他语言开发的程序再包装起来，方便使用。

- Python缺点
    - 运行速度慢，和C程序相比非常慢。
    - 代码不能加密。（C只需发布编译后机器码）

- 解释器版本
    - 官方版本的解释器：CPython。
    - IPython是基于CPython之上的一个交互式解释器。
    - PyPy是另一个Python解释器，它的目标是执行速度。

- Linux平台能够直接运行.py文件(Windows平台不可)
	>在.py文件的第一行加上：#!/usr/bin/env python
	>执行命令： $ chmod a+x hello.py

- print打印遇到逗号“,”会输出一个空格

- raw_input()读取用户输入信息

- 输入输出统称为Input/Output简写为IO。

- \#开头的语句是注释，

- Python程序是大小写敏感

- 进制

	十六进制用0x前缀和0-9，a-f表示，例如：0xff00，0xa5b4c3d2
	八进制用0前缀和0-7表示，例如：0100
	二进制用0b前缀和0,1表示，例如：0b10

- 整数和浮点数在计算机内部存储的方式是不同的。
	整数运算永远是精确的，而浮点数运算则可能会有四舍五入的误差，如round函数错误。

- 转义字符\可以转义很多字符。

	比如\n表示换行，\t表示制表符，字符\本身也要转义，\\表示的字符就是\。

- Python还允许用r''表示''内部的字符串默认不转义。

- 空值是Python里一个特殊的值，用None表示。

- 动态语言与静态语言

	变量本身类型不固定的语言称之为动态语言，与之对应的是静态语言。
	静态语言在定义变量时必须指定变量类型，如果赋值的时候类型不匹配，就会报错。

- 常量

	所谓常量就是不能变的变量。Python中通常用全部大写的变量名表示常量。
	如PI = 3.14159265359

- 编码问题

	最早的计算机在设计时采用8个比特（bit）作为一个字节，两个字节可以表示的最大整数是65535。
	
	- ASCII：
		由于计算机是美国人发明的，因此，最早只有127个字母被编码到计算机里，
		也就是大小写英文字母、数字和一些符号，称为ASCII编码。
	- Unicode：
		Unicode把所有语言都统一到一套编码里，不会有乱码问题了。
		ASCII编码和Unicode编码的区别：ASCII编码是1个字节，而Unicode编码通常是2个字节
	- UTF-8：
		把Unicode编码转化为“可变长编码”的UTF-8编码。
		UTF-8编码把一个Unicode字符根据不同的数字大小编码成1-6个字节，
		常用的英文字母被编码成1个字节，汉字通常是3个字节，只有很生僻的字符才会被编码成4-6个字节。
		如果你要传输的文本包含大量英文字符，用UTF-8编码就能节省空间。
	- 编码工作方式:
		在计算机内存中，统一使用Unicode编码，当需要保存到硬盘或者需要传输的时候，就转换为UTF-8编码。

- 字符串
    - Python提供了ord()和chr()函数，可以把字母和对应的数字相互转换：

            >>> ord('A')
            65
            >>> chr(65)
            'A'
    - 把Unicode编码的u'xxx'转换为UTF-8编码的'xxx'用encode('utf-8')方法：

            >>> u'ABC'.encode('utf-8')
            'ABC'
            >>> u'中文'.encode('utf-8')
            '\xe4\xb8\xad\xe6\x96\x87'
    - UTF-8编码表示的字符串'xxx'转换为Unicode字符串u'xxx'用decode('utf-8')方法：

            >>> 'abc'.decode('utf-8')
            u'ABC'
            >>> '\xe4\xb8\xad\xe6\x96\x87'.decode('utf-8')
            中文
    - len()函数可以返回字符串的长度。
    - 通常在文件开头写上这两行：

            #!/usr/bin/env python
            # -*- coding: utf-8 -*-
            第1行：Linux/OS X系统，这是一个Python可执行程序，Windows系统会忽略这个注释；
            第2行：Python解释器，按照UTF-8编码读取源代码，否则，你在源代码中写的中文输出可能会有乱码。
    - 字符串占位符

            在字符串内部，有几个%?占位符，后面就跟几个变量或者值，顺序要对应好。
            如果只有一个%?，括号可以省略。
            常见的占位符有：
            %d 整数 %f 浮点数 %s 字符串 %x 十六进制整数 用%%来表示一个%。

- list是一种有序的集合，可以随时添加和删除其中的元素。

        用len()函数可以获得list元素的个数。
        索引是从0开始的，当索引超出了范围时，Python会报一个IndexError错误。
		但特殊情况不报错，如切片操作：
		>>>L = [0,1,2,3,4]
		>>>L[0:5]
		[0,1,2,3,4]
		
        往list中追加内容作为原列表中的一个元素到末尾：
        >>> classmates.append('Adam')

        往list中追加列表一个或多个元素至末尾(所加元素必须可迭代)：
        >>> classmates.extend(['1','2'])
        把元素插入到指定的位置，比如索引号为1的位置。

        >>> classmates.insert(1, 'Jack')

        要删除list末尾的元素，用pop()方法：
        >>> classmates.pop()
        'Adam'

        要把某个元素替换成别的元素，可以直接赋值给对应的索引位置：
        >>> classmates[1] = 'Sarah'

        list元素也可以是另一个list
        >>> s = ['python','Java',['asp','php'],'scheme']
        >>> len(s)
        4

- tuple一旦初始化就不能修改。

        只有1个元素的tuple：
        >>> t = (1)
        >>> t
        1
        定义的不是tuple，是1这个数！

        只有1个元素的tuple定义时必须加一个逗号来消除歧义：
        >>> t = (1,)
        >>> t
        (1,)

        tuple所谓的“不变”是说，tuple的每个元素，指向永远不变。
        即指向'a'，就不能改成指向'b'，指向一个list，就不能改成指向其他对象，但指向的这个list本身是可变的！
        理解了“指向不变”后，要创建一个内容也不变的tuple怎么做？那就必须保证tuple的每一个元素本身也不能变。

- raw_input()读取的内容为字符串，需加以转换。

        birth = int(raw_input('birth: '))

- dict使用键-值（key-value）存储。

        一个key只能对应一个value，多次对一个key放入value，后面的值会把前面的值冲掉。

        判断key是否存在的两种方法：
        一是通过in判断key是否存在：
        >>> 'Thomas' in d False
        二是通过dict提供的get方法，如果key不存在，可以返回None，或者自己指定的value：
        >>> d.get('Thomas')
        >>> d.get('Thomas', -1)
        -1
        注意：返回None的时候Python的交互式命令行不显示结果。

        要删除一个key，用pop(key)方法，对应的value也会从dict中删除。
        dict内部存放的顺序和key放入的顺序是没有关系的。

        和list比较，dict有以下几个特点：
        查找和插入的速度极快，不会随着key的增加而增加；
        需要占用大量的内存，内存浪费多。
        而list相反： 查找和插入的时间随着元素的增加而增加；
        占用空间小，浪费内存很少。
        dict是用空间来换取时间的一种方法。

        牢记dict的key必须是不可变对象。
        这是因为dict根据key来计算value的存储位置,结果必须确定。
        这个通过key计算位置的算法称为哈希算法（Hash）
        字符串、整数等都是不可变的，可作为key。

- set set和dict类似，但无Value,重复元素在set中自动被过滤。

        显示的set([1, 2, 3])只是告诉你这个set内部有1，2，3这3个元素，显示的[]不表示这是一个list。
        set可以看成数学意义上的无序和无重复元素的集合。

        Set交集、并集等操作：
        >>> s1 = set([1, 2, 3])
        >>> s2 = set([2, 3, 4])
        >>> s1 & s2 set([2, 3])
        >>> s1 | s2 set([1, 2, 3, 4])

- 可变对象与不可变对象

        对于不变对象来说，调用对象自身的任意方法，也不会改变该对象自身的内容。
        相反，这些方法会创建新的对象并返回，这样，就保证了不可变对象本身永远是不可变的。

- 内置函数

        绝对值的函数abs(x),一个参数。
        比较函数cmp(x, y)，两个参数。如果x<y，返回-1，如果x==y，返回0，如果x>y，返回1。
        传入的参数数量不对，会报TypeError的错误。
        int()函数可以把其他数据类型转换为整数。
        isinstance(x,(int,float))数据类型检查。

- 函数小结

        定义函数时，需要确定函数名和参数个数；
        如果有必要，可以先对参数的数据类型做检查；
        函数体内部可以用return随时返回函数结果；
        函数执行完毕也没有return语句时，自动return None。
        函数可以同时返回多个值，但其实就是一个tuple。

- 函数参数
    - 默认函数

            设置默认参数时，有几点要注意：
            一是必选参数在前，默认参数在后，否则Python的解释器会报错
            二是当函数有多个参数时，把变化大的参数放前面，变化小的参数放后面。
            变化小的参数就可以作为默认参数，降低调用函数的难度。
    - 默认函数的大坑！！

            def add_end(L=[]):
                L.append('END')
                return L
            >>> add_end([1,2,3])
            [1,2,3,'END']
            >>> add_end(['x','y','z'])
            ['x','y','z','END']

            以上都没问题，但是
            >>>add_end()
            ['END']
            >>>add_end()
            ['END','END']
            >>>add_end()
            ['END','END','END']

            为什么会记住上次添加的'END'后的list
            原因如下：
            Python函数在定义的时候，默认函数L的值就被计算出来了，即[]，
            因为默认参数L也是一个变量，它指向对象[],
            每次调用该函数，如果改变了L的内容，
            则下次调用时，默认参数的内容就变了，不再是函数定义时的[]了。
            所以：定义默认函数一定要牢记，默认函数必须指向不变对象！

            为什么要设计str、None这样的不变对象呢？
            因为不变对象一旦创建，对象内部的数据就不能修改，
            这样就减少了由于修改数据导致的错误。
            由于对象不变，多任务环境下同时读取对象不需要加锁，同时读一点问题都没有。
            我们在编写程序时，如果可以设计一个不变对象，那就尽量设计成不变对象。
    - 可变参数

            定义可变参数和定义list或tuple参数相比，仅仅在参数前面加了一个*号。
            在函数内部，参数接收到的是一个tuple，
            Python允许你在list或tuple前面加一个*号，
            把list或tuple的元素变成可变参数传进去。
    - 关键字参数

            可变参数允许你传入0个或任意个参数，这些可变参数在函数调用时自动组装为一个tuple。
            而关键字参数允许你传入0个或任意个含参数名的参数，这些关键字参数在函数内部自动组装为一个dict。

            关键字参数可以扩展函数的功能。
            比如，在person函数里，我们保证能接收到name和age这两个参数，
            但是，如果调用者愿意提供更多的参数，我们也能收到。
            试想你正在做一个用户注册的功能，除了用户名和年龄是必填项外，其他都是可选项，
            利用关键字参数来定义这个函数就能满足注册的需求。
    - 参数定义的顺序必须是：必选参数、默认参数、可变参数和关键字参数。
    - *args是可变参数，args接收的是一个tuple； **kw是关键字参数，kw接收的是一个dict。

- 递归函数

        在函数内部，可以调用其他函数。
        如果一个函数在内部调用自身本身，这个函数就是递归函数。
         def fact(n):
            if n==1:
                return 1
            return n * fact(n - 1)


         递归函数的优点是定义简单，逻辑清晰。缺点过甚的调用会导致栈溢出。

- 切片

        取一个list或tuple的部分元素是非常常见的操作。(字符串也可以用)
        列表L后10个元素
        >>> L[-10:]
        原样复制列表
        >>> L[:]

- 迭代

        给定一个list或tuple，
        我们可以通过for循环来遍历这个list或tuple，
        这种遍历我们成为迭代。

        默认情况下，dict迭代的是key。
        如果要迭代value，可以用for value in d.itervalues()，
        如果要同时迭代key和value，可以用for k, v in d.iteritems()。

        由于字符串也是可迭代对象，因此，也可以作用于for循环：
        >>> for ch in 'ABC':
        ...print ch
        ...
        A B C

        判断对象是否可迭代：
        通过collections模块的Iterable类型判断。
        >>> from collections import Iterable
        >>> isinstance('abc', Iterable) # str是否可迭代
        同理可判断变量是否为字符串
        >>> x = 'abc'
        >>> y = 123
        >>> isinstance(x, str)
        True
        >>> isinstance(y, str) False

        Python内置的enumerate函数可以把一个list变成索引-元素对，
        这样就可以在for循环中同时迭代索引和元素本身：
        >>> for i, value in enumerate(['A', 'B', 'C']):
        ...     print i, value
        ...
        0 A
        1 B
        2 C
        任何可迭代对象都可以作用于for循环，包括我们自定义的数据类型，
        只要符合迭代条件，就可以使用for循环。

- 列表生成式

        列表生成式是Python内置的非常简单却强大的可以用来创建list的生成式。
	    >>>[x*x for x in range(1,11)]
	    [1,4,9,16,25,36,49,64,81,100]

- 生成器

        在Python中，这种一边循环一边计算的机制，称为生成器。
        generator保存的是算法，每次调用next()，就计算出下一个元素的值，
        直到计算到最后一个元素，没有更多的元素时，抛出StopIteration的错误。

        创建generator很简单，只需要把一个列表生成式[]改成()。
        g = (x * x for x in range(10))
        >>> for n in g:
        ...
        print n

        generator是非常强大的工具，在Python中，可以简单地把列表生成式改成generator，
        也可以通过函数实现复杂逻辑的generator。
        要理解generator的工作原理，它是在for循环的过程中不断计算出下一个元素，
        并在适当的条件结束for循环。
        对于函数改成的generator来说，遇到return语句或者执行到函数体最后一行语句，
        就是结束generator的指令，for循环随之结束。

- 函数式编程

        函数式编程就是一种抽象程度很高的编程范式，
        纯粹的函数式编程语言编写的函数没有变量。
        而允许使用变量的程序设计语言，由于函数内部的变量状态不确定，
        同样的输入，可能得到不同的输出，因此，这种函数是有副作用的。
        函数式编程的一个特点就是，允许把函数本身作为参数传入另一个函数，
        还允许返回一个函数！
        Python对函数式编程提供部分支持。
        Python允许使用变量，不是纯函数式编程语言。
    - map

            map()传入的第一个参数是f，即函数对象本身。
            像map()函数这种能够接收函数作为参数的函数，称之为高阶函数。

    - reduce

            把一个函数作用在一个序列[x1, x2, x3...]上，这个函数必须接收两个参数，
            reduce把结果继续和序列的下一个元素做累积计算，
            def str2int(s):
                return reduce(lambda x,y: x*10+y, map(int, s))

    - sorted()

            sorted可以接收一个比较函数来实现自定义的排序。
            def reversed_cmp(x,y):
                if x > y:
                    return -1
                if x < y:
                    return 1
                return 0
            >>>sorted([36, 5, 12, 9, 21], reversed_cmp)
            [36, 21, 12, 9, 5]
			
    - lambda函数

            匿名函数有个限制，就是只能有一个表达式，不用写return，
            返回值就是该表达式的结果。
            用匿名函数有个好处，因为函数没有名字，不必担心函数名冲突。
            此外，匿名函数也是一个函数对象，也可以把匿名函数赋值给一个变量，
            再利用变量来调用该函数。
    - 装饰器

            在代码运行期间动态增加功能的方式，称之为“装饰器”。
            本质上，装饰器就是一个返回函数的高阶函数。

            在面向对象（OOP）的设计模式中，decorator被称为装饰模式。
            OOP的装饰模式需要通过继承和组合来实现，
            而Python除了能支持OOP的decorator外，
            直接从语法层次支持decorator。
            Python的decorator可以用函数实现，也可以用类实现。
            decorator可以增强函数的功能，定义起来虽然有点复杂，
            但使用起来非常灵活和方便。

- 模块

        在计算机程序的开发过程中，随着程序代码越写越多，
        在一个文件里代码就会越来越长，越来越不容易维护。
        为了编写可维护的代码，我们把很多函数分组，分别放到不同的文件里，
        这样，每个文件包含的代码就相对较少，很多编程语言都采用这种组织代码的方式。
        在Python中，一个.py文件就称之为一个模块（Module）。

        使用模块有什么好处？
        最大的好处是大大提高了代码的可维护性。
        其次，编写代码不必从零开始。

        类似__xxx__这样的变量是特殊变量，可以被直接引用，但是有特殊用途。
        类似_xxx和__xxx这样的函数或变量就是非公开的（private），不应该被直接引用。
        Python提供了__future__模块，把下一个新版本的特性导入到当前版本。

- 面向过程与面向对象

        面向对象编程——Object Oriented Programming，简称OOP，是一种程序设计思想。
        OOP把对象作为程序的基本单元，一个对象包含了数据和操作数据的函数。

        面向过程的程序设计把计算机程序视为一系列的命令集合，即一组函数的顺序执行。
        而面向对象的程序设计把计算机程序视为一组对象的集合，
        而每个对象都可以接收其他对象发过来的消息，
        并处理这些消息，计算机程序的执行就是一系列消息在各个对象之间传递。

        数据封装、继承和多态是面向对象的三大特点。

        面向对象最重要的概念就是类（Class）和实例（Instance），
        必须牢记类是抽象的模板，比如Student类，
        而实例是根据类创建出来的一个个具体的“对象”，
        每个对象都拥有相同的方法，但各自的数据可能不同。

        类名通常是大写开头的单词。
        通常，如果没有合适的继承类，就使用object类，
        __init__方法的第一个参数永远是self，表示创建的实例本身

        类是创建实例的模板，而实例则是一个一个具体的对象，各个实例拥有的数据都不相同；
        通过在实例变量上调用方法，我们就直接操作了对象内部的数据，无需知道方法内部的实现细节。

        继承有什么好处？
        最大的好处是子类获得了父类的全部功能。
        继承的第二个好处：多态。
        当子类和父类都存在相同的run()方法时，总是会调用子类的run()。

- dir()

        获得一个对象的所有属性和方法

- 对象属性的操作

        >>> hasattr(obj, 'x') # 有属性'x'吗？
        True
        >>> setattr(obj, 'y', 19) # 设置一个属性'y'
        >>> getattr(obj, 'y') # 获取属性'y'
        19
        >>>getattr(obj, 'z', 404) # 获取属性'z'，如果不存在，返回默认值404
        404

- __slots__

        __slots__变量，限制可限制该class能添加的属性。
        若属性没有被放到__slots__中，所以不能绑定该属性，
        试图绑定将返回AttributeError的错误。
        __slots__定义的属性仅对当前类起作用，对继承的子类是不起作用的。
        除非在子类中也定义__slots__，
        这样，子类允许定义的属性就是自身的__slots__加上父类的__slots__。

- 多重继承

        通过多重继承，一个子类就可以同时获得多个父类的所有功能。
        只要选择组合不同的类的功能，就可以快速构造出所需的子类。

- __str__()与__repr__()区别

        __str__()返回用户看到的字符串，__repr__()返回程序开发者看到的字符串。
        __repr__()是为调试服务的。

- __iter__

        如果一个类想被用于for ... in循环，类似list或tuple那样，就必须实现一个__iter__()方法。
        该方法返回一个迭代对象，Python的for循环就会不断调用该迭代对象的next()方法拿到循环的下一个值，
        直到遇到StopIteration错误时退出循环。

- __getitem__

        要表现得像list那样按照下标取出元素，需要实现__getitem__()方法。

- Metaclass元类

        如何创建出类呢？必须根据metaclass创建出类.
        先定义metaclass，就可以创建类，最后创建实例。
        所以，metaclass允许你创建类或者修改类。
        换句话说，你可以把类看成是metaclass创建出来的“实例”。

- 错误与异常
    - assert

            assert的意思是，表达式n != 0应该是True，否则，后面的代码就会出错。
            如果断言失败，assert语句本身就会抛出AssertionError。
    - setUp与tearDown

            可以在单元测试中编写两个特殊的setUp()和tearDown()方法。
            这两个方法会分别在每调用一个测试方法的前后分别被执行。
            setUp()方法中连接数据库，在tearDown()方法中关闭数据库
            单元测试通过了并不意味着程序就没有bug了，但是不通过程序肯定有bug。

    - 异常

            完全无法在程序运行过程中预测的。
            比如写入文件的时候，磁盘满了，写不进去了，
            或者从网络抓取数据，网络突然断掉了。

    - 错误

            Python的错误其实也是class，所有的错误类型都继承自BaseException，
            如果错误没有被捕获，它就会一直往上抛，最后被Python解释器捕获，
            打印一个错误信息，然后程序退出。
    - try...except...finally用来处理错误十分方便。

- IO编程
    - CPU和内存的速度远远高于外设的速度。
    - 两种方式:同步IO、异步IO。

- 文件读取

		以读文件的模式打开一个文件对象
		>>> f = open('/Users/michael/test.txt', 'r')
		调用read()方法可以一次读取文件的全部内容，Python把内容读到内存，用一个str对象表示：
		>>> f.read()
		'Hello, world!'
		最后调用close()方法关闭文件。
		>>> f.close()

		Python引入了with语句来自动帮我们调用close()方法：
		with open('/path/to/file', 'r') as f:
		print f.read()

		调用read()会一次性读取文件的全部内容，内存若太大存在危险，
		可以调用read(size)方法，每次最多读取size个字节的内容。
		调用readline()可以每次读取一行内容，
		调用readlines()一次读取所有内容并按行返回list。
		for line in f.readlines():
			print(line.strip()) # 把末尾的'\n'删掉

		写文件和读文件是一样的
		with open('/Users/michael/test.txt', 'w') as f:
			f.write('Hello, world!')

- 操作文件和目录

        其实操作系统提供的命令只是简单地调用了操作系统提供的接口函数，
        Python内置的os模块也可以直接调用操作系统提供的接口函数。

        >>>import os
        >>> os.name # 操作系统名字
        >>> os.environ #在操作系统中定义的环境变量
        >>> os.getenv('PATH') #获取某个环境变量的值
        >>> os.path.abspath('.')  # 查看当前目录的绝对路径
        >>> os.path.join('/Users/michael', 'testdir')
        #把两个路径合成一个时，不要直接拼字符串，而要通过os.path.join()函数
        #这样可以正确处理不同操作系统的路径分隔符
        >>> os.path.split('/Users/michael/testdir/file.txt')
        #同样的道理，要拆分路径时，也不要直接去拆字符串，而要通过os.path.split()函数
        >>> os.mkdir('/Users/michael/testdir') # 然后创建一个目录
        >>> os.rmdir('/Users/michael/testdir') # 删掉一个目录
        >>> os.rename('test.txt', 'test.py') # 对文件重命名

- 序列化

        两个模块来实现序列化：cPickle和pickle。
        功能一样，cPickle是C语言写的，速度更快。

- 进程和线程

        可以同时运行多个任务的操作系统称之为多任务操作系统。
        对于操作系统来说，一个任务就是一个进程。
        在一个进程内部，若同时运行多个“子任务”，这些“子任务”称为线程（Thread）。
        线程是最小的执行单元，一个进程至少有一个线程。

        多任务的实现有3种方式：
        多进程模式；
        多线程模式；
        多进程+多线程模式。

        Python的标准库提供了两个模块：thread和threading。
        thread是低级模块，threading是高级模块，对thread进行了封装。

        多线程和多进程最大的不同：
        多进程中，同一个变量，各自有一份拷贝存在于每个进程中，互不影响，
        而多线程中，所有变量都由所有线程共享，
        任何一个变量都可以被任何一个线程修改，
        线程之间共享数据最大的危险在于多个线程同时改一个变量。

- 锁

        好处：就是确保了某段关键代码只能由一个线程从头到尾完整地执行，
        坏处：
        阻止了多线程并发执行，包含锁的某段代码实际上只能以单线程模式执行，效率受影响。
        由于可以存在多个锁，不同的线程持有不同的锁，并试图获取对方持有的锁时，
        可能会造成死锁，导致多个线程全部挂起，既不能执行，也无法结束。

        Python的线程虽然是真正的线程，但解释器执行代码时，
        有一个GIL锁：Global Interpreter Lock，
        任何Python线程执行前，必须先获得GIL锁，
        GIL全局锁实际上把所有线程的执行代码都给上了锁，
        Python不能利用多线程实现多核任务。
        但可以通过多进程实现多核任务。
        多个Python进程有各自独立的GIL锁，互不影响。

- 多进程与多线程

        多进程模式最大的优点就是稳定性高。
        因为一个子进程崩溃了，不会影响主进程和其他子进程。
        著名的Apache最早就是采用多进程模式。
        多进程模式的缺点是创建进程的代价大。
        在Unix/Linux系统下，用fork调用还行，在Windows下创建进程开销巨大。
        另外，操作系统能同时运行的进程数也是有限的。

        多线程模式通常比多进程快一点，
        多线程模式致命的缺点就是任何一个线程挂掉都可能直接造成整个进程崩溃。

- 协程

        Nginx就是支持异步IO的Web服务器，
        它在单核CPU上采用单进程模型就可以高效地支持多任务。
        在多核CPU上，可以运行多个进程（数量与CPU核心数相同），充分利用多核CPU。

        用异步IO编程模型来实现多任务是一个主要的趋势。
        对应到Python语言，单进程的异步编程模型称为协程。

- 正则表达式

        正则表达式是一种用来匹配字符串的强有力的武器。
        它的设计思想是用一种描述性的语言来给字符串定义一个规则，
        凡是符合规则的字符串，我们就认为它“匹配”了，否则，该字符串就是不合法的。

        用\d可以匹配一个数字
        \w可以匹配一个字母或数字
        .可以匹配任意字符
	    *表示任意个字符（包括0个）
	    用+表示至少一个字符
	    用?表示0个或1个字符
	    用{n}表示n个字符
	    用{n,m}表示n-m个字符
        \d{3}表示匹配3个数字，例如'010'
        \s可以匹配一个空格
        \s+表示至少有一个空格
        \d{3,8}表示3-8个数字，例如'1234567'
        [0-9a-zA-Z\_]可以匹配一个数字、字母或者下划线
        [0-9a-zA-Z\_]+可以匹配至少由一个数字、字母或者下划线组成的字符串
        [a-zA-Z\_][0-9a-zA-Z\_]*可以匹配由字母或下划线开头
        后接任意个由一个数字、字母或者下划线组成的字符串
        [a-zA-Z\_][0-9a-zA-Z\_]{0, 19}更精确地限制了变量的长度是1-20个字符
        ^表示行的开头，^\d表示必须以数字开头
        $表示行的结束，\d$表示必须以数字结束
        使用Python的r前缀，不考虑转义问题

    - match()方法判断是否匹配

            如果匹配成功，返回一个Match对象，否则返回None。
	- 切分字符串
            >>> 'a b   c'.split(' ')
            ['a', 'b', '', '', 'c']
            >>> re.split(r'\s+', 'a b   c')
            ['a', 'b', 'c']
            >>> re.split(r'[\s\,]+', 'a,b, c  d')
            ['a', 'b', 'c', 'd']
            >>> re.split(r'[\s\,\;]+', 'a,b;; c  d')
            ['a', 'b', 'c', 'd']

    - 提取分组
            注意到group(0)永远是原始字符串
            group(1)、group(2)……表示第1、2、……个子串。

    - 正则匹配默认是贪婪匹配。
       加个?就可以让\d+采用非贪婪匹配

- 内建模块
    - Base64

            一种任意二进制到文本字符串的编码方法，
            常用于在URL、Cookie、网页中传输少量二进制数据。
    - hashlib

            hashlib提供常见的摘要算法，如MD5，SHA1等等。
            MD5是最常见的摘要算法，速度很快。
            生成结果是固定的128字节，通常用一个32位的16进制字符串表示。
            SHA1的结果是160字节，通常用一个40位的16进制字符串表示。


            正确的保存口令的方式是不存储用户的明文口令，
            而是存储用户口令的摘要，比如MD5。

            由于常用口令的MD5值很容易被计算出来，
            要确保存储的用户口令不是那些已经被计算出来的常用口令的MD5，
            这一方法通过对原始口令加一个复杂字符串来实现，俗称“加盐”：
            可以通过把登录名作为Salt的一部分来计算MD5，
            从而实现相同口令的用户也存储不同的MD5。

            要注意摘要算法不是加密算法，不能用于加密，只能用于防篡改。

- 常用第三方模块

        所有的第三方模块都会在PyPI - the Python Package Index上注册，
        只要找到对应的模块名字，即可用easy_install或者pip安装

        PIL：Python Imaging Library，图像处理库。
        Tk是一个图形库，支持多个操作系统，使用Tcl语言开发；
        Tk会调用操作系统提供的本地GUI接口，完成最终的GUI。


- 网络编程

        TCP协议则是建立在IP协议之上的。TCP协议负责在两台计算机之间建立可靠连接，保证数据包按顺序到达。
        许多常用的更高级的协议都是建立在TCP协议基础上的，比如用于浏览器的HTTP协议、发送邮件的SMTP协议等。
        一个IP包除了包含要传输的数据外，还包含源IP地址和目标IP地址，源端口和目标端口。
        SMTP服务是25端口，FTP服务是21端口。
        端口号小于1024的是Internet标准服务的端口，端口号大于1024的，可以任意使用。

        使用UDP协议时，不需要建立连接，只需要知道对方的IP地址和端口号，就可以直接发数据包。
        虽然用UDP传输数据不可靠，但它的优点是和TCP比，速度快，对于不要求可靠到达的数据，就可以使用UDP协议。
        此外，服务器绑定UDP端口和TCP端口互不冲突，也就是说，UDP的9999端口与TCP的9999端口可以各自绑定。

        用标准的25端口连接SMTP服务器时，使用的是明文传输，发送邮件的整个过程可能会被窃听。
        要更安全地发送邮件，可以加密SMTP会话，实际上就是先创建SSL安全连接，然后再使用SMTP协议发送邮件。
        某些邮件服务商，例如Gmail，提供的SMTP服务必须要加密传输。Gmail的SMTP端口是587。

        Python内置一个poplib模块，实现了POP3协议，可以直接用来收邮件。
        用Python的poplib模块收取邮件分两步：
        第一步是用POP3协议把邮件获取到本地，
        第二步是用email模块把原始邮件解析为Message对象，
        然后，用适当的形式把邮件内容展示给用户即可。

        响应代码：
        200表示成功，
        3xx表示重定向，
        4xx表示客户端发送的请求有错误，
        5xx表示服务器端处理时发生了错误；

        HTTP请求的流程：
        步骤1：浏览器首先向服务器发送HTTP请求，
        请求包括：
        方法：GET还是POST，GET仅请求资源，POST会附带用户数据；
        路径：/full/url/path；
        域名：由Host头指定：Host: www.sina.com.cn
        以及其他相关的Header；
        如果是POST，那么请求还包括一个Body，包含用户数据。
        步骤2：服务器向浏览器返回HTTP响应，
        响应包括：
        响应代码2XX,3XX,4XX,5XX;
        响应类型：由Content-Type指定;
        以及其他相关的Header；
        通常服务器的HTTP响应会携带内容，也就是有一个Body，包含响应的内容。
        步骤3：如果浏览器还需要继续向服务器请求其他资源，
        比如图片，就再次发出HTTP请求，重复步骤1、2。

- 前端知识基础

        HTML定义了页面的内容，
        CSS来控制页面元素的样式，
        而JavaScript负责页面的交互逻辑。

        Web应用的本质就是：
        浏览器发送一个HTTP请求；
        服务器收到请求，生成一个HTML文档；
        服务器把HTML文档作为HTTP响应的Body发送给浏览器；
        浏览器收到HTTP响应，
        从HTTP Body取出HTML文档并显示。

- WSGI

        Web Server Gateway Interface是Python编写Web业务统一接口。
        无论多么复杂的Web应用程序，入口都是一个WSGI处理函数。
        Web就是写一个WSGI的处理函数，针对每个HTTP请求进行响应。

- MVC

        Model-View-Controller，中文名“模型-视图-控制器”。
        Python处理URL的函数就是C：Controller，
        Controller负责业务逻辑，比如检查用户名是否存在，取出用户信息等等；
        包含变量{{ name }}的模板就是V：View，
        View负责显示逻辑，通过简单地替换一些变量，
        View最终输出的就是用户看到的HTML。
        Model是用来传给View的，这样View在替换变量的时候，就可以从Model中取出相应的数据。

        通过MVC，我们在Python代码中处理M：Model和C：Controller，而V：View是通过模板处理。
        成功地把Python代码和HTML代码最大限度地分离了。
        使用模板的另一大好处是，模板改起来很方便，
        改完保存后，刷新浏览器就能看到最新的效果。

- 协程

        协程又称微线程，纤程。
        子程序，或者称为函数，在所有语言中都是层级调用，
        比如A调用B，B在执行过程中又调用了C，
        C执行完毕返回，B执行完毕返回，最后是A执行完毕。
        所以子程序调用是通过栈实现的，一个线程就是执行一个子程序。
        子程序调用总是一个入口，一次返回，调用顺序是明确的。
        而协程的调用和子程序不同。
        协程看上去也是子程序，但执行过程中，在子程序内部可中断，
        然后转而执行别的子程序，在适当的时候再返回来接着执行。

        协程的特点在于是一个线程执行，
        最大的优势就是协程极高的执行效率。
        因为子程序切换不是线程切换，而是由程序自身控制，
        因此，没有线程切换的开销，和多线程比，线程数量越多，协程的性能优势就越明显。
        第二大优势就是不需要多线程的锁机制，
        因为只有一个线程，也不存在同时写变量冲突，
        在协程中控制共享资源不加锁，只需要判断状态就好了，
        所以执行效率比多线程高很多。

        协程利用多核CPU方法：最简单的方法是多进程+协程，
        既充分利用多核，又充分发挥协程的高效率，可获得极高的性能。

- Gevent

        gevent是第三方库，通过greenlet实现协程，
        其基本思想是： 当一个greenlet遇到IO操作时，比如访问网络，就自动切换到其他的greenlet，
        等到IO操作完成，再在适当的时候切换回来继续执行。
        由于IO操作非常耗时，经常使程序处于等待状态，
        有了gevent为我们自动切换协程，就保证总有greenlet在运行，而不是等待IO。

        使用gevent，可以获得极高的并发性能，
        但gevent只能在Unix/Linux下运行，在Windows下不保证正常安装和运行。
        由于gevent是基于IO切换的协程，
        所以最神奇的是，我们编写的Web App代码，
        不需要引入gevent的包，也不需要改任何代码，
        仅仅在部署的时候，用一个支持gevent的WSGI服务器，
        立刻就获得了数倍的性能提升。

        gevent：把Python同步代码变成异步协程的库。
