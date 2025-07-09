# HTML

## 一、HTML

### 排版标签

 ```html
 <!--标题标签 -->
 <h1>1级标题</h1>
 <h2>2级标题</h2>
 <h3>3级标题</h3>
 <h4>4级标题</h4>
 <h5>5级标题</h5>
 <h6>6级标题</h6>
 
 <!--段落标签 -->
 <p>我是说一段文字</p>
 
 <!--换行标签 -->
 </br>
 ```

### 文本格式化标签

```html
<!--加粗 -->
<strong>加粗</strong>
<b>加粗</b>

<!--下划线-->
<ins>下划线</ins>
<u>下划线</u>

<!--倾斜-->
<em>倾斜</em>
<i>倾斜</i>

<!--删除线-->
<del>删除线</del>
<s>删除线</s>

<!--区别：strong,ins,em,del语言更强烈-->
```

### 媒体标签

```html
<!-- 图片标签-->
<img src="img/cat.jpg" title="猫" alt="这是只猫">
src：图片路径
alt：替换文本,当图片加载失败时,显示该文本
title：提示文本,当鼠标悬停在图片上时,显示文本
width:图片宽度
height：图片高度
当width和height只设置一个时，另一个属性会等比例缩放或扩大

<!--音频标签-->
<audio src="audio/xxx.mp3" controls autoplay loop ></audio>
src:音频路径
controls：显示播放控件
autoplay：自动播放(部分浏览器不支持，例如chrome，edge等)
loop：循环播放
muted：静音播放

<!--视频标签-->
<video></video>
src:视频路径
controls：显示播放控件
autoplay：自动播放(部分浏览器不支持，例如chrome，edge等)
loop：循环播放
muted：静音播放(chrome静音才允许自动播放)
```

### 链接标签

```html
<!--超链接-->
<a href="http://www.baidu.com">链接名称</a>
href:url,当不清楚url是什么时将href设置为#
target:目标网页打开方式,_self(默认)在当前网页中跳转
                      _blank在新网页中跳转

```

### 列表标签

````html
<!--无序列表-->
<ul>
    <li>a</li>
    <li>b</li>
</ul>

<!--有序列表-->
<ol>
    <li>a</li>
    <li>b</li>
</ol>

<!--自定义列表-->
<dl>
    <dt>列表标题</dt>
    <dd>a</dd>
    <dd>b</dd>
</dl>
````

### 表格标签

```html
<table border="1px">
    <caption>表格标题</caption>
    <tr >
        <th>表头单元格1</th>
        <th>表头单元格2</th>
    </tr>

    <tr>
        <td>第一行的第一个单元格</td>
        <td>第一行的第二个单元格</td>
    </tr>
</table>

table属性:
border:边框宽度
width:表格宽度
height:表格高度
cellpadding:规定单元边沿与其内容之间的空白
cellspacing:规定单元格之间的空白

合并单元格：
跨行合并：rowspan='向下合并单元格个数'
跨列合并：colspan='向右合并单元格个数'
```

### 表单标签

#### form标签的相关属性

| 属性名 | 说明                                                         |
| :----: | ------------------------------------------------------------ |
| action | 此属性表示提交表单时要执行的操作，通常是将表单数据提交到服务器处理表单数据的controller |
| target | 此属性表示在提交表单之后，服务器相应数据在何处显示。默认值是\_self，表示在当前窗口显示，\_blank表示在新窗口中显示 |
| method | 此属性表示提交表单时要使用的HTTP方法。可选值有get和post两种，默认值是get |

#### GET和POST的区别

| GET                               | POST                                            |
| --------------------------------- | ----------------------------------------------- |
| 表单数据以键值对的方式追加到URL中 | 表单数据不会追加到URL，会附加到HTTP请求的正文中 |
| URL的长度受到限制（2048个字符）   | 没有限制                                        |
| 用于提交非敏感数据                | 用于提交敏感数据（如密码）                      |

#### input标签

| 属性        | 说明                                                         |
| ----------- | ------------------------------------------------------------ |
| type        | text:文本框，用于输入单行文本<br/>passoword:密码框<br/>radio:单选框<br/>checkbox:多选框<br/>file:上传文件<br/>submit:提交按钮<br/>reset:重置按钮,用于重重置表单内容<br/>button:普通按钮,用于搭配js使用 |
| name        | 定义输入字段的名称，在表单提交时，服务器通过该名称来获取对应的值 |
| disabled    | 禁用输入框，使其无法被用户修改和操作，也不会被提交           |
| readonly    | 使输入框内容只读，无法编辑，但可以被选中和复制               |
| value       | 输入框的默认值                                               |
| placeholder | 输入框内的提示文本，当用户未输入内容时显示，输入内容后消失   |

#### button标签

| 属性 | 说明                                                         |
| ---- | ------------------------------------------------------------ |
| type | submit:提交按钮<br/>reset:重置按钮<br/>button:普通按钮,用于搭配js使用 |

#### 输入框详解

```html
<!-- 单行文本输入框 text -->
<input type="text" maxlength=10>
maxlength:可输入的最大字符数

<!-- 数字输入框 number -->
<input type="number" min="0" max="200" />
min:最小值
max:最大值
step:输入值的增量或减量

<!-- 滑块 range-->
<input type="range" name="range" min="0" max="100" step="1" />
min:最小值
max:最大值
step:输入值的增量或减量

<!-- 文件上传 file-->
<input type="file" multiple />
multiple:上传多个文件

<!-- 颜色选择器-->
<input type="color" />

<!--日期选择器-->
<input type="date"  />

<!--时间选择器-->
<input type="time"  />

<!--时间戳选择器-->
<input type="datetime-local" />
```

#### select下拉菜单标签

```html
    <select  name="city">
        <option selected>
            北京
        </option>
        <option>
            上海
        </option>
        <option>
            深圳
        </option>
    </select>

相关属性：
selected；默认选中
```

#### textarea文本域标签

```html
<textarea cols="10" rows="20" placeholder="请输入"></textarea>
相关属性：
cols:宽度
rows:高度
placeholder
```

#### lable标签

```html
用处：用于绑定内容和表单标签
使用方法：
1.用lable标签把内容包裹起来
2.在表单标签上添加id属性
3.在lable标签中的for属性设置对应的id属性值
<label for="1">女:</label><input type="radio" id="1" name="性别"><br>
<label for="2">男:</label><input type="radio" id="2"name="性别"><br>
```

### 字符实体

| 空格 | \&nbsp; |
| ---- | ------- |
| <    | \&lt;   |
| >    | \&gt;   |
