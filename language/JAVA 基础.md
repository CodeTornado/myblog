# JAVA简介

Java是一种广泛使用的计算机编程语言，拥有跨平台、面向对象、泛型编程的特性，广泛应用于企业级Web应用开发和移动应用开发



> 万物皆为对象

# 面向对象



## 面向对象的程序设计

- 面向对象的程序设计，一种设计程序的思想。（英语：Object-oriented programming，缩写：OOP）
- OOP是种具有对象概念的程序编程典范，同时也是一种程序开发的抽象方针。它可能包含资料、属性、代码与方法。对象则指的是类的实例。它将对象作为程序的基本单元，将程序和数据封装其中，以提高软件的重用性、灵活性和扩展性，对象里的程序可以访问及经常修改对象相关连的资料。
- 在面向对象程序编程里，计算机程序会被设计成彼此相关的对象



## 面向对象四大特性

1. **封装** 把关键属性私有化不对外提供访问, 要操作关键属性需要通过公开方法
2. **抽象** 把现实生活中的对象抽象为类
3. **继承** 把已经存在的类所定义的内容视为自己的内容,并可以加入若干新的内容,或修改原来的方法使之更适合特殊的需要
4. **多态** 父类或接口定义的引用变量所指向的具体实例对象的的方法



# JDK、JRE、JVM的说明

1. 关系

-  JDK包含JRE 

- JRE包含 JVM

![三者关系](https://gimg2.baidu.com/image_search/src=http%3A%2F%2Fimage.bubuko.com%2Finfo%2F201910%2F20191015221044571469.png&refer=http%3A%2F%2Fimage.bubuko.com&app=2002&size=f9999,10000&q=a80&n=0&g=0n&fmt=jpeg?sec=1614503820&t=b27ac532ff1ea90d0b5fa833e52a10c5)

2. 说明

**Java Development Kit 开发工具包**

- java javac 编译 运行java 文件的工具
- javadoc 生成api文档

**Java Runtime Environment 运行时环境**

- 包含Applet
- 一些基础库

**Java Virtual Machine 虚拟机**

- 这是一种规范 可以用软件或硬件实现,相当于在所有的操作系统上模拟了一个小巧的 cpu处理 java 相关的东西
- java 跨平台核心用了 JVM 在不同操作系统都使用 java 虚拟机,通过虚拟机屏蔽了底层系统的差别,真正实现了(一次编译, 到处运行)

> Java 虚拟机（JVM）是运行 Java 字节码的虚拟机。JVM 有针对不同系统的特定实现（Windows，Linux，macOS），目的是使用相同的字节码，它们都会给出相同的结果。字节码和不同系统的 JVM 实现是 Java 语言“一次编译，随处可以运行”的关键所在。





# Hello World

想要语言学得好 Hello World 少不了



```shell
touch Hello.java
vim Hello.java
javac Hello.java 
java Hello
# 控制台输出
Hello World!
```

```java
public class Hello{
	public static void main(String[] args){
		System.out.println("Hello World!");
	}
}
```





# Java 程序运行机制

## 常见的编程语言运行机制

- 编译型
  - 先一次将程序文件转换成机器码, 后续执行只转换后的文件
  - 特定: 每次需要整个翻译, 只需要执行翻译后的文件速度快, 但修改文件需要重新翻译
  - 例子: 操作系统、c 语言

- 解释型
  - 每次执行程序时, 将对应代码转换成机器码
  - 特点: 每次只翻译需要执行的部分, 但每次都翻译效率相对低一些
  - 例子: 网页、VB 开发的程序

java 这两种类型特点都有, 但在只在特定的情况下转变为对应类型



## java 程序运行的过程

- java 在执行前进行了一次预编译, 先将 java 文件转换成 java.class 是字节码文件 (字节码:介于 java 和机器码之间的文件)
- 执行的时候将*.class 文件放到 java 虚拟机的类装载器, 这样类就加载到 jvm里面
- jvm 操作
  - 类装载器> 字节码校验器> 解释器
  - 解释器和操作系统平台交互, 程序执行一步 解释一步





---



# JAVA 基础语法

## 注释

```java
//单行

/**
 * 多
 * 行
 */

/**
 * @Description 描述
 * @Author 作者
 * @Since
 * @Version 
 * @param
 * @return
 * @throws
 */
```

[java 文档注释详解超链接](https://www.runoob.com/java/java-documentation.html)



## 标识符

1. 标识符说明

​	标识符是人为定义的简称

​	在我们编写程序的时候，需要大量地为程序、类、变量、方法等取名字，于是就有了标识符，简单来说，标识符就是一个名字。

2. [JAVA关键字](https://baike.baidu.com/item/java%E5%85%B3%E9%94%AE%E5%AD%97/5808816?fr=aladdin)

​	JAVA 关键字是被赋予特殊含义的标识符, 开发时不能使用再关键字命名

| [abstract](https://baike.baidu.com/item/abstract)     | [assert](https://baike.baidu.com/item/assert)             | [boolean](https://baike.baidu.com/item/boolean)     | break                                                 | [byte](https://baike.baidu.com/item/byte)     |
| ----------------------------------------------------- | --------------------------------------------------------- | --------------------------------------------------- | ----------------------------------------------------- | --------------------------------------------- |
| case                                                  | [catch](https://baike.baidu.com/item/catch)               | [char](https://baike.baidu.com/item/char)           | [class](https://baike.baidu.com/item/class)           | const                                         |
| continue                                              | [default](https://baike.baidu.com/item/default)           | [do](https://baike.baidu.com/item/do)               | [double](https://baike.baidu.com/item/double)         | [else](https://baike.baidu.com/item/else)     |
| [enum](https://baike.baidu.com/item/enum)             | [extends](https://baike.baidu.com/item/extends)           | [final](https://baike.baidu.com/item/final)         | [finally](https://baike.baidu.com/item/finally)       | float                                         |
| [for](https://baike.baidu.com/item/for)               | goto                                                      | [if](https://baike.baidu.com/item/if)               | [implements](https://baike.baidu.com/item/implements) | [import](https://baike.baidu.com/item/import) |
| [instanceof](https://baike.baidu.com/item/instanceof) | [int](https://baike.baidu.com/item/int)                   | [interface](https://baike.baidu.com/item/interface) | long                                                  | native                                        |
| new                                                   | [package](https://baike.baidu.com/item/package)           | [private](https://baike.baidu.com/item/private)     | [protected](https://baike.baidu.com/item/protected)   | [public](https://baike.baidu.com/item/public) |
| [return](https://baike.baidu.com/item/return)         | [strictfp](https://baike.baidu.com/item/strictfp)         | [short](https://baike.baidu.com/item/short)         | [static](https://baike.baidu.com/item/static)         | [super](https://baike.baidu.com/item/super)   |
| [switch](https://baike.baidu.com/item/switch)         | [synchronized](https://baike.baidu.com/item/synchronized) | [this](https://baike.baidu.com/item/this)           | [throw](https://baike.baidu.com/item/throw)           | throws                                        |
| [transient](https://baike.baidu.com/item/transient)   | try                                                       | [void](https://baike.baidu.com/item/void)           | [volatile](https://baike.baidu.com/item/volatile)     | [while](https://baike.baidu.com/item/while)   |



### 标识符规范

- 开头字母、美元符号、下划线
- 不能用JAVA关键字作为自定义标识符
- 可以用中文但不建议使用



---



### 什么是字节、位、B、字符

- 位(bit) : 是计算机内部数据储存的最小单位, 11001100是一个八位二进制数。
- 字节(byte) : 是计算机中数据处理的基本单位,习惯上用大写B来表示
- 1B (byte,字节) = 8bit (位)
- 字符:是指计算机中使用的字母、数字、字和符号





## 数据类型

JAVA 是强类型语言, 要求严格符合规定, 所有变量需要先定义后使用

数据类型分为 两类

- 基本类型
  - 8 种
  - 数值
    - 整数
      - byte 1btye 1 字节
      - short  2btye 2 字节
      - int 4btye 4 字节 整数的**默认类型**
      - long 8btye 8 字节
    - 浮点数
      - float 4btye 4 字节
      - double 8btye 8 字节 浮点数的**默认类型**
    - 字符
      - char 2btye 2 字节
  - 布尔
    - boolean **1bit 1 位** 计算机中对应的JAVA  boolean 类型只有 0 和 1 
- 引用类型
  - 类
  - 接口
  - 数组

> 提示: 业务代码中 少用浮点数直接比较和计算, 使用推荐 BigDecimal数学工具类

> JDK7 新特性, 数字间可用下划线分割, 非常方便阅读. 例子: int total = 10_0000;



### 整数用某进制表示

​	0b二进制

​	0x 十六进制

​	0 八进制



### 字符型常量和字符串常量的区别

形式上的区别 : 

​	字符常量是单引号引起的一个字符

​	字符串常量是双引号引起的 0 个或若干个字符

含义上的区别 : 

​	字符常量相当于一个整型值( ASCII 值),可以参加表达式运算

​	字符串常量代表一个地址值(该字符串在内存中存放位置)

占内存大小的区别 : 

​	字符常量只占 2 个字节

​	字符串常量占若干个字节



### 字符和转义

- 一个字符占 2 字节

 - 转义字符用右斜杠表示'\\'
    - 所有的ASCII码都可以用“\”加数字（一般是8进制数字）来表示。而C中定义了一些字母前加"\"来表示常见的那些不能显示的ASCII字符，如\0,\t,\n等，就称为转义字符，因为后面的字符，都不是它本来的ASCII字符意思了

 - 所有字符本质还是数字
    - 字符对应编码Unicode 表, 用\u 前缀来转义, 例: char c1 = '\u0061';

常用转义字符

​	退格\\b

​	换行\\n

​	回车\\r

​	制表\\t

​	单引号\\'

​	双引号\\"

​	斜杠\\\\



---





## 常用中文编码

ASCII 中文占一个字节

Unicode 中文占两个字节

UTF-8 中文占三个字节, 中文一般用这个,Tomcat 默认,因为现有中文字比较多, Unicode 中文并没有 UTF-8全面 

GBK 中文占两个字节 Windows 默认



## 类型转换

强制转换

- (类型) 变量名

- 高类型>>>低类型

  > 注意内存溢出问题, 或丢失数据精度

  > 不能将对象类型转换成不相关的类型

自动转换

- 低>>>高





## JAVA 运算符



### 自增自减运算符

符号在前就先加减，符号在后就后加减





### instanceof的用法

是啥

- instanceof是JAVA 的一个二元操作符，类似于 ==，>，< 等操作符

例子 

- 对象的引用A instanceof 类型B
- instanceof 判断A是否为B类或 B的子类  
- A 和 B 必须有父子关系才能使用instanceof进行比较, 否则会编译时报错



### 运算符分类

``` java
算术运算符  + - * / % ++ --

赋值运算符  =

关系运算符	 >  <  >=  <= ==  !=  instanceof

逻辑运算符	 &&  ||  !

位运算符	  & | ^ ～  >>  << >>>

条件运算符  ?  :

扩展运算符	 += -= *= /=
```





略



---



## JAVA 循环

- if 
- Switch 
- While  
- DoWhile 
- For 
- Foreach

```java
//打印三角形
public class Triangle{
    public static void main(String[] args){
        for(int i=1;i<=5;i++){
            for(int j=5; i<=j; j--)
                System.out.print(" ");
            for(int j=1; j<=i; j++)
                System.out.print("*");
            for(int j=1; j<i; j++)
                System.out.print("*");
            System.out.println();
        }
    }
}
/**

		 *
    ***
   *****
  *******
 *********
 
 */
```



### continue、break、和 return 的区别是什么？

在循环结构中，当循环条件不满足或者循环次数达到要求时，循环会正常结束。但是，有时候可能需要在循环的过程中，当发生了某种条件之后 ，提前终止循环，这就需要用到这三个关键词

continue ：指跳出当前的这一次循环，继续下一次循环。

break ：指跳出整个循环体，继续执行循环下面的语句。

return :  用于跳出所在方法，结束该方法的运行。

- return 一般有两种用法：
  - return; ：直接使用 return 结束方法执行，用于没有返回值函数的方法
  - return value; ：return 一个特定值，用于有返回值函数的方法







---



# JAVA常用工具类

## Scanner 类使用

java.util.Scanner 是 Java5 的新特征，我们可以通过 Scanner 类来获取用户的输入。

```java
Scanner s = new Scanner(System.in);
```

通过 Scanner 类的 next() 与 nextLine() 方法获取输入的字符串

一般需要 使用 hasNext 与 hasNextLine 判断是否还有输入的数据

```java 
import java.util.Scanner; 
 
public class ScannerDemo {
    public static void main(String[] args) {
        Scanner scan = new Scanner(System.in);
        // 从键盘接收数据
 
        // next方式接收字符串
        System.out.println("next方式接收：");
        // 判断是否还有输入
        if (scan.hasNext()) {
            String str1 = scan.next();
            System.out.println("输入的数据为：" + str1);
        }
        scan.close();
    }
}

//$ javac ScannerDemo.java
//$ java ScannerDemo
//next方式接收：
//runoob com
//输入的数据为：runoob
```

### next() 与 nextLine() 区别

next():

- 1、一定要读取到有效字符后才可以结束输入。
- 2、对输入有效字符之前遇到的空白，next() 方法会自动将其去掉。
- 3、只有输入有效字符后才将其后面输入的空白作为分隔符或者结束符。
- next() 不能得到带有空格的字符串。

nextLine()：

- 1、以Enter为结束符,也就是说 nextLine()方法返回的是输入回车之前的所有字符。
- 2、可以获得空白。



> 如果要输入 int 或 float 类型的数据，在 Scanner 类中也有支持，但是在输入之前最好先使用 hasNextXxx() 方法进行验证，再使用 nextXxx() 来读取
>
> 

## 基本类型对应的包装类

说明

- 每一个基本数据类型都会对应一个包装类型
- Boolean Integer Long Boolean



自动装箱 拆箱 Integer i = 1;

自动拆箱 int j = i;

手动拆箱 包装类.valueOf(基本类型引用)>>>基本类型

手动装箱  基本类. intVlue(包装类引用)>>>包装类型的



### 有了基本为何还要包装类型?

- 基本数据类型不具备面向对象特性
- 面向对象有空特性 null 封装常用的方法 Max Min
- 单独用基本数据类型不能满足使用需求





## 日期类 Date、Calender 

Date 好多方法都过时了, 新的 JDK 推荐使用 Calender 日期类





## StringBuffer、StringBuilder类



### StringBuilder、StringBuffer区别

- StringBuffer 使字符串可变长度 线程安全 加了同步锁  效率相对 Stringbuilder 低
- StringBuilder 使字符串可变长度 线程不安全 效率相对StringBuffer高

### String、StringBuilder、StringBuffer 的区别

- String 内容不可变, 内部使用的是一个不可变的数组, 用 final 修饰
- StringBuilder StringBuffer 内容是可改变的, 内部使用的是一个可变的字符数组, 没用 final 修饰





---



# 递归

### 啥是递归

想要理解递归 就要理解递归

自己调用自己 给自己一个出口

### 递归特点

简化代码, 方便阅读, 在学术中常用



> 注意:
>
> ​	留递归出口
>
> ​	生产环境开发中慎用递归
>
> - 容易栈溢出
>- 递归不利于后人维护代码
> - 递归耗费计算机资源比循环多





# 线程的代码使用

## 创建方式

1. 继承 Thread 类创建一个线程

- 不建议使用, 继承扩展性不强,JAVA 只支持单根继承,如果类继承 Thread 就不能继承其他的类了

1. 实现 Runnable 接口创建一个线程

   

## 线程启动

```java
Thread myThread = new Thread(继承了 Thread 的对象/实现了 Runnable 的对象);
myThread.start();		//用 start 方法启动, 执行 run方法和 Runnable 的实现方法
```



## 区分线程

- 创建线程时设置线程名称 t.setName("xx");



## 四种线程池

- 可以换成的线程池
- 有固定大小的线程池
- 定长线程池
- 单线程化的线程池



## 线程池的作用

- 系统可控, 限定线程的个数,不会导致由于线程过渡导致系统运行缓慢
- 节约资源, 防止重复创建\销毁线程浪费的资源
- 方便使用, 使用线程从池中获取即可



---

