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

> [文档](https://developer.mozilla.org/zh-CN/docs/learn/HTML/Introduction_to_HTML/The_head_metadata_in_HTML#%E5%85%83%E6%95%B0%E6%8D%AE%EF%BC%9A%3Cmeta%3E%E5%85%83%E7%B4%A0)

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

##### 换行`<br>`和分割线`<hr>`

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

5. 链接到文档片段

   先给要链接到的片段分配一个`id`，再通过`<a href=''>`链接它

```html
<h2 id="Mailing_address">邮寄地址</h2>
<p><a href="contacts.html#Mailing_address">我们的地址</a>。</p>
<p>本页面底部可以找到 <a href="#Mailing_address">公司邮寄地址</a>。</p>
```



##### `<span>` 无语义元素（加CSS）

##### 描述列表 `<dl>`

```html
<dl>
  <dt>x</dt>
    <dd>x</dd>
  <dt>x</dt>
    <dd>x</dd>
  <dt>x</dt>
    <dd>x</dd>
</dl>
```

##### 引用

###### 块引用`<blockquote>`

```
<blockquote cite="1.html">xxx</blockquote>
```

###### 行内引用 `<q>`

```html
<q cite="">shit</q>
```

###### 引文`<cite>`

[`cite`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/blockquote#attr-cite)属性内容不会被浏览器显示、屏幕阅读器阅读，需使用 JavaScript 或 CSS，浏览器才会显示`cite`的内容。如果你想要确保引用的来源在页面上是可显示的，更好的方法是为`<cite>`元素附上链接

```html
<a href="1.html"><cite>1.html</cite></a>
```

##### 缩略语`<abbr>`

```html
<abbr title="fuck.html">fuck</abbr>
```

##### 标记时间`<time>`

```html
<time datetime="2016-01-20">2016年1月20日</time>
```

##### 标记联系方式`<address>`

##### 上标和下标`<sup>`和`<sub>`

##### 展示计算机代码

- `<code>`: 用于标记计算机通用代码。
- `<pre>`: 用于保留空白字符（通常用于代码块）——如果您在文本中使用缩进或多余的空白，浏览器将忽略它，您将不会在呈现的页面上看到它。但是，如果您将文本包含在`<pre></pre>`标签中，那么空白将会以与你在文本编辑器中看到的相同的方式渲染出来。
- `<var>`: 用于标记具体变量名。
- `<kbd>`: 用于标记输入电脑的键盘（或其他类型）输入。
- `<samp>`: 用于标记计算机程序的输出。

------

### 元素属性

#### 布尔属性

有时你会看到没有值的属性，它是合法的。这些属性被称为布尔属性，他们只能有跟它的属性名一样的属性值。例如[`disabled`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/Input#attr-disabled) 属性，他们可以标记表单输入使之变为不可用(变灰色)，此时用户不能向他们输入任何数据。

```html
<input type="text" disabled="disabled">
```

### HTML 布局细节

> [链接](https://developer.mozilla.org/zh-CN/docs/Learn/HTML/Introduction_to_HTML/Document_and_website_structure)

1. `<main>`存放每个页面独有的内容。每个页面上只能用一次 `<main>`且直接位于`<body>`中。最好不要把它嵌套进其它元素。
2. `<article>`包围的内容即一篇文章，与页面其它部分无关(比如一篇博文)
3. `<section>`是按功能组织页面
4. `<aside>`包含一些间接信息（术语条目、作者简介、相关链接，等等）。
5. `<header>`全局页眉或特定内容的页眉
6. `<nav>`导航栏
7. `<footer>`页脚

大致布局为

```html
<header>：页眉。
<nav>：导航栏。
<main>：主内容。主内容中还可以有各种子内容区段，可用<article>、<section> 和 <div> 等元素表示。
<aside>：侧边栏，经常嵌套在 <main> 中。
<footer>：页脚。
```

!> 无语义元素可以用 块级`<div>`或内联`<span>`包裹，但应该尽量避免使用，有替代方案应尽可能使用替代方案

