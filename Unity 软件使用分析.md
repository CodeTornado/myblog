Create a new scene

<img src="/Users/shimmer/Library/Application Support/typora-user-images/image-20210506203721486.png" alt="image-20210506203721486" style="zoom: 50%;" />



## 开始制作一个精灵

创建一个空文件

重命名为 Player

继续配置精灵动画

将准备好的精灵图片切割成一组独立的精灵图片

按住某一个, 再按 shift 连续转中多个图片

拖拽到Player上

并为该动画命名



> 将文件归类
>
> 动画文件放到动画文件夹中
>
> 动画控制器放到控制器文件夹中



---



## "捕捉设置"功能>>指定某规律来移动游戏对象



<img src="https://shimmerimg.oss-cn-beijing.aliyuncs.com/blog/screenshot/20210507172638.png" alt="image-20210507172638054" style="zoom:50%;" />

Snap Settings（对齐设置）：用户需要的对齐方式，工具需要进行设置

  Move X：设置游戏对象在XZ轴上移动的操作时的最小单位

  Move Y：设置游戏对象在Y轴上移动的操作时的最小单位

  Move Z：设置游戏对象在Z轴上移动的操作时的最小单位

  Scale：设置游戏对象进行缩放的百分比

  Rotation：设置游戏对象进行旋转操纵时的最小的角度



---

## Unity从资源商店导入资源

https://assetstore.unity.com/中找到需要的资源先收藏

window>package Manager>搜索>下载>导入

<img src="https://shimmerimg.oss-cn-beijing.aliyuncs.com/blog/screenshot/20210508164133.png" alt="image-20210508164133584" style="zoom:25%;" />

>  如果一直提示下载 Hub , 请重启电脑!  



  

## Unity  修改布局                                                                                                                                                                                                                                                                                                                                                                                                         

右上角 2 by 3

Project右上角右键选择一列显示*one column layout*



## 提示

.FBX 文件 美工的资源 

untiy package 是 Unity 包文件, 包含 unity 里的资源, 可以导入导出到 其他unity空间

<img src="https://shimmerimg.oss-cn-beijing.aliyuncs.com/blog/screenshot/20210521094109.png" alt="image-20210521094109305" style="zoom:25%;" />

拖拽导入资源到 Project 面板  

最好在U3d的 Project 文件夹中操作, 因为每一个资源 unity 都会生成并维护一个Meta文件

unity 大概 0.02 秒渲染一次页面(50fps, 1秒 50 次), 肉干感觉不出来, 看到的动画是连贯的, 不卡顿

别在模型上挂组件, 防止更换新模型组件需要删除设置组件值, 操作他的父物体



# Unity3d 界面

## Hierarchy 面板存放游戏对象

 

## Scene 面板 在界面中操作游戏对象

鼠标右键 + 拖动 = 视角旋转

鼠标滚轮 = 视角前进后退

按住鼠标滚轮 + 拖动 = 拖动

选中物体 + F 键 = 视角以物体居中

选中物体 + alt + 鼠标左键 + 拖动 = 视角围绕物体旋转

选中物体 + alt + 鼠标左键 = 视角以物体放大缩小

鼠标右键 + asdwqe = 实景漫游



场统一保存到 Scenes 文件夹中



## Game 面板 游戏运行后的界面

## Inspector 检视面板 检查检视选中的游戏对象

一行代表一个组件

一个组件一个功能

所有游戏物体都有 Transform 变化 存储位置\旋转\缩放比例

Inspector 面板中属性栏都可以进行简单的四则运算

### Transform 组件

Position x 横轴 y 纵轴 z 前后轴



## Scene 场景面板

一个关卡就是一个场景

右上角坐标

ISO = 正交观察模式 , 固定视角的, 适合 2D 游戏

Persp = 透视观察模式, 近大远小, 适合 3D 游戏

右上角点击坐标图案下方文字切换 Iso/persp

视图视角: 向下左右前后

<img src="../../Library/Application Support/typora-user-images/image-20210521211843779.png" alt="image-20210521211843779" style="zoom:25%;" />



# 快捷操作

复制出新的游戏对象 = ctrl + D

顶点吸附 = 选择一个物体 + V + 鼠标选一个点 + 鼠标左键 + 移动到另一个物体边缘

视图切换: 

 按快捷键Ctrl+1切换到Scene视图。

按快捷键Ctrl+2切换到Game视图。

按快捷键Ctrl+3切换到Inspector视图。

按快捷键Ctrl+4切换到Hierarchy视图。

按快捷键Ctrl+5切换到Project视图。

按快捷键Ctrl+6切换到Animation视图。

按快捷键Ctrl+7切换到Profler视图。



# 材质Material

材质 = shader 的实例

Shader着色器:专门用来渲染3D图形的技术,可以使纹理以某种方式展现。实际就是一段嵌入到渲染管线中的程序,可以控制GPU运算图像效果的算法

Texture纹理:附加到物体表面的贴图



## 呈现模式rendering mode 有几个选项 



不透明 默认 = Opaque

透明 = Transparent

镂空 = Cutout + 修改阿尔法 A 透明度 

淡入淡出 = Fade + 修改阿尔法 A 透明度 



## Shader

标准的 shader 有 Meallic 功能



## 纹理、着色器与材质的关系

<img src="https://shimmerimg.oss-cn-beijing.aliyuncs.com/blog/screenshot/20210524102015.png" alt="image-20210524102015598" style="zoom: 33%;" />



# 摄像机 

## 天空盒SkyBox

游戏场景远处的背景图 环绕式

围绕整个场景的包装器,用于模拟天空的材质。

### 摄像机添加天空盒

相机设置 Clear Flags 属性为 SkyBox

相机添加组件 Skybox 并将材质拽入



### 光照窗口添加天空盒

window > rendering > lighting settings > skybox 中设置

可将天空色彩反射一些到场景中, 更加真实



## Culling Mash 选择遮罩

只显示已勾选的图层物体



## Projection 投射 

Perspective 透视 近大远小

Orthographic 正交 2d 游戏视角



## Viewport Rect视口矩形

标明这台相机视图将会在屏幕上绘制的屏幕坐标。

X:摄像机视图的开始水平位置。

Y摄像机视图的开始垂直位置。

W宽度摄像机输出在屏幕上的宽度。

H高度摄像机输出在屏幕上的高度。



## Depth 深度

相机在渲染顺序上的位置。具有较低深度的摄像机将在较高深度像机之前渲染。

主摄像机 0  上层摄像机 > 0 即可



## 摄像机视角快速定位

选择摄像机 + ctrl + shift + F



## 两个摄像机叠加 空白的地方不渲染

摄像机的clear Flags 设置成 Depth only仅深度





> Draw Calls 受到**顶点数 veits**和**三角面数 tris**的影响

> hierarachy 面板物体越多内存占用越大
>
> Ctrl + 7 唤出Unity资源分析器
>
> LOD 多细节层次 Levels of Detail
>
> LOD技术指根据物体模型的节点在显示环境中所处的位置和重要度,决定物体渲染的资源分配,降低非重要物体的面数和细节度,从而获得高效率的渲染运算。



# 光light

## GI 全局光照Global Illumination

能够计算直接光、间接光、环境光以及反射光的光照系统。

通过G算法可以使渲染出来的光照效果更为真实丰富。



Range范围:光从物体的中心发射的范围。仅适用于点光源和聚光灯。

Spot Angle聚光角度:灯光的聚光角度。只适用于聚光灯.

Color颜色:光线的颜色。

Intensity强度:光线的明亮程度。

Culling Mask 选择蔽层:选择照射的层Layer

>  想只照射某片区域可以设置光的可照射层



## 阴影 Shadows

光组件中有**阴影类型**选择 : 无\硬阴影\软阴影



> MeshRender 组件中可以选择**接收阴影 投射阴影**
>
> MeshRender 组件 Cast shadows属性 选择双面阴影Two sided



## 光源侦测组件Light Probes

让游戏运行后的动态物体感知到烘焙前的光并计算渲染



# 声音

Unity支持的音频文件格式:mp3 , ogg , wav, aif, mod , it, s3m, xm

### 声音分为2D, 3D两类

3D声音:有空间感,近大远小。

2D声音:适合背景音乐。



## 播放声音 Audio Source 音频源组件

属性

Audio Clip音频剪辑:需要播放的音频资源。

Mute静音:如果启用,播放音频没有声音。

Play On Awake唤醒播放:勾选后场景启动时自动播放。

Loop循环:循环播放音频。

Volume音量:音量大小

Pitch音调:通过改变音调值调节音频播放速度。1是正常播放。

Stereo Pan : 2D声音设置左右声道。

Spatial Blend : 2D与3D声音切换。



## 接收声音 Audio Listener 音频侦听器组件

默认和主摄像机在一起

 