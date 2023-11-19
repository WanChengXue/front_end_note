# 表单

在前端中，分成列表，表格，以及表单，分别用在:

- 多种选项列表显示
- 表格显示
- 提交数据

这三种标签都是嵌套关系

## 列表

作用：布局内容排列整齐的区域，分为无序列表，有序列表，定义列表三种。无序列表最常用，清除列表前面的符号，使用`li{list-style: none}`

### 无序列表

使用`<ul></ul>`嵌套`<li></li>`，含义：`<ul></ul>`是无序列表的父标签，`<li></li>`中间的是值单独的一行

### 有序列表

使用`<ol></ol>`嵌套`<li></li>`，无论是`<ul></ul>, <ol></ol>`只能嵌套`<li></li>`，但是`<li></li>`内部可以有多种标签

### 定义列表

一般用在网页的底部，类似帮助中心的位置，一个标签多个内容。标签：`<dl></dl>`嵌套`<dt></dt> <dd></dd>`，其中 dt 表示的是第一列表的标题，dd 是定义列表的描述

## 表格

网页中的表格和 excel 表格类似，使用方式：table 嵌套 tr，tr 嵌套 td/th。解释：

- table 是表示表格
- tr 表示行
- th 表示表头单元格
- td 表示内容单元格

```html
<table>
  <tr>
    <th>第一列</th>
    <th>第二列</th>
    <th>第三列</th>
  </tr>

  <tr>
    <td>第一列的内容</td>
    <td>第二列的内容</td>
    <td>第三列的内容</td>
  </tr>
</table>
```

默认是什么都没有的，如果需要增加表格先就需要添加样式，比如`border`

表格结构标签（只是给浏览器看的，加不加无所谓）

- thead,表格头部内容
- tbody，表格主体，主要内容
- tfoot，表格底部，汇总信息

### 合并单元格

将多个单元格合并成为一个单元格，以合并同类信息，当然可以竖着合并，也可以横着合并（跨行合并，跨列合并）

- 保留最左最上单元格，添加属性，数字表示的是合并单元格的数目
- 跨行合并，使用 rowspan
- 跨列合并，使用 colspan
- 删除单元格

所有合并都只能在自己的这个结构标签内部合并

## 表单

作用：收集用户信息
使用场景：登录界面，注册页面，搜索区域

`<input>`标签使用，标签内部有一个 type 的属性，不同的属性值功能不同

- 如果是 text，文本框，用于输入单行文本
- password 密码框
- radio 表示单选框
- checkbox 表示多选框
- file 表示上传文件

input 标签使用占位文本，就是 placeholder，只在 text 和 password 类型下才起作用

### 单选框`radio`

常用属性：
<table border='1'>
<tr>
    <th>属性名</th>
    <th>作用</th>
    <th>特殊说明</th>
</tr>

<tr>
    <td>name</td>
    <td>控件名称</td>
    <td>控件分组，同组只能选择一个</td>
</tr>

<tr>
    <td>checked</td>
    <td>默认选中</td>
    <td>属性名和属性值相同，简写为一个单词</td>
</tr>
</table>

使用代码：
<input type="radio" name="gender" checked>男
<input type="radio" name="gender">女

就是在input里面定义name，checked表示默认选中

### 多文件上传
默认情况下，一次只能传一个文件，只要增加multiple即可

### 多选框checkbox
默认选中和radio一样，一样是checked，和radio不一样的是，在多个input中可以给checked
<br>
<input type="checkbox" name="interest" checked>摸鱼
<input type="checkbox" name="interest" checked>睡觉
<input type="checkbox" name="interest">工作

### 下拉菜单
使用select嵌套option，select是下拉菜单整体，option是下拉菜单中的每一项，也支持默认选中功能，增加selected
<br>
<select>
    <option>选项一</option>
    <option selected>选项二</option>
</select>

## 文本域标签
作用：多行输入文本标签
<textarea></textarea>
右下角的拖拽功能需要禁用，使用css设置尺寸，不是使用html设置

## label标签
作用：给表单添加说明文本，当然也可以使用label标签增加表单空间的点击范围
<ol>
  <li>
    label标签只包括内容，不包括表单控件，设置label标签的for属性值和表单控件id属性值相同
  </li>
  <li>
    使用label标签包含控件和文字，不需要属性
  </li>
</ol>
<br>
两种写法的demo：
<input type="radio" id="man" name="gender" checked>
<label for="man">男</label>
<label><input type="radio" name="gender">女</label>

## 按钮标签
使用双标签`<button></button>`，type属性不同，按钮功能也不一样，常用：

- submit(默认),点击按钮，数据提交到后台
- reset，重置按钮，一点击恢复表单的默认值
- button，普通按钮，没有功能，配合js使用

需要包含在form标签中使用，form会有一个action，表示表单内容提交到的后台地址：
<form>
<ul>
<li><input type="text">输入用户名</li>
<li><input type="password">请输入密码</li>
</ul>
<button type="reset">重置按钮</button>
</form>

## 布局标签`span,div`
作用：划分网页，其中div是独占一行，span是不换行
<div>第一行测试</div>
<div>第二行测试</div>
<span>第三行测试</span>
<span>第三行测试</span>

## 字符实体
如果想要在网页上显示`<>`这种符号，需要特殊写：

- `<`，小于号，使用`&lt` &lt;
- 空格，`&nbsp` &nbsp;
- `>`，大于号，使用`&gt` &gt;
