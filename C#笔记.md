# 学习资料推荐

MSDN 文档

C#语言定义文档

C# 5.0 in A Nutshell



# 控制台输出 helloworld

 ```c#
 using System;
 
 namespace hello
 {
     class Program
     {
         static void Main(string[] args)
         {
             Console.WriteLine("Hello World!");
           	Console.ReadLine();
         }
     }
 }
 
 ```



# Windows Forms(Old)是相比 WPF更老的技术

WPF全拼(Windows Presentation Foundation)





# 名词科普.Net

.net 是一个平台 Net Dotnet 微软新一代多语言的开发平台, 用于构建和运行应用程序

.Net Framework 是一个框架

c#(sharp, C#读C沙浦) 编程语言, 可以开发基于.net 平台的应用 2000 年出来的 2002 年发布的 1.0 版本



# C#语法小知识

Namespace 名称空间 是类似java包的概念

using xxx 名称空间.类名; 引用某名称空间下的类

不用 using 导入则需要使用全限定名调用某类(全限定名指名称空间+类名)



# Mono

Novell公司支持在其他操作系统下开发.NET程序的框架。

Unity借助Mono实现跨平台,核心是.NET Framework 框架。  



# VS studio2019

## 新建项目

创建新的项目>**空白的解决方案**>

解决方案资源管理器>空白处右键>新建项目>

visual C#>**控制台应用程序**



## 修改字体

工具>选项>字体和颜色



## 开启行号显示

文本编辑器>所有语言>行号



#  操作命令行 Console 类

`Console.WriteLine` 控制台输出一行

`Console.ReadLine` 控制台读一行输入

`Console.Title` 控制台标题属性



# vs studio 快捷键

`Ctrl + K + C` 注释选中代码

`Ctrl + K + U` 取消注释选中代码

`Ctrl + K + F` 格式化选中代码

 

# 计算机知识科普

## 计算机硬件

> 应用程序一般运行在内存中

cpu 很快  小

内存 稍快 中

硬盘 慢     大

> 程序在处理数据
> 程序中的变量就是内存中开普一块用于存储数据的空间

 

## 单位换算

1字节byte = 8 位bit

1Byte = 8 bit

1KB = 1024 Byte

1MB = 1024KB

1G = 1024MB



> 营业厅宽带的网速是 Mbps(兆位每秒) 是速率单位, 换上成字节需要除以 8, 结果数兆字节/秒



## 进制

十进制

逢十进一



二进制

逢二进一

 

## 整形/整数

1个字节:有符号sbyte(-128-127) ,无符号byte(0~255)2个字节:有符号short(-32768-32767)

与无符号ushort(0~65535)

4字节:有符int)无符号uint

8字节:有符号long ,无符号ulong

> int 是整形中常用的



# Unity脚本 

## 常用字段

 **SerializeField** 序列化字段 在编辑器中显示私有变量

**HideInInspector** 在编辑器中隐藏字段

**Range** 在编辑器中限制属性值范围, 并提供滚动条

用法`[Range(0,100)]`



## 脚本并不用太规范

c#类 需要遵循规范

需要`字段>属性>构造函数>方法`



c#脚本 不用太遵循规范, 写了属性也不好显示, 构造函数不能初始化值 

直接 `字段>方法`



## 常用类

`Time.time` 返回当前时间

``Debug.Log`在控制台打印信息

`print`



## 脚本中初始化注意

MonoBehaviour 子类不能再脚本的构造函数中做初始化, 需要在 Awake 或者 Start 中初始化

因为不能再子线程中访问主线程成员, 而且游戏运行时会调用两次构造函数

不要在脚本中写构造函数, 写也可以但更重要的是不要在构造函数中调用 untiy提供的功能



# 脚本生命周期函数

## Start 初始化

执行时机: 创建游戏对象 > 脚本启用 > 执行一次



## 物理阶段

### FixedUpdate 固定更新

每隔固定时间执行一次, 默认 0.02 秒, 可以在设置中更改间隔时间

适合做物理操作:移动\旋转, 不会受到渲染影响, 也不受到机器性能影响



### Update 更新

每次渲染帧执行, 执行时间不固定

适合处理游戏逻辑

特点: 机器的渲染时间不固定(每帧渲染量不同\机器性能不同)



### LateUpdate 延迟更新

update 做完后执行, 适合做跟随, 和 update 同一帧执行完



## 输入事件

绑定物体必须有 collider对撞机组件

`OnMouseEnter 鼠标移入`

`OnMouseOver 经过`

`OnMouseExit 离开`

`OnMouseDown 鼠标按下` 

`OnMouseUp 抬起`



## 场景渲染

`OnBecameVisible 当可见`

当 MeshRenderer 在任何相机上可见时调用

`OnBecameInvisible 当不可见`





## 结束阶段

`OnDisable 当不可用`

对象变为不可用或附属游戏对象非激活状态是此函数被调用

`OnDestroy 当销毁`

当脚本销毁或附属的游戏对象被销毁时被调用

`OnApplicationQuit 当程序结束`

应用程序退出是被调用



> 更加详细的生命周期在 UnityApi 文档message 里, 要频繁的翻文档, 工具要常用



## 脚本生命周期图

![img](https://shimmerimg.oss-cn-beijing.aliyuncs.com/blog/screenshot/20210608114705.png)

![img](https://shimmerimg.oss-cn-beijing.aliyuncs.com/blog/screenshot/20210608114741.png)

![img](https://shimmerimg.oss-cn-beijing.aliyuncs.com/blog/screenshot/20210608114752.png)

### 说明

- OnPreCull: 在相机剔除场景之前调用此函数。相机可见的对象取决于剔除。OnPreCull 函数调用发生在剔除之前。
- OnBecameVisible/OnBecameInvisible: 在对象对于相机可见/不可见时调用此函数。
- OnWillRenderObject: 如果对象可见，则为每个相机调用一次此函数。
- OnPreRender: 在相机开始渲染场景之前调用此函数。
- OnRenderObject: 在完成所有常规场景渲染后调用此函数。此时，可使用 GL 类或 Graphics.DrawMeshNow 绘制自定义几何图形。
- OnPostRender: 在相机完成场景渲染后调用此函数。
- OnRenderImage（仅限专业版）： 在完成场景渲染后调用此函数，以便对屏幕图像进行后处理。
- OnGUI: 在每帧上多次调用此函数，以响应 GUI 事件。程序首先将处理 Layout 和 Repaint 事件，然后再处理每个输入事件的 Layout 和 keyboard/鼠标事件。
- OnDrawGizmos 用于在场景视图中绘制小图示 (Gizmos)，以实现可视化目的。



# 调试

> 开控制台窗口 windows> console

## 控制台窗口说明

左边

clear 清空控制台

collapse 折叠相同项目, 计数累加

clear on paly 运行时清空

Error pause 错误暂停



右边

叹号 普通信息

警告 警告信息

异常 异常信息

> Debug.Log 和 Print 控制台调试代码记得删除, 消耗资源

## 反编译工具

ILSpy



## 查看项目脚本和unity 引擎的源代码

项目文件夹 > library > ScriptAssemblies\xxx.dll 文件 拖入 vsstudio 中, 点击 c#反编译

项目文件夹 > library > UnityAssemblies\unityEngine.dll 文件 拖入 vsstudio 中, 点击 c#反编译



## vs sto 调试

#### 修改 Untiy

在 Unity 项目面板中配置 vsstudio

edit> Preferences> Extermal Tools > Extermal scriptEditor > vs 2019



#### 修改 vs sto

在vs sto 中菜单栏工具 > 获取工具和功能 > 修改 > 找到 vs for Unity 安装 > 重启 vs

 

> 不要使用 2013 或早起版本 unity2018 已经不在支持旧的 vsstudio 了



#### vs sto 中开启调试

代码打断点> 菜单栏 调试 >选择附加 Unity 调试 ==> 打开 unity 运行程序



## **Unity常用脚本类继承关系图**

<img src="https://shimmerimg.oss-cn-beijing.aliyuncs.com/blog/screenshot/20210608154744.jpeg" alt="这里写图片描述" style="zoom: 50%;" />
在Unity开发框架中有4个基本层次：

工程（应用程序）、场景、游戏对象和组件。



> 组件不让 new  需要调用 gameObject 类的 AddComponent<XXX> 来添加组件



# 查找物体 

## 根据名称找对象

慎用 GameObject.Find("游戏对象名称") , 场景中游戏对象太多, 找东西像是大海捞针耗费资源

用 this.transform.Find("游戏对象名称") , 更加精准快速的找到游戏对象



## 根据标签找对象

`GameObject.FindWithTag("tagName") `一般于查找无关联的物体时用



## 根据类型查找对象 常用

`Object.FindObjectOfType<XXX>();`



