# Python语法糖

1. ==是否等于的布尔判断符号
2. if elif else语句使用方法

1. 1. if 布尔判断 : 
   2. elif 布尔判断：
   3. else：

1. 打印语句print

1. 1. print “输出内容”
   2. print(“输出内容”)
   3. 提示print中可以做运算，需要注意运算时的元素类型保持一致，错误例子【print("这是字符串" + 99)】,TypeError: cannot concatenate 'str' and 'int' objects

1. input("提示并获取用户输入信息:") 用户输入后返回的信息可赋值给变量
2. python使用缩减来区分代码块
3. 字符串拼接str+str
4. 反斜杠‘\’是转义字符
5. 单引号和双引号需要成对使用 引号可以使用三个引号 例如：“”“字符串”“”
6. 原始字符串只需要在字符串前加字母”r“ 但是最后一个字母不能加’\‘
7. 用模块工具类时需要导入模块，例如：imput random
8. 类型转换 int(var) str(var) float(var)

1. 1. int(var) 不会进行四舍五入 会直接抹去小数 精度下降

1. type(var)内置函数返回变量的当前类型

1. 1. shell中>>> type(1)  返回：<class 'int'>

1. 布尔值写法注意 为True和False
2. isinstance(var, 类型) 变量类型校验

1. 1. shell中>>> isinstance(1, str) 返回：False

1. python可以连续赋值变量

```
>>> a = b = c = d = 10
>>> a,b,c,d
(10, 10, 10, 10)
```



1. 地板除法双斜杠//

1. 1. 整数除整数返回的是整数

```python
>>> 10 // 3
3
```

1. 取余数% 

```python
>>> 11 % 2
1
```



1. 幂运算 **

```python
>>> 3 ** 2
9
```



1. 计算优先级 先乘除后加减 先算括号里边的

1. 1. 幂运算（特殊：幂运算时 左侧为一元运算符时幂运算优先级高，右侧为一元运算符时幂运算优先级低）
   2. 幂运算 》正负号 》 算是操作符 》 比较操作费 》逻辑运算符

1. 逻辑操作符 and or not

1. 1. not代表非

1. python中数字0 表示False
2. assert True/False 断言 当关键字后边布尔值为假时程序自动崩溃并且跑出AssertionError的异常 一般用于测试 在程序检查点使用

```python
>>> assert 1==2
Traceback (most recent call last):
  File "<pyshell#50>", line 1, in <module>
    assert 1==2
AssertionError
```



1. for循环语句

1. 1. for 目标 in 表达式：

1. 1. 1. 循环内容 print（目标）



```python
>>> for i in gamename:
    print(i, end=' ')
w o w 
```



1. 指定范围生成连续数字range内置函数 range（【start范围起始数默认0，】stop范围停止数并且不包括此数【，step=1步进数默认1】）



```python
>>> list(range(5))
[0, 1, 2, 3, 4]
>>> list(range(2, 9))
[2, 3, 4, 5, 6, 7, 8]
>>> list(range(2, 9, 3))
[2, 5, 8]
```



1. 跳出循环语句break跳出外层第一个循环 continue跳出本轮循环
2. 操作列表

1. 1. 列表名。append（元素）追加到此列表
   2. 列表名。extend（元素）扩展列表 将元素内容和追加元素放入新的列表中
   3. 列表名。insert（i插入位置0开始算， 元素）插入元素到列表第i个位置
   4. del 列表名[第几个元素] 删除某个元素
   5. del 列表名 删除整个列表
   6. 列表名。pop（） 移除该列表最后一个元素并返回该元素 pop（i想要移除索引值）
   7. 列表名【start：end】简称’分片‘ 返回列表该范围内元素列表的一个拷贝，start和end都可以不写
   8. count(var) 统计元素出现次数
   9. index(i) 返回元素出现的第一次索引位置
   10. reverse() 反转数组元素位置
   11. sort(func指定排序的算法, key算法对应的key, reverse=布尔值) 排序该数组元素，默认从小到大

1. “+”加号两边必须元素类型一致 列表可以直接相加
2. 列表可以直接乘以3 代表该数组一次追加两遍本数组，例如： 【1】*3  【1，1，1】
3. 元素 in 列表 判断此元素是否在该列表内第一层中
4. python访问二维数组 列表名【i】【j】
5. **dir()** 函数不带参数时，返回当前范围内的变量、方法和定义的类型列表；带参数时，返回参数的属性、方法列表。如果参数包含方法__dir__()，该方法将被调用。如果参数不包含__dir__()，该方法将最大限度地收集参数信息
6. python中给与变量名赋值对象时给与变量名是一个引用



```python
>>> list1
[1, 3, 7, 7]
>>> list2 = list1
>>> list2
[1, 3, 7, 7]
>>> list2.sort(reverse=True)
>>> list2
[7, 7, 3, 1]
>>> list1
[7, 7, 3, 1]
```



1. tuple元组 该元组定义后就不可改变了 tuplevar1 = （1，2，3，4，5），其操作和列表一样但是是只读的

1. 1. 注意是圆括号并且是0个或（1个的元素+一个逗号”，“）例如： tuplevar1 = （1，）
   2. 元组重点是逗号，并非只是圆括号，可以只用元素和逗号赋值 例如： tuplevar1 = 1，2，3  tuplevar1现在是一个元组类型的对象

1. python操作字符串 format函数
2. python格式化字符串操作符号

| 符号   | 释义                                                         |
| ------ | ------------------------------------------------------------ |
| **%c** | 1) 格式化字符 2) c 仅小写                                    |
| **%s** | 格式化字符串 详见 [[Python3\] 004 字符串的基本使用](https://www.cnblogs.com/yorkyu/p/10241785.html) 的 "4.2.1" |
| **%d** | 格式化整数 详见 [[Python3\] 004 字符串的基本使用](https://www.cnblogs.com/yorkyu/p/10241785.html) 的 "4.2.2" |
| **%o** | 1) 格式化无符号八进制数 2) o 仅小写                          |
| **%x** | 1) 格式化十六进制数 2) x 不区分大小写                        |
| **%f** | 1) 格式化浮点数字，可指定小数点后的精度 2) 指定方式见 "2.2" 辅助指令表 |
| **%e** | 1) 用科学计数法格式化浮点数 2) e 不区分大小写                |
| **%g** | 1) 根据值的大小决定使用 %f 或 %e 2) g 不区分大小写           |



```python
# 使用方法
>>> print('%c' % 97)    # 此处 c 为小写
a
>>> print('%c'%98)
b
# 多个格式化字符串字符出现 需要以元组对象方式给与其值
>>> '%c %c %c' % (97, 98, 99)
'a b c' 
>>> aaac =  (97, 98, 99)
>>> '%c %c %c' % aaac
'a b c'
```



1. %f格式化字符串后 格式化后的小数默认四舍五入
2. 格式化操作符辅助命令

```python
*   定义宽度或者小数点精度
–   用做左对齐
+   在正数前面显示加号(+)
#   在八进制数前面显示零(0)，在十六进制前面显示”0x”或者”0X”（取决于用的是”x”还是”X”）
0   显示的数字前面填充”0″而不是默认的空格
(var)   映射变量（通常用来处理字段类型的参数）
m.n m 是显示的最小总宽度，n 是小数点后的位数（如果可用的话）


>>> '%.4f' % 456465   ;; 留4位小数
'456465.0000'
>>> '%30.4f' % 45     ;; 要求最终返回的数字的宽度是30位，小数后4位小数。默认右对齐
'                       45.0000'
>>> '%-30.4f' % 45    ;; 左对齐
'45.0000                       
>>> '%+30.4f' % 45    ;; 显示正号
'                      +45.0000'
>>> '%+30.4f' % -45   ;; 正负得负
'                      -45.0000'

>>> '%+030.4f' % -45   ;; 总宽度30位，4个小数，默认右对齐，前面补O
'-000000000000000000000045.0000'
```

1. len(obj)返回对象长度
2. max(iteration)返回最大的值 如果是字符串则比较ascll码 迭代对象内的元素类型必须一致
3. min 和max函数相反
4. lambda表达式 匿名函数 使代码更加精简 有此函数可以省去起名的麻烦操作 优秀！

1. 1. lambda函数由三个部分组成:
   2. lambda 关键字
   3.  用 , 分割的参数,就是普通函数里的参数,后面跟一个 ：
   4. 函数体,就是普通函数里的函数体
   5. 冒号后边计算最终结果是函数返回值

1. 

```python
>>> def ds(x):
    return 2 * x + 1

>>> ds(5)
11
>>> lambda x : 2 * x + 1
<function <lambda> at 0x1132eef70>
>>> g = lambda x : 2 * x + 1
>>> g
<function <lambda> at 0x1132eeee0>
>>> g(5)
11
>>> p = lambda x : x + 1
>>> type(p)
<class 'function'> #lambda表达式也是方法类型对象
```



1. filter过滤器 过滤掉不需要的 filter(function or None, iterable) 

1. 1. 参数1是过滤规则
   2. 参数2是需要迭代过滤的对象
   3. 如果参数1位空None 则直接迭代参数对象，将结果为True的元素记录下来并返回

1. map 在编程中用作映射来解释 

1. 1. map() 会根据提供的函数对指定序列做映射。
   2. 第一个参数 function 以参数序列中的每一个元素调用 function 函数，返回包含每次 function 函数返回值的新列表。
   3. 两个参数都不能为空 否则会爆类型异常TypeError: 'NoneType' object is not callable 。TypeError: 'NoneType' object is not iterable



```python
>>>def square(x) :            # 计算平方数
...     return x ** 2
... 
>>> map(square, [1,2,3,4,5])   # 计算列表各个元素的平方
[1, 4, 9, 16, 25]
>>> map(lambda x: x ** 2, [1, 2, 3, 4, 5])  # 使用 lambda 匿名函数
[1, 4, 9, 16, 25]
 
# 提供了两个列表，对相同位置的列表数据进行相加
>>> map(lambda x, y: x + y, [1, 3, 5, 7, 9], [2, 4, 6, 8, 10])
[3, 7, 11, 15, 19]
```



1. 递归

1. 1. 函数中调用自己
   2. 如果不写此方法的出口则为死递归函数
   3. 慎用递归，在适合的地方使用 例如：学习、自己简单使用、梳理逻辑时简化代码
   4. 通常是用消耗运行时间和计算机资源换取开发时间
   5. 递归有出口才是完整的递归
   6. 递归是采用分治思想 将问题分解 细分到最后解决最小问题 则整个问题逐渐解决成功

1. python三元运算符 ：为真时的结果 if 判断条件 else 为假时的结果（注意，没有冒号）
2. python字典使用 字典很像java的Map数据结构 dict



```python
>>> dict1 = {'李宁':'a','耐克':'b','阿迪达斯':'c','鱼C工作室':'d'}
>>> dict1['李宁']
'a'
>>> dict1['鱼C工作室']
'd'
>>> dict1 = {'李宁':'a','耐克':'b','阿迪达斯':'c','鱼C工作室':'d','鱼C工作室':'d'}
>>> dict1
{'李宁': 'a', '耐克': 'b', '阿迪达斯': 'c', '鱼C工作室': 'd'}
>>> dict(喝水='农夫山泉', 水杯='黑色水杯')
{'喝水': '农夫山泉', '水杯': '黑色水杯'}
```



1. id（对象名） 获取对象地址
2. set集合

1. 1. 集合中数据是唯一的 如果发现重复会自动剔除
   2. set集合是无序的

```python
>>> set1 = {1,1,23,2,2,3,4}
>>> set1
{1, 2, 3, 4, 23}
```



1. 操作文件



```python
>>> file1 = open('/Users/shimmer/Desktop/cc.txt','r')
>>> file1
<_io.TextIOWrapper name='/Users/shimmer/Desktop/cc.txt' mode='r' encoding='UTF-8'>
>>> for each in file1:
    print(each)
  
先帝创业未半而中道崩殂，今天下三分，益州疲弊，此诚危急存亡之秋也。然侍卫之臣不懈于内，忠志之士忘身于外者，盖追先帝之殊遇，欲报之于陛下也。诚宜开张圣听，以光先帝遗德，恢弘志士之气，不宜妄自菲薄，引喻失义，以塞忠谏之路也。

宫中府中，俱为一体，陟罚臧否，不宜异同。若有作奸犯科及为忠善者，宜付有司论其刑赏，以昭陛下平明之理，不宜偏私，使内外异法也。
```

1. python运行系统单shell命令



```python
#打开谷歌浏览器百度
>>> os.system('open -a "/Applications/Google Chrome.app" http://www.baidu.com ')
0
```

1. os模块和os.path模块很常用 多看api练习一下
2. 神奇的'泡菜'模块

1. 1. 能将列表转换成二进制方式借助文件永久存储到磁盘中 需要时再调用泡菜模块加载出来

```python
#倒入泡菜模块
>>> import pickle
#定义一个混乱的列表对象
>>> my_list = [1, 2, 123, '小充沛', [66, 77, '嘿嘿']]
#打开文件 打开模式为二进制方式并且只改
>>> pickle_file = open('/小甲鱼python基础第一版/泡菜语法练习1.pkl','wb')
#将对象倒入‘pickle_file’文件中 以二进制的方式
>>> pickle.dump(my_list, pickle_file)
>>> pickle_file.close()
##打开文件 打开模式为二进制方式并且只读
>>> pickle_file = open('/小甲鱼python基础第一版/泡菜语法练习1.pkl','rb')
#调用泡菜，文件中加载并返回原对象
>>> pickle.load(pickle_file)
[1, 2, 123, '小充沛', [66, 77, '嘿嘿']]
```



1. 常见异常

名称	解释

AssertionError	断言语句（assert）失败

AttributeError	尝试访问未知的对象属性

EOFError	用户输入文件末尾标志EOF（Ctrl+d）

FloatingPointError	浮点计算错误

GeneratorExit	generator.close()方法被调用的时候

ImportError	导入模块失败的时候

IndexError	索引超出序列的范围

KeyError	字典中查找一个不存在的关键字

KeyboardInterrupt	用户输入中断键（Ctrl+c）

MemoryError	内存溢出（可通过删除对象释放内存）

NameError	尝试访问一个不存在的变量

NotImplementedError	尚未实现的方法

OSError	操作系统产生的异常（例如打开一个不存在的文件）

OverflowError	数值运算超出最大限制

ReferenceError	弱引用（weak reference）试图访问一个已经被垃圾回收机制回收了的对象

RuntimeError	一般的运行时错误

StopIteration	迭代器没有更多的值

SyntaxError	Python的语法错误

IndentationError	缩进错误

TabError	Tab和空格混合使用

SystemError	Python编译器系统错误

SystemExit	Python编译器进程被关闭

TypeError	不同类型间的无效操作

UnboundLocalError	访问一个未初始化的本地变量（NameError的子类）

UnicodeError	Unicode相关的错误（ValueError的子类）

UnicodeEncodeError	Unicode编码时的错误（UnicodeError的子类）

UnicodeDecodeError	Unicode解码时的错误（UnicodeError的子类）

UnicodeTranslateError	Unicode转换时的错误（UnicodeError的子类）

ValueError	传入无效的参数

ZeroDivisionError	除数为零

1. 异常捕捉

1. 1. 异常捕获区域如果出现异常则不会继续运行该区域后的代码

```python
>>> try:
    a = 1 / 0
    print(a)
except Exception as e:
    print('除零异常'+str(e))
finally:
    print('出没出异常都会执行该区域代码')

    
除零异常division by zero
出没出异常都会执行该区域代码
```



1. 引出异常raise 



```python
>>> raise
Traceback (most recent call last):
  File "<pyshell#140>", line 1, in <module>
    raise
RuntimeError: No active exception to reraise
>>> raise OSError
Traceback (most recent call last):
  File "<pyshell#141>", line 1, in <module>
    raise OSError
OSError
>>> raise OSError('操作系统异常！')
Traceback (most recent call last):
  File "<pyshell#142>", line 1, in <module>
    raise OSError('操作系统异常！')
OSError: 操作系统异常！
```



1. while语句配合else

1. 1. 如果while语句没有跳出过而是顺序执行的则继续执行else语句

1. try except语句配合else

1. 1. 如果try代码块中语句没有爆出过异常而是顺序执行的则继续执行else语句

1. with语句

1. 1. 打开文件后如果程序没有继续使用文件则自动关闭文件



```python
>>> with open('/Library/work/code/homework/pythonwork1/小甲鱼python基础第一版/第二节课/操作资源/with自动关闭文件练习1.txt', 'w') as fileNew1:
    fileNew1.write('现在什么都不做......就是我的觉悟！-----自己关闭文件吧！')
```



1. 导入模块中全部的函数： from 模块名 import * 
2. 导入模块后将模块重名： import 模块名 as newname
3. 声明一个类

- class 类名:
- class类名(父类名称): 继承父类方式

- - 支持多重继承 class类名(父类名称A,父类名称B):
  - 子类调用父类方法在子类使用supper().__init__()函数

- 声明该类的构造函数def __init__(self,xxxx):
- 变量可以在构造函数中通过self.变量名来声明
- 声明私有变量 __变量名
- 声明私有函数 def __函数名:
- self关键字相当于this

- - 如果声明方式时没有在形参处添加self 则只能通过完整类名调用该函数

1. 是否为子类判断issubclass(class, classinfo)
2. pass关键字Python中的pass是空语句，它的出现是为了保持程序结构的完整性。pass不做任何事情，一般用作占位语句
3. hasatter(object, ’属性名‘)测试对象是否有指定属性
4. getattr(object,'属性名'[, '不包含时返回的提示错误信息'])测试对象是否有指定属性，无此变量则报错
5. setattr(object,'属性名')给对象添加上某属性变量
6. delattr(object,'属性名')删除对象某属性变量，无此变量则报错
7. property() 函数的作用是在新式类中返回属性值。语法：class property([fget[, fset[, fdel[, doc]]]])

- fget -- 获取属性值的函数
- fset -- 设置属性值的函数
- fdel -- 删除属性值函数
- doc -- 属性描述信息



```python
class C(object):
    def __init__(self):
        self._x = None
 
    def getx(self):
        return self._x
 
    def setx(self, value):
        self._x = value
 
    def delx(self):
        del self._x
 
    x = property(getx, setx, delx, "I'm the 'x' property.")
```



1. 形参中“**”关键字参数允许你传入0个或任意个含参数名的参数,这些关键字参数在函数内部自动组装为一个dict



```python
def d(**kargs):
    print(kargs)
    
d(a=1,b=2)

#在函数混合使用*以及**。
def h(a,*args,**kargs):
    print(a,args,kargs)

h(1,2,3,x=4,y=5)
```



1. __new__ (构造函数)单独地创建一个对象

1. 1. 在多次创建该类事实时，会被多次自动调用
   2. 编写时不限制返回对象类型

1.  __init__ (初始化函数)负责初始化这个对象

1. 1. 如果重新了__new__构造函数则不会自动调用此init方法

1. python 中全局变量、局部变量、静态变量，实例变量的区别和理解

- 全局变量: 在这个模块内也就是在整个.py 文件里，并且在所以类和函数的外边
- 局部变量: 在函数内或者在类方法内（不要加self修饰 self 表示当前类的对象）
- 静态变量: 在类内，当不再类的方法里（函数内部需要使用类名来进行修改）
- 实例变量，在类的方法内，用self修饰的变量，属于当前类的对象所有

1. __del__（self）对象生成后没有引用时垃圾回收机制销毁该对象时运行
2. __python提供的魔法方法__

1. 1. 可以重新算数运算符让对象按照开发者的想法进行+=*？
   2. 提供众多魔法方法

1. generator生成器是一个特殊的迭代器

1. 1. yield可以让函数暂停 下次调用该函数时继续计算

1. 集合推导式

1. 1. { 表达式 for 迭代变量 in 可迭代对象 [if 条件表达式] }



```python
>>> {each : '任意元素' for each in range(10)}
{0: '任意元素', 1: '任意元素', 2: '任意元素', 3: '任意元素', 4: '任意元素', 5: '任意元素', 6: '任意元素', 7: '任意元素', 8: '任意元素', 9: '任意元素'}
>>> {each : '任意元素' for each in range(3, 8) if each != 5}
{3: '任意元素', 4: '任意元素', 6: '任意元素', 7: '任意元素'}
```



1. 生成器推导式



```python
>>> a = (i for i in range(5))
>>> next(a)
0
>>> next(a)
1
>>> next(a)
2
>>> next(a)
3
```



1. 主方法

1. 1. if _ *name_* == '__main__'

1. python搜索模块时如果sys.path 返回路径中无此模块则提示找不到该模块

1. 1. 想要增加修改路径调用append函数 sys.path.append('某路径')

1. 建议将新写模块放入/Library/Frameworks/Python.framework/Versions/3.8/lib/python3.8/site-packages文件夹里
2. python包

1. 1. 创建一个文件夹
   2. 创建__init__.py文件告诉python将此文件夹当成一个包来管理
   3. 导入一个包中某模块的方法 import 包名.模块名

1. 看某个模块的简介print.(模块名.__doc__)
2. 看某个模块的私有工业函数、变量 dir(模块名)
3. 看某个模块对外开放使用的函数和变量 模块名__all__
4. 获取该模块代码所在位置 模块名._ *file_* 
5. 爬虫模块urllib
6. json模块 将json字符串转换成字典dict对象  json.load('未转化的json字符串')
7. 睡眠 time.sleep(100)
8. random模块随机选择 random.choice(希望随机使用一个元素的列表对象)
9. re模块 正则表达式 re.search(r'正则表达式', '未解析字符串') 加上r代表原始字符串，避免转义的问题
10. 指定某串固定的正则表达式可以制作成模块编译好重复使用，防止总是编译浪费资源
11. re模块 正则表达式 开启编译标志后可以影响正则表达式执行规则 例如：re.VERBOSE(详细表达式模式，支持换行、注释、空格方便开发和理解)
12. re.findall(pattern,string,flags=0)如果正则表达式包含小括号，也就是子组时 会将子组匹配到的字符串单独返回 如果匹配到多个则将匹配内容组合起来以元组方式返回
13. Scrapy爬虫框架，用于数据挖掘数据提取，最初未来页面抓取设计的，可用于网络爬虫
14. [Python程序 #!/usr/bin/python 的解释](https://www.cnblogs.com/furuihua/p/11213486.html)



## 注意事项

1. python的变量是没有明确声明类型的
2. BIF代表内置函数

1. 1. Python中的BIF就是Built-in Functions，即内置函数的意思，内置函数就是为了方便程序员快速的编写脚本程序，Python提供了很多内置函数
   2. 获取python的BIF 打开python shell 输入dir(__builtins__) 小写的就是BIF

```python
>>> dir(__builtins__)
['ArithmeticError', 'AssertionError', 'AttributeError', 'BaseException', 'BufferError', 'BytesWarning', 'DeprecationWarning', 'EOFError', 'Ellipsis', 'EnvironmentError', 'Exception', 'False', 'FloatingPointError', 'FutureWarning', 'GeneratorExit', 'IOError', 'ImportError', 'ImportWarning', 'IndentationError', 'IndexError', 'KeyError', 'KeyboardInterrupt', 'LookupError', 'MemoryError', 'NameError', 'None', 'NotImplemented', 'NotImplementedError', 'OSError', 'OverflowError', 'PendingDeprecationWarning', 'ReferenceError', 'RuntimeError', 'RuntimeWarning', 'StandardError', 'StopIteration', 'SyntaxError', 'SyntaxWarning', 'SystemError', 'SystemExit', 'TabError', 'True', 'TypeError', 'UnboundLocalError', 'UnicodeDecodeError', 'UnicodeEncodeError', 'UnicodeError', 'UnicodeTranslateError', 'UnicodeWarning', 'UserWarning', 'ValueError', 'Warning', 'ZeroDivisionError', '__debug__', '__doc__', '__import__', '__name__', '__package__', 'abs', 'all', 'any', 'apply', 'basestring', 'bin', 'bool', 'buffer', 'bytearray', 'bytes', 'callable', 'chr', 'classmethod', 'cmp', 'coerce', 'compile', 'complex', 'copyright', 'credits', 'delattr', 'dict', 'dir', 'divmod', 'enumerate', 'eval', 'execfile', 'exit', 'file', 'filter', 'float', 'format', 'frozenset', 'getattr', 'globals', 'hasattr', 'hash', 'help', 'hex', 'id', 'input', 'int', 'intern', 'isinstance', 'issubclass', 'iter', 'len', 'license', 'list', 'locals', 'long', 'map', 'max', 'memoryview', 'min', 'next', 'object', 'oct', 'open', 'ord', 'pow', 'print', 'property', 'quit', 'range', 'raw_input', 'reduce', 'reload', 'repr', 'reversed', 'round', 'set', 'setattr', 'slice', 'sorted', 'staticmethod', 'str', 'sum', 'super', 'tuple', 'type', 'unichr', 'unicode', 'vars', 'xrange', 'zip']
```

1. 帮助 help(需要了解的BIF)
2. python对变量用法有些不同，并不是吧值存储在变量中，更像是吧名字贴在值边上，网上流传着这样一句话python没有’变量‘只有’名字‘
3. python中直接输入变量名可返回值
4. 变量名取名要见名知意
5. python shell 中输入长数字会变为科学计数法 输入科学计数法会变成长数字并且带小数点
6. python不会阻止程序员用关键字做变量名
7. python是面向对象的编程语言
8. python通过校验代码规范并提示用户方式避免‘悬挂else’的情况发生
9. python列表能放入不同类型元素
10. python计数默认从0开始记录
11. python两个列表比较时会先从第一位开始比较，相同则继续比较，不同则返回比较结果。若一直相同并且一方长度大 则长数组大。若完全相同则判断为等于
12. python定义函数 def methodname(): 换行xxxx
13. 形参 函数定义过程中方法接受参数叫做形参
14. 实参 函数调用时传入的参数叫做实参 很为他是具体的参数值
15. 函数文档 方便别人理解函数的意义

```python
>>> def func(name, age, *args):
    '''
    这里是函数的帮助文档
    :param name: 姓名
    :param age: 年龄
    :param args: 其他
    :return: 返回值
    '''
    n = 0
    for item in args:
        print("loop {0}".format(n))
        print(item)
        n += 1

>>> print(func.__doc__) #使用函数的__doc__属性查看函数文档

    这里是函数的帮助文档
    :param name: 姓名
    :param age: 年龄
    :param args: 其他
    :return: 返回值
    
>>> help(func)
Help on function func in module __main__:

func(name, age, *args)
    这里是函数的帮助文档
    :param name: 姓名
    :param age: 年龄
    :param args: 其他
    :return: 返回值
```

1. 函数调用时使用形参关键字索引参数



```
>>> def PrintAB(a, b):
    print(a + '+' + b)

>>> PrintAB('优', '秀')
优+秀
>>> PrintAB(b='优', a='秀')
秀+优
```

1. 函数定义时设置形参默认参数值

```python
>>> def PrintDefAB(a='默认值A', b='默认值B'):
    print(a + '+' + b)

>>> PrintDefAB()
默认值A+默认值B
```

1. 方法中可变参数/收集参数 形参定义时形参关键字前加'*'符号 收集参数会被转换成元组类型对象

```python
>>> def testA(*params):
    print(params)

>>> testA(1)
(1,)
>>> testA(1, 2, 3)
(1, 2, 3)
>>> 
```

1. python shell强行让函数停下来command + c
2. python3 默认递归最深深度100层 需要修改则调用sys模块中setrecursionLimit(层数)方法修改层数
3. mac电脑自带python2.7 内含pip安装包需要手动安装
4. python3 以自安装好pip3



#  Python其他相关信息

1. 科学计数法/e记法

1. 1. 1500000 = 1.5e6

```python
>>> 1.5e6
1500000.0
```



1. python默认0为False 1为True
2. python的创始人推荐简洁的方式编程，开始不支持三元操作符，后因应用程序员强烈需求python2.5后加入了三元操作符
3. i%2 != 0 （i余2 不等于 0）用于判断是否不是偶数 True为奇数 False为偶数
4. api文档里中括号代表参数是可选的
5. 迭代（科学概念）

1. 1. 迭代是重复反馈过程的活动，其目的通常是为了逼近所需目标或结果。每一次对过程的重复称为一次“迭代”，而每一次迭代得到的结果会作为下一次迭代的初始值。

重复执行一系列运算步骤，从前面的量依次求出后面的量的过程。此过程的每一次结果，都是由对前一次所得结果施行相同的运算步骤得到的。例如利用迭代法*求某一数学问题的解。

对计算机特定程序中需要反复执行的子程序*(一组指令)，进行一次重复，即重复执行程序中的循环，直到满足某条件为止，亦称为迭代。

1. python内置函数中无法修改全局变量
1. 1. 如果内置函数变量和全局变量重名 则会创建一个新的变量对其操作 不会影响全局变量.内置函数中不能同时进行全局变量读取和修改 会爆出UnboundLocalError: local variable 'num1' referenced before assignment异常
   2. 只要是在**函数体内被赋值过**，那么变量就是local的，任何赋值之前的操作都会出现一个RuntimeError
   3. [unboundlocalerror报错原因](https://blog.csdn.net/anlian523/article/details/81075841)
1. python能直接把方法作为对象传递 例如：（a = MethodName）还可通过变量名调用方 a.add(1, 2) python利用此方法做到闭包
2. 内部函数只能对外部变量进行访问不能进行修改
3. 闭包就是能够读取其他函数内部变量的函数。例如在javascript中，只有函数内部的子函数才能读取[局部变量](https://baike.baidu.com/item/局部变量/9844788)，所以闭包可以理解成“定义在一个[函数](https://baike.baidu.com/item/函数/301912)内部的函数“。在本质上，闭包是将函数内部和函数外部连接起来的桥梁。




>  Mac系统 快捷键
>
> - mac复制文件绝对路径好文件名cmd+option+c
> - mac仿达根据文件路径打开文件夹cmd+shit+g
> - mac显示所有隐藏文件和文件夹cmd+shit+。

> Mac系统 小提示
>
> mac python shell很蠢 不能直接打开任意指定文件夹 需要从根目录一层一层点进去



# Mac 控制台键入

1. mac打开python shell的方式 打开‘终端’输入idle
2. 修改’终端‘应用中python默认使用版本

```shell
vi ~/.bash_profile 
# 添加这一行  python3安装路径
alias python="/usr/local/bin/python3"
#保存退出 , 执行
source ~/.bash_profile
```

1. history查看历史键入命令





# python Idle shell窗口

快捷键

```python
IDLE编辑器快捷键
自动补全代码        Alt+/（查找编辑器内已经写过的代码来补全)
补全提示              Ctrl+Shift+space(默认与输入法冲突，修改之)
(方法：Options->configure IDLE…->Keys-> force-open-completions
提示的时候只要按空格就出来对于的，否则翻上下键不需要按其他键自动就补全了)

后退                    Ctrl+Z

重做                    Ctrl+Shift+Z
加缩进                 Ctrl+]
减缩进                 Ctrl+[
加注释                 Alt+3
去注释                 Alt+4

Python Shell快捷键

自动补全同上
上一条命令           Alt+P
下一条命令           Alt+N
```



---

# Python 简单编写小程序

## 斐波那契数列 

### 递归实现

```python
>>> def 斐波那契数列_递归法(进行几个月份繁殖):
    return 1 if (进行几个月份繁殖 == 1 or 进行几个月份繁殖 == 2) else 斐波那契数列_递归法(进行几个月份繁殖 - 1) + 斐波那契数列_递归法(进行几个月份繁殖 - 2)

>>> 斐波那契数列_递归法(12)
144
>>> 斐波那契数列_递归法(1)
1
>>> 斐波那契数列_递归法(2)
1
>>> 斐波那契数列_递归法(3)
2
>>> 斐波那契数列_递归法(5)
5
>>> 斐波那契数列_递归法(10)
55
```

### 迭代实现

```python
>>> def 斐波那契数列_迭代法(进行几个月份繁殖):

    ##列表长度为兔子数量 每个元素为小兔子生存日期 0月开始 2月后才可生小兔子
    小兔子列表 = [0]

    for i in range(1, 进行几个月份繁殖):
        #复制一下小兔子列表
        本月新的小兔子列表 = 小兔子列表[:]

        for 索引值,当前小兔子存活月份 in enumerate(小兔子列表):
            本月新的小兔子列表[索引值] = 当前小兔子存活月份 + 1
            #这个小兔子张了2月了 可以生了
            if 本月新的小兔子列表[索引值] >= 2:
                #生出来一个小兔子 所以加一个0
                本月新的小兔子列表.append(0)
        小兔子列表 = 本月新的小兔子列表

    最终有几个小兔崽子 = len(小兔子列表)
    return 最终有几个小兔崽子

>>> 斐波那契数列_迭代法(1)
1
>>> 斐波那契数列_迭代法(2)
1
>>> 斐波那契数列_迭代法(3)
2
>>> 斐波那契数列_迭代法(5)
5
>>> 
>>> 斐波那契数列_迭代法(12)
144
```





## 相声剧本拆分小程序



```python
#将相声txt文件按照说话人物拆出新的文本文件

相声文本文件 = open('/Library/work/code/homework/pythonwork1/小甲鱼python基础第一版/第二节课/操作资源/相声.txt')

#w每次重新覆盖此文件
相声曹文本 = open('/Library/work/code/homework/pythonwork1/小甲鱼python基础第一版/第二节课/操作资源/相声_曹.txt', 'w')
相声刘文本 = open('/Library/work/code/homework/pythonwork1/小甲鱼python基础第一版/第二节课/操作资源/相声_刘.txt', 'w')

#迭代每行文本
for each_line in 相声文本文件:
    #当前行不为空白
    if len(each_line) != 0:
        #发现是曹的台词 则将当前行'：'后开始字符串存入 相声曹文本中
        if each_line[:1] == '曹':
            startindex = each_line.index('：') + 1
            相声曹文本.write(each_line[startindex:])
        if each_line[:1] == '刘':
            startindex = each_line.index('：') + 1
            相声刘文本.write(each_line[startindex:])

#python程序中只有关闭文件，操作才会永久记录到磁盘中。  (已验)
相声曹文本.close()
相声刘文本.close()

print('相声剧本拆分小程序----运行结束！')
```





---



## Python 借助Appium应用控制安卓手机



---

### 先安装安卓sdk

1. 打开https://developer.android.com/
2. 下载安卓studio
3. 安卓安卓sdk和全部插件
4. 修改环境变量，指到安装studio配置中安卓路径

###  

### 再安装并使用adb

1. 查看正连接的手机

1. 1. 启动和关闭ADB服务（adb start-server和adb kill-server）
   2. 终端app》》》adb devices -l

1. 1. 1. List of devices attached     
      2. 2e7cc01d        device usb:339804160X product:cepheus model:MI_9 device:cepheus transport_id:2

1. 1. 手机设备型号model:MI_9
   2. 如果连不上用相关手机助手，帮忙安装usb驱动

1. adb无线链接手机命令

1. 1. 1. 首先把我们的手机连接到电脑上
      2. 在命令行里cd到我们的sdk下的 platform-tools的路径找到我们的adb命令输入 ,输入adb devices查看我们连接的设备
      3. 使用adb tcpip 8888 设置端口号，5555为默认端口号，也可以设置其它端口号，端口号为需要为4位数
      4. 拔掉我们的设备，开始无线连接 adb connect
      5. 使用adb connect 192.168.1.65:8888， 192.168.1.65为我们手机的ip地址， 其中8888是我们自己设的端口号，这个端口号要和adb tcpip 设置的端口号保持一样，如果我们没有自己设置端口号，直接adb connect192.168.1.65就行了，默认使用5555。 连接成功提示
      6. 取消连接就是 adb disconnect 192.168.1.65:8888

1. adb shell 进入
2. adb常用命令

1. 1. https://www.jianshu.com/p/6b64cf1e51bc
   2. https://github.com/mzlogin/awesome-adb

1. adb学习

1. 1. **获取打开当前窗口包名路径名**

1. 1. 1. **windos   ---》**adb shell dumpsys window windows I findstr mFocusedApp
      2. **mac/Liunx ---》**adb shell dumpsys window windows I grep mFocusedApp
      3. 查找返回中 mFocusedApp=AppwindowToken{53309da token=Token{2e2fa785

ActivityRecord{2928d4fc uo com.android.settings/.Settings t1127}}}

> adb 命令连通手机给与权限后已经可以简单控制了!





### 开始安装Appium

1. python客户端库和appium服务通信
2. 安装Appium Python Client包

1. 1. pip install Appium-Python-Client
   2. 要确保安装匹配版本的selenium和appium
   3. pip install selenium -U



1. 安装appium服务，都命令行和桌面版都装上，命令行版本可以无线连接手机

1. 1. 安装java环境
   2. 安装brew
   3. 安装第三方管理工具 brew install carthage
   4. node和npm都更新到最新
   5. 终端输入npm install -g appium
   6. 看下版本appium -v
   7. appium-doctor 安装
   8. 检查是否安装好appium-doctor --Android
   9. 安装Appium Server 

1. 1. 1. npm install -g appium



### 启动桌面Appium

1. 直接启动
2. 启动命令行版，终端输入appium即可





### Appium初次链接

1. 打开appium配置好安卓adk
2. 手机数据线连接电脑



```python
from appium import webdriver
import time

#配置字典
desired_caps = dict()
desired_caps['platformName'] = 'Android'
desired_caps['platformVersion'] = '9'
desired_caps['deviceName'] = '192.168.100.101:8888'
#包名
desired_caps['appPackage'] = 'com.android.settings'
#界面名
desired_caps['appActivity'] = '.Settings'


driver = webdriver.Remote('http://localhost:4723/wd/hub', desired_caps)

time.sleep(5)

driver.quit()
```

1. 执行Python脚本（手机初次运行appium有几个自动安装软件，手机点击继续即可）



---



# 有趣的话题

1. python魔法方法
2. 定时器模块timeit
3. re正则表达式模块
4. urllib爬虫模块
5. Scrapy爬虫框架
6. tkinter模块python标准gui
7. AppKit模块