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

  ![1525485957033](C:\Users\LIGHTN~1\AppData\Local\Temp\1525485957033.png)

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

![1525499613160](C:\Users\LIGHTN~1\AppData\Local\Temp\1525499613160.png)

**px**: 像素，用于屏幕显示器上，传统上一个像素对应于计算机屏幕上的一个点。

**%**: 百分比。相对于父元素。

如果对html元素设置font-size为百分比值，是以16px为参照进行计算的。

**em**: 

对于font-size, 1em等于父元素设置的字体大小。父级元素没有设置会一直网上找，如果都没有就参照浏览器默认大小。

对于其他属性（border, width, height, padding, margin, line-height），参照该元素的font-size.

em不建议使用。

```
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
```

```

注：chrome 浏览器最小的字体为 12px，如果设置 10px 也会渲染成 12px  

### 颜色

- 关键词

  颜色名

  transparent

  currentColor

- rgb(red, green, blue) 

- rgba(red, green, blue, alpha) 

- 十六进制

### 盒模型

![1525501552719](C:\Users\LIGHTN~1\AppData\Local\Temp\1525501552719.png)

默认情况下，实际内容宽高为设置的width和height，但是如果设置了 box-sizing 为 border-box，则实际内容的宽高要减去对应的 border 和 padding 值。 

![1525501891969](C:\Users\LIGHTN~1\AppData\Local\Temp\1525501891969.png)



### 元素的显示和隐藏

display:none 所有后代都隐藏，好像这个元素不存在

display: hidden 变透明；子元素设为visibility:visible子元素可见

overflow 规定元素溢出父容器时的展现形式，取值有auto, hidden等。

### 雪碧图

将零星的小图片合到一张图片，想显示什么内容就通过调整background的相关属性，如background-position。这样可以减少网站加载图片的数量，提高性能。



### 样式的继承与层叠

元素声明的样式>浏览器默认样式>继承自父元素的样式



### 样式优先级

![1525505817530](C:\Users\LIGHTN~1\AppData\Local\Temp\1525505817530.png)

!important是最高级别



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



