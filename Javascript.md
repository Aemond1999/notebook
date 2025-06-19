# Javascript

## 基本数据类型

| 类型                     | 说明                                                         |
| ------------------------ | ------------------------------------------------------------ |
| 字符串型（String）       |                                                              |
| 数值型（Number）         | 特殊数字：  Infinity：正无穷， -Infinity：，负无穷 NaN：非法数字（Not A Number） |
| 布尔型（Boolean）        | 布尔型只能够取真（true）和假（false）两种数值                |
| undefined型（Undefined） | 在使用 var 声明变量但未对其加以初始化时，这个变量的值就是 undefined。undefined值实际上是由null值衍生出来的，所以如果比较undefined和null是否相等，会返回true |
| null型（Null）           | null表示的是一个空的对象                                     |

### 类型转换

#### 转换为String类型

```js
//方法一：toString()
注意：null和undefined这两个值没有toString()方法，如果调用它们的方法，会报错。
//方法二：String()
对于Number和Boolean实际上就是调用的toString()方法，但是对于null和undefined，就不会调用toString()方法，它会将 null 直接转换为 “null”，将 undefined 直接转换为 “undefined”。
//方法三：为任意的数据类型 +""
```

#### 转化为Number类型

```js
//方法一：Number()
1.如果是纯数字的字符串-->数字
2.如果字符串中有非数字的内容-->NaN
3.如果字符串是一个空串或者是一个全是空格的字符串-->0
4.true-->1,false-->0
5.null-->0
5.undefined-->NaN
//方法二：parseInt(),parseFloat:专门用于String
注意：如果对非String使用parseInt()或parseFloat()，它会先将其转换为String然后在操作
```

#### 转换为Boolean类型

```js
//方法一：Boolean()
1.对于数字,除了0和NaN，其余的都是true
2.对于字符串,除了空串，其余的都是true
3.null和undefined都会转换为false
4.对象也会转换为true
```

## 函数

### 创建函数

```js
//1.第一种方法
function 函数名(形参1,形参2,...) {
    语句...
}

//2.第二种方法(不推荐)
var 函数名  = function(形参1,形参2,...) {
    语句....
}
```

## 对象

### 创建对象

```js
//第一种方式
    let person =new Object()
    person.name="丰川祥子"
    person.age=16
    person.fun=function(){
        console.log("hello world")
    }


//第二种方式
    let person={
        name:"千早爱音",
        age:15,
        fun:function(){
            console.log("hello world")
        }
    }


//第三种方式：构造方法
     function Person(name,age){
    this.name=name
    this.age=age
    this.fun=function(){
        console.log("hello world")
    }
  }
    let person1=new Person("长崎素食",16)

```

### 对象属性操作

```js
//1.访问属性
1.对象.属性名
2.对象['属性名']

//2.删除属性
delete 对象.属性名
```

### 原型

```js
//原型简述
1.在声明了一个函数之后，浏览器会自动按照一定的规则创建一个对象，这个对象就叫做原型对象
2.构造函数有一个属性prototype(构造函数独有)指向原型对象;原型对象有一个属性consructor指向构造函数
3.构造函数创造的实例对象有一个属性__proto__指向原型对象
//原型链
1.每个构造函数的Prototype属性指向它的原型对象。每个原型对象也有一个 Prototype属性，那么就形成了一个链式结构，称为原型链。最终，原型链会到达 Object的原型对象
//原型作用
1.这个原型对象添加属性和方法，那么实例就会共享这些在原型中添加的属性和方法。
```

### Object对象方法

#### toString()

| 调用者   | 返回值                                                       |
| -------- | ------------------------------------------------------------ |
| 对象     | [object Object]                                              |
| String   | String自生                                                   |
| Boolen   | 如果布尔值是true，则返回"true"。否则返回"false"。            |
| Array    | 将 Array 的每个元素转换为字符串，并将它们依次连接起来，两个元素之间用英文逗号作为分隔符进行拼接 |
| Date     | 返回日期的文本表示                                           |
| Error    | 返回一个包含相关错误信息的字符串                             |
| Function | 返回如下格式的字符串，其中 functionname 是一个函数的名称<br/>此函数的 toString 方法被调用： “function functionname() { [native code] }” |

#### hasOwnProperty()

检查自身对象是否含有某个方法或属性

#### object.keys()

返回对象的所有属性

#### object.create(proto)

创建一个空对象，令空对象的\__proto__指向参数



### 继承

#### 原型链继承

```js
//让一个构造函数的原型是另一个类型的实例，那么这个构造函数new出来的实例就具有该实例的属性。
function father(){
    this.fun1=function () {
        console.log("fun1")
     }
}

function son(){
}

son.prototype=new father()

//缺点:实例会共享父类的引用变量
```

#### 构造函数继承

```js
function father(money){
     this.money=money
}

function son(){
    father.call(this)
}
//缺点：实例不会共享父类原型上的方法和属性
```

#### 组合继承(推荐)

```js
function father(money){
     this.money=money
}
function son(){
    father.call(this)
}
son.prototype=new father(money);
//缺点：实例继承了两份父类的属性和方法
```

#### 寄生组合继承(推荐)

```js
function father(money){
     this.money=money
}
function son(){
    father.call(this)
}
son.prototype=object.create(father.prototype);
```

### This指向

```js
在全局作用域中：this指向window

在函数作用域中：
1.普通函数中的this：this指向window 

2.对象方法中的this：this就是调用方法的那个对象

3.回调函数中的this：
       1.作为对象方法调用回调函数：this将指向该对象
       2.作为普通函数调用回调函数: this指向window 
       
4.箭头函数中的this：继承外部作用域的this
      
```

## Javascript常用对象和函数

### Array数组对象

```js
1.push()：向数组的末尾添加一个或多个元素
2.pop()：删除并返回数组的最后一个元素
3.unshift()：向数组开头添加一个或多个元素，并返回新的数组长度
4.shift()：删除并返回数组的第一个元素
5.slice(first,end)：切片
6.splice()：删除并返回数组中的指定元素，该方法会影响到原数组，
7.concat()：连接两个或多个数组，并将新的数组返回
8.join("链接符号")：将数组转换为一个字符串，
9.reverse()：反转数组，该方法会直接修改原数组
```

### 函数对象

```js
//apply()和call()
call(),apply()和bind这两个方法都是函数对象的方法，需要通过函数对象来调用
一个对象指定为第一个参数，此时这个对象将会成为函数执行时的this
1.apply(函数内部的this的值,[参数1,参数2,...])

2.call(函数内部的this的值,参数1,参数2,...)

bind 会返回一个新的函数，目标函数在新函数调用时才会执行
3.bind(函数内部的this的值,参数1,参数2,...)->newFunction

```

## 作用域

```js
//变量提升
变量提升是指在代码执行阶段，变量声明（不包括赋值）会被提升到其作用域的最顶端

//函数提升
函数声明也会被提升到其作用域的顶部
```



```js
//1.全局作用域
全局变量是挂载在 window 对象下的变量，所以在网页中的任何位置都可以使用并且访问到这个全局变量。

//2.函数作用域
在 JavaScript 中，函数中定义的变量叫作函数变量，这种变量只能在函数内部才能访问到，所以它的作用域也就是函数的内部，在函数调用时创建，随着函数的运行结束而销毁。

//3.块级作用域
ES6 中新增了块级作用域，最直接的表现就是新增的 let 和 const 关键词，使用这两个关键词定义的变量只能在块级作用域中被访问,典型的块级作用域为if else，for循环
```



## DOM

### window,document,html的关系

```js
1.每个载入浏览器的 HTML 文档都会成为 Document 对象。由下图可以看出，document 是整个 DOM 树的根节点
2.window是BOM中的一个对象
3.document是DOM中的一个对象，同时也是BOM中的一个对象
4.每个载入浏览器的 HTML 文档都会成为 Document 对象。由下图可以看出，document 是整个 DOM 树的根节点
```

### 文档操作

#### 节点(Node)

```js
//概述
节点，是构成我们网页的最基本的组成部分，网页中的每一个部分都可以称为是一个节点。
比如：html标签、属性、文本、注释、整个文档等都是一个节点。
//文档节点
即document对象，代表整个HTML文档，网页中的所有节点都是它的子节点，
//元素节点
HTML中的各种标签
//属性节点
标签中的各种属性。可通过，元素节点.getAttributeNode("属性名")获取元素属性对象
//文本节点
标签内的文本内容
```

#### 节点属性

| 节点类型 | nodeType | nodeName  | nodeValue |
| -------- | -------- | --------- | --------- |
| 文档节点 | 9        | #document | null      |
| 元素节点 | 1        | 标签名    | null      |
| 属性节点 | 2        | 属性名    | 属性值    |
| 文本节点 | 3        | #text     | 文本内容  |

#### 获取元素节点

```js
//通过元素id 来查找元素。
document.getElementById(id)
//通过标签名来查找元素
document.getElementsByTagName(name)	
//通过类名来查找元素
document.getElementsByClassName(name)
//通过CSS选择器选择一个元素
document.querySelector(CSS选择器)。
//通过CSS选择器选择多个元素。
document.querySelectorAll(CSS选择器)
```

#### 获取父子节点

```js
//返回元素的父节点
元素节点.parentNode	。
//返回元素的父元素
元素节点.parentElement	
//parentNode 与 parentElement 的主要区别在元素是 html 时才表现出来
html元素的 parentNode 是 document
html元素的 parentElement 是 null

//返回元素的一个子节点的数组（包含文本Text节点）。
元素节点.childNodes	
//返回元素的一个子元素的集合（不包含文本Text节点）。
元素节点.children	

//返回元素的第一个子节点（包含文本Text节点）
元素节点.firstChild	
//返回元素的第一个子元素（不包含文本Text节点）
元素节点.firstElementChild


//返回元素的最后一个子节点（包含文本Text节点）
元素节点.lastChild。
//返回元素的最后一个子元素（不包含文本Text节点）
元素节点.lastElementChild	


//返回指定元素前一个兄弟节点（包含文本Text节点）
元素节点.previousSibling
//返回指定元素的前一个兄弟元素（不包含文本Text节点）。
元素节点.previousElementSibling


//返回某个元素后面一个兄弟节点（包含文本Text节点）
元素节点.nextSibling
//返回指定元素的后一个兄弟元素（不包含文本Text节点)
元素节点.nextElementSibling	
```

#### 获取元素节点的值

```js
//获取元素所有的文本内容，包括文本节点，子元素和后代元素的文本节点
元素节点.innerText

//获取元素所有的文本节点，注释节点，元素节点等内容。
元素节点.innerHTML。

//获取元素的属性值
元素节点.属性
元素节点.getAttribute(属性)

//获取元素的行内(重点！！！)样式值。
元素节点.style.样式	
```

#### 改变元素的值

```js
//该变元素的 innerText。
元素节点.innerText = new_textcontent

//改变元素的 innerHTML。
元素节点.innerHTML = new_htmlcontent

//改变素的属性值。
元素节点.属性 = new_value
元素节点.setAttribute(attribute, new_value)	

//改变元素的行内样式值。
元素节点.style.样式 = new_style	

```

#### 修改元素

```js
//创建元素节点。
document.createElement(element)	

//创建属性节点。
document.createAttribute(attribute)	
属性节点.value = 属性值
元素节点.setAttributeNode(属性节点)

//直接在元素节点上添加属性
元素节点.setAttribute(attributename,attributevalue)

//创建文本节点。
document.createTextNode(text)

//删除子元素。
元素节点.removeChild(element)

//添加子元素。
元素节点.appendChild(element)

//替换子元素。
元素节点.replaceChild(new_node,old_node)

//在指定的子节点前面插入新的子节点。
元素节点.insertBefore(newChild，Child)	

```

#### 获取元素尺寸

```js
//tips：
当display：none时取不到元素尺寸

//offsetHeight,offsetWeight
表示的是可视区域的尺寸，包含了border元素滚动条(不包含窗口滚动条)

//clientHeight,clientWeight
表示的是可视区域的尺寸，不包含border和元素滚动条和窗口滚动条

//scrollHeight,scrollWeight
表示了所有区域的尺寸，不包含border和元素滚动条和窗口滚动条

//window.innerHeight,innerWeight
表示即浏览器可视区域的尺寸，包括窗口滚动条。

//获取元素偏移量
1.offsetTop/Bottom/Left/Rigtht:距离最近有定位的父元素的距离
2.clientTop/Bottom/Left/Rigtht：border厚度
```

### 事件

#### 窗口事件

| 事件             | 说明                                                     |
| ---------------- | -------------------------------------------------------- |
| onblur           | 窗口失去焦点时                                           |
| onfocus          | 窗口获得焦点                                             |
| onload           | 文档加载之后                                             |
| DOMContentLoaded | DOM加载之后(不包括样式,图片,flash)仅支持以监听器绑定事件 |
| onresize         | 调整窗口大小时                                           |
| onstorage        | /当 Web Storage 区域更新时（存储空间中的数据发生变化时） |

#### 鼠标事件

| 事件         | 说明                                 |
| ------------ | ------------------------------------ |
| onclick      | 单击鼠标                             |
| ondblclick   | 双击鼠标                             |
| onmousedown  | 按下鼠标按钮                         |
| onmouseup    | 松开鼠标按钮                         |
| onmousemove  | 鼠标指针移动                         |
| onmouseover  | 鼠标指针移至元素之上(不可以阻止冒泡) |
| onmouseout   | 当鼠标指针移出元素(不可以阻止冒泡)   |
| onmouseenter | 鼠标指针移至元素之上(可以阻止冒泡)   |
| onmouseleave | 鼠标指针移出元素(可以阻止冒泡)       |
| onmousewheel | 转动鼠标滚轮                         |
| onscroll     | 滚动元素的滚动条                     |

#### 表单事件

| 事件      | 说明                           |
| --------- | ------------------------------ |
| onblur    | 当元素失去焦点时运行脚本。     |
| onfocus   | 当元素获得焦点时运行脚本。     |
| onchange  | 当元素改变时运行脚本。         |
| oninput   | 当元素获得用户输入时运行脚本。 |
| oninvalid | 当元素无效时运行脚本。         |
| onselect  | 当选取元素时运行脚本。         |
| onsubmit  | 当提交表单时运行脚本。         |

#### 键盘事件

| 属性       | 描述                         |
| ---------- | ---------------------------- |
| onkeydown  | 当按下按键时运行脚本。       |
| onkeyup    | 当松开按键时运行脚本。       |
| onkeypress | 当按下并松开按键时运行脚本。 |

#### 事件绑定

```js
//传统事件绑定
element.onclick=function(enent){}
缺点：同一种事件只能绑定一次

//监听器
1.element.addEventListener(tpye,listener,useCapture)
-type:事件类型
-listener:处理函数
-userCapture:true - 事件在捕获阶段执行;false - 事件在冒泡阶段执行，默认是false
2.事件解绑
element.reomveEventListener(tpye,listener)
```

#### 事件委派

```js
//简述
我们希望只绑定一次事件，即可应用到多个的元素上，即使元素是后添加的，我们可以尝试将其绑定给元素的共同的祖先元素，也就是事件的委派。事件的委派，是指将事件统一绑定给元素的共同的祖先元素，这样当后代元素上的事件触发时，会一直冒泡到祖先元素，从而通过祖先元素的响应函数来处理事件。事件委派是利用了事件冒泡，通过委派可以减少事件绑定的次数，提高程序的性能。

//实现事件委托三部曲：
把事件注册给上级
利用事件对象.target找到最先触发事件的元素。
用nodeName判断这个元素是否我们所需要的。
```

#### 事件对象

事件发生后，跟事件有关的一系列信息数据的集合都放到整个对象里面

| 属性                                 | 说明                                                         |
| ------------------------------------ | ------------------------------------------------------------ |
| type                                 | 获取事件类型（例如，“click”、"mousedown"等）                 |
| target                               | 获取触发事件的元素                                           |
| currentTarget                        | 获取绑定了事件的元素                                         |
| clientX和clientY                     | 获取鼠标光标的坐标                                           |
| key                                  | 在键盘事件中，key 属性返回按下的具体字符                     |
| altKey、ctrlKey、shiftKey 和 metaKey | 这些属性用于判断事件触发时是否按下了特定的修饰键             |
| button                               | 用于鼠标事件中，表示按下了哪个鼠标按钮。常见的取值包括(0：左键;1：中键（滚轮）;2：右键) |
| preventDefault()                     | 用于阻止事件的默认行为                                       |
| stopPropagation()                    | stopPropagation()                                            |

## BOM

### Window对象

#### 弹出框

| 方法                             | 说明   | 返回值   |
| -------------------------------- | ------ | -------- |
| alert("sometext")                | 警告框 |          |
| confirm("sometext")              | 确认框 | Boolean  |
| prompt("sometext","defaultText") | 提示框 | 用户输入 |

#### 定时任务

```js
//setTimeout(function, milliseconds)
在等待指定的毫秒数后执行函数。
//clearTimeout(定时器名)
移除定时器

//setInterval(function, milliseconds)
等同于 setTimeout()，但持续重复执行该函数。
//clearInterval(定时器名)
```

#### 其他方法

```js
//window.open(url,name,specs,replace):打开新窗口
url[必选参数]
name[可选参数]:
             _self:当前窗口中打开。
             _blank(默认)：新窗口中打开，窗口name为空字符串。
             name:窗口名
features[ 可选参数]：一个逗号分隔的字符串，指定新窗口的一些特性
                  width：窗口的宽度； 
                  height：窗口的高度；
                  top：窗口距离屏幕顶部的距离，默认0；
                  left：窗口距离屏幕左侧的距离，默认0；
                  menubar：是否显示菜单栏，yes\no；
                  toolbar：是否显示工具栏，yes\no；
                  location：是否显示地址栏，yes\no；
                  status：是否显示状态栏，yes\no；
                  esizable：是否允许用户调整窗口大小，yes\no；
                  scrollbars：是否显示滚动条，yes\no。
replace[可选参数]：一个布尔值，指定新打开的 URL 是否替换当前页面的历史记录
//window.close() ：关闭当前窗口
```

### location对象

Location对象中封装了浏览器的地址栏的信息

#### 常用属性

| 属性     | 说明                          |
| -------- | ----------------------------- |
| href     | href                          |
| origin   | 输出当前地址的来源(协议+域名) |
| protocol | 协议                          |
| hostname | 主机名                        |
| port     | 端口号                        |
| pathname | 路径名                        |
| search   | 当前地址的?后边的参数部分     |

#### 常用方法

| 方法         | 说明                                                         |
| ------------ | ------------------------------------------------------------ |
| assign(url)  | 用来跳转到其它的页面                                         |
| reload(true) | 重新加载当前页面，如果在方法中传递一个true，作为参数，则会强制清空缓存刷新页面 |
| replace(url) | 使用一个新的页面替换当前页面，调用完毕也会跳转页面，它不会生成历史记录，不能使用回退按钮 |

### history对象

History对象可以用来操作浏览器向前或向后翻页

| 方法           | 说明                                             |
| -------------- | ------------------------------------------------ |
| back()         | 回退到上一个页面，作用和浏览器的回退按钮一样     |
| forward()      | 可以跳转到下一个页面，作用和浏览器的前进按钮一样 |
| history.go(n); | 向前向后跳转n个页面                              |

### screen对象

Window 对象的 screen 属性都引用一个 Screen 对象。Screen 对象中存放着有关显示浏览器屏幕的信息

| 属性                 | 描述                                       |
| -------------------- | ------------------------------------------ |
| availHeight          | 返回显示屏幕的高度 (除 Windows 任务栏之外) |
| availWidth           | 返回显示屏幕的宽度 (除 Windows 任务栏之外) |
| height               | 返回显示屏幕的高度                         |
| width                | 返回显示器屏幕的宽度                       |
| bufferDepth          | 设置或返回调色板的比特深度                 |
| colorDepth           | 返回目标设备或缓冲器上的调色板的比特深度   |
| deviceXDPI           | 返回显示屏幕的每英寸水平点数               |
| deviceYDPI           | 返回显示屏幕的每英寸垂直点数               |
| fontSmoothingEnabled | 返回用户是否在显示控制面板中启用了字体平滑 |
| logicalXDPI          | 返回显示屏幕每英寸的水平方向的常规点数     |
| logicalYDPI          | 返回显示屏幕每英寸的垂直方向的常规点数     |
| updateInterval       | 设置或返回屏幕的刷新率                     |
| pixelDepth           | 返回显示屏幕的颜色分辨率（比特每像素       |

## 闭包

```js
//简述
```

## 异常

```js
//1.异常对象属性
1.name	    设置或返回异常类型
2.message	设置或返回错误消息（一条字符串）

//2.异常类型
1.EvalError(废弃)	   在eval()函数中发生的错误，。更新版本的 JavaScript 不会抛出任何 EvalError
2.RangeError	    发生超出数字范围的错误
3.ReferenceError	发生非法引用，引用了尚未声明的变量
4.SyntaxError	    发生语法错误
5.TypeError	        发生类型错误
4.URIError	        在 encodeURI() 中已发生的错误

//3.异常捕获
try {
    // 可能发生异常的代码
} catch (error) {
    // 发生错误执行的代码
} finally {
    // 无论是否出错都会执行的代码
}

//4.异常抛出
在大部分的代码执行过程中，都是出现错误的时候，由浏览器抛出异常，然后程序或者停止执行或被try…catch 捕获。然而有时候我们在检测到一些不合理的情况发生的时候也可以主动抛出错误，请使用 throw 关键字抛出来主动抛出异常。
throw new TypeError("您输入的是一个非法数字！")

//5.自定义异常
function MyError(message) {
    this.message = "注意：这是自定义的错误"
    this.name = "自定义错误";
}
MyError.prototype = new Error();
```

 

## ES6新特性

### Set

```
//属性和方法
size：返回集合的元素个数
add()：增加一个新元素，返回当前集合
delete()：删除元素，返回 boolean 值
has()：检测集合中是否包含某个元素，返回 boolean 值
clear()：清空集合，返回 undefined
keys():返回所有key
values()：返回所有value
```

### Map

```js
//属性和方法
size：返回 Map 的元素个数
set(key,value)：增加一个新元素，返回当前 Map
get(key)：返回键名对象的键值
has(key)：检测 Map 中是否包含某个元素，返回 boolean 值
clear()：清空集合，返回 undefined
//遍历
1. map.forEach((k,v) => {
     console.log(k, v);}

2. for (let [key, value] of map) {
     console.log(key, value);}

3.for (let key of map.keys()) {
     console.log(map.get(key));
 }
4.for (let [key, value] of map.entries()) {
     console.log(key, value);
 }

```

### let

```
不允许重复声明
块儿级作用域
不存在变量提升
```

### rest参数

用于获取函数的实参

```js
// rest 参数必须是最后一个形参
function minus(a, b, ...args) {
    console.log(a, b, args);
}
```

### spread 扩展运算符

也是三个点（…），它好比 rest 参数的逆运算，将一个数组转为用逗号分隔的参数序列，对数组进行解包

### symbol

```js
//定义
Symbol是ES6中新增的一种数据类型, 被划分到了基本数据类型中
//特点
Symbol 的值是唯一的，用来解决命名冲突的问题
Symbol 值不能与其它数据进行运算
Symbol 定义的对象属性不能使用 for…in遍历。无法通过,对象名.属性名，对象名["属性名"]的形式访问属性，但是可以通过对象名[属性名]的形式访问，可Object,getpropertySymbols()获取
//使用
let 变量名=Symbol("描述")
```

### 迭代器

```js
只有含有方法[Symbol.iterator]的对象才能被for of遍历,[Symbol.iterator]返回迭代器对象,迭代器对象中的next()指向下一个需要遍历的变量
```





