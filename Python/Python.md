> linux执行

```

#!/usr/bin/env python3  // 添加执行的程序
# -*- coding: utf-8 -*-  // 读取文件的编码
chmod a+x hello.py  // 修改成可执行文件

```

> basic

```

dir('ABC')  // 获取所有属性和方法

len('ABC')  // 3
'ABC'.__len__()  // 3

print('>>> n = %d' % n)  // 占位
assert n != 0, 'n is zero!'  // 断言  AssertionError: n is zero!

python3 -O err.py  // 关闭断言

['__add__', '__class__', '__contains__', '__delattr__', '__dir__', '__doc__', '__eq__', '__format__', '__ge__', '__getattribute__', '__getitem__', '__getnewargs__', '__gt__', '__hash__', '__init__', '__iter__', '__le__', '__len__', '__lt__', '__mod__', '__mul__', '__ne__', '__new__', '__reduce__', '__reduce_ex__', '__repr__', '__rmod__', '__rmul__', '__setattr__', '__sizeof__', '__str__', '__subclasshook__', 'capitalize', 'casefold', 'center', 'count', 'encode', 'endswith', 'expandtabs', 'find', 'format', 'format_map', 'index', 'isalnum', 'isalpha', 'isdecimal', 'isdigit', 'isidentifier', 'islower', 'isnumeric', 'isprintable', 'isspace', 'istitle', 'isupper', 'join', 'ljust', 'lower', 'lstrip', 'maketrans', 'partition', 'replace', 'rfind', 'rindex', 'rjust', 'rpartition', 'rsplit', 'rstrip', 'split', 'splitlines', 'startswith', 'strip', 'swapcase', 'title', 'translate', 'upper', 'zfill']

name = input('please...')  // 输入
print('100 + 200 =', 100 + 200)  // 输出

// 语句块
a = 100
if a >= 0:
    print(a)
else:
    print(-a)

isinstance(a, list)  // 判断a是list类型
type(123)  // <class 'int'>
type('str')  // <class 'str'>
type(None)  // <type(None) 'NoneType'>
type(123)==type(456)  // True
type(fn)==types.FunctionType  // True
type(abs)==types.BuiltinFunctionType  // True
type(lambda x: x)==types.LambdaType  // True
type((x for x in range(10)))==types.GeneratorType  // True
isinstance([1, 2, 3], (list, tuple))  // True 是否是某种类型中的一种

```

> 基本类型

```

String

ord('A')  // 65（转数字）
ord('中')  // 20013（转数字）
chr(66)  // B（转字符）
'\u4e2d\u6587'  // '中文'（Unicode转字符）
x = b'ABC'
'ABC'.encode('ascii')  // b'ABC'
'中文'.encode('utf-8')  // b'\xe4\xb8\xad\xe6\x96\x87'
b'\xe4\xb8\xad\xe6\x96\x87'.decode('utf-8')  // '中文'
len('ABC')  // 3

格式化

'Hello, %s' % 'world'  // 'Hello, world'
 'Hi, %s, you have $%d.' % ('Michael', 1000000)  // 'Hi, Michael, you have $1000000.'
%d  整数
%f  浮点数
%s  字符串
%x  十六进制整数
%%  表示%

Boolean

3 > 2  // True
True and True  // True
True or True  // True
not True  // False

None（特殊的空值）

常量

PI

数学

10 // 3  // 取整
10 % 3  // 取余

```

> 技巧

```

print(r'\\\t\\')  // r,内部不转义

// 多行输出
print('''line1
... line2
... line3''')

```

> 数据结构

```

list

classmates = ['Michael', 'Bob', 'Tracy']
len(classmates)  // 3
classmates[0]  // 'Michael'
classmates[-1]  // 'Tracy'
classmates[1] = 'Sarah'

classmates.append('Adam')  // add
classmates.pop()  // del
classmates.pop(i)  // del i[ndex]
classmates.insert(1, 'Jack')  // insert

tuple（不可修改）

classmates = ('Michael', 'Bob', 'Tracy')
t = (1)  // 1
t = (1,)  // 消歧添加元组

循环

names = ['Michael', 'Bob', 'Tracy']
for name in names:
    print(name)

list(range(5))  // [0, 1, 2, 3, 4]

dict

d = {'Michael': 95, 'Bob': 75, 'Tracy': 85}
d['Michael']  // 95
'Thomas' in d  // False
d.pop('Bob')  // del
d.get('Thomas')  // 返回None
d.get('Thomas', -1)  // 不存在则返回指定的-1

```