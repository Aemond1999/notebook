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

