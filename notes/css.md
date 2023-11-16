# CSS相关介绍
作用：美化页面内容，扩展html的样式
## 基础选择器，文字控制属性
在html中放在head标签内部，title标签的下面，使用`<style></style>`

这个部分没有啥技巧，就是记：

- color表示颜色
- font-size表示字体尺寸

简单给一个demo:
<style>
p: {
    color:red;
    font-size: 4em;
}
</style>

<p>
    简单的文本测试
</p>

## css的引入方式
<ul>
    <li>放在html内部</li>
    <li>放在外部专用css文件</li>
    <li>行内样式，配合js使用</li>
</ul>
外部引入css的使用方法使用

```
<link rel="stylesheet" href="xxx.css">
```

行内样式引入的方法，
```
<div style="xxx:xxx"></div>
```

<div style="color: red; font-size:20px">这是div标签的测试</div>

## css选择器
作用：查找标签，设置样式
<br>
基础选择器：
- 标签选择器（所有同名标签使用相同样式，如p,img,a,不是太实用，无法差异化同名标签的样式）
- 类选择器（查找标签，差异化设置标签的显示效果）
    - 定义类选择器，.类名
    - 使用类选择器，标签添加clss="类名"
    - 使用类选择器，可以同时使用多个类选择器，空格分开即可`<class="style_name_1 style_name_2">`，类选择器可以覆盖标签选择器
    - 开发习惯，类名一般使用多个单词，使用-连接
- id选择器
  - 一般配合js一起使用，很少用来设置css的样式
  - 定义id选择器， #id名
  - 使用id选择器，id=id名
  - 一个页面，同一个id只能使用一次
- 通配符选择器
  - 查找所有标签设置相同样式
  - 使用方法，*{}，开发初期使用，清楚标签的默认属性

## 文字控制属性
很多：
- 字体大小，`font-size`
- 字体粗细，`font-weight`，normal就是正常，bold就是加粗
- 字体倾斜，`font-style`，normal就是不倾斜，italic就是倾斜
- 行高，`line-height`，设置多行文本之间的距离，如果是数字，则表示行高为当前文字的倍数，也可以直接指定px，行高是由上间距，文本高度，下间距三部分组成，垂直居中技巧，设置行高等于盒子的高度，只能单行文字垂直居中
- 字体族，`font-family`，比如楷体
- 字体复合属性，`font`,写法是否倾斜，是否加粗，文字大小/行高，字体，必须写字号和字体，否则不生效
  <p style="font: italic bold 20px/2 sans-serif">test</p>
- 文本缩进，`text-indent`，属性值有两种，一种是数字+px，绝对大小，第二种是数字加em，这个表示是当前文字大小（推荐使用）
- 文本对其，`text-align`，调节文字水平对齐方式，`left, center, right`分别表示左对齐，居中，右对齐
  <p style="text-align: center; font-weight: bold; font-style: italic; color: yellow">测试文字居中</p>
- 修饰线，`text-decoration`，分成none，无；underline，下划线；line-through，删除线；overline，上划线
- 颜色，`color`，四种方式（后三种实际使用）：
  - 英文单词写法，red，yellow等
  - rgb表示，rgb(r,g,b)其中r,g,b分别是0-255范围内
  - rgba表示rgba(r,g,b,a)其中a是0-1表示透明度
  - 十六进制表示#RRGGBB
  <p style="color: yellow">黄色测试</p>
  <p style="color: rgb(138,26,223)">测试</p>
  <p style="color: rgba(138, 26, 223, 0.8)">测试</p>

  <p style="color: #1000ff">测试</p>

## 复合选择器
由两个或者多个基础选择器，通过不同的方式组合而成
### 后代选择器
选择器写法 父选择器 子选择器（css属性）
<div>
    <span>
        span测试
    </span>
</div>
这个选择器会将递归查找div/*/span下面的都会变

### 子代选择器
`div > span{}`只会查找div/span下面的标签，当然/div/div/span也是有效的，也就是说*/div/span/下面的会生效

### 并集选择器
并集选择器，选中多组标签设置相同的样式，选择器写法：选择器1，选择器2，...，选择器N {}即可


### 伪类选择器
伪类表示元素状态，选中元素的某个状态设置样式，比如鼠标悬停状态：选择器：hover(css属性)

超链接有四个状态：
- :link，访问前
- :visited，访问后
- :hover，鼠标悬停
- :active，点击时
## css特性

### 继承性
子级默认继承父级的文字控制属性，当标签具备自己的样式，则不继承

### 层叠性
- 相同的属性会覆盖，后面的css属性会覆盖前面的css属性
- 不同的属性会叠加，不同的css的属性都会生效

### 优先级
当一个标签使用了多种选择器的时候，生效顺序，谁的优先级高，谁生效，显然当选择器选择的范围越广，优先级越低。
通配符选择器 < 标签选择器  < 类选择器 < id选择器 < 小于行内样式 < !important(提权功能，提高到最高,谨慎使用)

提权使用，在css的style中，如：
```
*{
    color: red !important;
}
```

在复合选择器中，权重计算，行内样式，id选择器个数，类选择器的个数，标签选择器个数，从左向右依次比较选个数

### emment写法

## 背景属性

## 显示模式
