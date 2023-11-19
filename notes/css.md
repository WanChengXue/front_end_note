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
html的简写方法：
- 标签名.类名，直接生成标签加类
- 标签名#id名，生成标签加id
- 多标签生成 div+p同时生成两个标签
- 父子级标签 如：div> p，则先生成div，内部生成p
- 多个相同标签，如span*3，连续三个span标签
- 有内容的标签，如果div{}，就是标签{}
css的简写大部分都是首字母的简写
## 背景属性
- 背景色，`background-color`
- 背景图， `background-image`
- 背景图平铺方式，` background-repeat`，不平铺(no-repeat), 平铺（repeat，默认）,repeat-x，水平方向平铺，repeat-y垂直方向平铺
- 背景图位置，`background-position`，坐标+px，0，0默认是左上角，水平，正数右移，垂直正数朝下移动，数字和英文单词混用也可以，关键字只写一个，另外一个维度默认居中
- 背景图缩放，`background-size`，设置背景图的大小，常用属性：cover，等比例缩放背景图片以完全覆盖背景区，可能背景图片部分看不见，contain是等比例将图片完全放入，但是可能背景区部分留有空白；另外一种是百分比，长宽以不同百分比缩放
- 背景图固定， `background-attachment`，滚动之后，内容能够滚动，背景图不发生滚动，属性值fixed
- 背景图复合属性，`background`，背景色 背景图 背景图平铺方式 背景图位置/背景图缩放
## 显示模式
标签的显示方式，作用：布局网页的时候，根据标签的显示模式选择合适的标签拜访内容
- 块级元素（div标签）
  - 独占一行
  - 宽度默认是父级的100%
  - 添加宽高属性生效
- 行内元素（span标签）
  - 行内共存
  - 尺寸由内容撑开，加宽高是不生效的
- 行内块元素（img）
  - 一行共存多个
  - 默认尺寸和内容一样大，可以支持加宽高

### 转换显示模式
属性名，display，属性值：
<table border='1'>
<tr>
<th><span style="font: italic bold 16px/2 kai; color: red">属性值</span></th>
<th><span style="background: url(../imgs/cat.png)">效果</span></th
</tr>
<tr>
<td>block</td>
<td>块级</td
</tr>
<tr>
<td>inline-block</td>
<td>行内块</td>
</tr>
<tr>
<td>inline</td>
<td>行内</td>
</tr>
</table>

常用的两种属性是`block, inline-block`，


## 选择器
### 结构伪类选择器
作用：根据元素的结构关系查找元素，写法：
<table border="1">
<tr><th>选择器</th> <th>说明</th></tr>
<tr><td>E:first-child</td> <td>查找第一个E元素</td></tr>
<tr><td>E:last-child</td> <td>查找最后一个E元素</td></tr>
<tr><td>E:nth-child(N)</td> <td>查找第N个元素（第一个元素N值为1）</td></tr>
<tr><td>E:nth-child(2n-1)</td> <td>查找所有的奇数</td></tr>
</table>

**E表示选择器的名字**

### 伪元素选择器
作用：创建虚拟元素（伪元素），用来摆放装饰性的内容
<table border='1'>
<tr><th>选择器</th> <th>说明</th></tr>
<tr><td>E::before</td> <td>在E元素里面最前面添加一个伪元素</td></tr>
<tr><td> E::after</td> <td>在E元素里面最后面添加一个伪元素</td></tr>
</table>

## PxCook软件
倒入PSD文件，创建web项目，点击开发模式

## 盒子模型
作用：布局网页，摆放盒子和内容

### 组成
- 内容区域：width & height
- 内边距：padding，出现在内容和盒子边缘之间
- 边框线 border
- 外边距 margin 出现在盒子外面

#### 边框线
border(bd),属性值：边框线粗细，线条样式，颜色（不区分顺序）
常用的线条样式有：
<table border="1">
<tr><th>属性值</th> <th>线条样式</th></tr>
<tr><td>dashed</td><td>虚线</td>/<tr>
<tr><td>dotted</td> <td>点线</td></tr>
</table>

设置四个方向的border，border-top，border-right，border-left，border-bottom

#### 内边距
padding，和border一样，有padding，padding-top，padding-left，padding-right，padding-bottom，如果省略写法，使用多值写法
- padding: 10px 20px 40px 80px，这种写法定义上右下左四个边距，顺时针
- padding: 10px 20px 40px，这种写法上右下会变成10，20，40，左边会和右边一样
- padding: 10px 20px，这种写法上下为10px，左右为20px


#### 尺寸计算
默认情况：盒子尺寸=内容尺寸+border尺寸+内边距尺寸
<br>
结论：给盒子加border/padding会撑大盒子<br>
解决办法：
- 手动做减法：减掉border/padding的尺寸，修改div的width和height
- 内减：padding-size，border-size


#### 外边距
和padding一样，可以自己定义：margin-top，margin-right，margin-bottom，margin-left。同样，margin也有简写模式，使用一个margin，后面跟着四个值/三个值/两个值0

**设置版心居中，左右margin设置auto即可**


#### 清除默认样式
清除标签默认的样式，比如：默认的内外标签，使用的方式：
```
*{
  padding: 0px;
  margin: 0px;
  box-sizing: border-box;
}
```
#### 元素溢出
控制溢出元素的内容的显示方式，属性名overflow，属性值：
- hidden，溢出隐藏
- scroll，溢出滚动（无论是否溢出，都显示滚动条位置）
- auto，溢出滚动（溢出才显示滚动条的位置）


#### 外边距问题，合并现象
垂直排列的兄弟标签，A盒子的下标签和B盒子的上标签，A和B盒子之间的实际间距取决于A盒子下标签和B盒子上标签中较大的那个

#### 外边距问题，塌陷问题
父子级的标签，子级的添加上外边距会产生塌陷问题，会导致父级同时下移，解决办法：
- 取消子级margin，父级设置padding
- 父级设置overflow：hidden
- 父级设置border-top

#### 内外边距问题
行内元素添加margin和padding，无法改变元素垂直位置

#### 盒子外边框变成圆角
使用`border-radius`，记忆方法，左上，右上，右下，左小，同样支持2，3，值写法，缺省的和对角一样
<br>
圆角：
- 正圆形状，给正方形盒子设置圆角属性值为宽高的一半，或者百分之五十，用在img中，作为头像
- 胶囊形状，给长方形盒子设置圆角属性值为高度的一半，或者百分之五十，作为按钮

#### 盒子外边增加阴影属性
使用属性box-shadow，`x轴偏移量 y轴偏移量 模糊半径 扩散半径 颜色 内外阴影`，x，y轴偏移量必须书写，默认使用外阴影，内阴影必须添加inset
