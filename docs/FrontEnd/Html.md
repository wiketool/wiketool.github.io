# HTML5

## 基础入门

### 元素分类

------


#### 嵌套元素

把元素放到其它元素之中——这被称作嵌套。

```html
<p>我的猫咪脾气<strong>爆</strong>:)</p>
```

#### 元素和块级元素

- 块级元素在页面中以块的形式展现 —— 相对于其前面的内容它会出现在新的一行，其后的内容也会被挤到下一行展现。

- 内联元素通常出现在块级元素中，且不会导致文本换行

```html
<em>第一</em><em>第二</em><em>第三</em>
<p>第四</p><p>第五</p><p>第六</p>
```

#### 空元素

```html
<img src="images/firefox-icon.png" alt="测试图片">
```

------

### 常见Tag <>

##### 元数据 `<meta>`

1. `charset`字符编码
2. `description` 搜索引擎描述

##### 外部资源链接`link` 

1. `rel = stylesheet` css
2. `rel="shortcut icon" href="favicon.ico" type="image/x-icon"`

##### `script` 嵌入式脚本

1. `src = xxx`
2. `defer `这个布尔属性被设定用来通知浏览器该脚本将在文档完成解析后，触发 `DOMContentLoaded` 事件前执行。

##### 标题 `<h1>~<h6>`

##### 段落 `<p>`

##### 列表 （可嵌套）

1. 有序列表 `<ol>`
2. 无序列表 `<ul>`

```html
<ul>
	<li>我试试</li>
</ul>
<ol>
	<li>我在试试</li>
</ol>
```

##### 链接 `<a href = " ">`

```html
<a href="https://www.baidu.com"> 去百度一下吧</a>
```

1. `title = 'shit'` 悬停后显示标题信息
2. `download = ''`当您链接到要下载的资源而不是在浏览器中打开时，您可以使用 `download` 属性来提供一个默认的保存文件名（译注：此属性仅适用于同源URL）。
3. 电子邮件链接
4. 如上所述，你可以将一些内容转换为链接，甚至是[块级元素](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Block-level_elements)。例如你想要将一个图像转换为链接，你只需把图像元素放到`<a></a>`标签中间。

##### `<span>` 无语义元素（加CSS）

------

### 元素属性

#### 布尔属性

有时你会看到没有值的属性，它是合法的。这些属性被称为布尔属性，他们只能有跟它的属性名一样的属性值。例如[`disabled`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/Input#attr-disabled) 属性，他们可以标记表单输入使之变为不可用(变灰色)，此时用户不能向他们输入任何数据。

```html
<input type="text" disabled="disabled">
```

