# Javascript

## 基本数据类型

| 类型                     | 说明                                                         |
| ------------------------ | ------------------------------------------------------------ |
| 字符串型（String）       |                                                              |
| 数值型（Number）         | 特殊数字：  Infinity：正无穷， -Infinity：负无穷 ,NaN：非法数字 |
| 布尔型（Boolean）        | 布尔型只能够取真（true）和假（false）两种数值                |
| undefined型（Undefined） | 在使用 var 声明变量但未对其加以初始化时，这个变量的值就是 undefined。undefined值实际上是由null值衍生出来的，所以如果比较undefined和null是否==，会返回true |
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

### for

```js
1.for in
  for in循环由于历史遗留问题，它遍历的实际上是对象的属性名称。一个Array数组实际上也是一个对象，它的每个元素的索引被视为一个属性
2.for of
3.foreach()
a.forEach(function (element, index, array) {
    // element: 指向当前元素的值
    // index: 指向当前索引
    // array: 指向Array对象本身
    console.log(`${element}, index = ${index}`);
});

Set与Array类似，但Set没有索引，因此回调函数的前两个参数都是元素本身：
let s = new Set(['A', 'B', 'C']);
s.forEach(function (element, sameElement, set) {
    console.log(element);
});

Map的回调函数参数依次为value、key和map本身：
let m = new Map([[1, 'x'], [2, 'y'], [3, 'z']]);
m.forEach(function (value, key, map) {
    console.log(value);
});
```

## 函数

```js
//1.第一种方法
function 函数名(形参1,形参2,...) {
    语句...
}

//2.第二种方法，函数表达式写法(不推荐)
var 函数名  = function(形参1,形参2,...) {
    语句....
}
//3.arguments
JavaScript还有一个免费赠送的关键字arguments，它只在函数内部起作用，并且永远指向当前函数的调用者传入的所有参数。arguments类似Array但它不是一个Array。
//4.rest
为了获取除了已定义参数a、b之外的参数，我们不得不用arguments，并且循环要从索引2开始以便排除前两个参数，这种写法很别扭，ES6标准引入了rest参数
function foo(a, b, ...rest)
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

### 检查自身对象是否含有某个方法或属性

```js
1.hasOwnProperty()
2.in
3.propertyIsEnumerable():只能检查可遍历属性
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

#### Object.keys()

返回对象的所有属性

#### Object.create(proto)

创建一个空对象，令空对象的\__proto__指向参数

#### Object.defineProperty()

```js
//向对象添加属性，
defineProperty(对象,属性,{
              value:值,
              enumerable:false,//是否可遍历
           		writable:false,//是否可修改
  						configurable:false//是否可删除
  						get(){//当读取改属性时自动调用该函数
  								return
							}
							set(value){//当修改该属性时自动调用该函数
              }
               })
            

```

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

## this

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

### apply()和call()

```js
//apply()和call()
call(),apply()和bind这两个方法都是函数对象的方法，需要通过函数对象来调用
一个对象指定为第一个参数，此时这个对象将会成为函数执行时的this
1.apply(函数内部的this的值,[参数1,参数2,...])

2.call(函数内部的this的值,参数1,参数2,...)

bind 会返回一个新的函数，目标函数在新函数调用时才会执行
3.bind(函数内部的this的值,参数1,参数2,...)->newFunction

```

## Javascript常用对象和函数

### Array

```js
1.push()：向数组的末尾添加一个或多个元素
2.pop()：删除并返回数组的最后一个元素
3.unshift()：向数组开头添加一个或多个元素，并返回新的数组长度
4.shift()：删除并返回数组的第一个元素
5.slice(first,end)：切片
7.concat()：连接两个或多个数组，并将新的数组返回
8.join("链接符号")：将数组转换为一个字符串，
9.reverse()：反转数组，该方法会直接修改原数组

10.splice(index,num,value):替换项目，index：起始位置，num：替换个数，value：替换的值
11.splice(index,num):删除项目，index：起始位置，num：删除个数
12.splice(indx,0,value)：插入值
```

### map()和filter()

```js
//array.map(function(currentValue, index, array){} ,[thisArg])
}, thisArg);
该函数用于对数组中的每个元素进行处理，将其转换为另一个值，最终返回一个新的数组
1.currentValue：当前正在处理的元素
2.index（可选）：当前元素的索引
3.array（可选）：调用 map 的数组
4.thisArg（可选）：执行回调时使用的 this 值


//array.filter(function(currentValue, index, array) {}, thisArg);返回 true 保留该元素，false 则不保留

1.currentValue：当前正在处理的元素
2.index（可选）：当前元素的索引
3.array（可选）：调用 map 的数组
4.thisArg（可选）：执行回调时使用的 this 值
```

### String

```js
1.chatAt(index)：该方法可以根据索引获取指定位置的字符
2.concat(str...)：该方法可以用来连接两个或多个字符串
3.indexof(str)：该方法可以检索一个字符串中是否含有指定内容，如果字符串中含有该内容，则会返回其第一次出现的索引，如果没有找到指定的内容，则返回-1，可以指定一个第二个参数，指定开始查找的位置
4.lastIndexOf(str)
5.slice(start,end)方法演示：可以从字符串中截取指定的内容，不会影响原字符串，而是将截取到内容返回
6.substring(start,end)
7.split(sep):分割字符串
8.toUpperCase()/toLowerCase()
```

## 作用域

```js
//变量提升
变量提升是指在代码执行阶段，变量声明（不包括赋值）会被提升到其作用域的最顶端

//函数提升
函数声明也会被提升到其作用域的顶部，函数表达式除外
```

```js
//1.全局作用域
全局变量是挂载在 window 对象下的变量，所以在网页中的任何位置都可以使用并且访问到这个全局变量。

//2.函数作用域
在 JavaScript 中，函数中定义的变量叫作函数变量，这种变量只能在函数内部才能访问到，所以它的作用域也就是函数的内部，在函数调用时创建，随着函数的运行结束而销毁。

//3.块级作用域
ES6 中新增了块级作用域，最直接的表现就是新增的 let 和 const 关键词，使用这两个关键词定义的变量只能在块级作用域中被访问,典型的块级作用域为if else，for循环
```

## 严格模式

```js
1.必须使用 var、let 或 const 声明变量
2.不能删除变量、函数或不可删除的属性
3.对象中不允许重复属性名
4.函数参数不能重名
5.全局函数中的 this 为 undefined 而非全局对象
```

## DOM

### 简介

```js
1.DOM 全称是 Document Object Model，也就是文档对象模型。提供操作页面元素的方法和属性
2.DOM树是Web页面的模型，当浏览器加载一个Web页面时，它会创建这个页面的模型，称为DOM树。
3.DOM树主要由4类主要节点组成：文档节点，元素节点，属性节点，文本节点。
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

#### 不需要查找就能获取的元素节点

```js
1. document对象 —————  根节点
2. document.documentElement对象  —————  <html>元素对象
3. document.head对象  —————  <head>元素对象
4. document.body对象 —————  <body>元素对象
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
1.元素节点.属性 = new_value
2.元素节点.setAttribute(attribute, new_value)	

//改变元素的行内样式值。
元素节点.style.样式 = new_style	

```

#### 创建元素

```js
//创建元素节点。
document.createElement(element)	

//创建属性节点。
document.createAttribute(attribute)	
属性节点.value = 属性值
元素节点.setAttributeNode(属性节点)

//直接在元素节点上添加属性
元素节点.setAttribute(attributename,attributevalue)

//自定义属性的访问
不允许直接用"元素节点.属性"的方式访问自定义属性，只能用getAttribute()
当属性名为"data-**"的格式命名时，可以用元素节点.dataset.**的方式访问


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

 ## localStorage和sessionStorage

### localStorage 与 sessionStorage 的区别

```js
1.localStorage：数据的持久化程度高，即使用户关闭浏览器后，数据依然会被保留。除非显式删除，数据可以一直存在，适用于持久保存用户偏好设置、用户认证信息等需要长时间保存的数据。
2.sessionStorage：数据仅在浏览器的会话期间有效。一旦关闭页面或标签页，数据就会被清除，适用于存储临时性的数据，如表单状态、页面之间的传递数据等

```

### localStorage和sessionLocal的用法

localStorage和sessionStorage的方法基本一致

```js
//1.存储数据
localStorage.setItem(key, value)
//2.读取数据
localStorage.getItem(key)
//3.删除数据
localStorage.removeItem(key)
//4.清空所有数据
localStorage.clear()
//5.存储对象和数组
localStorage.setItem('user', JSON.stringify(user));
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
块级作用域
不存在变量提升：JavaScript的函数定义有个特点，它会先扫描整个函数体的语句，把所有用var申明的变量“提升”到函数顶部，不会提升变量的赋值
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

### promise

#### 简介

```js
//promise的属性
1.PormiseState：状态
2.PromiseResult：结果
//promise的3种状态
1.pending：准备中
2.fulfilled：成功
3.rejected：失败
//promise状态改变,promise只能改变一次状态
1.resolve():state->fullfilled
2.reject():state->rejected
//PromiseResult
可通过在resolve(),reject()传参改变PromiseResult
```

#### then()

```js
//参数
1.一个函数：成功时调用
2.另一个函数：失败时调用
 p.then((value)=>{
   //PromseState==fullfilled时调用
   //value==PromiseResult
   return
   //返回新promise实例的状态
    },(reason)=>{
   //PromiseState==rejected时调用
   //reaon==PromiseResult
    })
//返回值
返回一个新的promise实例
```

#### catch()

```js
//触发条件
1.reject()
2.代码出现错误
```

### 类

```js
//定义类
class 类名 extends 父类{
  //静态变量
  static c='666'
  //私有变量
  #b
	constructor(a,b){
    super()
    this.a=a
    this.b=b
  }
	function(){}
  static function(){}
  get a(){
    return 
  }
  set a(param){}
  
}
let 实例名=new 类名(a,b)

//类和ES5构造函数的区别
1.类没有变量提升，必须先定义类再创建实例
2.类的属性不能被for in public（默认） : 公有，可以在任何地方被访问。
//访问控制修饰符
1.public（默认） : 公有，可以在任何地方被访问。
2.protected : 受保护，可以被其自身以及其子类访问。
3.private : 私有，只能被其定义所在的类访问。遍历
```

### 数值扩展

```js
1.Number.isFinite(num):是否是有限数
2.Number.isNaN(num)
3.Number.isInteger(num)
4.Number.isFloat(num)
5.Math.trunc(num):向下取整
```

### 对象方法扩展

```js
1.Object.is(a,b):判断两个值是否相等
2.Object.assign(obj1,obj2):对象合并，如果有相同属性，后面会覆盖掉前面
3.Object.setPrototypeOf(obj1,obj2):将obj1的原型对象设置为obj2
4.Object.getPrototypeOf(obj1)
```

### 模块化

#### 导出

```js
//方式一：分别暴露
export let school = "北京大学";
export function study() {
    console.log("我们要学习！");
}

//方式二：统一暴露
let school = "北京大学";
function findJob() {
    console.log("我们要找工作！");
}
export {school, findJob};

//方式三：默认暴露
export default {
    school: "北京大学",
    change: function () {
        console.log("我们要改变自己！");
    }
}
```

#### 导入

```js
//方式一
import * as m1 from "./m1.js";
//方式二
import{school,study} from "./m1.js"
//方式三（只适用于默认暴露）
import m1 from "./m1.js"
```















# TypeScript

## 数据类型

### Js数据类型

```ts
1.string
2.number
3.undefined
4.null
5.symbol
6.bigint
```

### ts新增数据类型

```ts
1.Array
2.tuple：元祖
	元祖是一个明确元素数量以及每个元素类型的一个数组
  let person:[string,number]
3.enum：枚举
	enum Direction {
    Up=1,//默认从0自增
    Down,
    Left,
    Right,
}
4.any:
	任何值，会绕过类型检查，少用
5.void：
	用于函数，只允许返回undefined
	函数若没有返回值默认返回undefined
6.never：
	用于函数，什么都不能返回，适用于不能正常结束的函数，例如抛出异常，无限循环
7.unknown:
	unknown与any一样，所有类型都可以分配给unknown。与any的最大区别是： 任何类型的值可以赋值给any，同时any类型	的值也可以赋值给任何类型。unknown 任何类型的值都可以赋值给它
7.object：
	object 表示非原始类型，也就是除 number ， string ， boolean 之外的类型
8.Object
	除undefined和null
9.联合类型
	表示可以是多种类型之一
	let person:number|string
10.字面量类型
	字面量类型可以让变量只能拥有特定的值
  let direction: "up" | "down" | "left" | "right"
```

## interface

​	接口用来对对象或者类中的内容进行约束

```ts
//定义一个接口
interface Person{
	name:string
	age?:number
  work():void
}
//关键字
	？：可选属性
	readonly：只读属性
//对象
  let farmer:Person={
    name:"jack",
    age:50,
    work() {
        console.log("种田")
    }
}
//类
  class PoliceMan implements Person{
    age: number;
    name: string;
    constructor(name:string,age:number) {
        this.name=name
        this.age=age
    }
    work(): void {
        console.log("抓小偷")
    }
}
  
```

## 泛型

```ts
//接口
interface Person <T>{
  name:T
  age:T
}
//函数
function<U,V> fun1(a:U,b:V)

//类
class Person<T>{
  
}

//泛型约束
<T extends Person>
  
//默认值
  
<T=string>
```

## 抽象类

```ts
abstract Person{
  abstract word()
}
```







