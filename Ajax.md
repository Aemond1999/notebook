# Ajax

## 请求头

| 常见请求头      |                                                              |
| --------------- | ------------------------------------------------------------ |
| Accept          | 指定客户端能够接受的内容类型                                 |
| Accept-Encoding | 指定客户端能够接受的内容编码方式                             |
| Accept-Language | 指定客户端能够接受的自然语言                                 |
| Connection      | 指定连接是否保持持久连接                                     |
| Content-Length  | 请求体的长度                                                 |
| Content-Type    | 常见的Content-Type值包括：<br/>text/plain：纯文本格式<br/>text/html：HTML格式<br/>application/json：JSON格式<br/>application/xml：XML格式<br/>application/x-www-form-urlencoded：表单数据格式<br/>multipart/form-data：多部分表单数据格式 |
| Cookie          | 包含客户端的Cookie信息                                       |
| Host            | 指定请求的目标主机                                           |
| User-Agent      | 客户端的用户代理                                             |
| Authorization   | 包含客户端认证信息                                           |

## XMLHttpRequest对象方法

| 方法名                                              | 说明                     |
| --------------------------------------------------- | ------------------------ |
| open(method, url,[asyncFlah],[ussername],[password] | 配置请求                 |
| send(content)                                       | 向服务器发起请求         |
| getAllResponseHeaders()                             | 返回响应报文首部的值     |
| getResponseHeader(header)                           | 返回响应报文指定首部的值 |
| setRequestHeader(header, value)                     | 添加请求头               |
| abort()                                             | 停止请求                 |

## XMLHttpRequest对象属性

| 熟悉               | 说明                                                         |
| ------------------ | ------------------------------------------------------------ |
| onReadyStateChange | 绑定一个处理函数，每次ajax请求状态改变时都会调用该函数       |
| readyState         | 请求状态。                                                                                                                        readyState === 0 : 表示未初始化完成，也就是 open 方法还没有执行 <br/>readyState === 1 : 表示配置信息已经完成，也就是执行完 open 之后 <br/>readyState === 2 : 表示 send 方法已经执行完成<br/>readyState === 3 : 表示正在解析响应内容<br/>readyState === 4 : 表示响应内容已经解析完毕，可以在客户端使用了 |
| status             | 服务器返回的Http状态码                                       |
| reponseText        | 以文本形式返回响应。                                         |
| responseXML        | 以XML形式返回响应                                            |
| statusText         | 返回状态文本（例如 “OK” 或 “Not Found”）                     |

## ajax工作流程

```js
//发送一个带参数的Get请求
// 1.创建对象
const xhr = new XMLHttpRequest();
// 2.初始化
xhr.open('get', 'url?param1=xx&param2=xx');
// 发送请求
xhr.send();

//发送一个带参数的Post请求
// 1.创建对象
const xhr = new XMLHttpRequest();
// 2.初始化
xhr.setRequestHeader('content-type', 'application/x-www-form- urlencoded')
xhr.open('post', 'url');
// 发送请求
xhr.send(`param1=xx&param2=xx`);

```

## axios

### axios实例



### 拦截器

####  请求拦截器

```js

   /*需要拦截请求的原因
    *   1.config中包含了某些不符合服务器要求的信息
    *   2.发送网络请求的时候需要向用户展示一些加载中的图标
    *   3.网站需要登录才能请求资源，也就是需要token才能请求资源*/
    axios.interceptors.request.use(config => {
      // 在发送请求之前做些什么
      console.log(config)
      return config; //拦截器里一定要记得将拦截的结果处理后返回，否则无法进行数据获取
    }, err=>{
        // 对请求错误做些什么 
        console.log(err)
        return Promise.reject(err) // 在请求错误的时候的逻辑处理
    });


```

#### 响应拦截器

```js

    axios.interceptors.response.use(res => {
      // 在请求成功后的数据处理 
      console.log(res)
      return res.data; // 对响应数据做点什么
    }, err=>{
        // 对响应错误做些什么
        console.log(err)
        return Promise.reject(err)  // 在响应错误的时候的逻辑处理
    });
```





