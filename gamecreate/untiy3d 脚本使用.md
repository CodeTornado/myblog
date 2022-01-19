# Unity C#脚本

脚本类必须继承 MonoBehaviour

不要在脚本中写构造函数

不能在子线程中访问主线程成员



# MonoBehaviour常用函数

## Awake唤醒

当物体载入时立即调用1次;常用于在游戏开始前进行初始化,可以判断当满足某种条件执行此脚本this.enable=trueOnEnable当可用:

每当脚本对象启用时调用。

Start开始

物体载入且脚本对象启用时被调用1次。常用于数据或游戏逻辑初始化,执行时机晚于Awake.

Awake 和 start 简单的代替构造函数使用

## Update更新

脚本启用后,每次渲染场景时调用,频率与设备性能及渲染量有关。

将 Input.getButton()相关按钮放到 Update 里

## LatelUpdate,延迟更新

在Update函数被调用后执行,适用于跟随逻辑



## OnEnable

当对象已用并处于活动状态时调 此函数

## 输入事件

OnMouseEnter鼠标移入:

鼠标移入到当前Collider时调用。

OnMouseOver鼠标经过

鼠标经过当前Collider时调用。

OnMouseExit鼠标离开:

鼠标离开当前Collider时调用。

OnMouseDown鼠标按下:鼠标按下当前Collider时调用。

OnMouseUp鼠标抬起:

鼠标在当前Collider上抬起时调用。



---



# 对物体操作



**增C**

## 界面使用交互按钮,过时的

onGUI方法  (用于测试)

GUILayout.Button("Rotate")创建一个 Rotate 的按钮并且判断是否被按

GUILayout.RepeatButton("Rotate")创建一个 Rotate 的按钮并且判断是否被按,持续判断并执行,按住不撒手就每帧去做



## C创建 克隆原始物体并返回克隆物体

Object.Instantiate实例化

![image.png](http://47.116.9.227/img/blog/unity_script/1602634960023-a3a1b140-2c5c-49eb-957a-25f7da77c682.png)



## R销毁游戏对象

```
Destroy(xxx.gameObject);
```





## U修改调整物体位置

### 物体相对于世界坐标系原点的位置

```
this.transform.position
```

物体相对于父物体轴心点的位置

```
this.transform.localPosition
```

### 向自身坐标系z轴移动1米

```
this.transform.Translate(0, 0, 1);
```

向世界坐标系z轴移动1米

```
this.transform.Translate(0, 0, 1,Space.World);
```

### 围绕旋转

```
void Transform.RotateAround(Vector3 point, Vector3 axis, float angle)
```

Rotates the transform about axis passing through point in world coordinates by angle degrees.

以角度度为单位围绕通过世界坐标系中的点的轴旋转变换。



把以下代码绑定到要旋转的物体，具体要围绕x，y，z 哪个轴旋转就改相应的值即可。

```
transform.Rotate(new Vector3(0,1,0));  //绕y轴旋转
```



untiy会将旋转z值修改(unity旋转值是在[0,360)区间的，并没有所谓的负数，当你给他赋值负数角度时，会修改为360-负数的相反数，例如：-5度 会修改为360-5=355度)

https://blog.csdn.net/qq_39574690/article/details/89852108



### 通过物体的刚体调整位置

public Rigidbody2D rb;

![image.png](http://47.116.9.227/img/blog/unity_script/1604324028154-a0949b69-aa73-4e5e-83ca-624146719598.png)

//修改物体刚体的速度

```
rb.velocity = new Vector2(  希望移动的位置.x  ,  希望移动的位置 .y );
```

//乘上规定的 速度 乘上Time.fixedDeltaTime使移动更平滑

```
rb.velocity = new Vector2(inputHorizontal * speed * Time.fixedDeltaTime, rb.velocity.y);
```



#### 限制物体 位置xy/旋转z

![image.png](http://47.116.9.227/img/blog/unity_script/1604326162494-f37bb4f2-62e8-40ae-8ffa-85978b12c437.png)

### 通过 transform.localScale调整物体朝向

```
float facedircetion = Input.GetAxisRaw("Horizontal");
transform.localScale = new Vector3(facedircetion, 1, 1);
```



### 给物体施加普通力

1、先给物体添加刚体 

2、`transform.rigidbody.AddForce(0,0,1000); ` 一个简单例子让小球撞破墙





## D查找

### 查找最近的敌人

当前物体与敌人间距

```
float distance = Vector3.Distance(``物体``1``的位置``,``物体``2``的位置``)
```

### 遍历某个xxxx物体下边所有的子物体

```
foreach (Transform t in xxxx.gameobject. transform)
t.gameObject. GetComponent<Image>().enabled = false;
```



跳跃

## 按空格物体跳跃

```
if (Input.GetButtonDown("Jump"))
     {
       rb.velocity = new Vector2(rb.velocity.x, jumpforce * Time.fixedDeltaTime);
     }
```

**跳跃后坠落**

```
if (animator.GetBool("jumping"))
     {
       //下落
       if (rb.velocity.y < 0)
       {
         animator.SetBool("jumping", false);
         animator.SetBool("falling", true);
       }
     }
```



# 下蹲

通过改变BoxCollider2D碰撞体大小为之前一半实现,注意offset对撞机几何体的局部偏移。



```
private Rigidbody2D rb;
   private BoxCollider2D collider2D;
```



```
   private Vector2 colliderStandSize;
   private Vector2 colliderStandOffSet;
   private Vector2 colliderCrouchSize;
   private Vector2 colliderCrouchOffSet;
```





```
   void Start()
   {
     rb = GetComponent<Rigidbody2D>();
     collider2D = GetComponent<BoxCollider2D>();
```



```
     colliderStandSize = collider2D.size;
     colliderStandOffSet  = collider2D.offset;
     colliderCrouchSize = new Vector2(collider2D.size.x , collider2D.size.y / 2);
     colliderCrouchOffSet = new Vector2(collider2D.offset.x, collider2D.offset.y / 2);
```



```
   }
```



```
   private void FixedUpdate()
   {
     GroundMovementJump();
   }
```



```
   void GroundMovementJump()
   {
     if (Input.GetButton("Crouch"))
     {
       Crouch();
     }
     else if(isCrouch)
     {
       Stand();
     }
}
```



```
   void Crouch()
   {
     isCrouch = true;
     collider2D.size = colliderCrouchSize;
     collider2D.offset = colliderCrouchOffSet;
   }
```



```
   void Stand()
   {
     isCrouch = false;
     collider2D.size = colliderStandSize;
     collider2D.offset = colliderStandOffSet;
   }
```





# 移动

## 修改刚体 position 方式移动

2D 游戏俯视视角玩家移动

```
     movement.x = Input.GetAxisRaw("Horizontal");
     movement.y = Input.GetAxisRaw("Vertical");
     rb.MovePosition(rb.position + movement * speed * Time.deltaTime);
```





## 刚体添加力方式移动

![image.png](http://47.116.9.227/img/blog/unity_script/1606354579704-fddfbd20-f89c-4a58-b757-026c6031a0cd.png)

**第四个参数 指定添加力的方式**

**ForceMode**

Acceleration 加速

Force 力

Impulse 冲动

VelocityChange 速度变化



## 修改玩家朝向 

方向为即将移动的方向  使用四元数Qauternion类  朝向旋转方法改变朝向

瞬间转向某点

![image.png](http://47.116.9.227/img/blog/unity_script/1606453467150-8a1891cb-c5c8-4c58-8392-037afc3dfe9c.png)

**逐渐转动** 已自己设定转动速度逐渐转向目标点

![image.png](http://47.116.9.227/img/blog/unity_script/1606454347785-4413d0a2-ad2b-440b-8852-f57157231ac5.png)

细节 移动时朝着 45 度方向移动会减速移动

![image.png](http://47.116.9.227/img/blog/unity_script/1606455591480-3bf4fe7d-f3c1-49d7-9260-d1d042808c2f.png)





## 玩家朝向跟随鼠标移动

使用主摄像机记录玩家鼠标位置

鼠标位置 减去 玩家当前位置 

将计算后的目标位置 使用四元数类 lookRotation 方法 转换为四元数

修改玩家对象旋转角度 = V3.up (0,1,0) 沿着Y 轴转  *  [(玩家当前角度 -> 目标角度 ) 计算上旋转速度*时间缩放]的插值



![image.png](http://47.116.9.227/img/blog/unity_script/1606466156470-386d9ae4-b501-4ce8-ac5e-85f1aba3a938.png)

![image.png](http://47.116.9.227/img/blog/unity_script/1606466117827-febc9016-a753-40ff-bf80-199e095bdc71.png)





# 跑动

animation 窗口中增加 running float 变量

idel 动画和 run 动画通过 running 大于/小于 0.1 来切换

```
float inputHorizontal = Input.GetAxis("Horizontal");
animator.SetFloat("running", Mathf.Abs(inputHorizontal));
```





# 切换动画



2D 俯视视角游戏玩家角色切换动画



```
     if (movement != Vector2.zero)//保证Horizontal归0时，保留movment的值来切换idle动画的blend tree
     {
       anim.SetFloat("horizontal", movement.x);
       anim.SetFloat("vertical", movement.y);
     }
     anim.SetFloat("speed", movement.magnitude);//magnitude 也可以用 sqrMagnitude 具体
```



通过动画混合树来管理玩家角色动画

![image.png](http://47.116.9.227/img/blog/unity_script/1605748789333-418b28ec-b7fc-4814-a2c0-fefcee8cffd3.png)

![image.png](http://47.116.9.227/img/blog/unity_script/1605748733069-1f3fcb1c-cbd5-4982-8bea-1a170763da9e.png)



![image.png](http://47.116.9.227/img/blog/unity_script/1605748714219-c300f693-e81d-4522-9713-0b0f8e972ac5.png)



#  





# 定时执行

## 方法 1

任意声明一个方法Timerxxx();

**隔一段时间重复调用某方法**(被执行的方法名称,第一次执行时间,每次执行间隔）

```
InvokeRepeating("Timerxxx", 5, 1);
```

**取消某个方法的调用**

```
CancelInvoke("Timer");
**延迟一段时间执行**
Invoke(``被执行的方法，开始调用时间``);
```

## 方法 2

**创建一个定时器**

每0.5秒在鼠标位置弹出提示

![image.png](http://47.116.9.227/img/blog/unity_script/1604276149478-ed2a6c5c-cfdc-457e-a131-1fdef77c7276.png)





# 用户交互

## Unity3D鼠标、键盘的基本操作

### 键盘

GetKey       当通过名称指定的按键被用户按住时返回true

GetKeyDown  当用户按下指定名称的按键时的那一帧返回true。

GetKeyUp     在用户释放给定名字的按键的那一帧返回true。 

GetAxis(“Horizontal")和GetAxis(“Verical”) 用方向键或WASD键来  返回float类型变量1/-1 和 0

Input.GetAxisRaw("Vertical") == 1  获取整数 0 -1 1  返回由axisName标识的虚拟轴的值，不应用平滑过滤。

- Horizontal--卧式
- Vertical--垂直
- Fire--火
- Fire2
- Fire3
- Jump--跳
- Mouse X--鼠标X
- Mouse Y--鼠标Y
- Mouse ScrollWheel--鼠标滚动轮
- Horizontal--卧式
- Vertical--垂直
- Fire1--火
- Fire2
- Fire3
- Jump--跳
- Submit--提交
- Submit
- Cancel--取消



### 键盘判断  

```
If(Input.GetKeyDown(KeyCode.A)){//KeyCode表示包含键盘所有键   
print(“按下A键”); }  If(Input.GetKeyUp(KeyCode.D)){//当按D键松开时   
print(“松开D键”); }  If(Input.GetAxis(“Horizontal")){//当按下水平键时  
print(“按下水平键”); }  If(Input.GetKeyUp("Verical“)){当按下垂直键时   
print(“按下垂直键”); }  
```

### 鼠标  

GetButton      根据按钮名称返回true当对应的虚拟按钮被按住时。

GetButtonDown    在给定名称的虚拟按钮被按下的那一帧返回true。

GetButtonUp     在用户释放指定名称的虚拟按钮时返回true。  

### 鼠标判断 

```
if(Input.GetButton("Fire1")){//Fire1表示按下鼠标左键    
print(“按下鼠标左键”); }  if (Input.GetMouseButton(0)) {//0表示鼠标左键   
Debug.Log("按下鼠标左键"); }  if (Input.GetMouseButton(1)) {//1表示鼠标右键   
Debug.Log("按下鼠标右键");  }  if (Input.GetMouseButton(2)) {//2表示鼠标中键   
Debug.Log("按下鼠标中键"); } 
```

### 修改Unity用户交互输入按键

edit > Project Settings... > input Manage > Axes 点开下拉框

![image.png](http://47.116.9.227/img/blog/unity_script/1604321620671-3ef58e95-5a1f-4923-ab09-35e829ada8b0.png)





# 游戏中暂停 (砸瓦鲁多)

## Time.timeScale修改Unity时间缩放比例

Time.timeScale = 0可以暂停游戏，Time.timeScale = 1恢复正常，但这是作用于整个游戏的设置，不单单是当前场景，记得在需要的时候重置回Time.timeScale = 1。当然也可以使用Time.timeScale来做游戏的1倍、2倍整体加速

**timeScale影响的因素**

设置Time.timeScale = 0 将会暂停所有和帧率无关的事情。这些主要是指所有的物理事件和依赖时间的函数、刚体力和速度等，而且FixedUpdate会受到影响，会被暂停（不是Update）,即timeScale =0 时将不会调用FixedUpdate函数了。

但是，Update和LateUpdate函数本身的执行是不会受Time.timeScale的影响的。Update是依赖你的机器的，它的调用次数和你的机器渲染一样快慢（一些特殊情况除外）；性能高的机器，帧率高，Update函数执行次数也就多。因此，当使用Time.timeScale = 0时，所有和时间有关的事情都被暂停了。因为Time.timeScale为0时，Time.deltaTime将为0。这意味着，如果你使用**Time.deltaTime**来控制旋转和位移等，那么Time.timeScale = 0也将使这些物体停止运动。所以游戏看起来是被冻结了，但是，我们的游戏仍在渲染，也就是说Update函数仍在执行。

所以Update和LateUpdate这两个方法里面需要自己用代码控制，且可以设定某些地方不会暂停（比如UI动画），弊端是如果想暂停，所有动画相关都要与Time.deltaTime这个字段绑定。

不受时间缩放比例影响继续执行

Time.realtimeSinceStartup



获取游戏时间 Time.time (会被加速减速影响到)

获取游戏实际时间 Time.timeSinceLevelLoad

在 Update 里用 Time.deltaTime,在 FixedUpdate里用Time.fixedDeltaTime



# 父子物体关系

断绝全部父子对象关系

```
transform.DetachChildren();
```



Audio Lstener 听

Audio Source 音源

Audio Clips 声音片段





---

# 踩坑记录

物体代码逐渐透明修改失败

给材质换上透明着色器

(Legacy Shaders/Transparent/Diffuse)

![image.png](http://47.116.9.227/img/blog/unity_script/1606656727864-9dd33816-65bf-4d38-83e4-978d7cc9165e.png)

## 协成调用失败

![image.png](http://47.116.9.227/img/blog/unity_script/1606642648480-9a861ba4-9d47-46a5-bd98-f3b6fb3ab89a.png)

改成正确的IEnumerator



# 不懂的骚操作



??? 机会试验一下

![image.png](http://47.116.9.227/img/blog/unity_script/1606370661646-ad1ace6e-1d1b-427a-abd3-dc76f7308c0f.png)





## 画一条射线

摄像机从摄像机位置指向鼠标位置

```
Ray ray = cam.ScreenPointToRay(Input.mousePosition);
     Plane groundPlane = new Plane(Vector3.up, Vector3.zero);
     float rayDistance;
     if (groundPlane.Raycast(ray, out rayDistance))
     {
       Vector3 point = ray.GetPoint(rayDistance);
       Debug.DrawLine(ray.origin, point, Color.red);
       //controller.LookAt(point);
     }
```



#  







# [杂乱未整理的操场]



代码格式化 control + i

启动暂停 command + p

[unity监测按下键的键值并输出+unity键值](https://www.cnblogs.com/dsh20134584/p/7595797.html)

禁用启用物体 `gameObject.SetActive(true);`

切换加载其他场景对象不销毁`DontDestroyOnLoad(gameObject);`





## 使用事件调用封装方法

调用一个封装没有参数且不返回值的方法。

```
AAA类
public event System.Action OnDeath;
void xxxMethod(){
    if (OnDeath != null)
            {
                OnDeath();
            }
}

void xxxBBBMethod(){
    AAA类 aAA类Obj = Instantiate(AAA类) as AAA类;
    //声明封装该方法
    aAA类Obj.OnDeath += OnEnemyDeath;
}
void OnEnemyDeath()
 {
       xxxx
 }


//aAA类Obj  该对象若调用xxxMethod() ,OnDeath不为空则调用OnDeath封装方法
```



## 开枪脚本

![image.png](http://47.116.9.227/img/blog/unity_script/1606478826662-f1634fe5-4dff-4fa7-9946-b3deff4d6062.png)

![image.png](http://47.116.9.227/img/blog/unity_script/1606479048404-5a1ec1fa-d444-4eb3-811d-d73073870880.png)

![image.png](http://47.116.9.227/img/blog/unity_script/1606479121350-bcc210d5-3e16-4ce7-8609-d339c59077ef.png)



## 子弹壳脚本

落地逐渐透明后消失

![image.png](http://47.116.9.227/img/blog/unity_script/1606478932805-f81c97d5-aa88-4212-b187-0dabb70766dc.png)

##  

## 枚举用法

## ![image.png](http://47.116.9.227/img/blog/unity_script/1606469583179-3d928a30-cf70-44b3-b5ee-7dd206647acc.png)
![image.png](http://47.116.9.227/img/blog/unity_script/1606469614534-eb6a25cc-43f7-431c-a39f-bf3d209effc9.png)

## 鼠标右键后自动寻路到达

[YouTube教程](https://www.youtube.com/watch?v=CHV1ymlw-P8&list=PLPV2KyIb3jR5QFsefuO2RlAgWEz6EvVi6&index=26)

[Unity 官方教程](https://learn.unity.com/tutorial/unity-navmesh)

借助**NavMeshSurface 组件**、 AI 库的**NavMeshAgent**类、**摄像机类**点位置创建射线 和**射线类**实现

![image.png](http://47.116.9.227/img/blog/unity_script/1606381528142-65504c49-3cb9-44a9-bc0a-8c8afc75a93c.png)

去掉不需要图层

![image.png](http://47.116.9.227/img/blog/unity_script/1606381720473-e84c93d5-cc6a-491d-b023-60977a6266a9.png)



打开代理设置...调整相关参数

![image.png](http://47.116.9.227/img/blog/unity_script/1606381837353-26c419d4-9db1-41aa-9700-4608ae3ce145.png)
![image.png](http://47.116.9.227/img/blog/unity_script/1606381860169-8fed4bb8-148e-4a45-b645-286c942f3a32.png)

给地图墙上配置上NavMeshModifier组件 

忽略构建

覆盖区域

区域类型: 适宜步行,不可步行和跳跃



![image.png](http://47.116.9.227/img/blog/unity_script/1606381933318-bde10feb-6226-4b1f-b508-73e2b85cc5ac.png)

**给玩家添加 NavMeshAgent 代理**

![image.png](http://47.116.9.227/img/blog/unity_script/1606382255492-da6d9dc4-0d10-4e5f-adfc-6d37a4e094cb.png)

![image.png](http://47.116.9.227/img/blog/unity_script/1606381388795-1a9c04db-4a99-4417-bda5-7d0964e9d973.png)



如果地面中间有间隔 使用NavMeshLink组件连接两个 NavMeshSurface

![image.png](http://47.116.9.227/img/blog/unity_script/1606385462594-40b7f9c8-ff88-48ff-ac9a-671c7d4c135d.png)
![image.png](http://47.116.9.227/img/blog/unity_script/1606385515558-946acdf3-625f-444b-814e-0fd6081efb4e.png)





![image.png](http://47.116.9.227/img/blog/unity_script/1606370099209-f0f8f685-5b65-45e7-89b4-d3f27f622c3e.png)

属性上添加 Range 和指定范围, 在检查器已滚动条方式显示配置

![image.png](http://47.116.9.227/img/blog/unity_script/1606370190823-adabf188-08b5-4495-b477-30070b651e4c.png)

属性上添加 HideInInspector 在检查器中隐藏



 

[RequireComponent(typeof (CharacterController))]

RequireComponent属性自动将所需的组件添加为依赖项。





## 技能 CD图标

将 Image 设置为 Filled 类型, 调整 Fill Amount属性, 实现类似技能 CD 转动效果

![image.png](http://47.116.9.227/img/blog/unity_script/1606090873065-3c01f856-06b2-4825-9306-94e5fa888d03.png)

技能 CD 调整 Fill Amount 属性代码示例

![image.png](http://47.116.9.227/img/blog/unity_script/1606091352384-c559455c-3d5e-4cf0-9bdb-7ae1ffa03f74.png)

##  

## 退出游戏

```
Application.Quit();
```

## 两点之间画一条线

物体上绑定Line Renderer组件

通过两个 Position 设置线的起始和结束位置

再脚本中修改它们

![image.png](http://47.116.9.227/img/blog/unity_script/1606043375256-5ac3c8b2-23e4-487b-9f9c-64d69bc1661f.png)

```
using UnityEngine;

public class SpikedBallLineRender : MonoBehaviour
{
    public Transform startTransform;
    public Transform endTransform;
    LineRenderer lineRenderObj;

    private void Start()
    {
        lineRenderObj = GetComponent<LineRenderer>();
    }
    // Update is called once per frame
    void Update()
    {
        lineRenderObj.SetPosition(0, startTransform.position);
        lineRenderObj.SetPosition(1, endTransform.position);
    }
}
```



## 脚本拽到物体上报错/物体上脚本自动消失

类名和文件名不一致导致

![image.png](http://47.116.9.227/img/blog/unity_script/1605957887933-8b303492-cc85-40e8-beac-85c4b488f780.png)



## 拖拽物品跟随鼠标

鼠标点击可实现拖拽效果的库(事件管理库using UnityEngine.EventSystems;)



继承三个接口类并实现 IBeginDragHandler, IDragHandler, IEndDragHandler

分别是拖拽前\中\后

给该物体绑定 Canvas Group 组件, 可以配置鼠标射线参数

![image.png](http://47.116.9.227/img/blog/unity_script/1605928248465-d57d297e-8820-4fa6-8fc3-7ce7cb321080.png)

```
using System.Collections;
using System.Collections.Generic;
using UnityEngine;
using UnityEngine.EventSystems;

public class ItemOnDrag : MonoBehaviour, IBeginDragHandler, IDragHandler, IEndDragHandler
{
    Transform originalParent;
    Vector3 originalPosition;

    public void OnBeginDrag(PointerEventData eventData)
    {
        originalParent = transform.parent;
        originalPosition = transform.position;

        //使图片浮到最顶层
        transform.SetParent(transform.parent.parent);
        transform.position = eventData.position;
        //防止跟随鼠标的物体遮挡射线
        GetComponent<CanvasGroup>().blocksRaycasts = false;
    }

    public void OnDrag(PointerEventData eventData)
    {
        transform.position = eventData.position;
        //Debug.Log(eventData.pointerCurrentRaycast.gameObject.name);
    }

    public void OnEndDrag(PointerEventData eventData)
    {
        bool isMoveItem = false;
        GameObject touchGameObject = eventData.pointerCurrentRaycast.gameObject;
        if (touchGameObject != null)
        {
            string touchObjName = touchGameObject.name;
            if (touchObjName != null)
            {
                if (touchGameObject.name == "Item Image")
                {
                    transform.SetParent(touchGameObject.transform.parent.parent);
                    transform.position = touchGameObject.transform.parent.parent.position;
                    touchGameObject.transform.parent.position = originalParent.position;
                    touchGameObject.transform.parent.SetParent(originalParent);
                    isMoveItem = true;
                }
                else if (touchObjName.Contains("slot"))
                {
                    transform.SetParent(touchGameObject.transform);
                    transform.position = touchGameObject.transform.position;
                    isMoveItem = true;
                }

            }
        }

        if (!isMoveItem)
        {
            transform.position = originalPosition;
            transform.SetParent(originalParent);
        }
        GetComponent<CanvasGroup>().blocksRaycasts = true;
    }
}
```



## 鼠标拖拽画布移动



IDragHandler  事件管理库中>拖动处理程序 接口

```
using UnityEngine;
using UnityEngine.EventSystems;

public class MoveBag : MonoBehaviour, IDragHandler
{
    public Canvas canvas;
    //该类型取决于要移动物体上 Transform 编辑界面显示类型
    RectTransform currentRect;

    public void OnDrag(PointerEventData eventData)
    {
        //管理的锚点坐标  += 鼠标移动位置的偏移量
        currentRect.anchoredPosition += eventData.delta;
    }

    private void Awake()
    {
        currentRect = GetComponent<RectTransform>();
    }
}
```

## 存档/读档



\- 运用 File 和 FileStream 创建和打开文件 

\- JsonUtility 用法 

\- BinaryFormatter 二进制转换方法 

\- 序列化和反序列化



```
using System.Collections;
using System.Collections.Generic;
using System.IO;
using System.Runtime.Serialization.Formatters.Binary;
using UnityEngine;

public class GameSaveManager : MonoBehaviour
{
    string gameArchiveFolderName;
    string gameArchivePathAndFileName;
    
    public Inventory MyInventory;

    private void Awake()
    {
        string gameWorkDataPath = Application.persistentDataPath;
        Debug.Log(gameWorkDataPath);
        gameArchiveFolderName = gameWorkDataPath + "/game_archive";
        gameArchivePathAndFileName = gameArchiveFolderName + "/inventory.txt";

    }
    public void SaveGame()
    {
        if (!Directory.Exists(gameArchiveFolderName))
        {
            Directory.CreateDirectory(gameArchiveFolderName);
        }

        BinaryFormatter bf = new BinaryFormatter();
        FileStream fileStream = File.Create(gameArchivePathAndFileName);

        bf.Serialize(fileStream, JsonUtility.ToJson(MyInventory));

        fileStream.Close();
    }


    public void LoadGame()
    {
        BinaryFormatter bf = new BinaryFormatter();
        if (!Directory.Exists(gameArchivePathAndFileName))
        {
            FileStream fileStream = File.Open(gameArchivePathAndFileName, FileMode.Open);
            JsonUtility.FromJsonOverwrite((string)bf.Deserialize(fileStream), MyInventory);
            

            fileStream.Close();
        }
    }
}
```



## ScriptableObject脚本对象类

不需要挂在物体上就可以使用, ScriptableObject 是一个可独立于类实例来保存大量数据的数据容器。ScriptableObject 的一个主要用例是通过避免重复值来减少项目的内存使用量。如果项目有一个[预制件](https://docs.unity.cn/cn/2020.1/Manual/Prefabs.html)在附加的 MonoBehaviour 脚本中存储不变的数据，这将非常有用。

ScriptableObject可以通过邮件菜单创建的自定义资源, 该资源类型属于刚定义的类

通过ScriptableObject创建的自定义资源, **编辑器中**任何时候修改的数据会持久化存储在电脑中,注意游戏打包后没有持久存储的效果,每次打开游戏相关资源会重置



ScriptableObjects 的主要用例为：

在 Editor 会话期间保存和存储数据

将数据保存为项目中的资源，以便在运行时使用



```
ScriptableObject:
    Item 基础资源数据, 游戏中修改该资源会持久保存
    Inventory 作为 Item 的容器   单例, 游戏唯一
MonoBehaviour:
    ItemOnWorld
    Slot 预制件
    InventoryManager
每个装备物体挂上ItemOnWorld脚本,脚本中指定 Item,玩家触碰装备后自动添加到持久化资源Inventory的属性中 
Slot类挂在预制件上 > 里头有 Item 属性
启用背包时将Inventory中 Item对象列表通过 Slot预制件,逐个绑定到到游戏中并显示
```



```
[CreateAssetMenu(fileName = "New Item", menuName = "Inventory/New Item")]
public class Item : ScriptableObject
{
    public string itemName;
    public Sprite itemImage;
    public int itemHeld = 1;
    [TextArea]
    public string itemInfo;
    public bool equip;
}
[CreateAssetMenu(fileName = "New Inventory", menuName = "Inventory/New Inventory")]
public class Inventory : ScriptableObject
{
    public List<Item> itemList = new List<Item>();
}
```


//

```
public class Slot : MonoBehaviour
{
    public Item slotItem;
    public Image slotImage;
    public Text slotNum;
    public void ItemOnclicked()
    {
        InventoryManager.UpdateItemInfo(slotItem.itemInfo);
    }
}
```


/

```
public class ItemOnWorld : MonoBehaviour
{
    public Item thisItem;
    public Inventory playerInventory;
    private void OnTriggerEnter2D(Collider2D collision)
    {
        if (collision.gameObject.CompareTag("Player"))
        {
            AddNewItem();
            Destroy(gameObject);
        }
    }
    public void AddNewItem()
    {
        if (!playerInventory.itemList.Contains(thisItem))
        {
            playerInventory.itemList.Add(thisItem);
            //InventoryManager.CreateNewItem(thisItem);
           
        }
        else
        {
            thisItem.itemHeld++;
        }
        InventoryManager.RefreshItem();
    }
}
using UnityEngine.UI;
public class InventoryManager : MonoBehaviour
{
    static InventoryManager instance;
    public Inventory myBag;
    public GameObject slotGrid;
    public Slot slotPrefab;
    public Text itemInfromation;
    private void Awake()
    {
        if (instance != null)
            Destroy(this);
        instance = this;
    }
    public void OnEnable()
    {
        RefreshItem();
        instance.itemInfromation.text = "";
    }
    public static void UpdateItemInfo(string itemDescription)
    {
        instance.itemInfromation.text = itemDescription;
    }
    public static void CreateNewItem(Item item)
    {
        Slot newItem = Instantiate(instance.slotPrefab, instance.slotGrid.transform.position, Quaternion.identity);
        newItem.gameObject.transform.SetParent(instance.slotGrid.transform);
        newItem.slotItem = item;
        newItem.slotImage.sprite = item.itemImage;
        newItem.slotNum.text = item.itemHeld.ToString();
    }
    public static void RefreshItem()
    {
        for (int i = 0; i < instance.slotGrid.transform.childCount; i++)
        {
            Destroy(instance.slotGrid.transform.GetChild(i).gameObject);
        }
        for (int i = 0; i < instance.myBag.itemList.Count; i++)
        {
            CreateNewItem(instance.myBag.itemList[i]);
        }
    }
}
```







## 简单的单例

![image.png](http://47.116.9.227/img/blog/unity_script/1605611221556-1c94ccf2-fa7d-4eba-84d5-be928fa86303.png)

## 获取动画参数的整数哈希值

这样比将字符串传递给动画师更有效



```
 int hangingParamID;  //ID of the isHanging parameter
int groundParamID;  //ID of the isOnGround parameter
int crouchParamID;  //ID of the isCrouching parameter
int speedParamID;  //ID of the speed parameter
int fallParamID;  //ID of the verticalVelocity parameter
```





```
void Start()
{
  //Get the integer hashes of the parameters. This is much more efficient
  //than passing strings into the animator
  hangingParamID = Animator.StringToHash("isHanging");
  groundParamID = Animator.StringToHash("isOnGround");
  crouchParamID = Animator.StringToHash("isCrouching");
  speedParamID = Animator.StringToHash("speed");
  fallParamID = Animator.StringToHash("verticalVelocity");
}
```



```
 void Update()
  {
  //Update the Animator with the appropriate values
  anim.SetBool(hangingParamID, movement.isHanging);
  anim.SetBool(groundParamID, movement.isOnGround);
  anim.SetBool(crouchParamID, movement.isCrouching);
  anim.SetFloat(fallParamID, rigidBody.velocity.y);
```



```
  //Use the absolute value of speed so that we only pass in positive numbers
  anim.SetFloat(speedParamID, Mathf.Abs(input.horizontal));
  }
```



## 游戏编辑界面字段提示

```
[Header ("``移动参数``")]
public float speed =8f;
```



## 手机摇杆JOYSTICK PACK插件

```
float inputHorizontal = fixedJoystick.Horizontal;
float inputVertical = fixedJoystick.Vertical;
//左右移动
rb.velocity = new Vector2(inputHorizontal * speed * Time.deltaTime, rb.velocity.y);
     animator.SetFloat("running", Mathf.Abs(inputHorizontal));
//趴下
     else if (inputVertical < -0.5f && IsHitGround())
       {
       animator.SetBool("crouch", true);
       gameObject.GetComponent<BoxCollider2D>().enabled = false;
     }
```



## 射线RaycastHit2D

[`Physics2D`](https://www.yuque.com/guocheng-x3uab/qofn3o/Physics2D.html)`.Raycast`

向场景中的对撞机投射光线。

从概念上讲，射线*广播*就像是沿特定方向从空间中的某个点发射的激光束。可以检测并报告与光束接触的任何物体。

此函数返回一个RaycastHit对象，该对象具有对被射线击中的碰撞器的引用（如果没有被击中，结果的collider属性将为NULL）。的*layerMask*可用于检测选择性地仅在某些层的对象



```
//玩家的位置
     Vector2 pos = transform.position;
     //脚与玩家的相对位置
     Vector2 offset = new Vector2(-footOffset, 0f);
```



```
     //绘制2D射线广播命中,判断玩家的脚是否接触地面
     RaycastHit2D leftCheck = Physics2D.Raycast(pos + offset, Vector2.down, groundDistance, groundLayer);
     //将相同参数的射线绘制到游戏界面中
     Debug.DrawRay(pos + offset, Vector2.down, Color.red, 0.2f);
```



```
     //赋值判断射线触到地面层结果
     isOnGround = leftCheck;
```

![image.png](http://47.116.9.227/img/blog/unity_script/1605313994375-606b7d8e-f14a-4b52-b702-9688e63a6c5e.png)



将使用方法抽取成函数方便下次使用

```
   //射线广播
   RaycastHit2D Raycast(Vector2 offset, Vector2 rayDiraction, float length, LayerMask layer)
   {
     Vector2 pos = transform.position;
     Vector2 start = pos + offset;
     Debug.DrawRay(start, rayDiraction * length);
     return Physics2D.Raycast(start, rayDiraction, length, layer);
   }
```

## 悬挂墙边上跳

```
 if (isHanging)
     {
       if (jumpPressed)
       {
         rb.bodyType = RigidbodyType2D.Dynamic;
         rb.velocity = new Vector2(rb.velocity.x, hangingJumpForce);
         isHanging = false;
       }
       if (crouchPressed)
       {
         rb.bodyType = RigidbodyType2D.Dynamic;
         isHanging = false;
       }
     }
```

## 使用 2D 光效

安装插件 > Lightweight RP

![image.png](http://47.116.9.227/img/blog/unity_script/1604922053150-6ca08c8b-833c-4ac6-8dfe-637b2d4bd0c8.png)

物体材质更换成Default-Diffuse

打上点光源 > 调整 光强度\光范围和范围

## 视觉差 Parallax

通过各种层的不同移动速度来实现

```
using UnityEngine;
using System.Collections;
```



```
public class Parallax : MonoBehaviour
{
   public Transform videoCameraTransfrom;
   public float moveSpeed = 0.1f;
   private float startPositionX, startPositionY;
   public bool fixedY;
```



```
   void Start()
   {
     startPositionX = transform.localPosition.x;
     startPositionY = transform.localPosition.y;
   }
```



```
   void Update()
   {
     if (fixedY)
     {
       transform.localPosition = new Vector2(startPositionX + videoCameraTransfrom.localPosition.x * moveSpeed, transform.localPosition.y);
     }
     else
     {
       transform.localPosition = new Vector2(startPositionX + videoCameraTransfrom.localPosition.x * moveSpeed, startPositionY + videoCameraTransfrom.localPosition.y * moveSpeed);
     }
   }
}
```





## 使用"#FFFFFF"方式选择颜色 

```
Color ``xxxvarname;
ColorUtility.TryParseHtmlString("#FFFFFF", out xxxvarname);
```

## 切换并加载其他场景



```
using UnityEngine.SceneManagement;
SceneManager. LoadScene(0);
```



## 重新加载当前场景

```
 SceneManager.LoadScene(SceneManager.GetActiveScene().name);
```





## 3D 场景中 相机跟随脚本

玩家朝向改变或者翻滚后摄像机位置不会改变

![image.png](http://47.116.9.227/img/blog/unity_script/1606352662778-6aa65722-7cd8-471c-9589-c255e301fc15.png)

![image.png](http://47.116.9.227/img/blog/unity_script/1606352701680-724bb476-9aaa-410d-94f9-b95f4c671584.png)

## 3D 场景中 相机延迟跟随玩家

![image.png](http://47.116.9.227/img/blog/unity_script/1606456268067-69fe99ed-4b91-402e-9d8a-434a01390561.png)

---





