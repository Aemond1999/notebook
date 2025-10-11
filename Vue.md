# Vue2

## 创建Vue实例

```vue
  <body>
    <div id="root">
    </div>
  </body>

  <script>
    //tips:容器和vue实例是一对一关系
    const vm =new Vue({
      el:"#root",//绑定某个容器
      data:{} //用于存储数据，供某个容器去使用
    })
  </script>
```

## 插值表达式

```vue
<标签 >{{js表达式}}</标签>
js表达式：每个绑定仅支持单一表达式，也就是一段能够被求值的 JavaScript 代码。一个简单的判断方法是是否可以合法地写在 return 后面。
```

## 内容绑定 v-text v-html

```vue
 //v-text
   v-text与{{}}的作用是一样的，都是操控标签的内容区域信息，标签里的内容会被解析成字符串
 //v-html
   v-html 与 v-text、{{ }} 的作用一样，都是操控标签的内容区域,标签的内容会被解析成html
    
	<div id="root">
      <p v-text="a"></p>
      <div v-html="b"></div>
  </div>
 <script>
   new Vue({
      el:"#root",
      data:{
        a:"hello world",
        b:"<h1>hello world</h1>"
      }
    })
 </script>
```

## 数据绑定 v-bind v-model

```js
//v-bind：单向数据绑定
v-bind绑定标签的属性


//v-model：双向数据绑定
只能应用于有value属性的标签

//class绑定
1.第一种
<标签 class"固定样式" :class="classArr"></标签>

new Vue({
  data{
  classArr:["class1","class2"]
	}
})
2.第二种
<标签 class"固定样式" :class="classObj"></标签>

new Vue({
  data{
  classObj:{
  	class1:false,
  	class2:false
		}
	}
})
//style绑定
<标签 class"固定样式" :style="styleObj"></标签>

new Vue({
  data{
  styleObj:{
  	fontSize:"40px"
		}
	}
})
```

## 事件绑定 v-on

```js
v-on支持html中所有已知事件. 如: @click, @submit等, 只不过事件的名字不带on

//鼠标事件
onclick       单击鼠标                             
dblclick      双击鼠标                             
mousedown     按下鼠标按钮                         
mouseup       松开鼠标按钮                         
mousemove     鼠标指针移动                         
mouseover     鼠标指针移至元素之上(不可以阻止冒泡) 
mouseout      当鼠标指针移出元素(不可以阻止冒泡)   
mouseenter    鼠标指针移至元素之上(可以阻止冒泡)   
mouseleave    鼠标指针移出元素(可以阻止冒泡)       
mousewheel    转动鼠标滚轮                         
scroll        滚动元素的滚动条 
//键盘事件
keydown       当按下按键时运行脚本。       
keyup         当松开按键时运行脚本。       
keypress      当按下并松开按键时运行脚本。 
//绑定某个按键
v-on:keydown.按键名
//表单事件
blur          当元素失去焦点时运行脚本。     
focus         当元素获得焦点时运行脚本。     
change        当元素改变时运行脚本。         
input         当元素获得用户输入时运行脚本。 
invalid       当元素无效时运行脚本。         
select        当选取元素时运行脚本。         
submit        当提交表单时运行脚本。         
//窗口事件
blur              窗口失去焦点时                                           
focus             窗口获得焦点                                             
load              文档加载之后                                             
DOMContentLoaded  DOM加载之后(不包括样式,图片,flash)仅支持以监听器绑定事件 
resize            调整窗口大小时                                           
storage           当 Web Storage 区域更新时（存储空间中的数据发生变化时） 

//事件修饰符
.stop ：阻止事件冒泡, 也就是当前元素发生事件,但当前元素的父元素不发生该事件
.prevent ：阻止默认事件发生
.capture ：使用事件捕获模式, 主动获取子元素发生事件, 把获取到的事件当自己的事件执行
.self ：只有元素自身触发事件才执行。（冒泡或捕获的都不执行）
.once ：只执行一次

//语法
<button @事件名.事件修饰符="函数名/vue表达式">点我</button>

```

## 计算属性

```vue
<script type="text/javascript">
    const vm = new Vue({
        el: '#root',
        data: {
            firstName: '熊',
            lastName: '大'
        },
        computed:{
            fullName:{
               get(){
                   return this.firstName +'-'+  this.lastName
               },
               set(value){
               }
            }
        }
    })
</script>
//优点
计算属性是基于缓存实现的，只在计算属性所依赖的数据发生改变时它们才会重新求值，否则访问 计算属性会立即返回之前的计算结果，而不必再次执行函数
//简写：当计算属性不需要set时
fullName(){}
```

## 监视属性

```js
watch:{
  要监视的属性:{
    immediate:false,//立即执行一遍回调函数
    deep:false,//启用深度监视，当属性是对象时，对象内的属性改变，则会触发会调函数
    handler(newValue,oldValue){
      //回调函数
		}
  }
}

//简写
要监视的属性(newValue,oldValue){
  
}
```

## vue数据代理和数据监测

```js
//数据代理
1.通过Object.defineProperty（）把data对象中所有属性添加到vue实例上
2.为每个添加到vm上的属性都指定一个getter和setter
3.在getter/setter内部去操作（读或写）data中对应的属性
```

## v-show v- if 

```js
//v-show：是否展示标签，其实是使用了displa：none
v-show="js表达式" 

//v-if：是否展示标签，清除而非隐藏标签
v-if="js表达式"
v-else-if
v-else
v-if可以和<tempalte><template/>使用，v-show不能
```

## v-for

```js
//遍历数组
v-for="(value,index) in arr"
//遍历对象
v-for="(value,key,index) in obj"
```

## 生命周期

```js
//beforeCreaate
vue实例已经创建，数据监测和数据代理之前被调用
此时无法访问 data、computed、methods 等
//created
可以通过Vm访问到data当中的数据、methods当中配置的方法，发送初始化渲染的请求。
//beforeMount
虚拟dom转换为真实dom之前
//mounted
虚拟dom转换为真实dom之后
//beforeUpadte
数据已经更新，页面还未更新
//updated
数据和页面保持一致
//beforeDestroy
vue销毁前
vue.$destroy()调用后，vue销毁
//destroyed

```

## 组件化

### 多组件文件

```js
//创建组件
const 临时组件名 = Vue.extend({
  template:`<div>xxxx</div>`
	data(){
		return {}
	}
})
//注册组件
1.局部注册组件
new Vue({
  components:{
    组件名:临时组件名
  }
	
})
2.全局注册组件
Vue.components(组件名,临时组件名)
//使用组件
<组件名></组件名>
```

## vue项目结构

```
my-vue-project/
├── node_modules/     # 项目依赖的第三方库 
├── public/           # 静态资源（直接复制到构建输出目录）
│   ├── favicon.ico   # 网站图标
│   └── index.html    # 应用入口 HTML 模板
├── src/              # 核心源码目录
│   ├── assets/       # 静态资源
│   ├── components/   # 可复用组件（如按钮、卡片等独立功能单元）
│   ├── views/        # 页面级组件（路由对应的视图，如 Home.vue
│   ├── router/       # 路由配置（定义路径与组件的映射）
│   │   └── index.js  # 路由实例化文件 
│   ├── store/        # 状态管理（Vuex 或 Pinia）
│   │   └── index.js  # 状态仓库配置 
│   ├── App.vue       # 根组件（包含路由视图 `<router-view>`）
│   └── main.js       # 入口文件（初始化 Vue 实例并挂载）
├── .env              # 环境变量配置
├── package.json      # 项目元数据、依赖和脚本命令f)
└── vite.config.js    # Vite 配置文件（代理、别名等
```

## 过滤器

```js
//全局过滤器
Vue.filter('过滤器名字',function(value){

})
//局部过滤器
 filters:{
   过滤器名(value){}
 }
```

## ref

```js
1、ref 加在普通的元素上，用this.$ref.name 获取到的是dom元素
2、ref 加在子组件上，用this.$ref.name 获取到的是组件实例
```

## props

```js
//简介
Props 是 Vue 组件之间通信的一种方式，通过 Props，父组件可以向子组件传递数据，props中的属性不能被修改,props优先级大与data中的属性
//使用
1.方式一
	export default{
  	props:["属性1",...]
	}
2.方式二
	export default{
		props:{
          "属性1":属性类型
		}
}
3.方式三
	export default{
		props:{
          "属性1":{
            type:属性类型,
            require:是否必要,
            default:默认值  
          }
			}
}
      
```

## mixin



## 插件

### 定义插件

```js
export default{
  install(Vue){ 
  }
}
```

### 使用插件

```js
import plugins from "XXX"
Vue.use(plugins)
```











