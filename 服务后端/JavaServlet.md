
# Servlet api 有 4 个包

1. javax.servlet
2. javax.servlet.http
3. javax.servlet.annotation
4. javax.servlet.descriptor

# javax.servlet中主要的类

1. Servlet
   1. GenericServlet
2. ServletRequest
3. ServeltResponse
4. ServletContext
5. ServeltConfig
6. RequestDispatcber
7. Filter

# servlet 技术的核心

servlet 技术的核心是 Servlet 接口类, 所有 Servlet 类都必须直接或间接的实现 Servlet 接口

# Servelt 这么重要, 那servlet 与 servlet 容器的关系是什么?

Servlet 容器将 Servlet 类载入内存
在一个应用程序中, 每个 servlet类 只有一个实例
servlet 是单实例多线程的
防止线程安全问题, 不建议使用类级变量, 也就是公开的静态成员变量

# Servlet应用 是如何借助 Servlet 实现类处理用户请求?

用户请求到 Servlet 容器
容器启用接收用户的HTTP请求信息解析并将请求响应封装到 ServletRequest\ServletResponse 中
容器启用线程调用 Servlet 实例的 Service 方法, 并传入这两个类
Servlet 类通过操作这两个类实现与用户的交互

# 编写简单的 Servlet 程序

1. 先安装1 个 Servlet 容器例如 Tomcat
2. 写个类实现 Servlet 接口
3. 在类上方用 WebServlet 注解修饰, 并指定 Servlet 名称和访问路径
4. 写 service 中的行为
   1. 像请求方响应一个 html 格式的数据
      1. 设置响应格式
      2. 获取输出流
      3. 向流打印 html 文本
5. servlet 的代码在 servlet-api.jar 中, 可以在 maven 或 tomcat 的 lib 目录中找到
6. 部署到 Servlet 容器目录结构
   1. tomcat 为例
      1. webapp 下\项目名应用程序名\WEB-INF
         1. classes\字节码文件
         2. lib\jar 包
         3. web.xml
      2. webapp 下\项目名应用程序名\用户可以通过 url直接访问的资源文件
      3. 提示 :
         1. WEB-INF 目录内是 servlet 可以访问, 用户不可以直接访问
         2. WEB-INF 目录外的文件用户可以通过 url直接访问的

# 核心类

## javax.servlet

### Servlet接口类的5个方法

初始化\服务\销毁
获取 Servlet 的详情描述
获取 Servlet 的配置

#### ServletRequest

Servlet 接收请求后创建了这个实例并封装请求的信息
获取内容长度\类型\请求参数\请求协议名称版本

#### ServletResponse

Servlet 接收请求后创建了这个实例并隐藏了向浏览器发送响应的复杂过程
getWriter 返回打印流并使用写数据
getOutputStream 发送二进制数据

#### ServletConfig

可以获取初始化时设置的参数
可以获取当前 Servlet 的上下文信息
一些WebServlet 的注解
WebServlet
WebInitParam

#### GenericServlet

是 Servlet 接口的抽象类,  4 个方法都实现了, 除了 serivce 需要编写逻辑的方法未实现
这是个通用类, 防止代码冗余

## javax.servlet.http

#### HttpServelt类

继承 javax.servlet.GenericServlet, 实现 javax.servlet.Servlet 接口
用户请求后 Servlet 容器会调用 service 方法, service 会调用自定义的 service 新方法, 新方法根据请求协议的类型, 调用指定的 doXXX 方法, doXXX 需要自己重写

#### HttpServletRequest类

实现 javax.servelt.ServeltRequest

#### HttpServletResponse 接口

实现 javax.servlet.ServletResponse

#### HttpSession

#### Cookie

## 部署配置

### 注解式配置

### xml 式配置

编写后不用省去重新编译

### 描述 servlet 的映射关系, 加载顺序等

# servlet会话管理

因 http协议 是无状态的, 从而需要记录一些关键信息方便用户使用网站
将需要的数据存放到某个作用域, 并且加以限制
简单\数据量小的可以用 URL 重写\页面隐藏域的方式记录数据在页面, 用户再次请求服务器时默认附带这上传这些数据

## 更灵活的会话管理技术可以使用 cookie\session

### cookie 是存放的在用户浏览器目录下的, 有一定限制

一般一个网站总共可以使用 20 个 cookie 字段, 用户也可以在浏览器中禁用 cookie

### session 是存放在服务器缓存中的, 占用服务器资源, 慎用. 

#### servlet 容器在 session 过多时一般会用二级存储, 但会有性能问, 还是谨慎使用. session 不要存放太多\太大对象. 

#### session 可以存任意类型对象. 未实现序列化的类转存到二级存储上时会失败并报错

#### HttpSession 的会话标识

JESSIONIE 的 cookie
jessionie 的 session
Servlet 容器会自动选择用哪种方式传递会话

# jsp

## 为何出现 jsp 技术?

由于 servlet 逻辑中内嵌 html 格式文本数据编写和修改都太麻烦, 想对这样的编写过程在进行一次封装, 掩盖掉复杂的操作让使用的程序员通过 jsp 更便捷的开发, servlet容器通过jsp 内容自动生成 servlet+内嵌html文本的代码容器
不是在 servelt 逻辑中内嵌 html格式文本, 而是在 html页面内嵌 java 代码, 与原先servlet 的开发方式相反过来, 这种规范技术叫 jsp

### 优点

不用程序员手动编译字节码
不用相关的编写部署配置直接访问路径就可以使用 jsp
html 页面中写代码很方便开发,阅读,维护
支持热部署单独 jsp

### 自带 4 个包

javax.servlet.jsp
javax.servlet.jsp.tagext 常用
javax.el
javax.servlet.jsp.el

### 用法

#### 使用 java 代码

`<% java 代码 %>`
`out.println("页面要打印的字符");`
`<%@ page import="要导入的java包" %>`

#### 注释

`<%-- 内容 --%>`

#### 隐式对象

##### request

javax.sevelt.http.HttpServletRequest

##### response

javax.servlet.http.HttpServletResponse

##### out

javax.servlet.jsp.JspWriter

##### session

javax.servlet.http.HttpSession

##### application

javax.servlet.ServletContext

##### config

javax.servlet.ServletConfig

##### pageContext

javax.servlet.jsp.PageContext

##### page

javax.servlet.jsp.HttpJspPage

##### exception

java.lang.Throwable

### PageContext 属性值可存储在 4 个作用域

页面page_scope
请求request_scope
会话session_scope
应用applicaiton_scope

### 3 个语法元素

#### 指令

##### page

1. `<%@ page attribute1="value1" b="b2" %>`  
2. import 导入多个包
3. session 是否加入会话管理 true
4. buffer 隐式对象 out 的缓冲大小 8kb, 取决于 jsp 容器
5. autoFlush 缓存自动写入输入流 true
6. isThreadSafe false
7. info getServletInfo 的返回值
8. errorPage 错误处理页面
9. isErrorPage 是错误处理页面 false
10. contentType response 响应内容类型 text/html
11. laguage java
12. extends 继承某个类
13. deferredSyntaxAllowedAsLiteral 是否解析某个前缀 false
14. trimDirectiveWhitespaces 打印是否不出多余空格和空行 false
15. include 导入其他资源	
    1. `<%@ include file="url" %>`
    2. url/开头为绝对路径, 否则为相对路径
    3. jsp 碎片和段, 请将后缀命名为.jspf

#### 脚本元素

`<% java 代码 %>`
`<%= 要输出在页面的文本 %>`  === `<% out.print(xxx.toString()); %>`
`<%! 声明某个东西%>`

#### 动作

##### 引入

`<jsp:include page="url">`
文件名要用对应的标准来命名, 例如 jsp 用.jsp 结尾, jspf 则视为静态资源文件非 jsp

##### 跳转到其他 jsp

`<jsp:forward page="url">`
   `<jsp:param name="" value="">`
`</jsp:forward>`

##### 定义并存某个 bean 对象到指定域中

`<jsp:useBean id="自定义 id" class="类全路径">`
`<%= 自定义 id.toString()%>`
bean 对象设置\获取值
`<jsp:setProperty name="id1" property="字段名" value="值"/>`
`<jsp:getProperty name="id1" property="字段名"/>` 可以直接输出到页面

### 表达式语言el

jsp2.0 最重要特性之一就是表达式语言 el, jsp 用户可以用它来更轻松的访问应用程序数据.
页面再不用写 jsp 声明\表达式\脚本域, ${ el }

#### 历史

##### EL

JSP2.0将 EL 应用在 JSP 标准标签库(JSTL)1.0 规范中的.
JSP1.2 用户程序员使用标准库导入他们的应用中, 也可以使用 EL 了

##### JSF

JSF是 java 快速构建 web 程序的框架, 构建与 JSP1.2 之上, JSF1.0开发出了 EL 的变体

##### EL

EL+JSF
JSP2.1\2.2将以前 JSP2.0 中的 EL\JSF 中定义的表达式语言统一起来

#### 取值

[]和.取值都能取, ["属性名"]这样更规范, 能取一些不符合 java 命名规范的属性
能一起用

##### 取值规则

从左到右, 左右有值则继续向右取值
会自动根据类型灵活取值

#### 隐式对象

pageContext 包含之前全部的 JSP 隐式对象
initParam
param
paramValues
header
headerValues
cookie
applicationScope
sessionScope
reqeustScope
requestScope
pageScope

#### 运算符

##### 算术

+-*/div%mod
先乘除取模后加减

##### 逻辑

&&and||or!not

##### 关系

==eq!=ne>get>=get<lt<=le
empty
为各种空

#### JSP 中 java 脚本可以配置关闭

##### web.xml 中

`jsp-config>jsp-property-group>url-pattern>*.jsp]]]scripting-invalid>true`

##### `el 可以禁用

###### 页面中禁用

`<%@ page isELIgnored="true" %>`

###### web.xml 中禁用

`jsp-config>jsp-property-group>url-pattern>*/jsp]]]el-ignored>true`

### JSTL

JSP 标准标签库 JavaServer Pages Standard Tag Library 缩写 JSTL
需要下载 jar 包
http://jstl.java.net
javax.servlet.jsp.jstl
放到 WEB-INF/lib 下

#### 核心 c

url http://java.sun.com/jsp/jstl/core

##### 子函数

###### 变量支持

out <c:out value= escapXml=true default= />
set <c:set value= var= scope= />
remove <c:remove var= scope= />

###### 流控制

if <c:if test= scope= var= />
choose when otherwise 像 switch
forEach c:forEach var varStatus begin end step
			 varStatus 类型为 javax.servlet.jsp.jstl.core.LoopTagStatus, 里边有 count current first last index 

###### URL 管理

###### 其他

c:forTokens 切割字符串并遍历  c:forTokens items delims [var varStatus begin end step]

#### XML x

url http://java.sun.com/jsp/jstl/xml

##### 子函数

核心
流控制
转换

#### 国际化 fmt

url xxx/fmt

##### 子函数

语言区域
消息格式化

###### 数字和日期格式化

fmt:formatNumber value [type pattern currencyCode currencySYmbol groupingUsed maxIntegerDigits minIntegerDigits maxFractionDigits minFractionDigits var scope]
fmt:formatDate value [type dateStyle timeStyle pattern timeZone var scope]
fmt:timeZonde value
fmt:parseNumber value [type pattern parseLocal integerOnly]
fmt:parseDate value [type dateStyle timeStyle pattern timeZone parseLocale var scope]

#### 数据库 sql

url xxx/sql
子函数 sql

#### 函数 fn

url xxx/functions

##### 子函数

###### 集合长度

length(input)

###### 字符串操作

fn:contains(AAA, A)
fn:endsWith(AAA, A)
`fn:escapeXml(User <br/> to change lines)`
indexOf(AAA, A)
join(Array, separator)
replace AAA A B
split AAA ,
startsWith AAA A
substring AAA 0 3
substringAfter ABC B
substringBufore ABC B
toLowerCase AAA
toUpperCase aaa
trim "  AAA  "

#### JSP 页面使用 JSTL 库使用格式

​				`<%@ taglib url= prefix= %>`

#### 通用的 value 写法

`<value=/>`  === ↓

```xml
<>
  value
</>
```



# 监听器

### 在 servlet 某个位置当符合条件时触发自定义事件

### 代码存在位置于javax.servlet\javax.servlet.http

### ServletContext

ServletContextListener
ServletContextAttributeListener

### HttpSession

HttpSessionListener
HttpSessionAttributeListener
HttpSessionActivationListener
HttpSessionBindingListener

### ServletReuest

ServletRequestListener
ServletReqeustAttributeListener
AsyncListener

# 过滤器

## 拦截符合条件的请求并处理

## 通过注解@WebFilter或者 web.xml 来配置过滤器

### 过滤器的执行顺序通过 web.xml 的先后声明顺序来定义

### 多个过滤器会顺序执行, 每个过滤器执行完 doFilter 方法后调用 filterChain.doFilter(req, resp), 直到最后一个过滤器执行完, 才会到为对应请求进行处理.

### 若不调用 filterChain.doFilter 则请求终止

### 属性

asyncSupported
description
dispatcerTYpes
displayName
filterName
initParams
largeIocn
serletName
smallIcon
urlPatterns
values

## Filter

### javax.servlet.Filter 接口

#### init

##### filterConfig

getServeltContext()
getFilterName()
getParameterNames()
getInitParameter()

#### doFilter

##### req, reps, filterChain

#### destroy

## FIlterBean

### FilterConfig

### FilterChain

# 装饰者模式

将需要装饰的类继承并作为成员变量实例化,
将操作包裹起来只修改返回值