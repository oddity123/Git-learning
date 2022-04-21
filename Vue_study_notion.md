# 简介

Vue是一套构建用户界面的渐进式框架。
Vue 只关注视图层， 采用自底向上增量开发的设计。
Vue 的目标是通过尽可能简单的 API 实现响应的数据绑定和组合的视图组件。
# 理解
App.vue作为项目的主入口应用, 以它为根节点进行渲染
![image.png](https://cdn.nlark.com/yuque/0/2022/png/26464274/1650538562706-6ba76ce9-c7d9-4de7-8f8d-abe384c712cf.png#clientId=u142f7384-aaa9-4&crop=0&crop=0&crop=1&crop=1&from=paste&height=200&id=u19f8a704&margin=%5Bobject%20Object%5D&name=image.png&originHeight=252&originWidth=655&originalType=binary&ratio=1&rotation=0&showTitle=false&size=22869&status=done&style=none&taskId=u1d738d78-14af-41bf-9627-34a0d1a306b&title=&width=520)![image.png](https://cdn.nlark.com/yuque/0/2022/png/26464274/1650538627680-d85c3c59-d74f-4a56-8f0d-0b2636357eed.png#clientId=u142f7384-aaa9-4&crop=0&crop=0&crop=1&crop=1&from=paste&height=391&id=ue70bf3bb&margin=%5Bobject%20Object%5D&name=image.png&originHeight=528&originWidth=982&originalType=binary&ratio=1&rotation=0&showTitle=false&size=56425&status=done&style=none&taskId=u60e890d7-68d9-4ad3-b0ce-2e47d813601&title=&width=727)
```javascript
import { createApp } from 'vue'
import App from './App.vue'

createApp(App).mount('#app')
```
mout将vue组件挂载到id为app的元素上, 也就是将上面的那棵树挂载在app上面
```vue
<template>
  <img alt="Vue logo" src="./assets/logo.png">
  <HelloWorld msg="Welcome to Your Vue.js App"/>
  <bc/>
  <yesno/>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
import bc from "./components/button_counter.vue"
import yesno from "./components/Yes_or_NO.vue"

export default {
  name: 'App',
  components: {
    HelloWorld,
    bc,
    yesno,

  }
}
</script>
```
从中可以看到App文件将HelloWorld, button_counter, Yes_or_NO, 组件引入, 在自己的`<template></template>`中使用引入的组件, 直接可以以标签的方式使用, 提高了代码的服用程度
# 使用

1. 直接去官网下载Vue.js
1. 使用CDN方法, 我的理解就是Vue.js这些封装好的javaScript存放在CDN上, CDN, Content Dilivery Network, 即内容分发网络, 也就是根据用户的位置分配最近的资源, 用户访问资源的时候,, 不是直接访问源站, 而是访问"最近"
的一个CDN节点, 也就是边缘节点, 就是缓存了源站内容的的代理服务器, 通过中心平台实现了负载均衡, 减少了源站的访问压力, 提高用户的访问速度和命中率

![image.png](https://cdn.nlark.com/yuque/0/2022/png/26464274/1650355514391-ab690931-e8c2-4400-b874-2fdadb015e1e.png#clientId=u8651444c-a814-4&crop=0&crop=0&crop=1&crop=1&from=paste&height=266&id=u03610151&margin=%5Bobject%20Object%5D&name=image.png&originHeight=382&originWidth=640&originalType=url&ratio=1&rotation=0&showTitle=false&size=80946&status=done&style=none&taskId=ua7938161-9223-4d96-b966-756c8e87dec&title=&width=446)
# 创建项目
```vue
$ vue init webpack runoob-vue3-test
# 这里需要进行一些配置，默认回车即可
? Project name runoob-vue3-test
? Project description A Vue.js project
? Author runoob <test@runoob.com>
  ? Vue build standalone
  ? Install vue-router? Yes
  ? Use ESLint to lint your code? Yes
  ? Pick an ESLint preset Standard
  ? Set up unit tests Yes
  ? Pick a test runner jest
  ? Setup e2e tests with Nightwatch? Yes
  ? Should we run `npm install` for you after the project has been created? (recommended) npm
  
  vue-cli · Generated "runoob-vue3-test".
  
  
  # Installing project dependencies ...
# ========================
```
进入项目, 安装并运行
```bash
$ cd runoob-vue3-test
$ cnpm run dev
DONE  Compiled successfully in 2558ms          

 I  Your application is running here: http://localhost:8080
```
这里的`cnpm run dev`, 如下
![image.png](https://cdn.nlark.com/yuque/0/2022/png/26464274/1650366164487-0d2b5a5f-4a76-40e7-9b47-b2e9dea4c553.png#clientId=u8651444c-a814-4&crop=0&crop=0&crop=1&crop=1&from=paste&height=354&id=u6f08e24b&margin=%5Bobject%20Object%5D&name=image.png&originHeight=489&originWidth=1034&originalType=binary&ratio=1&rotation=0&showTitle=false&size=67503&status=done&style=none&taskId=u36e25984-ff1b-4c2c-8f0c-41832b75db3&title=&width=748)
创建一个Vue项目`vue create project_name`, 然后进入项目中, 使用`npm run serve`运行.
# 项目打包
打包Vue项目使用如下的命令
```bash
cnpm run build
```
完成以后会在Vue项目下生成一个`dist`目录, 该目录包含index.html和static目录, static目录包含了静态文件js, css, 图片等.
双击index.html, 显示空白, 需要修改index.html中的js, css的路径, 原来的是绝对路径, 将其修改为相对路径
# 项目目录解析

- public: 				公共资源目录
- node_modules: 		npm加载的项目依赖模块
- src:					开发的主要目录
   - assets：			 放置图片，如logo
   - components：	 组件文件，可以不用
   - App.vue：		 项目入口文件，也可以直接将组件写在这里，不使用上一个文件夹
   - main.js：			 项目的核心文件
- package.json：		项目配置文件
#  起步
```vue
<!DOCTYPE html>
<html>
<head>
<meta charset="utf-8">
<title>Vue 测试实例 - 菜鸟教程(runoob.com)</title>
<script src="https://unpkg.com/vue@next"></script>
</head>
<body>
<div id="hello-vue" class="demo">
  {{ message }}
</div>

<script>
const HelloVueApp = {
  data() {
    return {
      message: 'Hello Vue!!'
    }
  }，
  methods:{
    increment(){
      
    }
  }
}

Vue.createApp(HelloVueApp).mount('#hello-vue')
</script>
</body>
</html>
```

-  第六行引入Vue的js文件
- 22行的mount（'#hello-vue'）将vue应用HelloVueApp挂载到id="hello-vue"的div上
- {{ }}用于输出对象属性和函数的返回值
- data选项是一个函数，vue在创建新组件实例的时候调用此函数。它返回一个对象，然后vue通过响应性系统将其包裹起来，以$data的形式存储在组件实例中
# Vue3模版语法
##  插值
###  文本
最常见的形式就是{{message}}
其中的内容会被替代为对应组件实例中message属性的值，如果message的值改变，那么其中的内容也会改变
使用v-once指令一次性地插值，数据改变，此内容不会改变
```vue
<span v-once>这个将不会改变: {{ message }}</span>
```
###  html
```vue
<div id="example1" class="demo">
    <p>使用双大括号的文本插值: {{ rawHtml }}</p>
    <p>使用 v-html 指令: <span v-html="rawHtml"></span></p>
</div>
 
<script>
const RenderHtmlApp = {
  data() {
    return {
      rawHtml: '<span style="color: red">这里会显示红色！</span>'
    }
  }
}
 
Vue.createApp(RenderHtmlApp).mount('#example1')
</script>
```
### 属性
HTML属性中的值使用v-bind：指令，简写为 :属性名
```vue
<div id="app">
  <label for="r1">修改颜色</label><input type="checkbox" v-model="use" id="r1">
  <br><br>
  <div v-bind:class="{'class1': use}">
    v-bind:class 指令
  </div>
</div>
    
<script>
const app = {
  data() {
    return {
      use: false
    }
  }
}
 
Vue.createApp(app).mount('#app')
</script>
```
v-on指令，用于监听DOM事件
```vue
<!-- 完整语法 -->
<a v-on:click="doSomething"> ... </a>

<!-- 缩写 -->
<a @click="doSomething"> ... </a>
```
###  表达式
提供完全的js表达式的支持
```vue
<div id="app">
    {{5+5}}<br>
    {{ ok ? 'YES' : 'NO' }}<br>
    {{ message.split('').reverse().join('') }}
    <div v-bind:id="'list-' + id">菜鸟教程</div>
</div>
    
<script>
const app = {
  data() {
    return {
      ok: true,
      message: 'RUNOOB!!',
      id: 1
    }
  }
}
 
Vue.createApp(app).mount('#app')
</script>
```
## 用户的输入
在input中，我们可以使用v-model指令来实现双向数据绑定
v-model指令用在input，select，textarea等表单控件元素上创建双向数据绑定，根据表单上的值，自动更新绑定元素的值。
```vue
<!DOCTYPE html>
<html>
<head>
<meta charset="utf-8">
<title>Vue 测试实例 - 菜鸟教程(runoob.com)</title>
<script src="https://unpkg.com/vue@next"></script>
</head>
<body>
  
<div id="app">
    <p>{{ message }}</p>
    <input v-model="message">
</div>

<script>
const app = {
  data() {
    return {
      message: 'Runoob!'
    }
  }
}
</script>
</body>
</html>
```
# Vue3组件
组件是Vue3最强大的功能之一, 可以扩展HTML元素, 封装可重用代码, 组件系统可以用独立可复用的小组件来构建大型应用, 几乎所有的应用界面可以抽象为一个组件树
![image.png](https://cdn.nlark.com/yuque/0/2022/png/26464274/1650434376049-52b41f34-e2ba-4649-abd1-81582d203361.png#clientId=ub1206f3f-57c8-4&crop=0&crop=0&crop=1&crop=1&from=paste&height=256&id=ucae94c61&margin=%5Bobject%20Object%5D&name=image.png&originHeight=544&originWidth=1406&originalType=url&ratio=1&rotation=0&showTitle=false&size=32910&status=done&style=none&taskId=u545328e6-b376-4a6b-98e2-71d1bd0df29&title=&width=662)
每个vue应用通过`createApp`函数创建, 传递给其的选项用于配置根组件, 当我们挂载一个应用时, 该组件被用作渲染的起点.
```javascript
const RootComponent = { /* 选项 */ }
const app = Vue.createApp(RootComponent)
const vm = app.mount('#app')
```
## 全局组件
注册一个全局组件语法如下
```javascript
const app = Vue.createApp({...})
app.component('my-component-name', {
  /* ... */
})
```
`my-component-name`为组件名, ` /* ... */`部分为配置选项, 可以使用如下的方式调用组件:
`<my-component-name></my-component-name>`
实例如下:
```javascript
// 创建一个Vue 应用
const app = Vue.createApp({})

// 定义一个名为 button-counter 的新全局组件
app.component('button-counter', {
  data() {
    return {
      count: 0
    }
  },
  template: `
  <button @click="count++">
  点了 {{ count }} 次！
  </button>`
})
app.mount('#app')
</script>
```
然后在引入的地方可以直接使用其组件.`<button-counter></button-counter>`

在开发过程中, 更多的是用一个*.vue文件来保存一个组件, 上面的button-counter组件创建如下
![image.png](https://cdn.nlark.com/yuque/0/2022/png/26464274/1650450736899-d155e028-1e9f-4703-a98e-637605f63389.png#clientId=ub1206f3f-57c8-4&crop=0&crop=0&crop=1&crop=1&from=paste&height=457&id=u10664ac7&margin=%5Bobject%20Object%5D&name=image.png&originHeight=603&originWidth=1110&originalType=binary&ratio=1&rotation=0&showTitle=false&size=75465&status=done&style=none&taskId=u2455ef42-4d70-45bb-b7e4-4011fff4f27&title=&width=841)
`export default`表示导出默认的接口, 我的理解是将其封装成一个组件, 名字叫button_counter, 用于从模块中导出函数, 对象或者原始值, 以便其他的程序可以通过import语句使用它, 暴露出其中的方法, 属性等.

然后就可以在另外的组件中使用它, 如下
![image.png](https://cdn.nlark.com/yuque/0/2022/png/26464274/1650451453541-670c0467-080e-46ae-bbaf-50f2deb85072.png#clientId=ub1206f3f-57c8-4&crop=0&crop=0&crop=1&crop=1&from=paste&height=561&id=u18a21c0d&margin=%5Bobject%20Object%5D&name=image.png&originHeight=750&originWidth=1119&originalType=binary&ratio=1&rotation=0&showTitle=false&size=95959&status=done&style=none&taskId=u563f102e-d53f-4947-84d6-4246780053d&title=&width=837)
在App.vue入口文件中使用该组件, 要import导入其组件, 并且在第15行添加其导入的组件
## 局部组件
```vue
<div id="app">
    <runoob-a></runoob-a>
</div>
<script>
var runoobA = {
  template: '<h1>自定义组件!</h1>'
}
 
const app = Vue.createApp({
  components: {
    'runoob-a': runoobA
  }
})
 
app.mount('#app')
</script>
```
runoob组件只能在本实例中使用
## Prop
prop是子组件接受父组件传递过来的数据的一个自定义属性, 父组件的数据需要通过props把数据传给子组件, 子组件需要显示地用props选项声明"prop"
```vue
<div id="app">
  <site-name title="Google"></site-name>
  <site-name title="Runoob"></site-name>
  <site-name title="Taobao"></site-name>
</div>
 
<script>
const app = Vue.createApp({})
 
app.component('site-name', {
  props: ['title'],
  template: `<h4>{{ title }}</h4>`
})
 
app.mount('#app')
</script>
```
### Prop验证
组件可以为props指定验证要求
```javascript
Vue.component('my-component', {
  props: {
    // 基础的类型检查 (`null` 和 `undefined` 会通过任何类型验证)
    propA: Number,
    // 多个可能的类型
    propB: [String, Number],
    // 必填的字符串
    propC: {
      type: String,
      required: true
    },
    // 带有默认值的数字
    propD: {
      type: Number,
      default: 100
    },
    // 带有默认值的对象
    propE: {
      type: Object,
      // 对象或数组默认值必须从一个工厂函数获取
      default: function () {
        return { message: 'hello' }
      }
    },
    // 自定义验证函数
    propF: {
      validator: function (value) {
        // 这个值必须匹配下列字符串中的一个
        return ['success', 'warning', 'danger'].indexOf(value) !== -1
      }
    }
  }
})
```
# 计算属性
```vue
<!DOCTYPE html>
<html>
<head>
<meta charset="utf-8">
<title>Vue 测试实例 - 菜鸟教程(runoob.com)</title>
<script src="https://unpkg.com/vue@next"></script>
</head>
<body>
<div id="app">
  <p>原始字符串: {{ message }}</p>
  <p>计算后反转字符串: {{ reversedMessage }}</p>
</div>
    
<script>
const app = {
  data() {
    return {
      message: 'RUNOOB!!'
    }
  },
  computed: {
    // 计算属性的 getter
    reversedMessage: function () {
      // `this` 指向 vm 实例
      return this.message.split('').reverse().join('')
    }
  }
}
 
Vue.createApp(app).mount('#app')
</script>
```
第23行声明了一个计算属性reversedMessage, 提供的函数将用作vm.reversedMessage的getter, reversedMessage依赖于vm.message, 在vm.message改变时, reversedMessageu也会更新
# 监听属性
异步加载中使用watch
```vue
<!-- 因为 AJAX 库和通用工具的生态已经相当丰富，Vue 核心代码没有重复 -->
<!-- 提供这些功能以保持精简。这也可以让你自由选择自己更熟悉的工具。 -->
<script src="https://cdn.jsdelivr.net/npm/axios@0.12.0/dist/axios.min.js"></script>
<script>
  const watchExampleVM = Vue.createApp({
    data() {
      return {
        question: '',
        answer: '每个问题结尾需要输入 ? 号。'
      }
    },
    watch: {
      // 每当问题改变时，此功能将运行，以 ? 号结尾
      question(newQuestion, oldQuestion) {
        if (newQuestion.indexOf('?') > -1) {
          this.getAnswer()
        }
      }
    },
    methods: {
      getAnswer() {
        this.answer = '加载中...'
        axios
          .get('https://yesno.wtf/api')
          .then(response => {
            this.answer = response.data.answer
          })
          .catch(error => {
            this.answer = '错误! 无法访问 API。 ' + error
          })
      }
    }
  }).mount('#watch-example')
</script>
```
其中使用了axios, 它是一个基于Promise的HTTP库, 可以用在node.js中. axios使用通过Promise实现对ajax技术的一种封装, 就像JQuery对ajax封装一样, ajax实现了局部数据的刷新, axios有的ajax都有, ajax有的axios不一定有.
# 样式绑定
v-bind:class设置一个对象, 从而动态的切换class
```vue
<!DOCTYPE html>
<html>
<head>
<meta charset="utf-8">
<title>Vue 测试实例 - 菜鸟教程(runoob.com)</title>
<script src="https://unpkg.com/vue@next"></script>
<style>
.static {
	width: 100px;
	height: 100px;
}
.active {
	background: green;
}
.text-danger {
	background: red;
}
</style>
</head>
<body>
<div id="app">
    <div class="static" :class="classObject"></div>
</div>

<script>
const app = {
    data() {
      return {
         classObject: {
            'active': false,
            'text-danger': true
         }
      }
   }
}
Vue.createApp(app).mount('#app')
</script>
</body>
</html>
```

直接绑定一个数据
```vue
<!DOCTYPE html>
<html>
<head>
<meta charset="utf-8">
<title>Vue 测试实例 - 菜鸟教程(runoob.com)</title>
<script src="https://unpkg.com/vue@next"></script>
<style>
.static {
	width: 100px;
	height: 100px;
}
.active {
	background: green;
}
.text-danger {
	background: red;
}
</style>
</head>
<body>
<div id="app">
    <div class="static" :class="{ 'active': isActive, 'text-danger': hasError }">
    </div>
</div>

<script>
const app = {
    data() {
      return {
         isActive: false,
         hasError: true
      }
   }
}

Vue.createApp(app).mount('#app')
</script>
</body>
</html>
```

绑定一个数组
```vue
<div class="static" :class="[activeClass, errorClass]"></div>
```

三元表达式
```vue
<div id="app">
  <div class="static" :class="[isActive ? activeClass : '', errorClass]"></div>
</div>
```
## style内联样式
:style设置
```vue
<!DOCTYPE html>
<html>
<head>
<meta charset="utf-8">
<title>Vue 测试实例 - 菜鸟教程(runoob.com)</title>
<script src="https://unpkg.com/vue@next"></script>
</head>
<body>
<div id="app">
    <div :style="styleObject">菜鸟教程</div>
</div>

<script>
const app = {
  data() {
    return {
      styleObject: {
          color: "red",
          fontSize: "30px"
      }
    }
  }
}

Vue.createApp(app).mount('#app')
</script>
</body>
</html>
```
# 事件处理
使用v-on指令来监听DOM事件, 从而执行js代码, 缩写为@

接受一个定义的方法
```vue
<div id="app">
  
  <!-- `greet` 是在下面定义的方法名 -->
  <button @click="greet">点我</button>
  
  <button @click="say('what')">Say what</button> 	<!-- 内联JavaScript语句 -->
  
  <button @click="one($event), two($event)">			<!-- 绑定多个方法 -->
    </div>
  
  <script>
    const app = {
      data() {
        return {
          name: 'Runoob'
        }
      },
      methods: {
        
        greet(event) {
          // `methods` 内部的 `this` 指向当前活动实例
          alert('Hello ' + this.name + '!')
          // `event` 是原生 DOM event
          if (event) {
            alert(event.target.tagName)
          }
        },
        
        say(message) {
          alert(message)
        },
        
        one(event) {
          alert("第一个事件处理器逻辑...")
        },
        two(event) {
          alert("第二个事件处理器逻辑...")
        }
      }
    }
    
    Vue.createApp(app).mount('#app')
</script>
```
# 表单
```vue
<div id="app">
  <p>input 元素：</p>
  <input v-model="message" placeholder="编辑我……">
  <p>input 表单消息是: {{ message }}</p>
    
  <p>textarea 元素：</p>
  <textarea v-model="message2" placeholder="多行文本输入……"></textarea>
  <p>textarea 表单消息是:</p>
  <p style="white-space: pre">{{ message2 }}</p>
</div>
 
<script>
const app = {
  data() {
    return {
      message: '',
      message2: '菜鸟教程\r\nhttps://www.runoob.com'
    }
  }
}
 
Vue.createApp(app).mount('#app')
</script>
```
# 路由
```vue
<!DOCTYPE html>
<html>
<head>
<meta charset="utf-8">
<title>Vue 测试实例 - 菜鸟教程(runoob.com)</title>
<script src="https://unpkg.com/vue@next"></script>
<script src="https://unpkg.com/vue-router@4"></script>
</head>
<body>
<div id="app">
  <h1>Hello App!</h1>
  <p>
    <!--使用 router-link 组件进行导航 -->
    <!--通过传递 `to` 来指定链接 -->
    <!--`<router-link>` 将呈现一个带有正确 `href` 属性的 `<a>` 标签-->
    <router-link to="/">Go to Home</router-link>
    <router-link to="/about">Go to About</router-link>
  </p>
  <!-- 路由出口 -->
  <!-- 路由匹配到的组件将渲染在这里 -->
  <router-view></router-view>
</div>

<script>
// 1. 定义路由组件.
// 也可以从其他文件导入
const Home = { template: '<div>Home</div>' }
const About = { template: '<div>About</div>' }
 
// 2. 定义一些路由
// 每个路由都需要映射到一个组件。
// 我们后面再讨论嵌套路由。
const routes = [
  { path: '/', component: Home },
  { path: '/about', component: About },
]
 
// 3. 创建路由实例并传递 `routes` 配置
// 你可以在这里输入更多的配置，但我们在这里
// 暂时保持简单
const router = VueRouter.createRouter({
  // 4. 内部提供了 history 模式的实现。为了简单起见，我们在这里使用 hash 模式。
  history: VueRouter.createWebHashHistory(),
  routes, // `routes: routes` 的缩写
})
 
// 5. 创建并挂载根实例
const app = Vue.createApp({})
//确保 _use_ 路由实例使
//整个应用支持路由。
app.use(router)
 
app.mount('#app')
 
// 现在，应用已经启动了！
</script>
</body>
</html>
```
# Ajax(axios)
## Get请求
```javascript
// 直接在 URL 上添加参数 ID=12345
axios.get('/user?ID=12345')
  .then(function (response) {
  console.log(response);
})
  .catch(function (error) {
  console.log(error);
});

// 也可以通过 params 设置参数：
axios.get('/user', {
  params: {
    ID: 12345
  }
})
  .then(function (response) {
  console.log(response);
})
  .catch(function (error) {
  console.log(error);
  });
```
## Post请求
```javascript
axios.post('/user', {
    firstName: 'Fred',        // 参数 firstName
    lastName: 'Flintstone'    // 参数 lastName
  })
  .then(function (response) {
    console.log(response);
  })
  .catch(function (error) {
    console.log(error);
  });
```
## 请求方法的别名
```javascript
axios.request(config)
axios.get(url[, config])
axios.delete(url[, config])
axios.head(url[, config])
axios.post(url[, data[, config]])
axios.put(url[, data[, config]])
axios.patch(url[, data[, config]])
```
注意：在使用别名方法时， url、method、data 这些属性都不必在配置中指定。

