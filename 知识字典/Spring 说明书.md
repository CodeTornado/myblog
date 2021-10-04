# Spring 字典

# Spring 学习资源链接

[Spring 源码分析 pdf](https://pan.baidu.com/s/1jGxdGTg?_at_=1632014381983)

[Spring 官网](https://spring.io/)

「[Java学习+面试指南](https://github.com/Snailclimb/JavaGuide)」一份涵盖大部分 Java 程序员所需要掌握的核心知识。准备 Java 面试，首选 JavaGuide！

[spring 官方文档](https://docs.spring.io/spring-framework/docs/current/reference/html/core.html#beans-beanname)



# Spring概述

spring 是轻量级用于简化服务端开发而诞生的框架

他的包含的内容很多, 分为 20 个模块

分别列举出来这 20 个模块

下载 spring 看下

## Spring 是兴起 Java 轻量级框架

为了解决企业开发的复杂性而创建

它使用 JavaBean 完成了以前只能用 EJB 才能完成的事情

但Spring 不止用于服务端开发, 从简单性\可测试性\松耦合的角度而言,任何 Java 应用都可以从中受益



# Spring 的Ioc 容器

Ioc 也成为依赖注入（DI）。
Ioc 容器构造并使用 bean 的过程，可以认为是bean 本身通过使用类的[构造](javascript:void(0)) 来控制它的依赖项[实例化](javascript:void(0))的逆过程。

类之间的关系，不再用代码控制，而是由 Spring 容器来控制。控制权有代码翻转到容器中，这就叫控制反转。

初始化对象时，代码无序 new，而是把类之间的关系写到配置文件里。

------

在 Spring 中，构成应用程序主干并由 Spring IoC 容器管理的对象称为 bean。
bean 是由 Spring IoC 容器实例化、组装和管理的对象。
Bean 以及它们之间的依赖关系反映在容器使用的配置元数据中。
除此以外，bean 只是应用程序中众多对象之一。

```java
// 接口代表 Spring IoC 容器
org.springframework.context.ApplicationContext
```

IoC 容器，负责实例化、配置和组装 bean

容器通过读取配置元数据来获取有关要实例化、配置和组装哪些对象的指令。
配置元数据以 XML、Java 注释或 Java 代码表示。
它可以让您表达组成应用程序的对象以及这些对象之间丰富的相互依赖关系。

------

ApplicationContextSpring 提供了该接口的几种实现：

通常创建
ClassPathXmlApplicationContext、FileSystemXmlApplicationContext

提示：虽然 XML 一直是定义配置元数据的传统格式，但您可以通过提供少量 XML 配置来声明性地启用对这些附加元数据格式的支持，从而指示容器使用 Java 注释或代码作为元数据格式。

实例化[一个](http://localhost:8081/javacript(0)) Spring IoC 容器实例

(a) 在 Web 应用程序场景中，应用程序文件中的简单八行（左右）样板 Web 描述符 XML web.xml
(b) 如果您使用 Spring Tools for Eclipse（一个 Eclipse 驱动的开发环境），您可以通过点击几下鼠标或按键轻松创建这个样板配置。

------

Spring 工作流程简述：

1. 指定POJO，配置元数据告诉 Spring
2. 容器生产bean
3. 返回配置完成并可供使用的实例

# 容器基本用法

## Spring让 bean 成为一个纯粹的 POJO

代码示例 1

```java
BeanFactory bf = new XmlBeanFactory(new ClassPathResource("beanFactoryTest.xml"));
MyTestBean bean = (MyTestBean) bf.getBean("myTestBean");
assertEquals("testStr", bean.getTestStr());
```

现在有了 Spring, 只需要获取Bean就可以使用
Spring 做了什么：

- 读取配置文件
- 根据配置找到类位置并实例化
- 返回实例化的类

## Spring代码层的结构组成

包的层级结构

- 主要逻辑：src/main/java
- 系统配置文件：src/main/resources
- 主要逻辑单元测试：src/test/java
- 测试用的配置文件：src/test/resources

## 两个核心类介绍

### DefaultListableBeanFactory

功能列表：

1. 别名注册的增删改查操作
2. 单例接口的 bean 注册
3. 对 bean 定义的各种操作
4. 根据各种条件获取 bean 的配置清单
5. 创建 bean、自动注入、初始化、应用 bean 的后置处理器
6. 对 bean 注册后的处理
7. 定义获取 bean 和各种属性
8. 对父工厂的支持
9. 对bean 工厂的特殊处理
10. 提供配置工厂的各种方法
11. bean 工厂的配置清单，指定忽略类型及接口

### XmlBeanDefinitionReader

功能列表：

1. 根据资源文件地址返回对应的资源
2. 资源文件读取并转换为 bean 定义的各个功能
3. 获取环境信息
4. 资源文件加载并转为文档
5. bean 定义的读取
6. 读取文档并注册 bean 定义
7. 解析元素的各种方法

做了什么：

- 根据资源文件的路径查找并转换为资源文件
- 将资源文件转换为文档
- 解析文档的元素为 bean 定义

## 容器的基础 XmlBeanFactory

其对DefaultListableBeanFactory进行扩展，修改为主要从 xml 中读取 bean 定义，用XmlBeanDefinitionReader类对资源文件读取和注册。
代码示例 2：

```java
private final XmlBeanDefinitionReader reader = new XmlBeanDefinitionReader(this);

public XmlBeanFactory(Resource resource) throws BeansException {
  this(resource, null);
}

public XmlBeanFactory(Resource resource, BeanFactory parentBeanFactory) throws BeansException {
  super(parentBeanFactory);
  this.reader.loadBeanDefinitions(resource);
}
```


[（代码示例 1）](javascript:void(0);)中通过调用ClassPathResource构造函数获取Resrouce 实例对象，有此 Resrouce 对象就能进行 XmlBeanFactory 的初始化。
Spring对Resrouce是 如何封装？





配置元数据传统上，以简单直观的 XML 格式提供

但 XML 格式不是唯一允许的配置元数据形式, 现在很多是基于 Java 的配置

spring 至少包含 1 个bean 定义
基于 XML 的配置元数据的基本结构：

```XML
<? xml version="1.0" encoding="UTF-8" ?>
<beans xmlns="http://www.springframework.org/schema/beans"
    xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
    xsi:schemaLocation="http://www.springframework.org/schema/beans
        https://www.springframework.org/schema/beans/spring-beans.xsd">

    <bean id="..." class="...">  
        <!-- collaborators and configuration for this bean go here -->
    </bean>

    <bean id="..." class="...">
        <!-- collaborators and configuration for this bean go here -->
    </bean>

    <!-- more bean definitions go here -->

</beans>
```

该id属性是一个字符串，用于标识单个 bean 定义。
该class属性定义 bean 的类型并使用完全限定的类名。

## 实例化一个容器

```java
ApplicationContext context = new ClassPathXmlApplicationContext("services.xml", "daos.xml");
```

更多的Spring 的 Resource加载方式的封装（[如参考资料中所述](https://docs.spring.io/spring-framework/docs/current/reference/html/core.html#resources)）

## bean 的概述

bean 定义表示为 BeanDefinition 对象。

bean 包含如下元数据：

- 定义的 bean 的实际实现类
- Bean 在容器中的行为方式（范围、生命周期回调等）
- 对 bean 执行其工作所需的其他 bean 的引用
- 在新创建的对象中设置的其他配置设置

bean 的参数列表：

| Property                | Explained in... |
| ----------------------- | --------------- |
| class                   | 实例化 bean     |
| name                    | 命名            |
| scope                   | 作用域          |
| constructor arguments   | 依赖注入        |
| properties              | 依赖注入        |
| autowiring mode         | 自动装配模式    |
| lazy initalization mode | 延迟加载模式    |
| initialization method   | 初始化回调      |
| destruction method      | 销毁回调        |



支持容器外用户创建已有对象

防止并发访问异常、bean容器状态不一致问题，单例实例需要尽早注册

------

### 命名 bean

每个 bean 都有很多标识符。
这些标识符需要在成长 bean 的容器中保持唯一，多个名字要使用别名。
可以用 id、name 来制定 bean 标识符。
若您不声明 id、name 容器会自动为 bean 生成唯一名称，您要找该name 是需要通过ref 元素查找。
命名规范：

- id 保持唯一
- 可以包含特殊符号
- name中可以用（，）（；）（ ）作为分隔符
- 驼峰式大小写
- 名称使用标准 Java 约定

spring 通过类路径扫描加载的组件，bean 名称生成规则是当前类名首字母小写.
参考这个类： java.beans.Introspector.decapitalize

------

配置别名：

```xml
<alias name="fromName" alias="toName"/>

<alias name="myApp-dataSource" alias="subsystemA-dataSource"/>
<alias name="myApp-dataSource" alias="subsystemB-dataSource"/>
```

每个组件和主应用程序都可以通过不同别名来引用的同一个 bean

------

## 实例化 bean



### 通过无参构造实例化 bean

```xml
<bean id="exampleBean" class="examples.ExampleBean"/>

<bean name="anotherExample" class="examples.ExampleBeanTwo"/>
```

### 通过静态工程方法实例化bean

```xml
<bean id="clientService"
		class="examples.ClientService"
		factory-method="createInstance"/>
```

### 通过实例工厂方法实例化 bean

```xml
<!-- the factory bean, which contains a method called createInstance() -->
<bean id="serviceLocator" class="examples.DefaultServiceLocator">
  <!-- inject any dependencies required by this locator bean -->
</bean>

<!-- the bean to be created via the factory bean -->
<bean id="clientService" 
      factory-bean="serviceLocator" 
      factory-method="createClientServiceInstance"/>
```

```java
public class DefaultServiceLocator {

  private static ClientService clientService = new ClientServiceImpl();

  private static AccountService accountService = new AccountServiceImpl();

  public ClientService createClientServiceInstance() {
    return clientService;
  }

  public AccountService createAccountServiceInstance() {
    return accountService;
  }
}
```





## 依赖关系

程序需要多个对象协同工作，对象协作需要靠依赖关系。

### 依赖注入

依赖注入 (DI) 是一个过程，对象只会在容器创建 bean 时自动注入依赖项，这是 bean 本身的逆过程。

DI 原则使代码更清晰，当对象提供依赖关系时，解耦更有效。该对象不查找其依赖项，也不知道依赖项的位置或类。因此，您的类变得更容易测试，尤其是当依赖项位于接口或抽象基类上时，这允许在单元测试中使用存根或模拟实现。

代码运行时，通过配置文件的描述给类通过注入另一个类。

把类之间的依赖关系写到配置文件里，运行时会，根据配置文件，把 A 类注入到 B 类中。



---

简单的依赖注入程序

一个` sayhello `程序

xxx 属性

get()

set()

sayHello() 调用 xxx 属性执行一个行为



`xxx` 类

sayTxt 字符串属性

sayHello() 一个打印 sayTxt 的行为



`SpringMain` 中抵用 xxx 类打印的行为

```java
ApplicationContext context = new ClassPathXml ApplicationContext("conf/applicationContext-*.xml");

SayHello sayHello = (SayHello) Context.getBean("SayHello");
sayHello.sayHello();
```

所有代码都没有 new 类的实例, 根据配置文件来初始化类

通过 getBean 的方式获得类的实例

这是种**低耦合**的写法，多个类之间耦合度很低。假如公司的程序代码要修改某个类，只需要再修改 1 处 xml 配置，其他的类很可能不用修改，减少不必要的工作

---



##### 基于构造函数的依赖注入

`<constructor-arg/>`元素中显式指定构造函数参数索引或类型 

```java
package x.y;

public class ThingOne {

    public ThingOne(ThingTwo thingTwo, ThingThree thingThree) {
        // ...
    }
}
```

```xml
<beans>
    <bean id="beanOne" class="x.y.ThingOne">
        <constructor-arg ref="beanTwo"/>
        <constructor-arg ref="beanThree"/>
    </bean>
</beans>
```

通过 type 指定构造函数参数的类型

```xml
<constructor-arg type="int" value="7500000"/>
<constructor-arg type="java.lang.String" value="42"/>
```

通过索引

```xml
<constructor-arg index="0" value="7500000"/>
<constructor-arg index="1" value="42"/>
```

通过参数名称

```xml
<constructor-arg name="years" value="7500000"/>
<constructor-arg name="ultimateAnswer" value="42"/>
```



##### 基于 Setter 的依赖注入

###### 直接值

```xml
<bean id="myDataSource" class="org.apache.commons.dbcp.BasicDataSource" destroy-method="close">
    <!-- results in a setDriverClassName(String) call -->
    <property name="driverClassName" value="com.mysql.jdbc.Driver"/>
    <property name="url" value="jdbc:mysql://localhost:3306/mydb"/>
    <property name="username" value="root"/>
    <property name="password" value="misterkaoli"/>
</bean>
```

###### 直接值简写

更简洁，但拼写错误是在运行时而不是设计时发现，建议借助 IDE 发现错误

```xml
    <bean id="myDataSource" class="org.apache.commons.dbcp.BasicDataSource"
        destroy-method="close"
        p:driverClassName="com.mysql.jdbc.Driver"
        p:url="jdbc:mysql://localhost:3306/mydb"
        p:username="root"
        p:password="misterkaoli"/>
```

###### 配置一个配置文件格式

Spring 容器通过使用 JavaBeans机制将`<value/>`元素内部的文本转换为 `java.util.Properties`实例`PropertyEditor`。

```xml
<bean id="mappings"
    class="org.springframework.context.support.PropertySourcesPlaceholderConfigurer">

    <!-- typed as a java.util.Properties -->
    <property name="properties">
        <value>
            jdbc.driver.className=com.mysql.jdbc.Driver
            jdbc.url=jdbc:mysql://localhost:3306/mydb
        </value>
    </property>
</bean>
```



###### id 引用元素

```xml
<bean id="theTargetBean" class="..."/>

<bean id="theClientBean" class="...">
    <property name="targetName">
        <idref bean="theTargetBean"/>
    </property>
</bean>

     				|| 等效于
						\/

<bean id="theTargetBean" class="..." />

<bean id="client" class="...">
    <property name="targetName" value="theTargetBean"/>
</bean>
```



###### 引用其他bean

```xml
<ref bean="someBean"/>
```



内置 bean

```xml
<bean id="outer" class="...">
    <!-- instead of using a reference to a target bean, simply define the target bean inline -->
    <property name="target">
        <bean class="com.example.Person"> <!-- this is the inner bean -->
            <property name="name" value="Fiona Apple"/>
            <property name="age" value="25"/>
        </bean>
    </property>
</bean>
```



###### 集合

```xlm
<bean id="moreComplexObject" class="example.ComplexObject">
    <!-- results in a setAdminEmails(java.util.Properties) call -->
    <property name="adminEmails">
        <props>
            <prop key="administrator">administrator@example.org</prop>
            <prop key="support">support@example.org</prop>
            <prop key="development">development@example.org</prop>
        </props>
    </property>
    <!-- results in a setSomeList(java.util.List) call -->
    <property name="someList">
        <list>
            <value>a list element followed by a reference</value>
            <ref bean="myDataSource" />
        </list>
    </property>
    <!-- results in a setSomeMap(java.util.Map) call -->
    <property name="someMap">
        <map>
            <entry key="an entry" value="just some string"/>
            <entry key="a ref" value-ref="myDataSource"/>
        </map>
    </property>
    <!-- results in a setSomeSet(java.util.Set) call -->
    <property name="someSet">
        <set>
            <value>just some string</value>
            <ref bean="myDataSource" />
        </set>
    </property>
</bean>
```

###### 集合合并

```xml
<beans>
    <bean id="parent" abstract="true" class="example.ComplexObject">
        <property name="adminEmails">
            <props>
                <prop key="administrator">administrator@example.com</prop>
                <prop key="support">support@example.com</prop>
            </props>
        </property>
    </bean>
    <bean id="child" parent="parent">
        <property name="adminEmails">
            <!-- the merge is specified on the child collection definition -->
            <props merge="true">
                <prop key="sales">sales@example.com</prop>
                <prop key="support">support@example.co.uk</prop>
            </props>
        </property>
    </bean>
<beans>
```



###### 强类型集合

```java
public class SomeClass {

    private Map<String, Float> accounts;

    public void setAccounts(Map<String, Float> accounts) {
        this.accounts = accounts;
    }
}
```

```xml
<beans>
    <bean id="something" class="x.y.SomeClass">
        <property name="accounts">
            <map>
                <entry key="one" value="9.99"/>
                <entry key="two" value="2.75"/>
                <entry key="six" value="3.99"/>
            </map>
        </property>
    </bean>
</beans>
```

###### Null 和空字符串值

Spring 将属性等的空参数视为空参数`Strings`。

```xml
<bean class="ExampleBean">
    <property name="email" value=""/>
</bean>
```

```xml
<bean class="ExampleBean">
    <property name="email">
        <null/>
    </property>
</bean>
```

###### 带有 p 命名空间的 XML 快捷方式

p-namespace 允许您使用`bean`元素的属性（而不是嵌套 `<property/>`元素）来描述协作 bean 的属性值，或两者兼而有之。

p-namespace 是property内嵌标签元素的简写。

```xml
<beans xmlns="http://www.springframework.org/schema/beans"
    xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
    xmlns:p="http://www.springframework.org/schema/p"
    xsi:schemaLocation="http://www.springframework.org/schema/beans
        https://www.springframework.org/schema/beans/spring-beans.xsd">

    <bean name="classic" class="com.example.ExampleBean">
        <property name="email" value="someone@somewhere.com"/>
    </bean>
					
    <bean name="p-namespace" class="com.example.ExampleBean"
        p:email="someone@somewhere.com"/>
</beans>
```

###### 带有 c 命名空间的 XML 快捷方式

 c-namespace 是constructor-arg元素的简写。

```xml
<bean id="beanTwo" class="x.y.ThingTwo"/>
    <bean id="beanThree" class="x.y.ThingThree"/>

<!-- traditional declaration with optional argument names -->
<bean id="beanOne" class="x.y.ThingOne">
  <constructor-arg name="thingTwo" ref="beanTwo"/>
  <constructor-arg name="thingThree" ref="beanThree"/>
  <constructor-arg name="email" value="something@somewhere.com"/>
</bean>

<!-- c-namespace declaration with argument names -->
<bean id="beanOne" class="x.y.ThingOne" c:thingTwo-ref="beanTwo"
      c:thingThree-ref="beanThree" c:email="something@somewhere.com"/>
```

c 命名空间下使用索引的写法

> 由于 XML 语法，索引表示法需要存在前导`_`，因为 XML 属性名称不能以数字开头

```xml
<!-- c-namespace index declaration -->
<bean id="beanOne" class="x.y.ThingOne" c:_0-ref="beanTwo" c:_1-ref="beanThree"
    c:_2="something@somewhere.com"/>
```



###### 复合属性名称

`something`豆具有`fred`属性，该属性具有`bob`属性，其具有`sammy` 特性，并且最终`sammy`属性被设置为值`123`。

```xml
<bean id="something" class="things.ThingOne">
    <property name="fred.bob.sammy" value="123" />
</bean>
```

###### 指定先加载 

bean 加载前需要先初始化某 bean

```XML
<bean id="beanOne" class="ExampleBean" depends-on="manager"/>
<bean id="manager" class="ManagerBean" />

----------------
<bean id="beanOne" class="ExampleBean" depends-on="manager,accountDao">
    <property name="manager" ref="manager" />
</bean>

<bean id="manager" class="ManagerBean" />
<bean id="accountDao" class="x.y.jdbc.JdbcAccountDao" />
```



### 延迟初始化的 Bean

SpringIoc 容器默认初始化所有 Bean，通过 lazy-init 属性修改

```xml
<bean id="lazy" class="com.something.ExpensiveToCreateBean" lazy-init="true"/>
<bean name="not.lazy" class="com.something.AnotherBean"/>
```

若被其他未延迟初始化bean指定为依赖项，则延迟初始化失效

bean 默认懒加载

```xml
<beans default-lazy-init="true">
    <!-- no beans will be pre-instantiated... -->
</beans>
```





### 自动装配合设置

使用元素的`autowire`属性为 bean 定义指定自动装配模式

Spring 容器可以自动装配协作 bean 之间的关系。

自动装配可以显着减少指定属性或构造函数参数。

自动装配可以随着对象的发展更新配置。

autoire 的 4 个参数：

| 模式          | 解释                                                         |
| :------------ | :----------------------------------------------------------- |
| `no`          | （默认）没有自动装配。Bean 引用必须由`ref`元素定义。对于较大的部署，不建议更改默认设置，因为明确指定协作者可以提供更好的控制和清晰度。在某种程度上，它记录了系统的结构。 |
| `byName`      | 按属性名称自动装配。Spring 查找与需要自动装配的属性同名的 bean。例如，如果一个 bean 定义被设置为按名称自动装配并且它包含一个`master`属性（即它有一个 `setMaster(..)`方法），Spring 会查找一个名为的 bean 定义`master`并使用它来设置属性。 |
| `byType`      | 如果容器中只存在一个属性类型的 bean，则让属性自动装配。如果存在多个，则会引发致命异常，这表明您不能`byType`为该 bean使用自动装配。如果没有匹配的 bean，则不会发生任何事情（未设置属性）。 |
| `constructor` | 类似于`byType`但适用于构造函数参数。如果容器中没有一个构造函数参数类型的 bean，则会引发致命错误。 |



#### 从自动装配中排除 Bean

将元素的`autowire-candidate`属性设置`<bean/>`为`false`. 



### 方法注入

容器中大部分 bean 是单例的。当 bean 需要与另一个bean 协作时，需要通过属性来定义依赖关系。

当 bean 声明周期不同时会出现问题。

例如：单例 A 要用非单例 B，容器只创建一次 A，因 B 是 A 的属性，导致所用的 B 仅创建了 一次。



#### 查找方法注入

通过XML 的配置后，Ioc容器能覆盖掉 bean 上的方法。

能被覆盖的方法格式要求：

`<public|protected> [abstract] <return-type> theMethodName(no-arguments);`

- 如果方法是`abstract`，则动态生成的子类实现该方法。
- 否则，动态生成的子类会覆盖原始类中定义的具体方法。

考虑以下示例：

```xml
<!-- a stateful bean deployed as a prototype (non-singleton) -->
<bean id="myCommand" class="fiona.apple.AsyncCommand" scope="prototype">
    <!-- inject dependencies here as required -->
</bean>

<!-- commandProcessor uses statefulCommandHelper -->
<bean id="commandManager" class="fiona.apple.CommandManager">
    <lookup-method name="createCommand" bean="myCommand"/>
</bean>
```



#### 任意方法替换

A 类的 `aaaMethod` 方法要替换

需要先编写 B 类并实现org.springframework.beans.factory.support.MethodReplacer`接口, 重写reimplement 方法

```java
public Object reimplement(Object o, Method m, Object[] args) throws Throwable {
        // get the input value, work with it, and return a computed result
        String input = (String) args[0];
        ...
        return ...;
    }
```

并在 xml 中配置方法替换

```xml
<bean id="myValueCalculator" class="x.y.z.A">
    <replaced-method name="aaaMethod" replacer="B">
        <arg-type>String</arg-type>
    </replaced-method>
</bean>

<bean id="B" class="a.b.c.B"/>
```



## bean 的作用域



---

