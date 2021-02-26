

>参考文章: 
>
>https://www.cnblogs.com/ming1025/p/9887247.html
>
>https://cli.vuejs.org/zh/guide/cli-service.html#git-hook
>
>https://www.kuangstudy.com/down
>
>https://zhuanlan.zhihu.com/p/214138807

## MVVM

双向绑定的原理MVVM
MVVM全名Model-View-ViewModel

- M表示抽离出的obj(new Vue)
- V表示DOM(html + css)
- VM表示监听M修改V，

是双向绑定的要点MVVM怎么工作的？

ViewModel通过bind让obj中的dom能够实时显示，在通过listener监听dom事件，通过method来修改数据说白了也就是监听+绑定实现的

![mvvm](https://pic1.zhimg.com/v2-37ec0b2f9094be826dea6d6c1af7dd78_b.jpg)

> 不要把 VUE 当成简单的js前端库来用

## VUE简介



核心 : 数据驱动 , 组件化

优点 : 借鉴了 AngulaJS 的模块化开发 和 React 的虚拟Dom , 虚拟Dom就是把Dom操作放到内存中执行

​			Vue + 第三方控件(如element、layui) = 效率高 & 使用便利 & 组件化架构

## 

常用的属性 :

- v-if

- v-else-if
- v-else
- v-for
- v-on 绑定事件 , 简写 @
- v-model 数据双向绑定
- v-bind 给组件绑定参数,简写 :



组件化 :

- 组合组件， slot 插槽。

- 组件内部绑定事件需要使用到 this.$emit("事件名",参数) ;

- 计算属性的特色,缓存计算数据

遵循SoC 关注度分离原则,Vue是纯粹的视图框架,并不包含,比如Ajax之类的通信功能,为了解决通信问题,

我们需要使用Axios 框架做异步通信；






## VUE组件

组件化是VUE的精髓，VUE就是由一个一个的组件构成的

组件是可复用的 Vue 实例，说白了就是一组可以重复使用的模板，跟 JSTL 的自定义标签



**使用** **Vue.component()** **方法注册组件：**

```html
<!DOCTYPE html>
<html>
<body>
<div id="app">
  <ul>
    <!-- 有点类似自定义标签 -->
    <my-component-li></my-component-li>
  </ul>
</div>

<script src="https://cdn.jsdelivr.net/npm/vue@2.5.21/dist/vue.js"></script>
<script> 
  // 先注册组件  
  // template组件的模板
  Vue.component('my-component-li', {template: '<li>Hello li</li>'});
  // 再实例化 Vue 
  var vm = new Vue({el: '#app'});
</script>
</body>
</html>
```



## 组件参数传递

使用 props 属性传递参数,**默认规则下** **props** **属性里的值不能为大写**

```html
<body>
<div id="app">
  <ul>
    <my-component-li v-for="item in items" v-bind:item="item"></my-component-li>
  </ul>
</div>
<script src="https://cdn.jsdelivr.net/npm/vue@2.5.21/dist/vue.js"></script>
<script> // 先注册组件 
  Vue.component('my-component-li', {
    props: ['item'],
    template: '<li>Hello {{item}}</li>'
  }); // 再实例化 Vue 
  var vm = new Vue({el: '#app', data: {items: ["张三", "李四", "王五"]}}); </script>
</body>
```

v-for="item in items" ：遍历 Vue 实例中定义的名为 items 的数组，并创建同等数量的组件；

v-bind:item="item" ：将遍历的 item 项绑定到组件中 props 定义的名为 item 属性上；

= 号左边的 item 为 props 定义的属性名，右边的为 item in items 中遍历的 item 项的值；



## 组合组件--插槽

在 Vue 中我们使用 <slot> 元素，作为承载分发内容的出口，作者称其为 插槽，可以应用在组合组

件的场景中

```js
Vue.component('todo', {
  template: '<div>\
              <slot name="todo-title"></slot>\
                <ul>\
                  <slot name="todo-items"></slot>\
                  </ul>\
             </div>'
});
Vue.component('todo-title', 
              {props: ['title'], 
               template: '<div>{{title}}</div>'});

Vue.component('todo-items', 
              {props: ['item', 'index'], 
               template: '<li>{{index + 1}}. {{item}}</li>'});

//实例化 Vue 并初始化数据
new Vue({ el: '#app', data: { todoItems: ['Java', '运维', '前端'] } })

```

```html
<div id="app"> 
  	<todo>
      <todo-title slot="todo-title" title="IT职业列表"></todo-title> 
      <todo-items slot="todo-items" v-for="(item, index) in todoItems" v-bind:item="item" v-bind:index="index">
      </todo-items> 
  </todo> 
</div>
```

 todo-title 和 todo-items 组件分别被分发到了 todo 组件的 todo-title 和 todo-items 插槽

中



## 自定义事件

自定义时间用于操作组件

Vue 提供了自定义事件的功能 `this.$emit`('自定义事件名', 参数)



## let和var

总结一句话：**以后用let不要用var**
细细道来：事实上var的设计可以看成JavaScript语言设计上的错误，这种错误多半不能修复和移除，有个人修复了这个问题，他添加了一个关键字：let，所以可以将let看作更完美的var



js没有像Java一样是强类型语言，所以涉及一个作用域的问题。Java中可以在for循环中每次都int i，但var i不行。

js中使用var来证明一个变量，作用域主要和函数的定义有关



ES6 新增了let命令，用来声明局部变量。

它的用法类似于var，但是所声明的变量，只在let命令所在的代码块内有效，而且有暂时性死区的约束。

let变量不能重复声明,let不允许在相同作用域内，重复声明同一个变量。否则报错：`Uncaught SyntaxError: Identifier 'XXX' has already been declared`



> 接触let关键字，有一个要**非常非常要注意**的概念就是”javascript 严格模式”,
>
> 在文件头添加”javascript 严格模式”声明：'use strict';



## **const修饰变量**

const也就相当于Java中的final，不可修改，必须初始化。一般用于定义Vue对象，和一些常量。其中的标识(zhi)符不能改变其中指向，能改变指向的值。经常使用的const app = new Vue(){}



## vue 和 node 的关系

node是一个在浏览器外执行JavaScript语言的环境，就好比JRE是Java的运行环境。

VUE借助 node 技术, 让前后端彻底分离, 直接使用 node 直接VUE 前端项目独立运行起来

使用Vue-cli可以快速搭建一个在运行在node上的VUE项目。



## vue-cli 手脚架

vue-cli 官方提供的一个脚手架,用于快速生成一个 vue 的项目模板

预先定义好的目录结构及基础代码，就好比咱们在创建 Maven 项目时可以选择创建一个骨架项目，

​	这个骨架项目就是脚手架,我们的开发更加的快速

**主要的功能** **:**

- 统一的目录结构
- 本地调试
- 热部署
- 单元测试
- 集成打包上线

在 shell 窗口中用命令快速搭建vue 项目

```shell
#下边将使用 npm工具安装相关环境,如果安装速度太慢。可以安装淘宝镜像cnpm
npm install -g cnpm --registry=https://registry.npm.taobao.org
#然后使用cnpm来安装

#卸载旧 vue-cli
npm uninstall -g vue-cli

#安装 vue-cli
cnpm install vue-cli -g
vue --version
# 测试是否安装成功 
# 查看可以基于哪些模板创建 vue 应用程序，通常我们选择 
webpack vue list

#升级全局的 Vue CLI 包
npm update -g @vue/cli

#全局安装webpack 和 webpack-cli
npm install webpack webpack-cli -g
webpack -v

#vue init安装
npm i -g @vue/cli-init

#新建一个文件夹 hello-world
#创建一个新项目
vue init webpack hello-world

#输入命令后，会跳出几个选项让你回答：

#Project name (baoge)： -----项目名称，直接回车，按照括号中默认名字（注意这里的名字不能有大写字母，如果有会报错Sorry, name can no longer contain capital letters），阮一峰老师博客为什么文件名要小写 ，可以参考一下。
#Project description (A Vue.js project)： ----项目描述，也可直接点击回车，使用默认名字
#Author ()： ----作者，输入你的大名
#接下来会让用户选择：
#Runtime + Compiler: recommended for most users 运行加编译，既然已经说了推荐，就选它了
#Runtime-only: about 6KB lighter min+gzip, but templates (or any Vue-specificHTML) are ONLY allowed in .vue files - render functions are required elsewhere 仅运行时，已经有推荐了就选择第一个了
#Install vue-router? (Y/n) 是否安装vue-router，这是官方的路由，大多数情况下都使用，这里就输入“y”后回车即可。
#Use ESLint to lint your code? (Y/n) 是否使用ESLint管理代码，ESLint是个代码风格管理工具，是用来统一代码风格的，一般项目中都会使用。
#接下来也是选择题Pick an ESLint preset (Use arrow keys) 选择一个ESLint预设，编写vue项目时的代码风格，直接y回车
#Setup unit tests with Karma + Mocha? (Y/n) 是否安装单元测试，我选择安装y回车
#Setup e2e tests with Nightwatch(Y/n)? 是否安装e2e测试 ，我选择安装y回车

#安装新项目按照根目录下的package.json文件中依赖的模块
#安装完成后，多出node_modules文件夹，这就是所有依赖的模块。
npm install

#运行
npm run dev
#安装并运行成功后在浏览器输入：http://localhost:8080

#停止服务
lsof -i:8080

kill -9 xxxxx
```



vue-cli这个构建工具大大降低了webpack的使用难度，支持热更新

webpack-dev-server的支持，相当于启动了一个请求服务器，给你搭建了一个测试环境，只关注开发就OK



![文件夹说明](https://upload-images.jianshu.io/upload_images/10868449-01a038fa573b22c8.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/443)





项目配置文件 /config/index.js

```
port: 8080,//修改端口号
```



## .vue 文件说明

`template：HTML` 代码模板，会替换 < App /> 中的内容

`export default{...}`：导出 NodeJS 对象,作用是可以通过 import 关键字导入

- `name: 'App'`：定义组件的名称
- `components: { HelloWorld }`：定义子组件

`< style scoped>` 的说明：CSS 样式仅在当前组件有效，声明了样式的作用域,

是当前的界面私有的! 





## VUE 路由

> 官方文档:https://router.vuejs.org/installation.html#direct-download-cdn

Vue Router 是 Vue.js 官方的路由管理器。它和 Vue.js 的核心深度集成，让构建单页面应用变得易如反

掌。包含的功能有：

- 嵌套的路由/视图表
- 模块化的、基于组件的路由配置
- 路由参数、查询、通配符
- 基于 Vue.js 过渡系统的视图过渡效果
- 细粒度的导航控制
- 带有自动激活的 CSS class 的链接
- HTML5 历史模式或 hash 模式，在 IE9 中自动降级
- 自定义的滚动条行为
- 解决跨域请求问题



安装命令

先查看node_modules中是否存在 vue-router

`npm install vue-router --save-dev `

果在一个模块化工程中使用它，必须要通过 Vue.use() 明确地安装路由功能

```js
import Vue from 'vue' 
import VueRouter from 'vue-router' 
// 显示的使用 
Vue.use(VueRouter);
```

```js
// 1. 定义路由组件。
// 这些可以从其他文件导入
const Foo = { template: '<div>foo</div>' }
const Bar = { template: '<div>bar</div>' }

//定义一些路线
//每个路由应该映射到一个组件
const router = new VueRouter([
  { path: '/foo', component: Foo },
  { path: '/bar', component: Bar }
]
//创建并挂载根实例。
//使用router选项注入路由器
//整个应用程序的路由器感知。
const app = new Vue({
  router
}).$mount('#app')
```

类似`/foo`和的URL`/bar`都将映射到对应的组件。

通过注入路由器，我们可以访问它`this.$router`以及`this.$route`任何组件内部的当前路由：

```js
// Home.vue
export default {
  computed: {
    username() {
      // We will see what `params` is shortly
      return this.$route.params.username
    }
  },
  methods: {
    goBack() {
      window.history.length > 1 ? this.$router.go(-1) : this.$router.push('/')
    }
  }
}
```

`this.$router`是因为我们不想将路由器导入每个需要操纵路由的组件中



## 动态路由

从地址中获取参数

```js
const User = {
  template: '<div>User {{ $route.params.id }}--{{ $route.params.name }}</div>'
}

const router = new VueRouter({
  routes: [
    // dynamic segments start with a colon
    { path: '/user/:id/:name', component: User }
  ]
})
```



## 路由钩子函数

```js
const User = {
  template: '...',
  beforeRouteUpdate (to, from, next) { //进入路由之间 当然还有离开路由时触发的钩子函数
    // react to route changes...
    // don't forget to call next()
  }
}
```



## 路由全部捕获解决 404

```js
{
  // will match everything
  path: '*'
}
{
  // will match anything starting with `/user-`
  path: '/user-*'
}
```



## 路由模式,解决地址带#问题

hash：路径带 # 符号，这是默认配置, 如 http://localhost/#/login

history：路径不带 # 符号，如 http://localhost/login

```js
export default new Router({ mode: 'history', routes: [ ] });
```





## element-ui

```shell
npm install vue 
npm i element-ui -S
```

创建 ui.html，引入 js 和 css 文件

```html
<!-- import CSS --> 
<link rel="stylesheet" href="./lib/element-ui/lib/theme-chalk/index.css"> 
<!-- import Vue before Element --> 
<script src="./lib/vue.min.js"></script> 
<!-- import JavaScript --> 
<script src="./lib/element-ui/lib/index.js"></script>
```





## VUE 页面模板1--**vue-element-admin**

vue-element-admin是基于element-ui 的一套后台管理系统集成方案。

**功能：**https://panjiachen.github.io/vue-element-admin-site/zh/guide/#功能

**GitHub****地址：**https://github.com/PanJiaChen/vue-element-admin

**项目在线预览：**https://panjiachen.gitee.io/vue-element-admin



安装测试使用

1、在提供的素材中，找到 vue-element-admin-master ， 解压到我们的代码目录中

2、使用VsCode打开





##  VUE 页面模板2--vue-admin-template

**1****、简介**

vue-admin-template是基于vue-element-admin的一套后台管理系统基础模板（最少精简版），可作为

模板进行二次开发。

**GitHub****地址：**https://github.com/PanJiaChen/vue-admin-template

**建议：**你可以在 vue-admin-template 的基础上进行二次开发，把 vue-element-admin 当做工具

箱，想要什么功能或者组件就去 vue-element-admin 那里复制过来。