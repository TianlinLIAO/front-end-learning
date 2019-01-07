## CSS (Cascading Style Sheets)

### CSS示例

```
h1 {
    color: red;
    font-size: 20px;
}
```

h1是选择器，大括号里面是声明，由属性和值组成。

### CSS注释

```
/* 这是一行单行注释 */

/*
这个注释分散
在多个行上面
*/
```

###HTML中引入CSS

- 行内：代码冗余，不易维护，结构和样式没有分离

  ```
  <body>
  	<h1 style="color:red;">this is a red title</h1>
  	<p style="color:red;">this is a red paragraph</p>
  </body>
  ```

- 内嵌：通过在`<head>`元素中使用`<style>`元素来定义 

  ```
  <head>
      <style type="text/css">
          div {
              color: red;
          }
      </style>
  </head>
  ```

- 外链

  ```
  <head>
      <link rel="stylesheet" type="text/css" href="style.css">
  </head>
  ```

### CSS选择器

- 基本选择器：元素选择器，id选择器，类选择器，通配选择器*

  ```css
  p { color: gray; }
  ```
  ```css
  p.warning { font-weight:bold; }
  ```
  ```css
  #lead-para { font-weight:bold; }
  ```
  ```css
  * { color: red; }
  ```

- 关系选择器

  ```html
  <div class="block">
       <p>第一个p元素</p>
       <div class="bd">
           <p>第二个p元素</p>
       </div>
       <div class="ft">test</div>
  </div>
  <p>第三个p元素</p>
  ```

  ```css
  /* 后代 */
  .block p{
      color: green;
  }
  
  /* 子元素 */
  .block>p {
      color: blue;
  }
  
  /* 后面的兄弟 */
  p ~ div {
      width: 200px;
      border: 1px solid red;
  }
  
  /* 紧跟其后的一个兄弟 */
  p + div {
      width: 300px;
      border: 3px solid red;
  }
  ```

- 伪类选择器

```css
    /*设置a元素在未被访问前的css样式*/
    a:link{
    	color:red;
    }
    /*设置a元素在其链接地址已被访问过时的css样式*/
    a:visited{
    	color: gray;
    }
    /*设置a元素在其鼠标悬停时的css样式*/
	a:hover {
		color: blue;
	}
	 /*设置a元素在被用户激活（在鼠标点击与释放之间发生的事件）时的css样式*/
	a:active {
		color: green;
	}
```
| 伪类名    | 描述                                                         |
| --------- | ------------------------------------------------------------ |
| `:focus`  | 指示当前拥有输入焦点的元素，即可以接受键盘输入或者能以某种方式激活的元素 |
| `:hover`  | 指示鼠标指针停留在哪个元素上，例如，鼠标指针可能停留在一个超链接上 |
| `:active` | 指示被用户输入激活的元素，例如，鼠标指针停留在一个超链接上时，如果用户点击鼠标，就会激活这个超链接 |

`:first-child` : first child

`:last-child`: last child

`:nth-child(n)`: n可以是数字，关键词(odd,even)或者公式(2n+1) (是从1开始数，不是从0开始数)

例如 `:nth-child(even)` `:nth-child(2n+1)` `:nth-child(4)`

`:nth-last-child(n)`

```html
<div>
	<p>These are the necessary steps:</p>
	<ul>
		<li>Insert key</li>
		<li>Turn key <strong>clockwise</strong></li>
		<li>Push accelerator</li>
	</ul>
	<p>Do <em>not</em> push the brake at the same time as the accelerator</p>
</div>
```

```css
p:first-child {font-weight: bold;}
li:first-child {text-transform: uppercase;}
```

↑前一个规则将作为某元素第一个子元素的所有`p`元素设置为粗体。第二个规则将作为某个元素第一个子元素的所有`li`元素变成大写。

`:lang()`根据元素的语言来选择。

把所有法语元素变成斜体：

```css
*:lang(fr) {font-style: italic;}
```

伪类比属性选择器稍微健壮一些，在需要语言特定的样式时，大多数情况下伪类都是更好地选择。

伪类可以结合使用：

```css
a:link:hover {color: red;}
a:visited:hover {color: maroon;}
```

- 伪元素选择器

**设置首字母样式**

```css
p:first-letter {color: red;}
```

```css
h2:first-letter {font-size: 200%;}
```

**设置第一行的样式**

```css
p:first-line {color: purple;}
```

所有伪元素都必须放在出现该伪元素的选择器的最后面。

**设置之前和之后元素的样式**

在每个`h2`元素前加一对银色中括号：

```css
h2:before {
    content: "]]";
    color: silver;
}
```

在文档的最后用一个适当的结束语结束：

```css
body:after {content:" The End.";}
```

- 属性选择器

  | 选择器              | 描述                                                       |
  | ------------------- | ---------------------------------------------------------- |
  | [attribute]         | 用于选取带有指定属性的元素                                 |
  | [attribute=value]   | 用于选取带有指定属性和值的元素                             |
  | [attribute\^=value] | 匹配属性值以指定值开头的每个元素                           |
  | [attribute$=value]  | 匹配属性值以指定值结尾的每个元素                           |
  | [attribute*=value]  | 匹配属性值中包含指定值的每个元素                           |
  | [attribute~=value]  | 用于选取属性值中包含指定词汇的元素                         |
  | [attribute\|=value] | 用于选取带有以指定值开头的属性值的元素，该值必须是整个单词 |

选择有`class`属性(值不限)的所有h1元素：
```css
h1[class] { color: silver;}
```
将同时有`href`和`title`属性的HTML超链接的文本置为粗体：
```css
a[href][title] {font-weight: bold;}
```
指向web服务器上某个特定文档的超链接：
```css
a[href="http://www.css-discuss.org/about.html"] {font-weight: bold;}
```
多个属性-值选择器链接在一起来选择一个文档：
```css
a[href="http://www.w3.org/"][title="W3C Home"] {font-size: 200%;}
```
```css
/* 选中 title 属性链接 */
a[title] {}

/* 选中新窗口打开的链接 */
a[target="_blank"] {}

/* 选中 pdf */
a[href$=".pdf"] {}

/* 选中 png */
a[href$=".png"] {}

/* 选中绝对路径链接 */
a[href^="http://"],
a[href^="https://"] {}
```
```css
* [lang|="en"] {color: white;}
```
↑该规则会选择`lang`属性等于`en`或者以`en-`开头的所有元素。以下标记中的前3个元素将被选中。
```html
<h1 lang="en">Hello!</h1>
<p lang="en-us">Greetings!</p>
<div lang="en-au">G'day!</div>
<p lang="fr">Bonjour!</p>
<h4 lang="cy-en">Jrooana!</h4>
```

### 属性和值

![1525498653431](C:\Users\LIGHTN~1\AppData\Local\Temp\1525498653431.png)


##### 字体相关属性

- font-family：定义文本的字体，如：`font-family: arial;`
- font-size：字体尺寸，如：`font-size: 18px;`
- font-style ：字体样式，如：`font-style: italic;`
- font-weight：字体的粗细，如：`font-weight: bold;`

##### 文本相关属性

- color：定义文字颜色，如：`color: red;`
- line-height：设置行高，如：`line-height: 1.5;`
- text-align：文本的水平对齐方式，如：`text-aligin: center;`
- text-decoration：文本的装饰效果，如：`text-decoration: underline;`
- text-indent：首行的缩进，如：`text-indent: 2em;`
- text-shadow：文本的阴影效果，如：`text-shadow: 0 0 5px #ff0000;`

##### 列表属性

- list-style：在一个声明中设置所有的列表属性
- list-style-image：将图象设置为列表项标记
- list-style-position：设置列表项标记的放置位置
- list-style-type：设置列表项标记的类型

##### 表格属性
border-collapse：是否合并表格边框
border-spacing：相邻单元格边框之间的距离
table-layout：设置表格的布局算法

##### 盒子相关
盒子大小
主要是宽高及最小和最大宽高。

- width

- min-width

- max-width

- height

- min-height

- max-height

- box-sizing

盒子边框
每个元素都有四条边，你可以给任何一条边设置边框，分别为上（top）、右（right）、下（bottom）、左（left）表示，而每个边框又包括宽度（width）、样式（style）及颜色（color）三个样式。

- border：简写模式，四边边框
- border-width：边框宽度
- border-style：边框样式，常用的为solid和dashed
- border-color：边框颜色
- border-top：上边框
- border-right：右边框
- border-bottom：下边框
- border-left：左边框

盒子内外边距
内边距为 padding，外边距为 margin，和 border 一样，也有四边可以设置，分别为上（top）、右（right）、下（bottom）、左（left）。

- margin
- margin-top
- margin-right
- margin-bottom
- margin-left
- padding
- padding-top
- padding-right
- padding-bottom
- padding-left

盒子背景
设置背景图片，背景颜色，图片位置及是否平铺等，一般也采用简写形式。

- background：总的简写形式，包括了下面各个单条属性
- background-color：背景色
- background-image：背景图片
- background-position：背景图片起始位置
- background-repeat：背景图片平铺方式
- background-size：背景图片大小
- background-clip：背景图片绘制区域
- background-origin：背景图片的定位区域

盒子显示隐藏

- overflow：指定当内容溢出其块级容器时,是否剪辑内容，渲染滚动条或显示内容
- visibility：是否可见

盒子其他

- border-radius：圆角
- box-shadow：阴影

空间位置相关

- display

- float
- clear
- position
- top
- right
- bottom
- left
- transform
- z-index
- opacity

动画相关

- transition
- animation



### 单位

**px**: 像素，用于屏幕显示器上，传统上一个像素对应于计算机屏幕上的一个点。

**%**: 百分比。相对于父元素。

如果对html元素设置font-size为百分比值，是以16px为参照进行计算的。

**em**: 

对于font-size, 1em等于父元素设置的字体大小。父级元素没有设置会一直往上找，如果都没有就参照浏览器默认大小。

对于其他属性（border, width, height, padding, margin, line-height），参照该元素的font-size.

em不建议使用。

```css
p {
 font-size: 14px;
 width: 20em; /* 20em = 20*14px */
 padding: 1.5em; /* 1.5em = 1.5*14px */
}
/* 元素本身没有设置字体大小且父级元素也没有设置 */
.no-font-size {
 width: 40em; /* 40em = 40*16px */
 margin-bottom: 2em; /* 2em = 2*16px */
}
```

**rem**: 

font-size是基于根元素html来计算的。
```
html {
 font-size: 625%; /* 相当于100px = 625% * 16px */
}
div {
 font-size: 20px; 
 width: 2rem; /* 2rem = 2 * 100px(根元素的font-size) */
 height: 4rem; /* 4rem = 4 * 100px(根元素的font-size) */
 padding: 0.1rem; /* 0.1rem = 0.1 * 100px(根元素的font-size) */
}
```

**vw, vh, vmin, vmax**: 基于视窗大小（浏览器用来显示内容的区域大小）来计算的 

- vw：基于视窗的宽度计算，1vw 等于视窗宽度的百分之一
- vh：基于视窗的高度计算，1vh 等于视窗高度的百分之一
- vmin：基于vw和vh中的最小值来计算，1vmin 等于最小值的百分之一
- vmax：基于vw和vh中的最大值来计算，1vmax 等于最大值的百分之一

```
.box {
 height: 50vh; /* 视窗高度的50% */
 width: 25vw; /* 视窗宽度的25% */
 background: red;
}
```

**单位运算**：使用 calc 来进行单位运算 

注：chrome 浏览器最小的字体为 12px，如果设置 10px 也会渲染成 12px  

### 颜色

- 关键词

  颜色名

  transparent

  currentColor

- rgb(red, green, blue) 

- rgba(red, green, blue, alpha) 

- 十六进制

### 字体

* font-family

通用字体系列：`Serif`, `Sans-serif`, `monospace`, `cursive`, `fantasy`

理论上用户安装的任何字体系列都会落入到上述某种通用系列当中。

```css
p {font-family: Times, TimesNR, 'New Century Schoolbook', Georgia, 'New York', serif;}
```

用户代理会按所列的顺序查找这些字体。如果列出的字体都不可用，就会简单地选择一种可用的`serif`字体。

只有当一个字体名中有一个或多个空格，或者如果字体名包含#或$之类的符号，才需要在声明中加引号。

* font-weight

值：normal | bold | bolder | lighter| 100 | 200 | 300 | 400 | 500 | 600 | 700 | 800 | 900 | inherit

100-900本身并没有固有的加粗度。每一个数对应的加粗度至少与前一个数指定的加粗度相同。100、200、300、400可能都映射到同样的较细变形；500和600可能对应到同样的较粗字体变形；而700、800、900可能都生成同样的很粗的字体变形。

* font-size

```css
p {font-size: 12px;}
em {font-size: 120%;}
strong {font-size: 135%;}
```

```html
<p><em>14.4px </em><strong>19.44px </strong>12px</p>
```

* font-style

值：italic | oblique | normal | inherit

* font-variant

值：small-caps | normal | inherit

### 文本

* text-indent 首行缩进

* text-align 水平对齐

只应用于块级元素的内联内容。

`left`: 左对齐

`center`: 居中对齐

`right`: 右对齐

`justify`: 两端对齐

* line-height 行间距

* vertical-align

只应用于行内元素和替换元素。

`baseline`: 要求一个元素的基线与其父元素

`sub`: 下标

`sup`: 上标

`bottom`: 将元素行内框的底端与行框的底端对齐。

`text-bottom`

`top`: 顶端对齐

`text-top`

`middle`

百分数：把元素的基线相对于父元素的基线升高或降低指定的量。正百分数值会使元素升高，负值则会使其降低。

长度：把一个元素升高或降低指定的距离。正长度值使元素上升，负元素值使元素下降。

* word-spacing
* letter-spacing
* text-transformation: uppercase | lowercase | capitalize | none | inherit
* text-decoration
* text-shadow

每个阴影都由一个颜色和3个长度值来定义。颜色是阴影的颜色。前2个长度值确定了阴影与文本的偏移距离，第三个长度值可选，定义了阴影的“模糊半径”。

定义一个相对于文本向右偏移5像素、向下偏移0.5em的绿色阴影，而且不模糊，可以写作：

```css
text-shadow: green 5px 0.5em;
```

负长度值会使阴影落在原文本的左上方。

* white-space

`normal`: 去掉多余的空白符。换行字符（回车）会转换为空格，一行中多个空格的序列也会转换为一个空格。

`pre`: 空白符不会被忽略

`nowrap`: 它会防止元素中的文本换行，除非使用了一个br元素。

| 值       | 空白符 | 换行符 | 自动换行 |
| -------- | ------ | ------ | -------- |
| pre-line | 合并   | 保留   | 允许     |
| normal   | 合并   | 忽略   | 允许     |
| nowrap   | 合并   | 忽略   | 不允许   |
| pre      | 保留   | 保留   | 不允许   |
| pre-wrap | 保留   | 保留   | 允许     |

* direction 文本方向

### 盒模型

![](C:\Users\liao_\Documents\前端学习\front-end-learning\CSS框模型.png)

####水平格式化

margin-left + border-left + padding-left + width(内容) + padding-left + border-right + margin-right = 父元素宽度

7个属性中，只有3个属性可以设置为`auto`: width, margin-left, margin-right。其他元素必须设置为特定的值，不设置就默认是0。

假设7个属性的和必须等于400px：

```css
p {margin-left: auto; margin-right: 100px; width: 100px;} /*'auto' left margin evaluates to 200px*/
```

如果3个属性都设置了非auto的某个值，总会把`margin-right`强制为`auto`:

```css
p {margin-left: 100px; margin-right: 100px; width: 100px;} /*right margin forced to be 200px*/
```

将某个外边距以及width设置为auto。设置auto的外边距会减为0：

```css
p {margin-left: auto; margin-right: 100px; width: auto;} /*left margin evaluates to 0*/
```

如果3个属性都设置了auto：2个外边距都会设置为0，而width会尽可能宽。

将两个外边距设置为相等的长度是将元素居中的一种正确方法。

```css
p {width: 100px; margin-left: auto; margin-right: auto;}
```



padding, border和内容宽度（及高度）绝对不能为负。只有外边距能小于0。

默认情况下，实际内容宽高为设置的width和height，但是如果设置了 box-sizing 为 border-box，则实际内容的宽高要减去对应的 border 和 padding 值。 

#### 替换元素

```css
<img src="smile.png" style="display: block; width: auto; margin: 0;">
```

原图像是多宽，元素就多宽。

指定width, height也会随着变化，除非height也被指定。

#### 垂直格式化

一个元素的默认高度由其内容决定。

对任何块级元素可以设置显式高度。

假设指定高度大于显示内容所需的高度，多余的高度看起来好像有额外的内边距一样。

假设高度小于显示内容所需的高度，浏览器会提供某种方法来查看所有内容，如滚动条，具体行为取决于overflow属性的值，而不是增加元素框的高度。

margin-top + border-top + padding-top + height(内容) + padding-bottom + border-bottom + margin-bottom = 父元素高度

7个属性中，只有3个属性可以设置为`auto`: height, margin-top, margin-bottom。其他元素必须设置为特定的值，不设置就默认是0。

**垂直相邻的外边距会被合并。**

负的上外边距会使段落看上去被向上拉；负的下外边距会使段落看上去被向下拉。

### 元素的显示和隐藏

display:none 所有后代都隐藏，好像这个元素不存在

display: hidden 变透明；子元素设为visibility:visible子元素可见

overflow 规定元素溢出父容器时的展现形式，取值有auto, hidden等。

### 雪碧图

将零星的小图片合到一张图片，想显示什么内容就通过调整background的相关属性，如background-position。这样可以减少网站加载图片的数量，提高性能。







### 样式优先级

**选择器的特殊性(specificity)**

初始都是`0,0,0,0`

* 对于选择器中给定的各个ID属性值，加`0,1,0,0`
* 对于选择器中给定的各个类属性值、属性选择或伪类，加`0,0,1,0`
* 对于选择器中给定的各个元素和伪元素，加`0,0,0,1`
* 结合符和通配选择器`*`对特殊性没有任何贡献，即`0,0,0,0` (0特殊性)

```css
h1 {color: red;} /*0,0,0,1*/
body h1 {color: green;} /*0,0,0,2 (winner)*/

h2.grape {color: purple;} /*0,0,1,1 (winner)*/
h2 {color: silver;} /*0,0,0,1*/

html>body table tr[id="totals"] td ul>li {color: maroon;} /*0,0,1,7*/
li#answer {color: navy;} /*0,1,0,1 (winner)*/
```

* 每个内联声明的特殊性都是`1,0,0,0`
* `!important`是最高级别

```css
p.dark {color: #333 !important; background: white !important;}
```

* 继承的值没有特殊性，甚至不如0特殊性

```css
* {color: gray;}
h1#page-title {color: black;}
```

```html
<h1 id="page-title">Meerkat <em>Central</em></h1>
<p>
	Welcome to the best place on the web for meerkat infomation!
</p>
```

↑`em`元素会显示为灰色而不是黑色。

### 样式的继承与层叠

元素声明的样式>浏览器默认样式>继承自父元素的样式

基于继承机制，样式不仅应用到指定的元素，还会应用到它的后代元素。

有些属性不能继承，如属性`border`就不会继承。大多数框模型属性（包括margin, padding, background, border）都不能继承。

```css
p {color: gray !important;}

<p style="color: black;">Well, <em>hello</em> there!</p>
```

↑有`!important`标志的规则胜出，所以段落为灰色。`em`元素也会继承这个灰色。

权重和来源：

1. 读者的重要声明
2. 创作人员的重要声明
3. 创作人员的正常声明
4. 读者的正常声明
5. 用户代理声明

在样式表后面出现的胜出。

```css
h1 {color: red;}
h1 {color: blue;} /*winner*/
```

文档中包含的规则比导入的规则权重高。

```css
p em {color: purple;} /*from imported style sheet*/
p em {color: gray;} /*rule contained within the document (winner)*/
```

层叠的规则：

1. 找出所有相关的规则，这些规则都包含与一个给定元素匹配的选择器。。
2. 按权重和来源对应用到该元素的所有声明排序。
3. 按特殊性对应用到给定元素的所有声明排序。
4. 按出现顺序对应用给定元素的所有声明排序。

`inherit`关键字

考虑以下样式和标记：

```css
#toolbar {background: blue; color: white;}
```

```html
<div id="toolbar">
	<a href="one.html">One</a> | <a href="two.html">Two</a> | 
    <a href="three.html">Three</a>
</div>
```
↑蓝色背景上是蓝色文本，之间有白色的竖线使其分隔。
向样式表增加以下规则：
```css
#toolbar a {color: inherit;}
```

↑这会让链接使用继承的`color`值而不是用户代理的默认样式。



## 浮动和定位

###浮动

> float
> 值：left|right|none|inherit

一个元素浮动时，其他内容会“环绕”该元素。

浮动元素周围的外边距不会合并。

如果要浮动一个非替换元素，则必须为该元素声明一个width。否则，根据CSS规范，元素的宽度趋于0.

包含块：浮动元素的包含块是其最近的块级祖先元素。
如果一个元素向左浮动，而另一个元素已经在那个位置，后放置的元素将挨着前一个浮动元素的右外边界放置。
####清除
> clear
> 值：left|right|both|none|inherit

确保h3元素不会与任何浮动元素在同一行上，要使用值both:
```css
h3 {clear: both;}
​```css
如果只是不希望h3元素的右边有浮动元素，要使用h3{clear: right;}
```
`clear:none`允许元素浮动到另一个元素的任意两边。

### 定位

利用定位，可以准确地定义元素框相对于其正常位置应该出现在哪里，或者相对于父元素、另一个元素甚至浏览器窗口本身的位置。

> position
>
> 值：static|relative|absolute|fixed|inherit

元素绝对定位时，会从文档流中完全删除，然后相对于其包含块定位。
绝对定位元素的包含块是最近的position值不为static的祖先元素。
如果left,right, top, bottom设置为auto, 会相对于其未定位前本来的顶端位置对齐。
>z-index
>值：<integer>|auto|inherit


###内容溢出和剪裁
> overflow
> 值：visible|hidden|scroll|auto|inherit

>clip
>值：rect(top, right, bottom, left)|auto|inherit
>应用于：绝对定位元素

如果一个剪裁矩形涵盖元素左上角20X20像素的一个正方形，可以定义如下：
```css
rect(0, 20px, 20px, 0)
```

###元素可见性
> visibility
> 值：visible|hidden|collapse|inherit

如果设置为`visiblity:none`，元素还是会影响文档的布局，也就是说，元素还在那里，只不过你看不见它。注意这与`display:none`的区别。`display:none`的元素不仅不会显示，还会从文档中删除。

# Sublime

### 快捷键

- Ctrl+X 删除当前行
- Ctrl+D 选择单词，重复可增加选择下一个相同的单词
- Ctrl+/ 注释单行
- Ctrl+Shift+/ 注释多行
- Ctrl+L 选中整行，继续操作则继续选择下一行，效果和 Shift+↓ 效果一样
- Ctrl+Shift+D 复制光标所在整行，插入到下一行
- Ctrl+Shift+P 打开命令框 

### 插件

- Emmet

  一个很方便生产html代码块的插件，比如要输入下面复杂的html结构，只需要这样输入 `ul.nav>li.item*5>{常用插件 $}` 然后按 `Tab` 即可快速生成。

  ```
  <ul class="nav">
      <li class="item">常用插件 1</li>
      <li class="item">常用插件 2</li>
      <li class="item">常用插件 3</li>
      <li class="item">常用插件 4</li>
      <li class="item">常用插件 5</li>
  </ul>
  ```

- SideBarEnhancements

- JsFormat : 自动帮你格式化js代码的插件，可以帮助你对齐代码或者美化被压缩后的js代码。 

- DocBlockr: 方便写注释的插件，还会自动分析函数名和参数，帮你自动生成函数注释。 

- SublimeLinter: 可以对代码进行检测并且提示，经常配合SublimeLinter-jshint 和 SublimeLinter-csslint 等一起使用。 

- TrailingSpaces: 代码里面经常会有一些看不到的没用的空格字符，这个插件可以自动帮你高亮这些字符, 并且可以一键删除。 



