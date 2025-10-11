# JS

## 基础数据类型

```js
//一，数据类型
1.string
2.number：包括int,float以及特殊数字 Infinity：正无穷，-Infinity：负无穷 ,NaN：非法数字
3.boolean
4.undefined：未初始化的值 undefined==null为true
5.null:空对象
//二，数据转换
//转换为string
	1.toString():注意：null和undefined这两个值没有toString()方法，如果调用它们的方法，会报错
  2.String(a):对于Number和Boolean实际上就是调用的toString()方法，但是对于null和undefined，就不会调用				toString()方法，它会将 null 直接转换为 “null”，将 undefined 直接转换为 “undefined”。
  3.为任意的数据类型 +""

//转换为number
	//Number()
	1.如果是纯数字的字符串-->数字
	2.如果字符串中有非数字的内容-->NaN
	3.如果字符串是一个空串或者是一个全是空格的字符串-->0
	4.true-->1,false-->0
	5.null-->0
	5.undefined-->NaN
	//parseInt(),parseFloat:专门用于String
	注意：如果对非String使用parseInt()或parseFloat()，它会先将其转换为String然后在操作

//转化为boolean
	//Boolean()
	1.对于数字,除了0和NaN，其余的都是true
	2.对于字符串,除了空串，其余的都是true
	3.null和undefined都会转换为false
	4.对象也会转换为true
```

## 集合

```js
//1.Array
1.创建数组
	let arr=new Array() or let arr=[]
2.push():向数组尾部新增元素
3.pop():从数组最后一项删除
4.unshift():向数组头部新增元素
5.shift():从数组头部删除数据
6.concat():合并数组，要用新的变量去接收
7.reverse():数组反转
8.sort():数组排序
9.slice():切片
10.join(连接符号)：将数组内所有变量连接成一个字符串
10.splice()
	splice(index,num)
	删除项目，第一个参数为索引位置（从第几个索引开始），第二个参数为要删除几个。
	splice(index,0,insertValue)，返回值为空数组，array值为最终结果值。
	添加项目（插入项目），第一个参数（插入位置），第二个参数（0） ，第三个参数（插入的项）。
  splice(index,num,insertValue)，返回值为删除内容，array为结果值
	替换项目，第一个参数（起始位置），第二个参数（删除的项数），第三个参数（插入任意数量的项）。
//2.Set
1.size：返回集合的元素个数
2.add()：增加一个新元素，返回当前集合
3.delete()：删除元素，返回 boolean 值
4.has()：检测集合中是否包含某个元素，返回 boolean 值
5.clear()：清空集合，返回 undefined
6.keys():返回所有key
7.values()：返回所有value key==value
//3.Map
1.size：返回 Map 的元素个数
2.set(key,value)：增加一个新元素，返回当前 Map
3.get(key)：返回键名对象的键值
4.has(key)：检测 Map 中是否包含某个元素，返回 boolean 值
5.clear()：清空集合，返回 undefined
6.keys() 
7.values() 
8.entries() 返回键值对
```

## 遍历

```js
1.普通for循环
2.for in 
它遍历的实际上是对象的属性名称。一个Array数组实际上也是一个对象，它的每个元素的索引被视为一个属性
3.for of 【es6】
遍历对象必须是iterable可被迭代的。如Array, Map, Set。不能遍历对象属性
4.foreach()
	forEach(function (element, index, array) {
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

//4.rest[es6]
为了获取除了已定义参数a、b之外的参数，我们不得不用arguments，并且循环要从索引2开始以便排除前两个参数，这种写法很别扭，ES6标准引入了rest参数
function foo(a, b, ...rest)
```

## 高阶函数

```
```



## var let const

```js
//var
1.声明的变量属于函数作用域
2.声明的变量存在提升
3.变量可以重复声明
//let
1.变量属于块级作用域
2.不存在变量提升
3.块级作用域内不能重复声明
4.与var不同，使用let在全局作用域中声明的变量不会成为this或window对象的属性（var声明的则会）
//const
const 的行为与let基本相同，唯一一个重要的区别是它声明变量时必须同时赋值，声明一个对象时，它保证的是变量名指向的内存地址不变，而不是该地址上的对象内容不可修改。
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

### 相关操作

```js
//1.访问属性
1.对象.属性名
2.对象['属性名']
//2.删除属性
delete 对象.属性名
//3.检查自身对象是否含有某个方法或属性
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
1.每个构造函数的Prototype属性指向它的原型对象。每个原型对象也有一Prototype属性，那么就形成了一个链式结构，称为原型链。最终，原型链会到达Object的原型对象
//原型作用
1.这个原型对象添加属性和方法，那么实例就会共享这些在原型中添加的属性和方法。
```

### object对象方法

```js
//1.toString()
1.对象：object Object]
2.String：String自己
3.Boolean:如果布尔值是true，则返回"true"。否则返回"false"
4.Array:将 Array 的每个元素转换为字符串，并将它们依次连接起来，两个元素之间用英文逗号作为分隔符进行拼接
5.Date:返回日期的文本表示
6.Error:返回一个包含相关错误信息的字符串
//2.Object.keys(obj)
返回对象的所有属性
//3.Object.create(obj)
创建一个空对象，令空对象的__proto__指向参数
//4.Object.defineProperty()
向对象添加属性，
defineProperty(对象,属性,{
              value:值,
              enumerable:false,//是否可便利
           		writable:false,//是否可修改
  						configurable:false//是否可删除
  						get(){//当读取改属性时自动调用该函数
  								return
							}
							set(value){//当修改该属性时自动调用该函数
              }
               })
                  //tips
               			数据属性：使用 value 和可选的 writable, enumerable, configurable
										访问器属性：使用 get 或 set，以及可选的 enumerable, configurable
//5.Object.is(a,b)
判断两个值是否相等
//6.Object.assign(obj1,obj2)
对象合并，如果有相同属性，后面会覆盖掉前面
//7.Object.setPrototypeOf(obj1,obj2)
将obj1的原型对象设置为obj2
//8.Object.getPrototypeOf(obj1)
```

## this

```js
//1.this指向
在全局作用域中：this指向window

在函数作用域中：
1.普通函数中的this：this指向window 
2.对象方法中的this：this就是调用方法的那个实例
3.回调函数中的this： 1.作为对象方法调用回调函数：this将指向该实例
       						2.作为普通函数调用回调函数: this指向window     
4.箭头函数中的this：继承外部作用域的this

//apply()和call()
call(),apply()和bind这两个方法都是函数对象的方法，需要通过函数对象来调用
一个对象指定为第一个参数，此时这个对象将会成为函数执行时的this
1.apply(函数内部的this的值,[参数1,参数2,...])
2.call(函数内部的this的值,参数1,参数2,...)
3.bind(函数内部的this的值,参数1,参数2,...)->newFunction
  bind 会返回一个新的函数，目标函数在新函数调用时才会执行
```

## 继承

```js
//第一种：原型链继承
function father(){}
function son(){}
son.Prototype=new father()
缺点：实例会共享父类的引用变量
//第二种：构造函数继承
function father(){}
function son(){
    father.call(this)
}
缺点：实例不会共享父类原型上的方法和属性
//第三种：组合继承
function father(){}
function son(){
    father.call(this)
}
son.prototype=new father();
缺点：实例继承了两份父类的属性和方法
//第四种：寄生组合继承
function father(money){}
function son(){
    father.call(this)
}
son.prototype=object.create(father.prototype);
son.prototype.constructor=son
```

## 严格模式

```js
"use strict"
1.必须使用 var、let 或 const 声明变量
2.不能删除变量、函数或不可删除的属性
3.对象中不允许重复属性名
4.函数参数不能重名
5.全局函数中的 this 为 undefined 而非全局对象
```

## 箭头函数

```js
1.箭头函数没有自己的this，只会继承在自己作用域的上一层this。
2.箭头函数的this不会改变，使用call apply bind也没用
3.箭头函数没有prototype属性
4.箭头函数不能使用arguments对象
5.箭头函数不能用作Generator函数
```

## 闭包

```
//定义

```



