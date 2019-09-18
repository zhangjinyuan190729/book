# VUE.JS 基础

Vue是一个优秀的**`前端框架
Vuejs 开发H5,微信小程序  Vue语法+ 一点react语法 + 一点自创语法 => 微信小程序
般新框架 不是以vue作为基础语言,就是用react
作用:当前Vue实例所管理的html视图

## DAY1

### VUE现状

它是一个前端框架。
当下模式：vueZ React/Angular
MVVM`** 双向绑定  => v-model => 数据变化 => 视图变化   视图变化 => 数据变化

### vue渲染步骤

body中,设置Vue管理的视图<div id="app"></div>去
 引入vue.js
实例化Vue对象 new Vue();
设置Vue实例的选项:如el、data...   new Vue({选项:值});  
 在<div id='app'></div>中通过{{ }}使用data中的数据。

### 实力选项 el 

作用:当前Vue实例所管理的html视图
值:**`通常`**是id选择器(或者是一个 HTMLElement 实例)
不要让el所管理的视图是html或者body!
class选择器 只匹配第一个满足条件的元素 (Vue实例 => 管理视图 1对1)

### 实力选项 data

`数据驱动视图`** => 数据变化 => 视图一定变化  只需要关注数据。
Vue 实例的数据对象，是响应式数据(数据驱动视图) 数据变化 => 视图变化
可以通过 `vm.$data` 访问原始数据对象
Vue 实例也代理了 data 对象上所有的属性，因此访问 `vm.a` 等价于访问 `vm.$data.a`
视图中绑定的数据必须**`显式`**的初始化到 data 中 必须声明引用变量

数据对象的更新方式 直接 采用 **实例.属性 = 值
数据对象的更新方式 直接 采用 **实例.属性 = 值

### 实例选项 methods

methods是一个对象
可以直接通过 VM 实例访问这些方法，或者在**`插值表达式中使用`**
方法中的 `this` 自动绑定为 Vue 实例。
methods中所有的方法 同样也被代理到了 Vue实例对象上,都可通过this访问。
注意，**不应该使用箭头函数来定义 method 函数** (例如 `plus: () => this.a++`)。理由是箭头函数绑定了**`父级作用域`**的上下文，所以 `this` 将不会按照期望指向 Vue 实例，`this.a` 将是 undefined

### 插值表达式

MVVM`** 双向绑定  => v-model => 数据变化 => 视图变化   视图变化 => 数据变化。
会将绑定的数据实时的显示出来:
形式: 通过 **`{{ 插值表达式 }}`**包裹的形式
通过任何方式修改所绑定的数据,所显示的数据都会被实时替换(**响应式数据**)**数据驱动视图**

插值表达式 => **`为所欲为`*
注意`**:不能写 `var a = 10; 分支语句 循环语句`

### template标签

不想增加额外标签,同样可以用**`template
不会在html标签显示。

### 术语解释-指令

指令 (Directives) 是带有 `v-` 前缀的特殊特性。 v- 相当于标识  ng-   wx- 
指令特性的值预期是**`单个 JavaScript 表达式`**(`v-for` 是例外情况，稍后我们再讨论)。
指令的职责是，当表达式的值改变时，将其产生的连带影响，**`响应式`**地作用于 DOM。
指令位置:  **起始标签**
语法;
<p v-text="'我是p标签的内容'"></p>

- v-text  渲染文本

  v-text:更新标签中的内容
  v-text:更新标签中的内容
  v-text  更新**`整个`**标签中的内容
  插值表达式: 更新标签中**`局部`**的内容

- v-html 渲染html

  v-html:更新标签中的内容/标签
  可以渲染内容中的HTML标签
  - 注意:尽量避免使用，容易造成危险 (XSS跨站脚本攻击)

- V-if 添加与删除

  v-if 是直接决定元素 的 添加 或者删除
  如果在运行时条件很少改变，则使用 `v-if` 较好

- v-show显示与隐藏

  v-show的表达式返回的布尔值 来决定 该元素显示隐藏
  如果需要非常频繁地切换，则使用 `v-show` 较好；

- v-on 绑定事件

  使用: 绑定 v-on:事件名.修饰符="方法名"   可使用 @事件名="方法名的方式"
  语法：
  <button v-on:click="count += 1">增加 1</button>
  <button @click="count += 1">增加 1</button>
  方法不传参数时，event事件对象存在
  传参数时，传入$event获取
  修饰符：
  .once  只执行一次
  .prevent  阻止默认行为

- v-for  循环

  1.循环数组
  语法;
  (item,index) in items item为当前遍历属性数组项的值 index为数组的索引
  item in items   // item为当前遍历属性数组项的值
  
  2.循环对象
  <p v-for="(value,key,i) in per">{{value}}   第一个参数是  值
  第二个是键, 第三个是下标

- 系统指令-v-for-key

  场景:列表数据变动会导致 视图列表重新更新 为了 提升性能 方便更新 需要提供 一个属性 key
  使用: 通常是给列表数据中的唯一值 也可以用索引值
  语法;
   <li v-for="(item,index) in list" :key="index">
  :属性="表达式" => 后面的表达式是变量

- 当v-if和v-for相遇

  v-for 的优先加载 ,所有v-if才能使用v-for的变量.

## DAY2

### 术语解释-指令

- v-bind  绑定标签属性

  v-bind 绑定属性名 ，他原来值就会变为变量，里边再加单引号变作字符串。
  语法:  v-bind:属性名=变量；
  简写：：属性名=变量；
  -------------------------------------------
  :class="{ class名称": 布尔值 }"特定用法，加花括号里边就不是变量，是一个class类名，由后边的布尔值变量控制显隐。
  注意**: 绑定class和原生class会进行合并
  --------------------------------------------
  class-数组语法：:class="[class变量1,class变量2..]"
  --------------------------------------------
  绑定style-对象语法：
  语法: :style="{css属性名: 变量}"
  注意 css属性名 例如 font-size要写成 fontSize  以此类推
  
  原有的style不受影响
  但是 后面的样式会顶替到前面的样式 因为合并时原生样式在前
  --------------------------------------------
  v-bind-绑定style-数组语法：
  语法:style = '[对象，对象]'

-  v-model  双向绑定

  语法：v-model =  “vm变量”；
  数据发生变化可以更新到界面 => 响应式数据
  作用:表单元素 的绑定
  v-mondel =>表单value
  多个的checkbox  绑定的值是个 数组 数组里面是选项

- v-cloak  解决页面闪烁问题

  将代码：v-cloak] {
   display: none;
  }写入style里
  将v-cloak  写入要管理视图的标签内即可。

-  v-once 只渲染一次视图

  作用: 使得所在元素只渲染一次
  场景:静态化数据 。

- v-ref  绑定dom元素节点

  语法：
  <input type="text" ref="myInput" /> // 定义ref
  
  focus() {
  this.$refs.myInput.focus();
  }  // 获取dom对象 聚焦

###  过滤器

场景: data中的数据格式(日期格式/货币格式/大小写等)需要数据时
使用位置:{{}}和v-bind="表达式 | 过滤器名称"
具体用法:{{msg | 过滤器名字}}

- 全局过滤器

  过滤器不会影响原来的值
  Vue.filter('该过滤器的名字',(要过滤的数据)=>{return 对数据的处理结果});,
  全局: 在new Vue上面 Vue.filter()  => 所有实例都可以使用
  在视图中通过{{数据 | 过滤器的名字}}或者v-bind使用过滤器
  注意** 可使用多种表达式形式  全局过滤器 多个Vue实例可共享使用
  一定带返回值的

- 局部过滤器

  语法：
  filters: {
  toUpper(value) {
    return value.charAt(0).toUpperCase() + value.substr(1);
  }
  }
  注意** 局部过滤器只能用在当前Vue实例视图上
  (key)过滤器的名字: (value)(要过滤的数据)=>{return 过滤的结果}
  在视图中使用过滤器:  {{被过滤的数据 | 过滤器的名字}}

- moment 时间模块

  语法：formatDate(value, format) {
    return moment(value).format(format);
  }  // 过滤器代码

- 过滤器传参和串联使用

  过滤器可以传递参数,第一个参数永远是前面传递过来的过滤值。
  过滤器也可以多个串行起来并排使用,
  串联语法：
  	<p>{{ text | toUpper(2) }}</p> 后边过滤器过滤的是前边过滤器过滤后的值。

### 拓展内容

toUpperCase :字符串里的英文字母转成大写。
string.charAt() 方法可返回指定位置的字符。
string.substr():截取字符串
debugger  调试专用
tolowercae  字符串里的英文字母转成小写。
array .map():遍历数组。

## DAY3

### 自定义指令

使用场景:需要对普通 DOM 元素进行操作，这时候就会用到自定义指令 。
分类:全局注册和局部注册
在创建 Vue 实例之前定义全局自定义指令Vue.directive().

- 全局自定义指令

  Vue.directive('指令名称（不加v-)',{
     inserted:funtion(DOM节点名称参数){
             元素调用指令执行里边代码}
  语法:
  Vue.directive('指令的名称',{ inserted: (使用指令的DOM对象) => { 具体的DOM操作 } } );
  
  		实例：Vue.directive("focus", {
  
          inserted(dom) {
  
            dom.focus();
  
          }

- 局部自定义指令

  语法实例：
  		directives: {
  focus: {
    inserted(dom) {
      dom.focus();
    }
  }
  } // 局部自定义指令实现

###  计算属性

计算属性 会比较data变化 => data不变化 =>  从缓存中取值 => data变化 => 重新计算=> 放入缓存
计算属性不需要调用形式的写法  而methods方法必须采用 方法() 调用的形式
语法：
computed: {
nameReverse() {
return this.name
.split("")
.reverse()
.join("");
}
} // 定义计算属性

### 发送网络请求

-  vue-resource

  vue.js插件 ，已经不再维护 不推荐。

- axios 插件

  说明: 既可以在浏览器端又可以在node.js中使用的发送http请求的库，**`支持Promise`**，不支持jsonp
  
  如果遇到jsonp请求, 可以使用插件 `jsonp` 实现
  **不是vue的插件**，可以在任何地方使用，**`推荐`**
  axios ===  new Promise(function(reslove,reject){       
  })
  
  axios().then(拿到返回数据(接口返回数据)).catch(err=> )
  如果reject  .相当于执行失败 =>  执行失败=>不会进入到then => 会进入到promise的catch
  链式调用

### json-server

目的: 没有后端的支撑下 ,前端难以为继,json-server可以快速构建一个后台的接口服务,供前端调用.
mock => 模拟数据
json-server 是一个命令行工具 可以json文件变成接口文件 
json-server遵循**`restful`**接口规则

- 命令及用法

  安装：npm i -g  json-server  （安装node 情况下）
  json-server --watch json文件（开启服务，有笑脸提示）
  文件配置：数据库 { 数据表名（字符串）[{数据 },{数据}、、、、、], 其他表[、、、、]}

### RESTFUL接口规则

RESTful是一套**`接口设计规范
用**`不同的请求类型`**发送**`同样一个请求标识`** 所对应的处理是`不同的`
同样的请求标识 => 相同的请求地址**`url`**
通过Http请求的不同类型(POST/DELETE/PUT/GET)来判断是什么业务操作(CRUD )
CRUD => 增删改查 => C =>Create(增)  R => Read(查)    U => UPDATE(改)  D =>DELETE(删)

- 方法原则举例

  查询数据  GET  /brands 获取db.json下brands对应的所有数据 **`列表`**
  GET /brands/1 查询id=1数据 **`单条`
  删除数据 DELETE   /brands/1 删除id=1数据
  修改数据 PUT  /brands/1 请求体对象 {name:'李四' }
  1. 上传/添加 POST /brands 请求体  {name:'李四'}
  > PUT和POST用法一样  请求体 {name:"张三",age: 18, sex:'男'}
  查询 GET /brands?title_like=关键字  -> 模糊搜索

### axios 基本使用

除去post请求 ,所有接口的正确请求返回码都是**`200`** 但是post的状态码是**`201`**
本地引入axios文件
语法：
axios.get(url).then((res) => {
// 请求成功 会来到这  res响应体
}).catch((err) => {
// 请求失败 会来到这 处理err对象
})	
url :请求地址
method :请求方式
data: post 请求发送的数据。
注意： axios中data为body参数   路径参数 url?id=3  params

### 实例选项   watch  监听数据

场景: 当需要根据**`数据变化`** 进行相应业务操作,且该操作是**`异步操作`**时,**`计算属性不能再使用`**,可以使用监听watch特性
watch=> 是监听data数据 中数据项的变化对象 => data中数据变化  => watch 监控函数执行 =>监控函数 
监控函数 =>  newValue.oldValue
语法：
watch: {//newValue是最新的值 oldValue为后面的旧值city(newValue, oldValue) {this.list = this.list.map(item => ({city: item.name,count: newValue}));}}

### 组件

组件是一个特殊的vue实例。里边构成和vue实例相近。
和实例相似之处:   data/methods/computed/watch  等一应俱全  
**注意** 值得注意的是  data和Vue实例的区别为 组件中data为一个函数   没有el选项

- 全局组件

  语法：
  Vue.component('组件名'，{
  		template: `<div>
          {{count}}
          </div>`, 只有一个根元素
  		data() {
            return {
              count: 1
            };
          }
  }
  data 是一个函数 带返回值的函数   返回值是一个对象 对象里面的内容就是我们的data数
  =========================
  组件命名规范：
  组件名称 => 不能和html元素标签重名
  
   组件命名规范 推荐 abc(单词全小写)  abc-d(menu-counter)(全小写)

- 局部组件

  语法：
  		new Vue({el: "#app",
  		data: {},
  		methods:{ },
  		components:{ "content-a": {     					   			template: `
  	<div> {{count}} </div>`,
   data() {   return {     count: 1   }; }
  组件名称都带双引号。

## DAY4

### promise  回顾

为了接解决回调地狱 ，
原理实现：
promise 对象里的函数有一个异步请求，同时里边还有一个判断，接受成功则抛出这个异步请求的结果函数
使用then 进行下一步操作。链式调用解决回调地狱不美观。

###  组件的嵌套

全局组件可以在任何的地方使用。（局部组件的template里边使用
局部组件的嵌套，子组件只能在父组件的template里边使用。（爷孙关系也不行）
语法：
var comA = {
template: `<div>我是子组件</div>`
};
var parentA = {
template: `<div>
我是父组件
<com-a></com-a>
</div>`,
components: {'com-a': comA }
};
var vm = new Vue({
el: "#app",
data: {},
methods: {},
components: {
'parent-a":parentA
}
});

### 组件通信  父传子

1.先找到子组件的HTML标签。（在父组件模板，或页面）
挂一个自定义属性，不能与子组件内部重名。
属性值是变量（父组件的data）
子组件内部定义一个props 的数组（与data，methods同级别）接收自定义变量
注：接收的变量有双引号。

### 组件通信  子传父

先定义一个方法用来触发$enit这个抛出事件
在子组件自己模板呢调用这个方法触发$emit事件
$emit( )两个参数，一个自定义事件，一个是要传的参数
自定义事件只能 自己的HTML标签使用
注册自定义事件后绑定父元素的方法，方法会携带着我们要传的参数进入父元素的方法内，方法的形参就是传过来的数据。

### 单页应用-SPA

single page application => 单页应用 =>Vue为单页应用而生
与传统模式的区别：
传统模式： 每个页面及其内容都需要从服务器**`一次次请求`**  如果网络差, 体验则会感觉很慢。
spa模式, ：`第一次加载`** 会将所有的资源都请求到页面 模块之间切换**`不会再请求`**服务器
SPA优点:
速度快,**`切换模块不需要经过网络请,用户体验好,因为前段操作几乎感受不到网络的延迟.
完全**`组件化`**开发 ,由于**`只有一个页面`**,所以原来属于一个个页面的工作被归类为一个个**`组件`**
缺点：
**`首屏加载慢`**->**`按需加载`** 不刷新页面 之请求js模块
**`不利于SEO`**->**`服务端渲染`**(node->自己写路由->express-art-template+res.render()
开发难度高(框架) 相对于传统模式,有一些学习成本和应用成本

- 原理

  SPA要能**`记忆当前切换的模块`**,并且刷新页面模块依然还在当前视图
  SPA要实现在**`前端切换模块`**时,不能**`引起页面刷新`**,否则页面内容会被重置
  可以通过页面地址的**`锚链接`**来实现（hash值）
  hash(锚链接)位于链接地址 **`#`**之后。
  hash值的改变**`不会触发`**页面刷新。
  hash值是url地址的一部分,会存储在页面地址上 我们**`可以获取`**到。
  可以通过**`事件监听`**hash值得改变。
  拿到了**`hash值`**,就可以根据不同的hash值进行不同的**`模块切换`**

### vue-router  路由文档

Vue-Router 是 [Vue.js](http://cn.vuejs.org/) 官方的**`路由管理器`**。它和 Vue.js 的核心深度集成，让构建单页面应用变得易如反掌 
实现根据不同的**`请求地址`** 而**`显示不同的组件`**
如果要使用 vue开发项目,**`前端路由`**功能**`必须使用`**vue-router来实现

- 使用步骤

  引入vue-router 
  设置导航  类似于a标签 不完全等同 a：<router-link to="/bj"></router-link>
  容器必须有  承载组件的内容：<router-view></router-view>
  实例化一个vue-router对象
  配置路由选项 => 路由表 => hash值对应的组件或者模块
  将路由实例挂载到Vue实例上。

### vue -router  动态路由

路由规则中增加参数，在path最后增加形参。
通过 <router-link> 传参，在路径上传入具体的值(实参`)。
在组件内部可以使用，**`this.$route`** 获取当前路由对象  并通过**`params`**获取定义的参数**`形参
用来传递参数的

### vue- router- to属性赋值

<!-- <router-link to="/sport">体育</router-link> -->

      <!-- 变量 -->

      <!-- <router-link :to="path">体育</router-link> -->

      <!-- 根据对象name跳转 -->

      <!-- <router-link :to="{name:'abcdefg'}">体育</router-link> -->

      <!-- 根据对象path跳转 -->

      <!-- <router-link :to="{path:'/sport'}">体育</router-link> -->

      <!-- 带参数的跳转 -->

      <router-link :to="{name:'abcdefg',params:{a:1}}">体育</router-link>

### vue- router-tag 改变标签属性

语法：<router-link  tag = “标签名”></router-link>

### 导航标签样式重命名

在 实例化router  ：linkActiveClass: "active",  默认样式是roter给的。

### vue -router  重定向

重定向 拦截谁就在谁的路由中写`** redirect
`你希望它去哪就写谁的`** 地址 **`pat
实例：
{
path: "/sport",
redirect: "/news", // 强制跳转新闻页
component: {
template: `<div>体育</div>`
}
},

### vue- router  编成式导航

路由对象的实例方法 有 push  replace, go() 
 push 方法 相当于往历史记录里推了一条记录 如果点击返回 会回到上一次的地址  相当于 to属性
go(数字) 代表希望是前进还是回退,当数字大于0 时 就是前进 n(数字)次,小于0时,就是后退n(数字)次
写在自己组件的方法里 才能生效
语法：this.$router.push(path)

### vue-router-routerlink-tag-激活样式

class名称是可以设置的
可以给  选中的router-link-active设置样式

### vue中的css过度和动画

标签必须有显示与隐藏属性 v-if  v-show
transition标签是一个组件,Vue提供的 我们必须用它来包裹我们的组件 =>我们的组件必须有显示隐藏这个动作.
v-enter：定义进入过渡的开始状态。有name  用name -enter
v-leave-active：定义离开过渡生效时的状态/定义进入过渡生效时的状态。（过渡）
v-leave-to: 2.1.8版及以上 定义离开过渡的结束状态。

## DAY5

### 路由嵌套

一个导航下边还有一个导航，那么第一个导航就是一级路由  他的容器写在可视化界面。
导航项里嵌套的那个小导航就是二级路由。他的导航写在一级导航项的组件template里边。
二级路由的路由表，写在所属一级路由项 和path 、component同级的children ，格式与routes一样，是一个数组对象，每个对象里边又有path、component。
path 带‘  / ’  就写绝对路径（一级路由/path),不带（/)就直接写path就可以。

### v-cli脚手架

介绍: vue-cli是一个**`辅助开发工具`=> **`代码编译`** + **`样式`** + **`语法校验`** + **`输出设置`** + 其他 .
中间过程 => 转化过程(Vuejs/脚手架) => 浏览器可识别,支持
作用: 可以为开发者提供一个**`标准`**的**`项目开发结构`** 和配置  **开发者**不需要再关注
vue-cli 一个**`命令行`**工具,最新版本也支持图形化操作,可快速搭建大型网页应用
使用vue-cli =>  综合性服务 => nodejs开发的=> 五花八门=> 开发期间 暂时先不关注

- 2.0 和3.0 安装命令

  npm i -g @vue/cli  全局安装脚手架  默认安装的最新版本 3.0+
  # 注册淘宝镜像$ npm install -g cnpm --registry=https://registry.npm.taobao.org# 执行完毕之后 cnpm 完全可替代npm 
  vue -V  // 查看脚手架版本号
  npm install -g @vue/cli-init  // 安装桥接工具 将2.0的功能补齐到目前的脚手架上
  注意** vue-cli的命令行 关键字 是**vue**
  简单业务用2.0   复杂业务用3.0.

- 2.0 创建项目

  vue  init webpack-simple heroes（webpack-simple 为模板名，heroes为项目名）
  nmp install   (安装依赖  第三方辅助模块）

- 项目目录解释

  node_modules => 存放包依赖文件 (不能提交)
  .bablelrc=>存放 babel编译的配置信息 => ES7/ES6 => ES5 => ES3
  .editorconfig => 存放编辑器的配置信息
  .gitignore => git忽略文件  => 忽略**`不需要提交`**的文件
  index.html => 单页应用的html
  package.json => 用于存放依赖信息 及 其他项目信息 => dependencies/devDependencies
  dependencies  运行时依赖  => 项目上线之后依然再用 => axios /vuejs
  devDependencies 开发时依赖  =>开发时 需要用的=> vue-cli =>  上线时不再需要 =>脚手架
  	dev   运行依赖
   build  最后编译

- ES6模块的导入和导出

  导出：export default vue //导出对象 vue
  导入：import vue from 'vue'
  ES6**提供**import**   别名   **from**  路径(包名)   语法 来引入 组件   引入
  提供 **export**  **default**  {     } 语法来导出组件  导出
  ，上面的代码 换成import 
  import 路径  => 引入css文件/less文件/sass文件

*XMind: ZEN - Trial Version*