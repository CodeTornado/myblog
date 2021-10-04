超文本标记语言(英语:HyperText Markup Language,简称:*HTML*)是一种用于创建网页的标准标记语言

HTML 文档是由 HTML 元素定义的。

HTML 元素指的是从开始标签（start tag）到结束标签（end tag）的所有代码。

HTML 文档由嵌套的 HTML 元素构成。

HTML 标签对大小写不敏感：<P> 等同于 <p>。许多网站都使用大写的 HTML 标签。在 HTML 4 中*推荐*使用小写，而在未来 (X)HTML5 版本中*强制*使用小写。



属性

属性总是以名称/值对的形式出现，比如：*name="value"*。

属性总是在 HTML 元素的*开始标签*中规定。

html5要求使用小写属性。



> html 中的注释`<!--...-->`
>
> 水平线 `hr`
>
> 标题 `h1--h6` 由大到小
>
> 文档的主体 `body`
>
> html 文档 `html`
>
> `<p>` 是块级元素
>
> `<br />`换行 , 即使 `<br>` 在所有浏览器中的显示都没有问题，使用` <br />` 也是*更长远的保障*。



> 当显示页面时，浏览器会移除*源代码中*多余的空格和空行。所有连续的空格或空行都会被算作一个空格。所有连续的空行（换行）也被显示为一个空格。

```html
<html>

<body>

<h1>春晓</h1>

<p>
    春眠不觉晓，
      处处闻啼鸟。
        夜来风雨声，
          花落知多少。
</p>

<p>注意，浏览器忽略了源代码中的排版（省略了多余的空格和换行）。</p>

</body>

</html>

```





## 文本格式化

| b      | 定义粗体文本。 |
| ------ | -------------- |
| Big    | 定义大号字。   |
| Em     | 定义着重文字。 |
| i      | 定义斜体字。   |
| Small  | 定义小号字。   |
| Strong | 定义加重语气。 |
| Sub    | 定义下标字。   |
| Sup    | 定义上标字。   |
| Ins    | 定义插入字。   |
| Del    | 定义删除字。   |



用于双向重写的 HTML `<bdo>`

HTML *<bdo>* 元素定义双流向覆盖（bi-directional override）。

<bdo> 元素用于覆盖当前文本方向：

```
<bdo dir="rtl">This text will be written from right to left</bdo>
```

## 引用标签

| <abbr>       | 定义缩写或首字母缩略语。         |
| ------------ | -------------------------------- |
| <address>    | 定义文档作者或拥有者的联系信息。 |
| <bdo>        | 定义文本方向。                   |
| <blockquote> | 定义从其他来源引用的节。         |
| <dfn>        | 定义项目或缩略词的定义。         |
| <q>          | 定义短的行内引用。               |
| <cite>       | 定义著作的标题。                 |



## 条件注释

您也许会在 HTML 中偶尔发现条件注释：

```
<!--[if IE 8]>
    .... some HTML here ....
<![endif]-->
```

条件注释定义只有 Internet Explorer 执行的 HTML 标签。

## 链接标签

### HTML 链接 - target 属性

使用 Target 属性，你可以定义被链接的文档在何处显示。

下面的这行会在新窗口打开文档：

```html
<a href="http://www.w3school.com.cn/" target="_blank">Visit W3School!</a>
```

### HTML 链接 - name 属性

name 属性规定锚（anchor）的名称。

您可以使用 name 属性创建 HTML 页面中的书签。

书签不会以任何特殊方式显示，它对读者是不可见的。

### 命名锚的语法：

```html
<a name="label">锚（显示在页面上的文本）</a>
```

### 实例

首先，我们在 HTML 文档中对锚进行命名（创建一个书签）：

```
<a name="tips">基本的注意事项 - 有用的提示</a>
```

然后，我们在同一个文档中创建指向该锚的链接：

```
<a href="#tips">有用的提示</a>
```



## 图片标签

alt 属性用来为图像定义一串预备的可替换的文本。替换文本属性的值是用户定义的。

图片标签默认对其方式时bottom底部对其

```html
<img src="boat.gif" alt="Big Boat">
```

修改浮动为左对齐

`<img src ="/i/eg_cute.gif" align ="left"> `

通过改变 img 标签的 "height" 和 "width" 属性的值，您可以放大或缩小图像。

图片用 a 标签包裹后可作为点击跳转图片

```html
<!-- 您也可以把图像作为链接来使用：-->
<a href="/example/html/lastpage.html">
<img border="0" src="/i/eg_buttonnext.gif" />
</a>
```



图像地图 map

点击图片指定位置后会连接到新的页面

```html
<html>
<body>

<p>请点击图像上的星球，把它们放大。</p>

<img
src="/i/eg_planets.jpg"
border="0" usemap="#planetmap"
alt="Planets" />

<map name="planetmap" id="planetmap">

<area
shape="circle"
coords="180,139,14"
href ="/example/html/venus.html"
target ="_blank"
alt="Venus" />

<area
shape="circle"
coords="129,161,10"
href ="/example/html/mercur.html"
target ="_blank"
alt="Mercury" />

<area
shape="rect"
coords="0,0,110,260"
href ="/example/html/sun.html"
target ="_blank"
alt="Sun" />

</map>

<p><b>注释：</b>img 元素中的 "usemap" 属性引用 map 元素中的 "id" 或 "name" 属性（根据浏览器），所以我们同时向 map 元素添加了 "id" 和 "name" 属性。</p>

</body>
</html>
```







## 使用 css 样式

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



## iframe 标签

内嵌一个 html 页面

点击 a 标签，iframe 内调整

```html
<iframe src="demo_iframe.htm" name="iframe_a"></iframe>
<p><a href="http://www.w3school.com.cn" target="iframe_a">W3School.com.cn</a></p>
```



## HTML `<base>` 元素

<base> 标签为页面上的所有链接规定默认地址或默认目标（target）：

```
<head>
<base href="http://www.w3school.com.cn/images/" />
<base target="_blank" />
</head>
```

## HTML `<meta>` 元素

元数据（metadata）是关于数据的信息。

<meta> 标签提供关于 HTML 文档的元数据。元数据不会显示在页面上，但是对于机器是可读的。

典型的情况是，meta 元素被用于规定页面的描述、关键词、文档的作者、最后修改时间以及其他元数据。

<meta> 标签始终位于 head 元素中。

元数据可用于浏览器（如何显示内容或重新加载页面），搜索引擎（关键词），或其他 web 服务。

### 针对搜索引擎的关键词

一些搜索引擎会利用 meta 元素的 name 和 content 属性来索引您的页面。

下面的 meta 元素定义页面的描述：

```
<meta name="description" content="Free Web tutorials on HTML, CSS, XML" />
```

下面的 meta 元素定义页面的关键词：

```
<meta name="keywords" content="HTML, CSS, XML" />
```

name 和 content 属性的作用是描述页面的内容。

## `<!DOCTYPE>` 声明

`<!DOCTYPE>` 不是 HTML 标签。它为浏览器提供一项信息（声明），即 HTML 是用什么版本编写的。

`<!DOCTYPE html>`

| 版本      | 年份 |
| :-------- | :--- |
| HTML      | 1991 |
| HTML+     | 1993 |
| HTML 2.0  | 1995 |
| HTML 3.2  | 1997 |
| HTML 4.01 | 1999 |
| XHTML 1.0 | 2000 |
| HTML5     | 2012 |
| XHTML5    | 2013 |



### 常用的 DOCTYPE 声明

### HTML 5

```
<!DOCTYPE html>
```

### HTML 4.01 Strict

该 DTD 包含所有 HTML 元素和属性，但不包括展示性的和弃用的元素（比如 font）。不允许框架集（Framesets）。

```
<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01//EN" "http://www.w3.org/TR/html4/strict.dtd">
```

### HTML 4.01 Transitional

该 DTD 包含所有 HTML 元素和属性，包括展示性的和弃用的元素（比如 font）。不允许框架集（Framesets）。

```
<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN" 
"http://www.w3.org/TR/html4/loose.dtd">
```

### HTML 4.01 Frameset

该 DTD 等同于 HTML 4.01 Transitional，但允许框架集内容。

```
<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01 Frameset//EN" 
"http://www.w3.org/TR/html4/frameset.dtd">
```

### XHTML 1.0 Strict

该 DTD 包含所有 HTML 元素和属性，但不包括展示性的和弃用的元素（比如 font）。不允许框架集（Framesets）。必须以格式正确的 XML 来编写标记。

```
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN" 
"http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">
```

### XHTML 1.0 Transitional

该 DTD 包含所有 HTML 元素和属性，包括展示性的和弃用的元素（比如 font）。不允许框架集（Framesets）。必须以格式正确的 XML 来编写标记。

```
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "
http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
```

### XHTML 1.0 Frameset

该 DTD 等同于 XHTML 1.0 Transitional，但允许框架集内容。

```
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Frameset//EN" 
"http://www.w3.org/TR/xhtml1/DTD/xhtml1-frameset.dtd">
```

### XHTML 1.1

该 DTD 等同于 XHTML 1.0 Strict，但允许添加模型（例如提供对东亚语系的 ruby 支持）。

```html
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.1//EN" "http://www.w3.org/TR/xhtml11/DTD/xhtml11.dtd">
```

> **注释：**<!DOCTYPE> 声明没有结束标签。
>
> **提示：**<!DOCTYPE> 声明对大小写不敏感。
>
> **提示：**请使用 W3C 的验证器来检查您是否编写了有效的 HTML / XHTML 文档！





> 文件名中应使用连字符。谷歌搜索引擎把连字符当作单词的分隔符， 但不会识别下划线。基于此，最好在一开始就养成习惯，文件夹和文件名使用小写，用短横线而不是空格来分隔。可以避免许多问题。



## css、js的注释

`/*``*/` 不可嵌套

// 单行注释

## 一切皆是盒子

编写 CSS 时你会发现，你的工作好像是围绕着一个一个盒子展开的——设置尺寸、颜色、位置，等等。页面里大部分 HTML 元素都可以被看作若干层叠的盒子。

每个占据页面空间的块都有这样的属性：

- `padding`：即内边距，围绕着内容（比如段落）的空间。
- `border`：即边框，紧接着内边距的线。
- `margin`：即外边距，围绕元素外部的空间。





## margin

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



##  `text-shadow` 属性

`  text-shadow: 3px 3px 1px black;`

- 第一个值设置**水平偏移值** —— 即阴影右移的像素数（负值左移）。
- 第二个值设置**垂直偏移值** —— 即阴影下移的像素数（负值上移）。
- 第三个值设置阴影的**模糊半径** —— 值越大产生的阴影越模糊。
- 第四个值设置阴影的基色。



## 图像居中

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



## JS 大小写敏感

JavaScript 对大小写敏感，`myVariable` 和 `myvariable` 是不同的。如果代码出现问题了，先检查一下大小写！



## var 和 let 的区别

当你使用 `var` 时，可以根据需要多次声明相同名称的变量，但是 `let` 不能。 以下将有效：

```js
var myName = 'Chris';
var myName = 'Bob';
```

但是以下内容会在第二行引发错误：

```js
let myName = 'Chris';
let myName = 'Bob';
```

你必须这样做：

```js
let myName = 'Chris';
myName = 'Bob';
```

同样，这是一个明智的语言决定。没有理由重新声明变量——这只会让事情变得更加混乱。

出于这些以及其他原因，我们建议您在代码中尽可能多地使用 `let`，而不是 `var`。因为没有理由使用 `var`，除非您需要用代码支持旧版本的 Internet Explorer (它直到第 11 版才支持 `let` ，现代的 Windows Edge 浏览器支持的很好)。



## 字符串自动转换

两个变量进行运算时，一个为字符串，另一个为其他类型，只有运算符为`+`时，会字符串拼接，否则转为其他类型在运算。

```js
'1' + 1
'11'
----------
'1' - 1
0
----------
'1' * 1
1
----------
'1' / 1
1
```

==比较值时自动转为相同类型

```js
'1' == 1
true
'2' == 2
true
'true' == true
false
```

注意 布尔类型比较时，js 会自动转为 Number类型，又导致字符串转为 Number 类型，Number('true') 返回`NaN`, Numer(true)返回 1, 所以返回 false





## 用自带函数prompt获取用户输入

弹出提示框，并获取用户输入字符串

```js
 let myName = prompt('请输入你的名字。')
```

## 用自带函数localStorage将值写入本地存储

`localStorage.setItem('name', myName)`

`localStorage.getItem('name')`

第一次访问网页时，页面将询问用户名并发出一段个性化的信息。可随时点击按钮来改变用户名 。告诉你一个额外的福利，因为用户名是保存在 `localStorage` 里的，网页关闭后也不会丢失，所以重新打开浏览器时所设置的名字信息将依然存在:)



## js 方法绑定必须要加方法括号

```js
myButton.onclick = function() {
   setUserName()
}

// 错误示范 ↓ 会直接执行，并且绑定失败，还不报错
myButton.onclick = setUserName()

```



## meta 元素

许多`<meta>` 元素包含了`name` 和 `content` 特性：

- `name` 指定了meta 元素的类型； 说明该元素包含了什么类型的信息。
- `content` 指定了实际的元数据内容。



meta 可以定义页面字符

```html
<meta charset="utf-8">
```

> 一些浏览器（比如Chrome）会自动修正错误的编码，所以取决于你所使用的浏览器，你或许不会看到这个问题。无论如何，你仍然应该为你的页面手动设置编码为`utf-8`，来避免在其他浏览器中可能出现的潜在问题。

meta 记录页面开发者和页面描述

```html
<meta name="author" content="Chris Mills">
<meta name="description" content="The MDN Learning Area aims to provide
complete beginners to the Web with all they need to know to get
started with developing web sites and applications.">
```



## 网站标签栏图标

以.ico格式保存（大多数浏览器将支持更通用的格式，如.gif或.png，但使用ICO格式将确保它能在如Internet Explorer 6一样久远的浏览器显示）

```html
<link rel="shortcut icon" href="favicon.ico" type="image/x-icon">
```

根据分辨率的不同使用对应的图标

```html
<!-- third-generation iPad with high-resolution Retina display: -->
<link rel="apple-touch-icon-precomposed" sizes="144x144" href="https://developer.mozilla.org/static/img/favicon144.png">
<!-- iPhone with high-resolution Retina display: -->
<link rel="apple-touch-icon-precomposed" sizes="114x114" href="https://developer.mozilla.org/static/img/favicon114.png">
<!-- first- and second-generation iPad: -->
<link rel="apple-touch-icon-precomposed" sizes="72x72" href="https://developer.mozilla.org/static/img/favicon72.png">
<!-- non-Retina iPhone, iPod Touch, and Android 2.1+ devices: -->
<link rel="apple-touch-icon-precomposed" href="https://developer.mozilla.org/static/img/favicon57.png">
<!-- basic favicon -->
<link rel="shortcut icon" href="https://developer.mozilla.org/static/img/favicon32.png">
```



## 引入 css 样式

```html
<link rel="stylesheet" href="my-css-file.css">
```

 `link`元素经常位于文档的头部。这个link元素有2个属性，rel="stylesheet"表明这是文档的样式表，而 href包含了样式表文件的路径



引入 Js文件

`<script src="my-js-file.js"></script>`

`script`部分没必要非要放在文档头部；实际上，把它放在文档的尾部（在 `</body>标签之前`）是一个更好的选择，这样可以确保在加载脚本之前浏览器已经解析了HTML内容（如果脚本加载某个不存在的元素，浏览器会报错）。



## 设置 html 语言格式

```html
<html lang="zh-CN">
```

你还可以将文档的分段设置为不同的语言。例如，我们可以把日语部分设置为日语，如下所示：

```html
<p>日语实例: <span lang="jp">ご飯が熱い。</span>.</p>
```

这些codes是根据 [ISO 639-1](https://en.wikipedia.org/wiki/ISO_639-1) 标准定义的。你可以在[Language tags in HTML and XML](https://www.w3.org/International/articles/language-tags/)找到更多相关的。



## 为什么我们需要语义？

在我们身边的任何地方都要依赖语义学 — 我们依靠以前的经验就知道日常事物都代表什么；当我们看到什么，我们就会知道它代表什么。举个例子, 我们知道红色交通灯表示“停止”，绿色交通灯表示”通行“。 如果运用了错误的语义，事情会迅速地变得非常棘手 (难道有某个国家使用红色代表通行？我不希望如此)

同样的道理，我们需要确保使用了正确的元素来给予内容正确的意思、作用以及外形。在这里，[ (en-US)](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/Heading_Elements) 元素也是一个语义元素，它给出了包裹在您的页面上用来表示顶级标题的角色（或意义）的文本。

一般来说，浏览器会给它一个更大的字形来让它看上去像个标题（虽然你可以使用CSS让它变成任何你想要的样式。更重要的是，它的语义值将以多种方式被使用，比如通过搜索引擎和屏幕阅读器。



## 链接到某页面并移动到对应id 元素

```html
<p>要提供意见和建议，请将信件邮寄至 <a href="contacts.html#Mailing_address">我们的地址</a>。</p>
```



## 下载链接使用 dowload属性

当您链接到要下载的资源而不是在浏览器中打开时，您可以使用 download 属性来提供一个默认的保存文件名

```html
<a href="https://download.mozilla.org/?product=firefox-latest-ssl&os=win64&lang=zh-CN"
   download="firefox-latest-64bit-installer.exe">
  下载最新的 Firefox 中文版 - Windows（64位）
</a>
```



## 电子邮件链接

当点击一个链接或按钮时，打开一个新的电子邮件发送信息而不是连接到一个资源或页面，这种情况是可能做到的。这样做是使用`<a>`元素和`mailto`：URL的方案。
其最基本和最常用的使用形式为一个`mailto`:link （链接），链接简单说明收件人的电子邮件地址。例如:

```html
<a href="mailto:nowhere@mozilla.org">向 nowhere 发邮件</a>
```

邮件地址甚至是可选的。如果你忘记了（也就是说，你的`href`仅仅只是简单的"`mailto:`"）





## 通过为图片搭配说明文字的方式来解说图片

说到说明文字, 这里有很多种方法让你添加一段说明文字来搭配图片。比如，没有人会阻止你这么做：

```html
<div class="figure">
  <img src="/images/dinosaur_small.jpg"
     alt="一只恐龙头部和躯干的骨架，它有一个巨大的头，长着锋利的牙齿。"
     width="400"
     height="341">
  <p>曼彻斯特大学博物馆展出的一只霸王龙的化石</p>
</div>
```

这是可以的 ， [``](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/p) 中包含了你需要的内容，以及方便使用 CSS 的一种很好的风格。但是这里有一个问题 ，从语义的角度上来讲，[``](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/img) 和 [``](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/p) 并没有什么联系，这会给使用屏幕阅读的人造成问题，比如当你有 50 张图片和其搭配的 50 段说明文字，那么一段说明文字是和哪张图片有关联的呢？

有一个更好的做法是使用 HTML5 的 `<figure>` 和 `<figcaption>` 元素，它正是为此而被创造出来的：为图片提供一个语义容器，在标题和图片之间建立清晰的关联。我们之前的例子可以重写为:

```
<figure>
  <img src="https://raw.githubusercontent.com/mdn/learning-area/master/html/multimedia-and-embedding/images-in-html/dinosaur_small.jpg"
     alt="一只恐龙头部和躯干的骨架，它有一个巨大的头，长着锋利的牙齿。"
     width="400"
     height="341">
  <figcaption>曼彻斯特大学博物馆展出的一只霸王龙的化石</figcaption>
</figure>
```

