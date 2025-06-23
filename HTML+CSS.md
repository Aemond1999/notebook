# HTML+CSS

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

## 二、CSS

### 选择器

#### 简单选择器

```html
<!--标签选择器-->
也称为元素选择器，使用HTML标签作为选择器的名称
<style>
    
 p{
   color: red;
  }
    
</style>
<p>hello world!!!</p>
<p>hello world!!!</p>


<!--类选择器-->
使用自定义的名称，以 . 号作为前缀，以标签的class属性作为样式应用的依据,一对多的关系
<style>
    
 .hello{
   color: red;
  }

</style>
<p class="hello">hello world!!!</p>
<p class="hello">hello world!!!</p>

<!--id选择器-->
使用自定义的名称，以#号作为前缀，以标签的id属性作为样式应用的依据,，一对一的关系
<style>
    
 #hello{
   color: red;
  }

</style>
<p class="hello">hello world!!!</p>

```

#### 复杂选择器

```html
<!--复合选择器-->
标签选择器和类选择器、标签选择器和ID选择器，一起使用
<style>
    /** 标签选择器+类选择器**/
  p.hello{
    color: blue;
  }

</style>
<p class="hello">hello world!!!</p>
<h1 class="hello">hello world!!!</h1>


<!--组合选择器-->
也称为集体声明，将多个具有相同样式的选择器放在一起声明，使用逗号隔开
<style>
     p,.hello{
        color: blue;
     }
</style>
<p class="hello">hello world!!!</p>
<h1 class="hello">hello world!!!</h1>


<!--嵌套选择器-->
在某个选择器内部再设置选择器，通过空格隔开，使用 空格 时不区分父子还是后代，使用CSS3中新增的 > 时必须是父子关系才行
<style>
      div span div{
           color:red;
       }

</style>

<div >
    <span >
        <div >
            <span>1</span>
            <span>2</span>
            <span>3</span>
        </div>
        <div>
            <span>4</span>
            <span>5</span>
            <span>6</span>
        </div>
    </span>
</div>



<!--伪元素选择器-->
:first-letter 为第一个字符的样式
:first-line 为第一行添加样式
:before 在元素内容的最前面添加的内容，需要配合content属性使用
:after 在元素内容的最后面添加的内容，需要配合content属性使用
<style>
		p:first-letter{
			color:red;
			font-size:30px;
		}
		p:first-line{
			background:pink;
		}
		p:before{
			content:"嘿嘿";
		}
		p:after{
			content:"哈哈";
		}
	</style>

```

#### 伪类选择器

**伪类是选择器的一种，它用于选择处于特定状态的元素，****让你的代码更灵活、更易于维护**

```html
<!--动态伪类-->
1. :link 超链接未被访问的状态。
2. :visited 超链接访问过的状态。
3. :hover 鼠标悬停在元素上的状态。
4. :active 元素激活的状态。
5. :focus 获取焦点的元素。

<!--否定伪类-->
1.:not(选择器)
/* 在div标签中排除.text3类 */
div:not(.text3) {
    color: red;
    background-color: orange;}

<!--UI伪类-->
1. :checked 被选中的复选框或单选按钮。
2. :enable 可用的表单元素（没有 disabled 属性）。
3. :disabled 不可用的表单元素（有disabled 属性）。

<!--语言伪类-->
1.:lang() 根据指定的语言选择元素
<div lang="zh-CH">这是一段文字1</div>
<div>这是一段文字2</div>
div:lang(zh-CH) {
    background-color: green;
    color: orange;

```



#### 选择器优先级

行内样式>ID选择器>类选择器>标签选择器

原因：首先加载标签选择器,再加载类选择器，然后加载ID选择器，最后加载行内样式，后加载会覆盖先加载的同名样式

可以使用!important使某个样式有最高的优先级

### 常用CSS样式

#### 字体属性

| 属性        | 含义       | 取值                                                         |
| ----------- | ---------- | :----------------------------------------------------------- |
| font-size   | 大小、尺寸 | inherited:继承默认从父标签继承字体大小，所有CSS属性的默认值都是inherited<br/>px:像素<br/>%:相对父标签字体大小的百分比<br/>em:相对于父标签字体大小的倍数 |
| font-weight |            | normal:普通（默认）<br/>bold:粗体                            |
| font-family | 字体       | 一般建议写3种字体：首选,其次,备用。以逗号隔开                |
| font-style  |            | normal:普通(默认)<br/>italic:斜体                            |
| font        | 简写       | font:font-style font-weight font-size font-family            |

#### 文本属性

| 属性            | 含义           | 取值                                                         |
| --------------- | -------------- | ------------------------------------------------------------ |
| color           | 颜色           | 颜色名称：使用英文单词<br/>16进制的RGB值：#RRGGBB<br/>rgb函数：rgb(red,green,blue)<br/>rgba函数：rbga(red,green,blue,alpha)<br/>可以设置透明度，alpha取值范围：[0,1] 0表示完全透明 1表示完全不透明 |
| line-height     | 行高           | px:像素                                                      |
| text-align      | 水平对齐方式   | left(默认)、center、right                                    |
| vertical-align  | 垂直对齐方式   | 取值：top、middle、bottom可以用于图片和文字的对齐方式        |
| text-indent     | 首行缩进       | px:像素<br/>em：缩进标签字体个数                             |
| text-decoration | 文本修饰       | underline:下划线<br/>overline:上划线<br/>line-through:删除线 |
| text-transform  | 字母大小写转换 | lowercase、uppercase、capitalize(首字母大写)                 |
| letter-spacing  | 字符间距       | px:像素<br/>em：间距为标签字体个数                           |
| word-spacing    | 单词间距       | 只对英文有效                                                 |

### 背景属性

| 属性                  | 含义               | 取值                                                         |
| --------------------- | ------------------ | ------------------------------------------------------------ |
| background-color      | 背景颜色           | 颜色名称：使用英文单词<br/>16进制的RGB值：#RRGGBB<br/>rgb函数：rgb(red,green,blue)<br/>rgba函数：rbga(red,green,blue,alpha)<br/>默认值为transparent |
| background-image      | 背景图片           | none:无背景图（默认的）<br/>url("文件路径")                  |
| background-repeat     | 背景图片的重复方式 | repeat(默认):平铺<br/>repeat-x：水平方向平铺<br/>repeat-y：垂直方向平铺<br/>no-repeat：不平铺 |
| background-position   | 背景图片的显示位置 | 关键字：top、bottom、left、right、center<br/>坐标：左上角为(0,0)坐标，向右为x正方向,向下为y正方向<br/>可以只写一个关键字，另一个关键字默认为center |
| background-size       | 背景图大小         | cover：时高度和宽度等比例拉伸，以使背景图像完全覆盖背景区域。背景图像的某些部分也许无法显示在背景定位区域中。<br/>contain：高度和宽度等比例拉伸，当宽度 或者 高度 铺满div盒子就不再进行拉伸了，可能有部分空白区域。<br/>百分比：50% 50%<br/>数字：100px 100px |
| background-attachment | 背景附着           | scroll（背景滚动） / fixed（背景固定）                       |
| background            | 简写               | 以空格隔开，书写顺序没有要求                                 |

#### 背景渐变

```
background: linear-gradient(to right,#333399,#ff00cc);
渐变方向
to top : 从下向上填充渐变色
to right:从左向右填充渐变色
to bottom:从上向下填充渐变
to left  :从右向左填充渐变色
```



### 显示模式

```python
#block：块级元素
1.常见块级元素
<div>、<h1>~<h6>、<p>、<ul>、<ol>、<li>等
#特点：
1.独占一行
2.高度、宽度、内外边距各方向可以自由控制；
3.默认宽度是父容器的100%;
4.里面可以放行内元素、行内块元素或块级元素;(文字类标签里面不能放块级元素)

#inline：行内元素
1.常见行内元素
<a>、<strong>、<b>、<em>、<i>、<del>、<s>、<span>
#特点：
1、前后无换行符 （相邻的行内元素在一行上，一行可以有多个行内元素，但之间有空隙（可以设置负margin值解决，设置的大小各浏览器不一））；
2、设置的宽和高是不起作用，元素大小根据元素内文本决定； 竖直方向的margin无效，水平有效；竖直和水平方向的padding都有效（竖直方向的padding有效，但不会撑开周围的盒子）
3、行内元素里只能放文本或者行内元素；（a标签里可以放块级元素）



#inline-block
1.常见
<img/>、<input/>、<td>
#行内块元素特点：
1、相邻的行内元素在一行上，一行可以有多个行内元素，但之间有空隙（可以设置负margin值解决，设置的大小各浏览器不一）
2、默认的宽度为内容决定；可以设置宽高，会覆盖默认的宽度；
3、各个方向的margin和padding都有效
```





### 盒子模型

```python
#盒子的组成
   一个盒子由外到内可以分成四个部分：margin（外边距）、border（边框）、padding（内边距）、content（内容）。会发现margin、border、padding是CSS属性，因此可以通过这三个属性来控制盒子的这三个部分。而content则是HTML元素的内容

```

#### Margin

````python

#1.设置margin
1.margin属性后跟两个值，第一个值设置上下边距，第二个是设置左右边距
2.margin属性后跟三个值，第一个值设置上边距，第二个是设置左右边距，第三个值设置下边距
3.margin属性后跟四个值，第一个值设置上边距，第二个是设置右边距，第三个值设置下边距，第四个值设置左边距
#2.marign合并
垂直排列的两个兄弟元素,上下margin会合并,取两个margin的较大值
在垂直方向上，父元素的 margin-top 和子元素的 margin-top 之间会发生合并，合并后的 margin-top 取两者中的较大值。类似地，父元素的 margin-bottom 和子元素的 margin-bottom 之间也会发生合并

````

#### Border

```python
#1.圆角
border-top-left-radius：左上角
border-top-right-radius：右上角
border-bottom-left-radius：左下角
border-bottom-right-radius：右下角
#2.常见应用
1.圆形
border-radius:宽高的一半px/50%
2.胶囊形
border-radius:盒子高度的一半
```

#### 盒子阴影：box-shadow

  box-shadow:offset-x offset-y blur spread color inset;

| 属性          | 取值 | 说明                                          |
| ------------- | ---- | --------------------------------------------- |
| offset-x      | px   | 阴影位置                                      |
| offset-y      | px   |                                               |
| spread-radius | px   | 阴影面积                                      |
| blur-radius   | px   | 阴影模糊程度                                  |
| color         |      |                                               |
| inset         |      | 默认阴影在边框外。使用 inset 后，阴影在边框内 |

#### 格式清除

```html
<style>
     *{
            margin:0;
            padding: 0;
            box-sizing: border-box; padding和border的值就不会在影响元素的宽高，相当于把padding和border                                       的值都算在content里
      }
    li{
        list-style:none; 去掉列表符号
    }
</style>
```

#### 元素溢出

```
属性名：overflow
取值：
hidden:隐藏溢出
scroll：设置滚动条(有没有溢出都会显示)
auto:当一溢出时设置滚动条
```

### 弹性布局：flex

| 属性            | 说明                                                         | 取值                                                         |
| --------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| justify-content | 定义了项目在主轴上的对齐方式                                 | flex-start（默认值）：左对齐<br/>flex-end：右对齐<br/>center： 居中<br/>space-between：两端对齐，项目之间的间隔都相等。<br/>space-around：每个项目两侧的间隔相等。项目之间的间隔比项目与边框的间隔大一倍。<br/>space-evenly：项目之间的间隔比项目与边框的间隔一样 |
| align-items     | 项目在侧轴上的对齐方式                                       | flex-start：交叉轴的起点对齐。<br/>flex-end：交叉轴的终点对齐。<br/>center：交叉轴的中点对齐。<br/>baseline: 项目的第一行文字的基线对齐。<br/>stretch（默认值）：如果项目未设置高度或设为auto，将占满整个容器的高度。 |
| align-self      | 项目在侧轴上的对齐方式，控制某个弹性盒子                     |                                                              |
| flex-direction  | 决定主轴的方向                                               | column：主轴为垂直方向，起点在上沿。<br/>                    |
| flex-wrap       | 元素超出容器，是否换行                                       | nowrap（默认）：不换行<br/>wrap：换行，第一行在上方。        |
| align-content   | align-content属性定义了多根轴线的对齐方式。如果项目只有一根轴线，该属性不起作用 | flex-start（默认值）：左对齐<br/>flex-end：右对齐<br/>center： 居中<br/>space-between：两端对齐，项目之间的间隔都相等。<br/>space-around：每个项目两侧的间隔相等。项目之间的间隔比项目与边框的间隔大一倍。<br/>space-evenly：项目之间的间隔比项目与边框的间隔一样 |
| flex            | 控制弹性盒子主轴方向的尺寸                                   | 数字：表示占用父级剩余尺寸的份                               |

### 网格布局：grid

```js
//dispaly
我们通过在元素上声明 display：grid 或 display：inline-grid 来创建一个网格容器。声明 display：grid 则该容器是一个块级元素，设置成 display: inline-grid 则容器元素为行内元素

//grid-template-columns：定义列数和容器内元素宽度
1.grid-template-columns: 1fr 1fr：一行分为两列
2.grid-template-columns: 1fr 200px 1fr：中间固定200px，两边自动平均分配
//grid-template-rows：定义行数和容器内元素高度

//repeat()函数
如果多列的元素宽度相同，可以使用repeat()函数，grid-template-columns: repeat(5,1fr)

//auto-fill 关键字
表示自动填充，让一行（或者一列）中尽可能的容纳更多的单元格
grid-template-columns: repeat(auto-fill,100px)

//minmax() 函数
定义网格元素一个最小和最大的尺寸
grid-template-columns: 1fr 1fr minmax(300px, 2fr) 的意思是，第三个列宽最少也是要 300px，但是最大不能大于第一第二列宽的两倍

//auto 关键字
通过 auto 关键字，我们可以轻易实现三列或者两列布局。grid-template-columns: 100px auto 100px 表示第一第三列为 100px，中间由浏览器决定长度

//grid-row-gap 属性、grid-column-gap 
分别设置行间距和列间距。grid-gap 属性是两者的简写形式。

// grid-auto-flow 
指定在网格中的元素怎样排列。默认的放置顺序是"先行后列"，即先填满第一行，再开始放入第二行，默认值是 row。
grid-auto-flow: row dense //表示尽可能填满表格。

//grid-auto-columns 和 grid-auto-rows 属性
1.显式网格:grid-template-columns 和 grid-template-rows 属性中定义的行和列
2.隐式网格：如果你在网格定义之外又放了一些东西，或者因为内容的数量而需要的更多网格轨道的时候，网格将会在隐式网格中创建行和列。
3.假如有多余的网格，那么它的行高和列宽可以根据 grid-auto-columns 属性和 grid-auto-rows 属性设置

```

### Transform

```python
#1.translate:改变元素位置,当下x,y为百分比时,参照对象为自身
1.translate(x,y)
2.translateX(x)
3.translateY(y)
4.translateZ(z):按z轴位移,因为z轴是朝向我们的，所以看不出效果
5.translate3d(x,y,z)

#2.rotate:元素旋转
1.rotate(deg)：2d旋转,可以通过transform-origin设置旋转点,默认为元素中心
               transform-origin: x-axis y-axis z-axis
               transform-origin属性值可以是百分比、em、px等具体的值，也可以是top、right、bottom、left和                  center这样的关键词。
2.rotateX(deg)
3.rotateY(deg)
4.rotateZ(deg)
4.rotate3D(x,y,z)

#3.scale
1.scale(x,y)      定义2D的缩放转换,实时上是缩放x轴y轴的刻度
2.scaleX(x)    通过设置 x 轴的值来定义缩放转换
3.scaleY(y)    通过设置 y 轴的值来定义缩放转换
4.scaleZ(z)    通过设置 z 轴的值来定义缩放转换
5.scale3d(x,y,z)   定义3D的缩放转换

#4.perspective：视距
定义观察者与屏幕的距离，添加给父级，取值范围800-1200px

#5.transform-style
设置子元素是位于3d空间还是2d平面
transform:flat,preserve-3d



```

### Transition过渡动画

| 属性                       | 说明                                                         | 取值                                                         |
| -------------------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| transition-property        | 设置元素中参与过渡的属性                                     | none \| all \| property                                      |
| transition-duration        | 设置过渡需要花费的时间（单位为秒或者毫秒)使用scale无效       | s or ms                                                      |
| transition-timing-function | 设置过渡动画的类型                                           | linear：表示过渡效果以匀速进行<br/>ease(默认）：以慢速开始，然后加速，最后又变慢。<br/>ease-in：以慢速开始，然后逐渐加速。<br/>ease-out：以快速开始，然后逐渐变慢。。<br/>ease-in-out：以慢速开始，然后加速，最后再变慢。<br/>cubic-bezier(n,n,n,n)：自定义时间曲线，其中n是0到1之间的数值 |
| transition-delay           | 设置过渡效果开始之前需要等待的时间                           | s or ms                                                      |
| transition                 | 简写，通过 transition 属性也可以设置多组过渡效果，每组之间使用逗号进行分隔 | transition: transition-property transition-duration transition-timing-function transition-delay; |
