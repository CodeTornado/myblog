# CSS



## css 修改文本样式

### 文字粗细

CSS使用font-weight设置字体的粗细

- normal 默认值（不加粗）400
- bold 定义粗体（加粗）700
- 100-900 注意不跟单位
- 让加粗的文字不加粗，如标题，则改为normal

### 字体样式

CSS使用font-style属性设置文本的风格

- normal 默认值，浏览器会显示标准的字体样式
- italic 浏览器显示斜体的字体样式
- **平时我们很少给文字加斜体，反而要给斜体标签（em,i)改为不倾斜的字体。**

### 字体复合属性

属性font，不可以更换属性值的顺序，其中字体大小和 字体 必须同时出现
font: font-style(可省略) font-weight（可省略） font-size（不可省略）/line-height（可省略） font-family（不可省略）

<img src="https://shimmerimg.oss-cn-beijing.aliyuncs.com/blog/screenshot/20210305142609.png" alt="示例" style="zoom:50%;" />

### color 文本颜色

text-align 文本对齐

text-indent 文本缩进

text-decoration 文本下划线

ine-height 行高



### Css 文本属性

![image-20210305142859405](https://shimmerimg.oss-cn-beijing.aliyuncs.com/blog/screenshot/20210305142859.png)

## Css 单位 em\rem

**em**

em是相对长度单位。相对于当前对象内文本的字体尺寸（参考物是父元素的font-size）

如当前父元素的字体尺寸未设置，则相对于浏览器的默认字体尺寸

特点：

  　　1. em的值并不是固定的；

    　　2. em会继承父级元素的字体大小

 

**rem**

rem是CSS3新增的一个相对单位，rem是相对于HTML根元素的字体大小（font-size）来计算的长度单位

如果你没有设置html的字体大小，就会以浏览器默认字体大小，一般是16px

```
html{font-size: 62.5%}  /* 10 ÷ 16 × 100% = 62.5% */

body{font-size: 1.4rem;} /* 1.4 × 10px = 14px */

/*在根元素中定义了一个基本字体大小为62.5%（也就是10px。设置这个值主要方便计算，如果没有设置，将是以“16px”为基准 ）*/
```

优点是，只需要设置根目录的大小就可以把整个页面的成比例的调好

rem兼容性：除了IE8及更早版本外，所有浏览器均已支持rem

em与rem的区别：

　　rem是相对于根元素（html）的字体大小，而em是相对于其父元素的字体大小

两者使用规则：

- 如果这个属性根据它的font-size进行测量，则使用em``
- 其他的一切事物属性均使用rem



## CSS的复合选择器

复合选择器建立在基础选择器之上，对基本选择器进行组合形成的。
常用的复合选择器包括：后代选择器、子元素选择器、并集选择器、链接伪类选择器、focus伪类选择器。



## CSS的元素显示模式

定义：元素（标签）以什么方式进行显示，比如< div>自己占一行，一行可以放多个< span>
HTML元素一般分为**块元素**和**行内元素**两种类型, 但还有特殊的**行内块元素**

### 元素显示模式的转换

转为块元素：dispaly:block;(转换常常转为块元素，因为要改变其高度和宽度）
转为行内元素：dispaly:inline;
转为块元素：dispaly:inline-block;



## 链接伪类选择器

### 为`a`链接标签添加特殊的效果。

最大的特点是用冒号`：` 表示
` a:link` 选择所有未被访问的链接
`a:visited` 选择所有被访问过的链接
`a:hover` 选择鼠标经过的链接
`a:active `选择鼠标点了但链接还没有弹出来的链接
顺序不能变！
a链接标签是不能用Body这种标签一起改样式的
一般来说并不需要所有的链接样式（一般就用到`a:hover`)，可以先给标签`a`指定样式，再用`a:hover `

### focus伪类选择器

**focus伪类选择器**用于选取**获得焦点**（光标）的**表单元素**。



## 单行文字垂直居中的图解

使文字的line-height=盒子的高度

简单理解:行高的上空隙和下空隙把文字挤到中间了,是如果行高小于盒子高度,文字会偏上如果行高大于盒子高度,则文字偏下 

<img src="https://shimmerimg.oss-cn-beijing.aliyuncs.com/blog/screenshot/20210305145710.png" alt="image-20210305145710652" style="zoom:25%;" />





## CSS的背景

通过背景属性给页面元素添加背景样式。
背景颜色、背景图片、背景平铺、背景图片位置、背景图像固定等…
![在这里插入图片描述](https://shimmerimg.oss-cn-beijing.aliyuncs.com/blog/screenshot/20210305145853.png)

### 背景颜色color

- 默认为：transparent 透明的 

- url 图片路径

### 背景平铺repeat

- repeat:背景图像在纵向和横向上平铺
- no-repeat : 背景图像不平铺
- repeat-x: 背景图像在横向上平铺
- repeat-y: 背景图像在纵向平铺



### **背景图片位置**position

参数x,y代表坐标可以用方位名词或精神单位。

- 如果两个参数都是方位名词
  - **left top和top left一样，right center 和center right也是一个道理（因为right肯定是x轴的参数）**
  - 如果省略其中一个参数则默认居中
- 参数是精确单位
  - 如果参数值是精确单位，则顺序为x y
  - 如果只指定一个值则另一个一定是y居中
- 参数是混合单位
  - 则顺序肯定是xy



### 背景图像固定（背景附着）attachment

- 默认为scroll / 固定为fixed



### 背景复合写法

习惯性约定：color image repeat attachment position(没有强执行要求）

background:背景颜色  背景图片地址 背景平铺  背景图像滚动  背景图片位置;

![image-20210305175044171](https://shimmerimg.oss-cn-beijing.aliyuncs.com/blog/screenshot/20210305175044.png)





## 颜色

## RGB

rgb 是red green blue三原色的缩写

6 位 16 进制表示, 从 00 00 00 到 FF FF FF

每两段代表一个颜色

也可用 10 进制表示, 从 0 . 0. 0 - 255. 255. 255

也直接使用可用颜色单词

```css 
FFFFFF 白色 white 255.255.255

000000 黑色 black 0.0.0

FF000  红色 255.0.0 red

00FF00 绿色 0.255.0 green

0000FF 蓝色 0.0.255 blue

CCCCCC 灰色
```

> 颜色简写:	 FF FF FF = FFF		33 33 00 = 330



### RGBA

在 rgb 基础上加一个alpha 不透明度参数

 值范围 (0~1) 

 0 是完全透明 

1 是不透明

> rgba 是css3中提供的, IE9 +版本浏览器才支持



## CSS三大特性

### 层叠性

相同选择器给设置同样的样式时，一个样式会覆盖（层叠）另一个冲突的样式。

当样式冲突，遵循就近原则，即那个样式离结构近，就执行哪个样式；
样式不冲突不会层叠。

### 继承性

子元素可以继承父元素的样式（text- font- line-(height ) color）但是高度、盒子模型等都不可继承

龙生龙，凤生凤，老鼠的孩子会打洞。

### CSS优先级

同一个元素指定多个选择器，则会有优先级产生。
**选择器相同，执行层叠性。
选择器不同，根据选择器权重进行。**
优先级由若到强向下，注意权重数值。比较从左往右比较数值大小，权重叠加时永远只有叠加没有进位。

<img src="https://shimmerimg.oss-cn-beijing.aliyuncs.com/blog/screenshot/20210305152135.png" alt="在这里插入图片描述" style="zoom: 67%;" />

> 权重以四组为一个单位, 权重会叠加但权重不会进位
>
> 选定范围越精确权重值越大





## 盒子模型

### 盒子模型的组成（Box Model)

boder边框 content内容 padding内边距 margin外边距

![在这里插入图片描述](https://shimmerimg.oss-cn-beijing.aliyuncs.com/blog/screenshot/20210306202317.png)

### 边框

![在这里插入图片描述](https://shimmerimg.oss-cn-beijing.aliyuncs.com/blog/screenshot/20210306202356.png)

**复合写法：** `border:1px solid red` 该复合写法规定没有顺序！

> 边框会影响盒子的实际大小, 需要减去边框长度

### 内边距复合写法: 

![在这里插入图片描述](https://shimmerimg.oss-cn-beijing.aliyuncs.com/blog/screenshot/20210306202624.png)

### 外边距（margin)

控制盒子与盒子之间的距离
margin-top margin-bottom…
此外也可以复合写margin: …px（和padding一样的~）

### 外边距的典型应用（块级盒子水平居中）

![在这里插入图片描述](https://shimmerimg.oss-cn-beijing.aliyuncs.com/blog/screenshot/20210306202819.png)



一般上下是0，左右auto。
注意，图片为典型的行内块元素，行内元素（行内块元素）在其父亲中添加text-align:center;即可水平居中对齐。



### 外边距合并

相邻块元素垂直外边距的合并
当上下两相邻块元素（兄弟关系）相遇时，如果上面的元素有margin-bottom，下面的有margin-top，则它们之间的垂直距离不是两者之和，而是取两个值中较大的一个，这种现象称为相邻块元素垂直外边距的合并。
解决：尽量只给一个盒子添加margin值。

![在这里插入图片描述](https://shimmerimg.oss-cn-beijing.aliyuncs.com/blog/screenshot/20210306202940.png)

### 嵌套块元素垂直外边距合并

对于嵌套关系（父子关系）的块元素，父元素有上边距同时子元素也有上边距，此时父元素会塌陷较大的外边距值。

![在这里插入图片描述](https://shimmerimg.oss-cn-beijing.aliyuncs.com/blog/screenshot/20210306202949.png) 

### 清除内外边距

网页元素很多都带有默认的内外边距且不同浏览器不一样，在布局前要先清除网页元素内外边距

![在这里插入图片描述](https://shimmerimg.oss-cn-beijing.aliyuncs.com/blog/screenshot/20210306203042.png)

> 去掉ul li前面的`·` `list-style:none;`



> 转自: https://blog.csdn.net/weixin_43200099/article/details/110574510



# 圆角边框

可以使盒子模型变圆角

border-radius:length;(圆的半径）

![在这里插入图片描述](https://img-blog.csdnimg.cn/20201203212848164.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MzIwMDA5OQ==,size_16,color_FFFFFF,t_70)
当length数值越大弧形越明显。

![在这里插入图片描述](https://shimmerimg.oss-cn-beijing.aliyuncs.com/blog/screenshot/20210311085443.png)

> 注意：top-left这种顺序不能打乱；如果只写两个数字，则左上右下为一对，剩余两个为一对

# 盒子阴影

![在这里插入图片描述](https://shimmerimg.oss-cn-beijing.aliyuncs.com/blog/screenshot/20210311085601.png)

![image-20210311090548966](https://shimmerimg.oss-cn-beijing.aliyuncs.com/blog/screenshot/20210311090549.png)

# 文字阴影

在CSS3中可以用 text-shadow设置阴影用于文字。写法和盒子阴影一样
![在这里插入图片描述](https://shimmerimg.oss-cn-beijing.aliyuncs.com/blog/screenshot/20210311090622.png)







# CSS浮动



## 传统网页布局的三种方式

网页布局的本质-用CSS来摆放盒子
css提供了三种传统（pc）布局方式：

### 标准流（普通流/文档流）

即标签按照规定好默认方式排列。（块、行内元素、行内块元素。。。）



![在这里插入图片描述](https://shimmerimg.oss-cn-beijing.aliyuncs.com/blog/screenshot/20210311090853.png)

#### **网页布局第一准则**

多个块级元素纵向排列找标准流，多个块级元素横向排列找浮动；

### 网页布局第二准则

先设置盒子的大小，再设置盒子的位置；**

#### 什么是浮动？

float属性用于创建浮动框，将其移到一边，直到左边缘或右边缘触及包含块或另一个浮动框的边缘。



#### 浮动特性

![在这里插入图片描述](https://shimmerimg.oss-cn-beijing.aliyuncs.com/blog/screenshot/20210311091248.png)

脱离标准普通流的控制（浮）移动到指定位置（动）（脱标）。
浮动的盒子不再保留原先的位置。

如果多个盒子都设置了浮动，则它们会按照属性值（左浮动/右浮动）一行内显示并且顶端对齐排列。

设置浮动后 div 位置会随着浏览器的大小变化

浮动元素具有行内块元素的特点！（浮动可以设置给任何元素）
首先行内元素本没有宽度和高度，但如果添加了浮动就有了；块级元素本来独占一行，但添加浮动以后就可以一行内有多个挨在一起（紧挨在一起中间没有缝隙）；如果块级盒子没有指定宽度，默认和父亲一样宽，但添加浮动以后，它的大小由内容的多少来决定（行内块元素的特点，即盒子是被内容撑起来的）

浮动元素通常和标准流父级搭配使用



### 一个元素浮动 兄弟元素也要浮动

一个盒子里面有多个子盒子,如果其中一个盒子浮动了,那么其他兄弟也应该浮动,以防止引起问题。

浮动的盒子只会影响浮动盒子后面的标准流不会影响前面的标准流.



### 清除浮动

如果都是标准流，不给父盒子设置高度，子盒子可以撑开父盒子；
如果子盒子是浮动的，父盒子会高度塌陷（浮动相当于不占有位置，飘起来了）
清除浮动以后，父亲就有了高度，也不会影响后面的标准流。

#### 每个浮动标签添加css样式

选择器`{clear:属性值;}`
属性值：left right both(同时清除左右两侧浮动的影响）
实际中我们只使用 clear:both;



#### 清除浮动的策略：闭合浮动；

闭合浮动即把浮动的影响限制在父元素中。



##### 隔墙法

就是在最后一个浮动的子元素后面添加一个额外标签添加清除浮动样式. 代码结构比较差难看, 写起来不方便, 不常用



##### 清除浮动–父级添加 overflow

给**父级**添加overflow属性，将其属性值设置为hidden、auto或scroll
缺点：无法显示溢出盒子（会把溢出的部分切掉）

![在这里插入图片描述](https://shimmerimg.oss-cn-beijing.aliyuncs.com/blog/screenshot/20210311093425.png)



##### 清除浮动–：after 伪元素法

相当于在大盒子内部后面插入一个盒子
![在这里插入图片描述](https://shimmerimg.oss-cn-beijing.aliyuncs.com/blog/screenshot/20210311093502.png)
在style里面写，然后让需要清除浮动的父盒子拥有clearfix这个属性。
![在这里插入图片描述](https://shimmerimg.oss-cn-beijing.aliyuncs.com/blog/screenshot/20210311093502.png)
![在这里插入图片描述](https://shimmerimg.oss-cn-beijing.aliyuncs.com/blog/screenshot/20210311093502.png)





##### 清除浮动–：双伪元素法

其实就是在盒子**前后都**插入盒子
![在这里插入图片描述](https://img-blog.csdnimg.cn/20201221173025160.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MzIwMDA5OQ==,size_16,color_FFFFFF,t_70)

![image-20210311093820859](https://shimmerimg.oss-cn-beijing.aliyuncs.com/blog/screenshot/20210311093820.png)



---

