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
- 通配符选择器
