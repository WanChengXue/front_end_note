# WebAPI
## 1. WebAPI初识
### 1.1 作用和分类
作用：使用js去操作html和浏览器 <br>
分类：DOM(文档对象模型)，BOM(浏览器对象模式)

### 1.2 DOM
document object model：开发网页内容特效和实现用户交互
### 1.3 DOM树
- 将HTML标签以树状结构直观的表现出来
- 描述网页内容的名词
- 作用：文档树直观的体现了标签与标签之间的关系
#### 1.4 DOM对象
- DOM对象：浏览器根据HTML标签生成的JS对象
  - 所有的属性标签都可以在这个对象上找到
  - 修改这个对象的属性会自动映射到标签身上
- DOM的核心思想
  - 把网页内容当做对象来处理
- document对象
  - 是DOM里提供的一个对象
  - 所以它提供的属性和方法都是用来访问和操作网页内容的`document.write()`
  - 网页所有内容都在document里面

## 2 获取DOM对象
根据css选择器的方式获取DOM对象
### 2.1 根据css选择器获取DOM对象
- 选择匹配的第一个元素`document.querySelector('css选择器')`
- 选择多个元素`docuement.querySelectorAll('css选择器')`，返回的一定是一个伪list

### 2.2 操作元素的内容
- 对象.innerText(修改标签内的文本，不解析标签)
- 对象.innerHTML(修改标签内的html，建议使用模板字符串)

### 2.3 操作元素的属性
使用querySelector选择出来某一个标签对象，然后使用.操作修改内部的属性，如`<img src="xxx">`，然后使用`const img = document.querySelector('img')`得到这个对象，通过`img.src = xx`即可更换图片

### 2.4 修改元素的css
通过`object.style.attr`方式修改边框的颜色

### 2.5 通过类名来修改样式
```javascript
<style>
    .box{
        width: 100px
    }
</style>
<div></div>
// 通过给div增加类名box来修改css样式
<script>
    const div_object = document.querySelector('div')
    /* 这里使用className是因为class是关键字 */
    div_object.className = 'box'
</script>
```
### 2.5 通过classList操作类控制css（追加写入）
```javascript
.class1 {
    xxx:xxx
    }

.class2{
    sss:sss
    }
<div class="class1"></div>
<script>
    const div = document.querySelector('div')
    div.classList.add('class2')
    {/* div.classList.remvoe('class1'),删除class1类 */}
    {/* div.classList.toggle('class2'),如果div有class2这个类就删除，没有就添加 */}
</script>
```
### 2.6 操作表单元素属性
- 表单很多情况，也需要修改属性，比如点击眼睛，可以看到密码，本质是把表单类型转换为文本框
- 正常的有属性有取值的 跟其他的标签属性没有任何区别
- 表单属性添加就有效果，移除就没有效果，一律使用bool值表示

### 2.7 自定义属性
- 标准属性：标签天生自带的属性，比如class id title等，可以直接使用点语法操作，比如：disabled，checked，selected
- 自定义属性：
  - 在html5中推出了专门的data-自定义属性
  - 在标签上一律以data-开头
  - 在DOM对象上一律以dataset对象方式获取

### 2.8 定时器-间歇函数
网页中经常会出现：每隔一段时间需要自动执行一段代码

<div style="background-color: white">
  setInterval(function(){}, 1000)， 每隔1s执行一下前面的匿名函数
</div>

关闭定时器
```javascript
let n = setInterval(fn, 1000)
clearInterval(n)
```
当然一般不会这么做，在实际的应用中，都是鼠标经过事件定时器关闭，移开之后重新开启

## 3. 事件
### 3.1 事件监听
目标：能够给DOM元素添加事件监听
- 什么是事件
  - 事件是在编程时系统内发生的动作或者发生的事情，比如用户在网页上单击一个按钮
- 什么是事件监听
  - 就是让程序检测是否有事件产生，一旦有事件触发，就立即调用一个函数做出response，也称为绑定事件或者注册事件，比如鼠标经过显示下拉菜单

语法：
```javascript
元素对象.addEventListener('事件类型', 要执行的函数)
```
### 3.2 事件监听版本
- DOM L0 事件源.on事件 = 匿名函数
- DOM L1 元素对象.addEventListener('事件', 匿名函数)
- 区别，on方式会被覆盖，addEventListener方式可以绑定多次，拥有事件更多特性

### 3.3 事件对象
- 鼠标事件
  - click 鼠标点击
  - mouseenter 鼠标移动
  - mouseleave 鼠标离开
- 焦点事件
  - focus 获得焦点
  - blur 失去焦点
- 键盘事件
  - keydown 键盘按下触发
  - keyup 键盘抬起触发
- 文本事件
  - input 用户输入事件

- 事件对象
  - 也是个对象，这个对象里面有事件触发时候的相关信息
  - 例如：鼠标点击事件中，事件对象就存了鼠标点在哪个位置等信息
- 使用场景
  - 可以判断用户按下哪个键，比如按下回车键可以发布新闻
  - 可以判断鼠标点击了哪个元素，从而做相应的操作
  - 在回调函数中的第一个参数就是事件对象
  - 在事件绑定的回调函数的第一个参数就是事件对象，也就是写在`addEventListener('click', function(e){})`，其中e就是事件对象
- 常见的属性
  - type，事件的类型
  - clientX/clientY获取事件的位置，相对于浏览器左上角而言
  - offsetX/offsetY获取事件的相对位置，相对于当前DOM元素左上角的位置
  - key用户按下键盘的值

### 3.4 环境变量
指的是函数内部特殊的变量this，每一个函数内部中都会有this对象，哪个对象调用这个函数，this就是指向谁
