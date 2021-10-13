# 学习前提

官方指南假设你已了解关于 HTML、CSS 和 JavaScript 的中级知识。如果你刚开始学习前端开发，将框架作为你的第一步可能不是最好的主意——掌握好基础知识再来吧！之前有其它框架的使用经验会有帮助，但这不是必需的。



# 简介

Vue (读音 /vjuː/，类似于 **view**) 是一套用于构建用户界面的**渐进式框架**。与其它大型框架不同的是，Vue 被设计为可以自底向上逐层应用。Vue 的核心库只关注视图层，不仅易于上手，还便于与第三方库或既有项目整合。另一方面，当与现代化的工具链以及各种支持类库结合使用时，Vue 也完全能够为复杂的单页应用提供驱动。



> VUE 官方教程视频地址 https://cn.vuejs.org/v2/guide/



# 优点

- 体积小
  - 压缩后33K;
- 更高的运行效率
  - 基于虚拟dom,一种可以预先通过JavaScript进行各种计算,把最终的DOM操作计算出来并优化的技术,由于这个DOM操作属于预处理操作,并没有真实的操作DOM,所以叫做虚拟DOM。
- 双向数据绑定
  - 让开发者不用再去操作dom对象，把更多的精力投入到业务逻辑上;
- 生态丰富、学习成本低
  - 市场上拥有大量成熟、稳定的基于vue.js的ui框架、常用组件!拿来即用实现快速开发！
  - 对初学者友好、入门容易、学习资料多；



# 推荐工具,

HBuilderX 2.2.2



# 特点

- 编程范式
  - VUE 是声明式编程
    - 我们将 DOM 对象绑定给VUE 实例, DOM 交由 VUE 处理, 只需要安装规范简单调用即可实现复杂操作, 中间每一步怎么做的不需要自己编写
    - 数据和界面完全分离, 处理数据在Scrpit 块中, 界面在界面中编写
  - 传统 Js 是命令式
    - 每一行怎么做,直到出最终效果都需要自己编写
- 响应式
  - 自动数据绑定在前端, 如果数据发送变动,前端页面自动修改不需要编写额外修改代码
  - 全交给 VUE实例来管理
- 双向绑定
  - 更改 2 边中任意一边,对应的值会进行更改



# 简单使用 插值

数据绑定最常见的形式就是使用“Mustache”语法 (双大括号) 的文本插值

```js
<span>Message: {{ msg }}</span>
```

无论何时，绑定的数据对象上 msg property 发生了改变，插值处的内容都会更新。



# 条件与循环



## v-if、v-else-if、v-else 

```js
<div id="app-3">
  <p v-if="seen == 'A'">现在你看到A了</p>
  <p v-else-if="seen == 'B'">现在你看到B了</p>
  <p v-else>AB都没有看到</p>
</div>

var app3 = new Vue({
  el: '#app-3',
  data: {
    seen: 'A'
  }
})
```

## v-show

只是简单地切换元素的 CSS property display。
注意，v-show 不支持 <template> 元素，也不支持 v-else。



## v-if 和 v-show比较
v-if 是“真正”的条件渲染，因为它会确保在切换过程中条件块内的事件监听器和子组件适当地被销毁和重建。
v-if 也是惰性的：如果在初始渲染时条件为假，则什么也不做——直到条件第一次变为真时，才会开始渲染条件块。
相比之下，v-show 就简单得多——不管初始条件是什么，元素总是会被渲染，并且只是简单地基于 CSS 进行切换。
一般来说，v-if 有更高的切换开销，而 v-show 有更高的初始渲染开销。因此，如果需要非常频繁地切换，则使用 v-show 较好；如果在运行时条件很少改变，则使用 v-if 较好。



## v-for

```js
<div id="app-4">
  <ol>
    <li v-for="todo in todos">
      {{ todo.text }}
    </li>
  </ol>
</div>
var app4 = new Vue({
  el: '#app-4',
  data: {
    todos: [
      { text: '学习 JavaScript' },
      { text: '学习 Vue' },
      { text: '整个牛项目' }
    ]
  }
})
```

v-for 渲染的动态选项

```js
<select v-model="selected">
  <option v-for="option in options" v-bind:value="option.value">
    {{ option.text }}
  </option>
</select>
<span>Selected: {{ selected }}</span>
new Vue({
  el: '...',
  data: {
    selected: 'A',
    options: [
      { text: 'One', value: 'A' },
      { text: 'Two', value: 'B' },
      { text: 'Three', value: 'C' }
    ]
  }
})
```



# 过滤器

全局

私有

过滤器调用的时候,采用的是就近原则,如果私有过滤器和全局过滤器名称一致了,这时候优先调用私有过滤器



# 数组更新检测

Vue 将被侦听的数组的变更方法进行了包裹，所以它们也将会触发视图更新。这些被包裹过的方法包括

## list 集合添加新元素

```js
app4.todos.push({ text: '新项目' })
```



变更方法

```js
push()
pop
shift
unshift
splice
sort
reverse
```

替换数组

```js
filter
concat
slice
```



# 父子传递值

使用this.$refs来获取元素和组件



# 表单输入绑定

## v-model

你可以用 v-model 指令在表单 <input>、<textarea> 及 <select> 元素上创建双向数据绑定。它会根据控件类型自动选取正确的方法来更新元素。尽管有些神奇，但 v-model 本质上不过是语法糖。它负责监听用户的输入事件以更新数据，并对一些极端场景进行一些特殊处理。

> v-model 会忽略所有表单元素的 value、checked、selected attribute 的初始值而总是将 Vue 实例的数据作为数据来源。你应该通过 JavaScript 在组件的 data 选项中声明初始值。



text 和 textarea 元素使用 value property 和 input 事件；

checkbox 和 radio 使用 checked property 和 change 事件；

select 字段将 value 作为 prop 并将 change 作为事件。



```js
<input v-model="message" placeholder="edit me">
<p>Message is: {{ message }}</p>

<span>Multiline message is:</span>
<p style="white-space: pre-line;">{{ message }}</p>
<br>
<textarea v-model="message" placeholder="add multiple lines"></textarea>

<input type="checkbox" id="checkbox" v-model="checked">
<label for="checkbox">{{ checked }}</label>

<input type="checkbox" id="jack" value="Jack" v-model="checkedNames">
<label for="jack">Jack</label>
<input type="checkbox" id="john" value="John" v-model="checkedNames">
<label for="john">John</label>
<input type="checkbox" id="mike" value="Mike" v-model="checkedNames">
<label for="mike">Mike</label>
<br>
<span>Checked names: {{ checkedNames }}</span>
new Vue({
  el: '...',
  data: {
    checkedNames: []
  }
})
```



## 修饰符

### .lazy

在默认情况下，v-model 在每次 input 事件触发后将输入框的值与数据进行同步 (除了上述输入法组合文字时)。你可以添加 lazy 修饰符，从而转为在 change 事件_之后_进行同步：

```js
<!-- 在“change”时而非“input”时更新 -->
<input v-model.lazy="msg">
```

### .number

如果想自动将用户的输入值转为数值类型，可以给 v-model 添加 number 修饰符：

这通常很有用，因为即使在 type="number" 时，HTML 输入元素的值也总会返回字符串。如果这个值无法被 parseFloat() 解析，则会返回原始的值。

```js
<input v-model.number="age" type="number">
```



### .trim

如果要自动过滤用户输入的首尾空白字符，可以给 v-model 添加 trim 修饰符：

```js
<input v-model.trim="msg">
```





# 组件

组件是可复用的 Vue 实例，且带有一个名字



```js
// 定义一个名为 button-counter 的新组件
Vue.component('button-counter', {
  data: function () {
    return {
      count: 0
    }
  },
  template: '<button v-on:click="count++">You clicked me {{ count }} times.</button>'
})
```

在这个例子中是 <button-counter>。我们可以在一个通过 new Vue 创建的 Vue 根实例中，把这个组件作为自定义元素来使用

组件命名规范  大驼峰 or 短横线



## 注册组件



### 全局注册Vue.component

不推荐, 因为不管组件是否使用, 都会注册并消耗资源, 造成了用户下载的 JavaScript 的无谓的增加

```js
Vue.component('my-component-name', { /* ... */ })
```



### 局部注册

```js
//通过一个普通的 JavaScript 对象来定义组件

var ComponentA = { /* ... */ }
var ComponentB = { /* ... */ }
var ComponentC = { /* ... */ }

new Vue({
  el: '#app',
  components: {
    'component-a': ComponentA,
    'component-b': ComponentB
  }
})

//组件可以套用其他组件
var ComponentA = { /* ... */ }

var ComponentB = {
  components: {
    'component-a': ComponentA
  },
  // ...
}
```



# 指令Directives

- 指令带有前缀 v-，以表示它们是 Vue 提供的特殊 attribute。

- 它们会在渲染的 DOM 上应用特殊的响应式行为。



## v-bind



```js
V-bind:title="message"
```

该指令的意思是：“将这个元素节点的 title attribute 和 Vue 实例的 message property 保持一致”。

```js
<div id="app-2">
  <span v-bind:title="message">
    鼠标悬停几秒钟查看此处动态绑定的提示信息！
  </span>
</div>
var app2 = new Vue({
  el: '#app-2',
  data: {
    message: '页面加载于 ' + new Date().toLocaleString()
  }
})
```

> “:”是指令 “v-bind”的缩写

> Mustache 语法不能作用在 HTML attribute 上，遇到这种情况应该使用 v-bind 指令



## v-html

输出真正的 HTM

## v-once

你也能执行一次性地插值，当数据改变时，插值处的内容不会更新。

但请留心这会影响到该节点上的其它数据绑定



## v-on事件

指令监听 DOM 事件，并在触发时运行一些 JavaScript 代码。

通过 v-on 指令内联处理器中的方法

```js
<div id="example-3">
  <button v-on:click="say('hi')">Say hi</button>
  <button v-on:click="say('what')">Say what</button>
</div>
new Vue({
  el: '#example-3',
  methods: {
    say: function (message) {
      alert(message)
    }
  }
})
```

在内联语句处理器中访问原始的 DOM 事件。可以用特殊变量$event把它传入方法

```js
<button v-on:click="warn('Form cannot be submitted yet.', $event)">
  Submit
</button>
// ...
methods: {
  warn: function (message, event) {
    // 现在我们可以访问原生事件对象
    if (event) {
      event.preventDefault()
    }
    alert(message)
  }
}
```

> “@”是指令“v-on”的缩写



### v-on修饰符

#### 事件修饰符

```js
.stop 停止冒泡
<!-- 阻止单击事件继续传播 -->
<a v-on:click.stop="doThis"></a>

.prevent 阻止默认行为, a 标签自动跳转可用此修饰符阻止
<!-- 滚动事件的默认行为 (即滚动行为) 将会立即触发 -->
<!-- 而不会等待 `onScroll` 完成  -->
<!-- 这其中包含 `event.preventDefault()` 的情况 -->
<div v-on:scroll.passive="onScroll">...</div>

.capture 添加事件侦听器时使用事件捕获模式

.self 只当事件在该元素本身 比如不是子元素 触发时触发回调 .once 事件只触发一次

.once 点击事件将只会触发一次
<a v-on:click.once="doThis"></a>

<!-- 提交事件不再重载页面 -->
<form v-on:submit.prevent="onSubmit"></form>

<!-- 修饰符可以串联 -->
<a v-on:click.stop.prevent="doThat"></a>

<!-- 只有修饰符 -->
<form v-on:submit.prevent></form>

<!-- 添加事件监听器时使用事件捕获模式 -->
<!-- 即内部元素触发的事件先在此处理，然后才交由内部元素进行处理 -->
<div v-on:click.capture="doThis">...</div>

<!-- 只当在 event.target 是当前元素自身时触发处理函数 -->
<!-- 即事件不是从内部元素触发的 -->
<div v-on:click.self="doThat">...</div>
```



#### 按键修饰符

在监听键盘事件时，我们经常需要检查详细的按键。

Vue 允许为 v-on 在监听键盘事件时添加按键修饰符

```js 
<!-- 只有在 `key` 是 `Enter` 时调用 `vm.submit()` -->
<input v-on:keyup.enter="submit">
  
<!-- 
可以用如下修饰符来实现仅在按下相应按键时才触发鼠标或键盘事件的监听器。
.ctrl
.alt
.shift
.meta 
-->
```

你可以直接将 KeyboardEvent.key 暴露的任意有效按键名转换为 kebab-case 来作为修饰符。

你还可以通过全局 config.keyCodes 对象自定义按键修饰符别名：

```js
// 可以使用 `v-on:keyup.f1`
Vue.config.keyCodes.f1 = 112
```



.exact 

修饰符允许你控制由精确的系统修饰符组合触发的事件。

```js
<!-- 即使 Alt 或 Shift 被一同按下时也会触发 -->
<button v-on:click.ctrl="onClick">A</button>

<!-- 有且只有 Ctrl 被按下的时候才触发 -->
<button v-on:click.ctrl.exact="onCtrlClick">A</button>

<!-- 没有任何系统修饰符被按下的时候才触发 -->
<button v-on:click.exact="onClick">A</button>
```

常用的修饰符 

- .tab
- .delete (捕获“删除”和“退格”键)
- .esc
- .space
- .up
- .down
- .left
- .right



#### 鼠标按钮修饰符

这些修饰符会限制处理函数仅响应特定的鼠标按钮。

- .left
- .right
- .middle







## true-value 和 false-value

可用于复选框选中值修改

```js
<input
  type="checkbox"
  v-model="toggle"
  true-value="yes"
  false-value="no">
```



## v-cloak

用于解决闪烁问题

页面加载时, vue.js 没加载出来时页面会显示{{ msg }}等 vue 代码, 需要 v-cloak 执行结合 dispaly: none;解决闪烁 vue 代码问题



## v-text

v-text会覆盖元素中原本的内容,但是插值表达式 只会替换自己的这个占位符,不会把整个元素的内容清空



# 自定义指令

官方详细说明链接 https://cn.vuejs.org/v2/guide/custom-directive.html

```js
// 注册一个全局自定义指令 `v-focus`
Vue.directive('focus', {
  // 当被绑定的元素插入到 DOM 中时……
  inserted: function (el) {
    // 聚焦元素
    el.focus()
  }
})
```

## 钩子函数

- bind：只调用一次，指令第一次绑定到元素时调用。在这里可以进行一次性的初始化设置。
- inserted：被绑定元素插入父节点时调用 (仅保证父节点存在，但不一定已被插入文档中)。
- update：所在组件的 VNode 更新时调用，但是可能发生在其子 VNode 更新之前。指令的值可能发生了改变，也可能没有。但是你可以通过比较更新前后的值来忽略不必要的模板更新 (详细的钩子函数参数见下)。
- componentUpdated：指令所在组件的 VNode 及其子 VNode 全部更新后调用。
- unbind：只调用一次，指令与元素解绑时调用。



### 钩子函数参数

- el：指令所绑定的元素，可以用来直接操作 DOM。
- binding：一个对象，包含以下 property：
  - name：指令名，不包括 v- 前缀。
  - value：指令的绑定值，例如：v-my-directive="1 + 1" 中，绑定值为 2。
  - oldValue：指令绑定的前一个值，仅在 update 和 componentUpdated 钩子中可用。无论值是否改变都可用。
  - expression：字符串形式的指令表达式。例如 v-my-directive="1 + 1" 中，表达式为 "1 + 1"。
  - arg：传给指令的参数，可选。例如 v-my-directive:foo 中，参数为 "foo"。
  - modifiers：一个包含修饰符的对象。例如：v-my-directive.foo.bar 中，修饰符对象为 { foo: true, bar: true }。
- vnode：Vue 编译生成的虚拟节点。移步 VNode API 来了解更多详情。
- oldVnode：上一个虚拟节点，仅在 update 和 componentUpdated 钩子中可用。



# JS 中 多行模板字符串

在 js 脚本中编写多行 html 模板字符串时可能出现问题

这有效：

```js
var htmlString = "<div>This is a string.</div>";
```

这将失败：

```js
var htmlSTring = "<div>
  This is a string.
</div>";
```

有时，这对于可读性而言是理想的。

添加反斜杠以使其正常工作：

```js
var htmlSTring = "<div>\
  This is a string.\
</div>";
```





# 网络请求库

## axios

官方地址 https://github.com/axios/axios

>  vue中使用axios需要注意
>
> - axios回调函数中的 this 已经改变 无法访问到 data 中数据
> - 把 this 保存起来 回调函数中直接使用保存的 this 即可
> - 和本地应用的最大区别就是改变了数据来源



# Mustache 语法中使用 JS 的 表达式

对于所有的数据绑定，Vue.js 都提供了完全的 JavaScript 表达式支持。

这些表达式会在所属 Vue 实例的数据作用域下作为 JavaScript 被解析。有个限制就是，每个绑定都只能包含单个表达式

举个反例

```js
<!-- 这是语句，不是表达式 -->
{{ var a = 1 }}

<!-- 流控制也不会生效，请使用三元表达式 -->
{{ if (ok) { return message } }}
```

模板表达式都被放在沙盒中，只能访问全局变量的一个白名单，如 Math 和 Date 。

你不应该在模板表达式中试图访问用户定义的全局变量。





# 就地更新

v-for 渲染列表时，如果列表数据发生了变化，Vue 会使用一种最大限度减少动态元素并且尽可能的尝试就地修改/复用相同类型元素的算法。也就是说默认的情况下Vue会尽量使用已经存在的DOM元素，直接在已有的DOM上进行复用修改，这样可以带来一定性能上的提升。

为了给 Vue 一个提示，以便它能跟踪每个节点的身份，从而重用和重新排序现有元素，你需要为每项提供一个唯一 v-bind:key  缩写:key

建议尽可能在使用v-for时提供keyattribute，除非遍历输出的 DOM 内容非常简单，或者是刻意依赖默认行为以获取性能上的提升。



# 一些未分类的提示



> “.”  是修饰符 (Modifiers) 是以半角句号 . 指明的特殊后缀，用于指出一个指令应该以特殊方式绑定。例如，.prevent 修饰符告诉 v-on 指令对于触发的事件调用 event.preventDefault()：

