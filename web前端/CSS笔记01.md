# 使用 css 样式

### 内部样式表

```html
<head>
  <style type="text/css">
  body {background-color: red}
  p {margin-left: 20px}
  </style>
</head>
```

### 外部样式表

```html
<html>

<head>
	<link rel="stylesheet" type="text/css" href="/html/csstest1.css" >
</head>

<body>
  <h1>我通过外部样式表进行格式化。</h1>
  <p>我也一样！</p>
</body>

</html>
```

### 内联样式

```html
<p style="color: red; margin-left: 20px">
	This is a paragraph
</p>
```

# css的注释

`/* */` 不可嵌套



# 一切皆是盒子

编写 CSS 时你会发现，你的工作好像是围绕着一个一个盒子展开的——设置尺寸、颜色、位置，等等。页面里大部分 HTML 元素都可以被看作若干层叠的盒子。

每个占据页面空间的块都有这样的属性：

- `padding`：即内边距，围绕着内容（比如段落）的空间。
- `border`：即边框，紧接着内边距的线。
- `margin`：即外边距，围绕元素外部的空间。

>  

# 图像居中

```css
img {
  // 图像原本是内联元素 改为块元素
  display: block;
  // 外边距改为 上下0 水平居中
  margin: 0 auto;
}
```



> body 是块元素
>
> Img 图片是**内联**元素，不具备块级元素的一些功能。所以为了使图像有外边距，我们必须使用 `display: block` 给予其块级行为。

# css 修改文本样式

## 文字粗细

CSS使用font-weight设置字体的粗细

- normal 默认值（不加粗）100 - 900  600是默认值，也可用词汇代替，例如：Medium、thin、black
- bold 定义粗体（加粗）700
- 100-900 注意不跟单位
- 让加粗的文字不加粗，如标题，则改为normal

## 字体样式

CSS使用font-style属性设置文本的风格

- normal 默认值，浏览器会显示标准的字体样式
- italic 浏览器显示斜体的字体样式
- **平时我们很少给文字加斜体，反而要给斜体标签（em,i)改为不倾斜的字体。**

## 字体复合属性

属性font，不可以更换属性值的顺序，其中字体大小和 字体 必须同时出现
font: font-style(可省略) font-weight（可省略） font-size（不可省略）/line-height（可省略） font-family（不可省略）

<img src="https://shimmerimg.oss-cn-beijing.aliyuncs.com/blog/screenshot/20210305142609.png" alt="示例" style="zoom:50%;" />

## Css 文本属性

![image-20210305142859405](https://shimmerimg.oss-cn-beijing.aliyuncs.com/blog/screenshot/20210305142859.png)

## 文字写方向

```css
writing-mode: horizontal-tb;; /*从水平顶到底 默认*/
writing-mode: vertical-lr; /*从垂直左到右*/
writing-mode: vertical-lr; /*从垂直左到右*/
```

## 首行缩进

```css
text-index: xxxpx;
```

## 行尾对其方式

```css
text-align-last: left;
```



## 下划线遮挡剔除

```css
text-decoration-skip-link: auto;
```

## 单行文字垂直居中的图解

使文字的line-height=盒子的高度

简单理解:行高的上空隙和下空隙把文字挤到中间了,是如果行高小于盒子高度,文字会偏上如果行高大于盒子高度,则文字偏下 

<img src="https://shimmerimg.oss-cn-beijing.aliyuncs.com/blog/screenshot/20210305145710.png" alt="image-20210305145710652" style="zoom:25%;" />



## 改变文字方向标签 dir

- `ltr`，表示*从左到右，用于从左到右*书写的语言（如英语）；
- `rtl`，这意味着*从右到左*，用于*从右到左*书写的语言（如阿拉伯语）；
- `auto`，这让用户代理决定。它使用基本算法解析元素内的字符，直到找到具有强方向性的字符，然后将该方向性应用于整个元素。



## css文字排列方向

`writing-mode`的三个值分别是：

- `horizontal-tb`: 块流向从上至下。对应的文本方向是横向的。
- `vertical-rl`: 块流向从右向左。对应的文本方向是纵向的。
- `vertical-lr`: 块流向从左向右。对应的文本方向是纵向的。

t 代表 top

b 代表 bottom

r 。。。

l 。。。

若修改文字排列方向，设定宽高的会有些问题，需要使用新的属性来调整宽度高度。

横向书写模式下，映射到`width`的属性被称作内联尺寸（[`inline-size`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/inline-size)）——内联维度的尺寸。而映射`height`的属性被称为块级尺寸（[`block-size`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/block-size)），这是块级维度的尺寸。

```css
.box {
  /* width: 150px; */
  inline-size: 150px;
  /* height: 400px; */
  block-size: 400px;
}

.horizontal {
  writing-mode: horizontal-tb;
}

.vertical {
  writing-mode: vertical-rl;
}
```

`margin-top`属性的映射是[`margin-block-start`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/margin-block-start)——总是指向块级维度开始处的边距。

`margin-bottom`属性的映射是`margin-block-end`

`margin-left`属性的映射是`margin-inline-start`

`margin-right`属性的映射是`margin-inline-end`

margin-block == margin-top + margin-bottom

margin-inline == margin-left + margin-right

（如`top`、`right`、`bottom`和`left`）。这些值同样拥有逻辑值映射（`block-start`、`inline-end`、`block-end`和`inline-start`）。

[`padding-left`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/padding-left)属性映射到 [`padding-inline-start`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/padding-inline-start)，这是应用到内联开始方向（这是该书写模式文本开始的地方）上的内边距。

[`border-bottom`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/border-bottom)属性映射到的是[`border-block-end`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/border-block-end)，也就是块级维度结尾处的边框。





## css 字体样式

- `font-style`

  : 用来打开和关闭文本 italic (斜体)。 可能的值如下 (你很少会用到这个属性，除非你因为一些理由想将斜体文字关闭斜体状态)：

  - `normal`: 将文本设置为普通字体 (将存在的斜体关闭)
  - `italic`: 如果当前字体的斜体版本可用，那么文本设置为斜体版本；如果不可用，那么会利用 oblique 状态来模拟 italics。
  - `oblique`: 将文本设置为斜体字体的模拟版本，也就是将普通文本倾斜的样式应用到文本中。

- `font-weight`

  : 设置文字的粗体大小。这里有很多值可选 (比如 

  -light

  -normal

  -bold

  -extrabold

  ,

   

  -black

  , 等等), 不过事实上你很少会用到 

  ```
  normal
  ```

   和 

  ```
  bold
  ```

  以外的值：

  - `normal`, `bold`: 普通或者**加粗**的字体粗细
  - `lighter`, `bolder`: 将当前元素的粗体设置为比其父元素粗体更细或更粗一步。`100`–`900`: 数值粗体值，如果需要，可提供比上述关键字更精细的粒度控制。

- `text-transform`

  : 允许你设置要转换的字体。值包括：

  - `none`: 防止任何转型。
  - `uppercase`: 将所有文本转为大写。
  - `lowercase`: 将所有文本转为小写。
  - `capitalize`: 转换所有单词让其首字母大写。
  - `full-width`: 将所有字形转换成全角，即固定宽度的正方形，类似于等宽字体，允许拉丁字符和亚洲语言字形（如中文，日文，韩文）对齐。

- `text-decoration`

  : 设置/取消字体上的文本装饰 (你将主要使用此方法在设置链接时取消设置链接上的默认下划线。) 可用值为：

  - `none`: 取消已经存在的任何文本装饰。
  - `underline`: 文本下划线.
  - `overline`: 文本上划线
  - `line-through`: 穿过文本的线 strikethrough over the text.



## css 去除下划线

`text-decoration-line: none;`



> 浏览器的 `font-size` 标准设置的值为 16px



# Css 单位 em\rem

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







# CSS的元素显示模式

定义：元素（标签）以什么方式进行显示，比如< div>自己占一行，一行可以放多个< span>
HTML元素一般分为**块元素**和**行内元素**两种类型, 但还有特殊的**行内块元素**

### 元素显示模式的转换

转为块元素：dispaly:block;(转换常常转为块元素，因为要改变其高度和宽度）
转为行内元素：dispaly:inline;
转为块元素：dispaly:inline-block;

# CSS的背景

通过背景属性给页面元素添加背景样式。
背景颜色、背景图片、背景平铺、背景图片位置、背景图像固定等…
![在这里插入图片描述](https://shimmerimg.oss-cn-beijing.aliyuncs.com/blog/screenshot/20210305145853.png)

## 背景颜色color

- 默认为：transparent 透明的 

- url 图片路径

## 背景平铺repeat

- repeat:背景图像在纵向和横向上平铺
- no-repeat : 背景图像不平铺
- repeat-x: 背景图像在横向上平铺
- repeat-y: 背景图像在纵向平铺



## **背景图片位置**position

参数x,y代表坐标可以用方位名词或精神单位。

- 如果两个参数都是方位名词
  - **left top和top left一样，right center 和center right也是一个道理（因为right肯定是x轴的参数）**
  - 如果省略其中一个参数则默认居中
- 参数是精确单位
  - 如果参数值是精确单位，则顺序为x y
  - 如果只指定一个值则另一个一定是y居中
- 参数是混合单位
  - 则顺序肯定是xy

```css
backgournd-position: center center;
backgournd-position: 100px 200px;
backgournd-position-x: 100px;
backgournd-position-y: 200px;
```

## 背景图像固定（背景附着）attachment

- 默认为scroll / 固定为fixed

`backgound-attachement: fixed;`

## backgound-size

```css
50% /* 宽度50% 高度 auto */
50% 50% /* 缩放为父容器 50%宽度 */
100% 100%/* 铺满父容器 */
```



## 背景复合写法

习惯性约定：color image repeat attachment position(没有强执行要求）

background:背景颜色  背景图片地址 背景平铺  背景图像滚动  背景图片位置;

![image-20210305175044171](https://shimmerimg.oss-cn-beijing.aliyuncs.com/blog/screenshot/20210305175044.png)

> 背景图片可以同时设置多个`backgournd: url(1), url(2)`url2 位于 url1 的底部



## backgound-origin

背景图片根据盒子模型哪个位置定位

Content-box, padding-box, border-box

## 背景渐变

```css
background: linear-gradient(aColor, bColor)
```

背景色的渐变默认从上到下渐变，会根据盒子宽高自动变化



<section style="display:flex;text-align: center;">
        <div
            style="display:inline-block;color:white; width: 200px; height: 100px;background: linear-gradient(green, blue)">
            defalut</div>
        <div
            style="display:inline-block;color:white; width: 200px; height: 100px;background: linear-gradient(to left,green, blue)">
            to left</div>
        <div
            style="display:inline-block;color:white; width: 200px; height: 100px;background: linear-gradient(to right, green, blue)">
            to right</div>
        <div
            style="display:inline-block;color:white; width: 200px; height: 100px;background: linear-gradient(to top left, green, blue)">
            to top left</div>
        <div
            style="display:inline-block; color:white;width: 200px; height: 100px;background: linear-gradient(to top right, green, blue)">
            to top right</div>
        <div
            style="display:inline-block;color:white;width: 200px; height: 100px;background: linear-gradient(to bottom left, green, blue)">
            to bottom left</div>
        <div
            style="display:inline-block; color:white;width: 200px; height: 100px;background: linear-gradient(to bottom right,green,  blue)">
            to bottom right</div>
       <div
  	        style="display:inline-block; color:white; width: 200px; height: 100px;background: linear-gradient(10deg, yellow, red)">
  	        10deg</div>
  	    <div
  	        style="display:inline-block; color:white; width: 200px; height: 100px;background: linear-gradient(20deg, yellow, red)">
  	        20deg</div>
  	    <div
  	        style="display:inline-block; color:white; width: 200px; height: 100px;background: linear-gradient(30deg, yellow, red)">
  	        30deg</div>
  	    <div
  	        style="display:inline-block; color:white; width: 200px; height: 100px;background: linear-gradient(40deg, yellow, red)">
  	        40deg</div>
  	    <div
  	        style="display:inline-block; color:white; width: 200px; height: 100px;background: linear-gradient(50deg, yellow, red)">
  	        50deg</div>
  	    <div
  	        style="display:inline-block; color:white; width: 200px; height: 100px;background: linear-gradient(60deg, yellow, red)">
  	        60deg</div>
  	    <div
  	        style="display:inline-block; color:white; width: 200px; height: 100px;background: linear-gradient(70deg, yellow, red)">
  	        70deg</div>
  	    <div
  	        style="display:inline-block; color:white; width: 200px; height: 100px;background: linear-gradient(80deg, yellow, red)">
  	        80deg</div>
  	    <div
  	        style="display:inline-block; color:white; width: 200px; height: 100px;background: linear-gradient(90deg, yellow, red)">
  	        90deg</div>
  	</section>



### 线性渐变

`background: Repeating-linear-gradient (white 100px, black 200px, white 300px)`

<div style="display: inline-box; height: 500px; width: 400px;background: repeating-linear-gradient(yellow 0px, black 200px ,green 500px)"></div>

### 径向渐变

`background: Repeating-radial-gradient(white 100px, black 200px, white 300px)`

<div style="display: inline-box; height: 500px; width: 400px; background: Repeating-radial-gradient(green 0px, gray 200px, blue 300px)"></div>

# 颜色

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



## RGBA

在 rgb 基础上加一个alpha 不透明度参数

 值范围 (0~1) 

 0 是完全透明 

1 是不透明

> rgba 是css3中提供的, IE9 +版本浏览器才支持

## hsl

**HSL**是一种将RGB色彩模型中的点在圆柱坐标系中的表示法。这两种表示法试图做到比基于[笛卡尔坐标系](https://baike.baidu.com/item/笛卡尔坐标系/4522878)的几何结构RGB更加直观。是运用最广的颜色系统之一。

中文名: 色相、饱和度、亮度

外文名: Hue, Saturation, Lightness，HSL



HSL即色相、饱和度、亮度（英语：Hue, Saturation, Lightness）。

色相（H）是色彩的基本属性，就是平常所说的颜色名称，如红色、黄色等。

饱和度（S）是指色彩的纯度，越高色彩越纯，低则逐渐变灰，取0-100%的数值。

明度（V），亮度（L），取0-100%。

| 值                    | 描述                                                         |
| :-------------------- | :----------------------------------------------------------- |
| *hue - 色相*          | 定义色相 (0 到 360) - 0 (或 360) 为红色, 120 为绿色, 240 为蓝色 |
| *saturation - 饱和度* | 定义饱和度; 0% 为灰色， 100% 全色                            |
| *lightness - 亮度*    | 定义亮度 0% 为暗, 50% 为普通, 100% 为白                      |



```css
#p1 {background-color:hsl(120,100%,50%);} /* 绿色 */
#p2 {background-color:hsl(120,100%,75%);} /* 浅绿  */
#p3 {background-color:hsl(120,100%,25%);} /* 暗绿  */
#p4 {background-color:hsl(120,60%,70%);} /* 柔和的绿色 */
```



# CSS三大特性

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





# css继承

一些设置在父元素上的css属性是可以被子元素继承的，有些则不能。

widths , margins, padding, 和 borders 不会被继承。如果borders可以被继承，每个列表和列表项都会获得一个边框 — 可能就不是我们想要的结果!

### 通过属性的值来控制继承

[`inherit`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/inherit)

设置该属性会使子元素属性和父元素相同。实际上，就是 "开启继承".

> 开启继承

[`initial`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/initial)

设置属性值和浏览器默认样式相同。如果浏览器默认样式中未设置且该属性是自然继承的，那么会设置为 `inherit` 。

> 与默认样式相同，若没有默认样式则自然继承

[`unset`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/unset)

将属性重置为自然值，也就是如果属性是自然继承那么就是 `inherit`，否则和 `initial`一样

> 自然继承，若没有使用默认样式

重置所有属性

```css
all: unset;
```



# 盒子模型

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



`margin` 属性为给定元素设置所有四个（上右下左）方向的外边距属性。也就是 [`margin-top`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/margin-top)，[`margin-right`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/margin-right)，[`margin-bottom`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/margin-bottom)，和 [`margin-left`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/margin-left) 四个外边距属性设置的[简写](https://developer.mozilla.org/zh-CN/docs/Web/CSS/Shorthand_properties)。

`margin` 1 2 3 4 = margin-top 1; margin-rignt: 2; margin-bottom:3; margin-left: 4

`margin` 1 2 3 = margin-top 1; margin-rignt: 2; margin-bottom:2; margin-left: 3

`margin` 1 2 = margin-top 1; margin-rignt: 2; margin-bottom:1; margin-left: 2

`margin` 1 = margin-top 1; margin-rignt: 1; margin-bottom:1; margin-left: 1

```css
/* 应用于所有边 */
margin: 1em;
margin: -3px;

/* 上边下边 | 左边右边 */
margin: 5% auto;

/* 上边 | 左边右边 | 下边 */
margin: 1em auto 2em;

/* 上边 | 右边 | 下边 | 左边 */
margin: 2px 1em 0 auto;

/* 全局值 */
margin: inherit;
margin: initial;
margin: unset;

margin: 2em auto;           /* 上边和下边：2em 的外边距 */
                            /* 水平方向居中            */

margin: auto;               /* 上边和下边：无外边距 */
                            /* 水平方向居中        */
```

>  Margin  值 auto：让浏览器自己选择一个合适的外边距。有时，在一些特殊情况下，该值可以使元素居中。





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

### css 让边框合并

 `border-collapse: collapse;` 





# 角边框

可以使盒子模型变圆角

border-radius:length;(圆的半径）

![在这里插入图片描述](https://img-blog.csdnimg.cn/20201203212848164.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MzIwMDA5OQ==,size_16,color_FFFFFF,t_70)
当length数值越大弧形越明显。

![在这里插入图片描述](https://shimmerimg.oss-cn-beijing.aliyuncs.com/blog/screenshot/20210311085443.png)

> 注意：top-left这种顺序不能打乱；如果只写两个数字，则左上右下为一对，剩余两个为一对



椭圆边框`border-radius: xpx ypx;`

# 盒子阴影

![在这里插入图片描述](https://shimmerimg.oss-cn-beijing.aliyuncs.com/blog/screenshot/20210311085601.png)

![image-20210311090548966](https://shimmerimg.oss-cn-beijing.aliyuncs.com/blog/screenshot/20210311090549.png)

# 文字阴影

在CSS3中可以用 text-shadow设置阴影用于文字。写法和盒子阴影一样
![在这里插入图片描述](https://shimmerimg.oss-cn-beijing.aliyuncs.com/blog/screenshot/20210311090622.png)

# 传统网页布局的三种方式

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



# css 变量

```css
/*定义变量*/
xxx {__变量名: value}```
/*使用变量*/
xxx { color: __变量名}
```



# 隐藏元素

```css
visibility: visible; /*默认 能看见*/
visibility: hidden;
```





# css选择器

## 混合使用

选中每个 `special` 类的 `li` 元素：

```css
li.special,
span.special {
  color: orange;
  font-weight: bold;
}

body h1 + p .special {
  color: yellow;
  background-color: black;
  padding: 5px;
}
```

## 包含选择器：

```css
li em {
  color: rebeccapurple;
}
```



## 相邻选择器，同级选择器：

```css
h1 + p {
  font-size: 200%;
}
```

## 状态选择器：

下面的CSS代码使得没有被访问的链接颜色变为粉色、访问过的链接变为绿色。

```css
a:link {
  color: pink;
}

a:visited {
  color: green;
}
```

## 标签属性选择器：

```css
a[href="https://example.com"] { }
```

伪类选择器：

这组选择器包含了伪类，用来样式化一个元素的特定状态。例如`:hover`伪类会在鼠标指针悬浮到一个元素上的时候选择这个元素：

```css
a:hover { }
```

## 伪元素选择器：

它还可以包含了伪元素，选择一个元素的某个部分而不是元素自己。例如，`::first-line`是会选择一个元素（下面的情况中是`<p>`）中的第一行，类似`<span>`包在了第一个被格式化的行外面，然后选择这个`<span>`。

```css
p::first-line { }
```

运算符？：

最后一组选择器可以将其他选择器组合起来，更复杂的选择元素。下面的示例用运算符（`>`）选择了`<article>`元素的初代子元素。

```css
article > p { }
```



## 全局选择器：

`* { xxx }`

全局选咋去用于避免混淆

```
article *:first-child {

} 
```

为了告诉浏览器我们只想匹配带有所有这些类的元素，我们可以将这些类不加空格地连成一串。

```css
.notebox.warning {
  border-color: orange;
  font-weight: bold;
}

.notebox.danger {
  border-color: red;
  font-weight: bold;
}
```

```html
<div class="notebox warning">
    This note shows a warning.
</div>

<div class="notebox danger">
    This note shows danger!
</div>
```

## 存否和值选择器:

这些选择器允许基于一个元素自身是否存在（例如`href`）或者基于各式不同的按属性值的匹配，来选取元素。

| 选择器              | 示例                            | 描述                                                         |
| :------------------ | :------------------------------ | :----------------------------------------------------------- |
| `[*attr*]`          | `a[title]`                      | 匹配带有一个名为*attr*的属性的元素——方括号里的值。           |
| `[*attr*=*value*]`  | `a[href="https://example.com"]` | 匹配带有一个名为*attr*的属性的元素，其值正为*value*——引号中的字符串。 |
| `[*attr*~=*value*]` | `p[class~="special"]`           | 匹配带有一个名为*attr*的属性的元素 ，其值正为*value*，或者匹配带有一个*attr*属性的元素，其值有一个或者更多，至少有一个和*value*匹配。注意，在一列中的好几个值，是用空格隔开的。 |
| `[*attr*|=*value*]` | `div[lang|="zh"]`               | 匹配带有一个名为*attr*的属性的元素，其值可正为*value*，或者开始为*value*，后面紧随着一个连字符。 |

## 子字符串匹配选择器:

这些选择器让更高级的属性的值的子字符串的匹配变得可行。例如，如果你有`box-warning`和`box-error`类，想把开头为“box-”字符串的每个物件都匹配上的话，你可以用`[class^="box-"]`来把它们两个都选中。

| 选择器              | 示例                | 描述                                                         |
| :------------------ | :------------------ | :----------------------------------------------------------- |
| `[*attr*^=*value*]` | `li[class^="box-"]` | 匹配带有一个名为*attr*的属性的元素，其值开头为*value*子字符串。 |
| `[*attr*$=*value*]` | `li[class$="-box"]` | 匹配带有一个名为*attr*的属性的元素，其值结尾为*value*子字符串 |
| `[*attr**=*value*]` | `li[class*="box"]`  | 匹配带有一个名为*attr*的属性的元素，其值的字符串中的任何地方，至少出现了一次*value*子字符串。 |

## 字字符串匹配，防止大小写敏感

如果你想在大小写不敏感的情况下，匹配属性值的话，你可以在闭合括号之前，使用`i`值。这个标记告诉浏览器，要以大小写不敏感的方式匹配ASCII字符。没有了这个标记的话，值会按照文档语言对大小写的处理方式，进行匹配——HTML中是大小写敏感的。

```css
li[class^="a" i] {
    color: red;
}
```

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



## focus伪类选择器

**focus伪类选择器**用于选取**获得焦点**（光标）的**表单元素**。

### 错误的选择器，一个失效整个都失效

```css
h1, ..special {
  color: blue;
} 
```



## 伪元素选择器

```css
.box::before {
    content: "";
    display: block;
    width: 100px;
    height: 100px;
    background-color: rebeccapurple;
    border: 1px solid black;
}   
```

`<p class="box">Content in the box in my HTML page.</p>`

<img src="https://shimmerimg.oss-cn-beijing.aliyuncs.com/blog/screenshot/20211006152305.png" alt="image-20211006152305677" style="zoom:25%;" />

| 选择器                                                       | 描述                                                         |
| :----------------------------------------------------------- | :----------------------------------------------------------- |
| [`:active`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/:active) | 在用户激活（例如点击）元素的时候匹配。                       |
| [`:any-link`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/:any-link) | 匹配一个链接的`:link`和`:visited`状态。                      |
| [`:blank`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/:blank) | 匹配空输入值的[``元素](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input)。 |
| [`:checked`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/:checked) | 匹配处于选中状态的单选或者复选框。                           |
| [`:current` (en-US)](https://developer.mozilla.org/en-US/docs/Web/CSS/:current) | 匹配正在展示的元素，或者其上级元素。                         |
| [`:default`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/:default) | 匹配一组相似的元素中默认的一个或者更多的UI元素。             |
| [`:dir`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/:dir) | 基于其方向性（HTML`dir`属性或者CSS`direction`属性的值）匹配一个元素。 |
| [`:disabled`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/:disabled) | 匹配处于关闭状态的用户界面元素                               |
| [`:empty`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/:empty) | 匹配除了可能存在的空格外，没有子元素的元素。                 |
| [`:enabled`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/:enabled) | 匹配处于开启状态的用户界面元素。                             |
| [`:first`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/:first) | 匹配[分页媒体](https://developer.mozilla.org/en-US/docs/Web/CSS/Paged_Media)的第一页。 |
| [`:first-child`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/:first-child) | 匹配兄弟元素中的第一个元素。                                 |
| [`:first-of-type`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/:first-of-type) | 匹配兄弟元素中第一个某种类型的元素。                         |
| [`:focus`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/:focus) | 当一个元素有焦点的时候匹配。                                 |
| [`:focus-visible`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/:focus-visible) | 当元素有焦点，且焦点对用户可见的时候匹配。                   |
| [`:focus-within`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/:focus-within) | 匹配有焦点的元素，以及子代元素有焦点的元素。                 |
| [`:future` (en-US)](https://developer.mozilla.org/en-US/docs/Web/CSS/:future) | 匹配当前元素之后的元素。                                     |
| [`:hover`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/:hover) | 当用户悬浮到一个元素之上的时候匹配。                         |
| [`:indeterminate`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/:indeterminate) | 匹配未定态值的UI元素，通常为[复选框](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input/checkbox)。 |
| [`:in-range`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/:in-range) | 用一个区间匹配元素，当值处于区间之内时匹配。                 |
| [`:invalid`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/:invalid) | 匹配诸如`<input>`的位于不可用状态的元素。                    |
| [`:lang`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/:lang) | 基于语言（HTML[lang](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Global_attributes/lang)属性的值）匹配元素。 |
| [`:last-child`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/:last-child) | 匹配兄弟元素中最末的那个元素。                               |
| [`:last-of-type`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/:last-of-type) | 匹配兄弟元素中最后一个某种类型的元素。                       |
| [`:left`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/:left) | 在[分页媒体 (en-US)](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Pages)中，匹配左手边的页。 |
| [`:link`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/:link) | 匹配未曾访问的链接。                                         |
| [`:local-link` (en-US)](https://developer.mozilla.org/en-US/docs/Web/CSS/:local-link) | 匹配指向和当前文档同一网站页面的链接。                       |
| [`:is()`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/:is) | 匹配传入的选择器列表中的任何选择器。                         |
| [`:not`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/:not) | 匹配作为值传入自身的选择器未匹配的物件。                     |
| [`:nth-child`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/:nth-child) | 匹配一列兄弟元素中的元素——兄弟元素按照an+b形式的式子进行匹配（比如2n+1匹配元素1、3、5、7等。即所有的奇数个）。 |
| [`:nth-of-type`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/:nth-of-type) | 匹配某种类型的一列兄弟元素（比如，`<p>`元素）——兄弟元素按照an+b形式的式子进行匹配（比如2n+1匹配元素1、3、5、7等。即所有的奇数个）。 |
| [`:nth-last-child`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/:nth-last-child) | 匹配一列兄弟元素，从后往前倒数。兄弟元素按照an+b形式的式子进行匹配（比如2n+1匹配按照顺序来的最后一个元素，然后往前两个，再往前两个，诸如此类。从后往前数的所有奇数个）。 |
| [`:nth-last-of-type`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/:nth-last-of-type) | 匹配某种类型的一列兄弟元素（比如，`<p>`元素），从后往前倒数。兄弟元素按照an+b形式的式子进行匹配（比如2n+1匹配按照顺序来的最后一个元素，然后往前两个，再往前两个，诸如此类。从后往前数的所有奇数个）。 |
| [`:only-child`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/:only-child) | 匹配没有兄弟元素的元素。                                     |
| [`:only-of-type`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/:only-of-type) | 匹配兄弟元素中某类型仅有的元素。                             |
| [`:optional`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/:optional) | 匹配不是必填的form元素。                                     |
| [`:out-of-range`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/:out-of-range) | 按区间匹配元素，当值不在区间内的的时候匹配。                 |
| [`:past` (en-US)](https://developer.mozilla.org/en-US/docs/Web/CSS/:past) | 匹配当前元素之前的元素。                                     |
| [`:placeholder-shown`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/:placeholder-shown) | 匹配显示占位文字的input元素。                                |
| [`:playing` (en-US)](https://developer.mozilla.org/en-US/docs/Web/CSS/:playing) | 匹配代表音频、视频或者相似的能“播放”或者“暂停”的资源的，且正在“播放”的元素。 |
| [`:paused` (en-US)](https://developer.mozilla.org/en-US/docs/Web/CSS/:paused) | 匹配代表音频、视频或者相似的能“播放”或者“暂停”的资源的，且正在“暂停”的元素。 |
| [`:read-only`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/:read-only) | 匹配用户不可更改的元素。                                     |
| [`:read-write`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/:read-write) | 匹配用户可更改的元素。                                       |
| [`:required`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/:required) | 匹配必填的form元素。                                         |
| [`:right`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/:right) | 在[分页媒体 (en-US)](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Pages)中，匹配右手边的页。 |
| [`:root`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/:root) | 匹配文档的根元素。                                           |
| [`:scope`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/:scope) | 匹配任何为参考点元素的的元素。                               |
| [`:valid`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/:valid) | 匹配诸如`<input>`元素的处于可用状态的元素。                  |
| [`:target`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/:target) | 匹配当前URL目标的元素（例如如果它有一个匹配当前[URL分段](https://en.wikipedia.org/wiki/Fragment_identifier)的元素）。 |
| [`:visited`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/:visited) | 匹配已访问链接。                                             |

### [伪元素](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Building_blocks/Selectors/Pseudo-classes_and_pseudo-elements#伪元素)

| 选择器                                                       | 描述                                                 |
| :----------------------------------------------------------- | :--------------------------------------------------- |
| [`::after`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/::after) | 匹配出现在原有元素的实际内容之后的一个可样式化元素。 |
| [`::before`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/::before) | 匹配出现在原有元素的实际内容之前的一个可样式化元素。 |
| [`::first-letter`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/::first-letter) | 匹配元素的第一个字母。                               |
| [`::first-line`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/::first-line) | 匹配包含此伪元素的元素的第一行。                     |
| [`::grammar-error`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/::grammar-error) | 匹配文档中包含了浏览器标记的语法错误的那部分。       |
| [`::selection`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/::selection) | 匹配文档中被选择的那部分。                           |
| [`::spelling-error`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/::spelling-error) | 匹配文档中包含了浏览器标记的拼写错误的那部分。       |



```css
/* 奇数段 */
p:nth-of-type(2n+1) {
  color: red;
}

/* 偶数段 */
p:nth-of-type(2n) {
  color: blue;
}

/* 第一段 */
p:nth-of-type(1) {
  font-weight: bold;
}
```

>  公式`2n-1`会选择所有奇数的子元素(1、3、5等)，而公式`2n`会选择所有偶数的子元素(2、4、6等等)。我们在代码中使用了`odd`和`even`的关键字，这与前面提到的公式作用完全相同



### 伪类选择器target 目标

**`:target`** [CSS](https://developer.mozilla.org/en-US/docs/Web/CSS) [伪类](https://developer.mozilla.org/en-US/docs/Web/CSS/Pseudo-classes) 代表一个唯一的页面元素(目标元素)，其[`id`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Global_attributes#attr-id) 与当前URL的截图匹配。

<img src="https://shimmerimg.oss-cn-beijing.aliyuncs.com/blog/screenshot/20211006173137.png" alt="image-20211006173137760" style="zoom:50%;" />

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <title>Document</title>
    <style>
        p:target {
            background-color: gold;
        }
        /* 在目标元素中增加一个伪元素*/
        
        p:target::before {
            font: 70% sans-serif;
            content: "►";
            color: limegreen;
            margin-right: .25em;
        }
        /*在目标元素中使用italic样式*/
        
        p:target i {
            color: red;
        }
    </style>
</head>

<body>
    <h3>Table of Contents</h3>
    <ol>
        <li><a href="#p1">Jump to the first paragraph!</a></li>
        <li><a href="#p2">Jump to the second paragraph!</a></li>
        <li><a href="#nowhere">This link goes nowhere,
                because the target doesn't exist.</a></li>
    </ol>

    <h3>My Fun Article</h3>
    <p id="p1">You can target <i>this paragraph</i> using a URL fragment. Click on the link above to try out!</p>
    <p id="p2">This is <i>another paragraph</i>, also accessible from the links above. Isn't that delightful?</p>
</body>

</html>
```



## css关系选择器

子选择器

`父 > 子 {xxx }`

后代选择器：

> 选择器利用后代组合符被称作后代选择器。

`祖宗 任意子孙 {xxx}`

兄弟选择器：

> 只会选择同级的下一个元素

`兄弟 + 兄弟 {xxx}`

通用兄弟选择器：

如果你想选中一个元素的兄弟元素，即使它们不直接相邻，你还是可以使用通用兄弟关系选择器（`~`）。要选中所有的`<p>`元素后*任何地方*的`<img>`元素。

`兄弟 ~ 兄弟 {xxx}`

<img src="https://shimmerimg.oss-cn-beijing.aliyuncs.com/blog/screenshot/20211006174738.png" alt="image-20211006174738017" style="zoom:25%;" />

## css选择器优先级

稍后的样式将覆盖以前的样式。这就是起作用的**级联**。

同样的选择器，最后出现的优先；

不同样的选择器，选择范围更小的优先；

它底部是将选择转换为数字并累计，比较最大值来计算的

```css
p {
  color: red;
}

p {
  color: blue;
}

```

现在让我们来看看浏览器如何计算优先级。我们已经知道一个元素选择器比类选择器的优先级更低会被其覆盖。本质上，不同类型的选择器有不同的分数值，把这些分数相加就得到特定选择器的权重，然后就可以进行匹配。

一个选择器的优先级可以说是由四个部分相加 (分量)，可以认为是个十百千 — 四位数的四个位数：

1. **千位**： 如果声明在 [`style`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Global_attributes#attr-style) 的属性（内联样式）则该位得一分。这样的声明没有选择器，所以它得分总是1000。
2. **百位**： 选择器中包含ID选择器则该位得一分。
3. **十位**： 选择器中包含类选择器、属性选择器或者伪类则该位得一分。
4. **个位**：选择器中包含元素、伪元素选择器则该位得一分。

**注**: 通用选择器 (`*`)，组合符 (`+`, `>`, `~`, ' ')，和否定伪类 (`:not`) 不会影响优先级。

**警告:** 在进行计算时不允许进行进位，例如，20 个类选择器仅仅意味着 20 个十位，而不能视为 两个百位，也就是说，无论多少个类选择器的权重叠加，都不会超过一个 ID 选择器。

有一个特殊的 CSS 可以用来覆盖所有上面所有优先级计算，不过需要很小心的使用 — `!important`。用于修改特定属性的值， 能够覆盖普通规则的层叠。



# css 移除li默认样式

```css
li {
  list-style-type: none;
}
```

a标签移除默认样式

```css
/*包含以下四种的链接*/
a {
    text-decoration: none;
}
/*正常的未被访问过的链接*/
a:link {
    text-decoration: none;
}
/*已经访问过的链接*/
a:visited {
    text-decoration: none;
}
/*鼠标划过(停留)的链接*/
a:hover {
    text-decoration: none;
}
/* 正在点击的链接*/
a:active {
    text-decoration: none;
}
```



# css防止不支持属性，使用多个相同属性

举例来说，一些老的浏览器不接收`calc()`(calculate的缩写，CSS3新增，为元素指定动态宽度、长度等，注意此处的动态是计算之后得一个值)作为一个值。我可能使用它结合像素为一个元素设置了动态宽度（如下），老式的浏览器由于无法解析忽略这一行；新式的浏览器则会把这一行解析成像素值，并且覆盖第一行指定的宽度。

```css
.box {
  width: 500px;
  width: calc(100% - 50px);
}
```







# css外边距折叠

若两个盒子都定义了外边距，他们之间的外边距会重合，外边距只要符合设定范围盒子就不会再推其他盒子了。

理解外边距的一个关键是外边距折叠的概念。如果你有两个外边距相接的元素，这些外边距将合并为一个外边距，即最大的单个外边距的大小。



# css控制背景平铺

[`background-repeat`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/background-repeat)属性用于控制图像的平铺行为。可用的值是:

- `no-repeat` — 不重复。
- `repeat-x` —水平重复。
- `repeat-y` —垂直重复。
- `repeat` — 在两个方向重复。



# css 调整背景图大小

background-size:

- x y
- `cover` —浏览器将使图像足够大，使它完全覆盖了盒子区，同时仍然保持其高宽比。在这种情况下，有些图像可能会跳出盒子外
- `contain` — 浏览器将使图像的大小适合盒子内。在这种情况下，如果图像的长宽比与盒子的长宽比不同，则可能在图像的任何一边或顶部和底部出现间隙。





# css 溢出盒子

我们知道，CSS中万物皆盒，因此我们可以通过给[`width`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/width)和[`height`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/height)（或者 [`inline-size`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/inline-size) 和 [`block-size`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/block-size)）赋值的方式来约束盒子的尺寸。溢出是在你往盒子里面塞太多东西的时候发生的，所以盒子里面的东西也不会老老实实待着。

通过溢流属性设置溢出盒子时如何显示

[`overflow`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/overflow)属性是你控制一个元素溢出的方式，它告诉浏览器你想怎样处理溢出。`overflow`的默认值为`visible`，这就是我们的内容溢出的时候，我们在默认情况下看到它们的原因。

overflow: 

 hidden;

 visible;

 Auto;

Scroll;



overflow 代表 overflow-x overflow-y

例如：

`overflow: scroll hidden`会把`overflow-x`设置成`scroll`，而`overflow-y`则为`hidden`。

多媒体文件则用`object-fit`属性解决溢出 

- `contain`

  被替换的内容将被缩放，以在填充元素的内容框时保持其宽高比。 整个对象在填充盒子的同时保留其长宽比，因此如果宽高比与框的宽高比不匹配，该对象将被添加“[黑边](https://zh.wikipedia.org/wiki/黑邊)”。

- `cover`

  被替换的内容在保持其宽高比的同时填充元素的整个内容框。如果对象的宽高比与内容框不相匹配，该对象将被剪裁以适应内容框。

- `fill`

  被替换的内容正好填充元素的内容框。整个对象将完全填充此框。如果对象的宽高比与内容框不相匹配，那么该对象将被拉伸以适应内容框。

- `none`

  被替换的内容将保持其原有的尺寸。

- `scale-down`

  内容的尺寸与 `none` 或 `contain` 中的一个相同，取决于它们两个之间谁得到的对象尺寸会更小一些。

>  坑爹的 IE：应该在`<textarea>`上设置`overflow: auto` 以避免IE在不需要滚动条的时候显示滚动条：

```css
textarea {
  overflow: auto;
}
```

# css不同明度

opacity: 0.6; 让盒子边框背景内容都变的透明



# css 定位指定一个方向值后，另一个方向自动设为居中

一个典型的位置值由两个值组成——第一个值水平地设置位置，第二个值垂直地设置位置。如果只指定一个轴的值，另一个轴将默认为 `center`。





# 二维变换

二维变化包括对 html 元素的移动、旋转、缩放

tansform: translate\rotate\scale

`tansform: translate(x, y);` 值可以是 百分比，px。。。

`tansform: ratate( 360deg );`

`tansform: scaleb(x, y);`

### 修改元素旋转中心点 Tansform-origin(x, y) 

`tansform-origin: 0% 0%;`左上角为中心点

`tansform-origin: 0 100%;左下角`

`tansform-origin: 100% 0%;`右上角为中心点

`tansform-origin: 100% 100%;` 右下角



## 三维变化

```css
/* 旋转 */
transform: rotateX(30deg);  /*沿着 x 轴旋转，水平方向*/
transform: rotateY(30deg);  
transform: rotateZ(30deg);  
perspective: 400px; /* 屏幕显示的三维元素沿着 z 轴的透视距离设置，近大远小自动修改三维图形*/
perspective-origin: 50% 50%; /* 修改移动透视原点*/

/* 缩放 */
transform: scaleX(30deg);
transform: scaleY(30deg);
transform: scaleZ(30deg);

/* 移动 */
transform: translateX(30deg); /*沿着 x 轴移动，水平方向*/
transform: translateY(30deg);
transform: translateZ(30deg);/*沿着 z轴移动*/

/* 三维矩阵 4*4 一共 16 个值*/
transform: matrix3d(n, n, n, ...16n)
```

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <style>
        section:nth-of-type(1),
        section:nth-of-type(2),
        section:nth-of-type(3) {
            perspective: 400px;
            display: inline-block;
            margin: 1em;
        }

        section:nth-of-type(4),
        section:nth-of-type(5),
        section:nth-of-type(6) {
            perspective: 1000px;
            display: inline-block;
            margin: 1em;
        }

        div {
            display: inline-block;
            width: 200px;
            height: 120px;
            background: blue;
            /* transform: rotate(0deg); */
            text-align: center;
            color: white;
            transform: rotateX(45deg);
        }

        div:nth-of-type(1) {
            perspective-origin: 75% 50%;
        }

        div:nth-of-type(2) {
            perspective-origin: 50% 50%;
        }

        div:nth-of-type(3) {
            perspective-origin: 25% 50%;
        }

        div:nth-of-type(4) {
            perspective-origin: 75% 50%;
        }

        div:nth-of-type(5) {
            perspective-origin: 50% 50%;
        }

        div:nth-of-type(6) {
            perspective-origin: 25% 50%;
        }
    </style>
</head>

<body>
    <section>
        <div>123</div>
    </section>
    <section>
        <div>123</div>
    </section>
    <section>
        <div>123</div>
    </section>
    <hr>
    <section>
        <div>123</div>
    </section>
    <section>
        <div>123</div>
    </section>
    <section>
        <div>123</div>
    </section>

</body>

</html>
```



```css
transform-style: preserve-3d; /* 元素有遮挡关系 由于这个属性不会被继承，因此必须为元素的所有非叶子子元素设置它。*/
transform-style: float; 
```

### 构建立方体

![image-20211016133907496](https://shimmerimg.oss-cn-beijing.aliyuncs.com/blog/screenshot/20211016133907.png)

```css
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <style>
        .view {
            /* margin: 200px auto; */
            width: 200px;
            height: 200px;
            perspective: 300px;
        }

        .cube {
            width: 100%;
            height: 100%;
            position: relative;
            transform-style: preserve-3d;
            transform: translateX(200px) translateY(200px);
        }

        .face {
            position: absolute;
            width: 100px;
            height: 100px;
            background: transparent;
            border: 2px solid gray;
            text-align: center;
            line-height: 100px;
            backface-visibility: hidden;
            border-radius: 10px;
        }

        .front {
            transform: rotateY(0deg) translateZ(50px)
        }

        .right {
            transform: rotateY(90deg) translateZ(50px)
        }

        .back {
            transform: rotateY(180deg) translateZ(50px)
        }

        .left {
            transform: rotateY(-90deg) translateZ(50px)
        }

        .top {
            transform: rotateX(90deg) translateZ(50px)
        }

        .bottom {
            transform: rotateX(-90deg) translateZ(50px)
        }
    </style>
</head>

<body>
    <div class="view">
        <div class="cube">
            <div class="face front">front</div>
            <div class="face back">back</div>
            <div class="face right">right</div>
            <div class="face left">left</div>
            <div class="face top">top</div>
            <div class="face bottom">bottom</div>
        </div>
    </div>
</body>

</html>
```

