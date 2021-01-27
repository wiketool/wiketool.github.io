# CSS - Cascading Style Sheets

```html
<link href="styles/style.css" rel="stylesheet">
```

`rel`代表外部资源与当前文档的关系

## CSS基础

```css
p(选择器) {
  color: red;
  width: 500px;
  border: 1px solid black;
}
```

### 选择器

#### 元素选择器（标签选择器）

```css
p{
    
}
选择 <p>
```

#### ID选择器

```css
#my-id{
    
}
```

#### 类选择器

```css
.class{
    
}
```

#### 属性选择器

```css
img[xxxx]{
    
} 
选择 <img src="xxxx"> 而不是 <img>
```

#### 伪（Pseudo）类选择器

特定状态下的特定元素（比如鼠标指针悬停）

```css
a:hover{

}
仅在鼠标指针悬停在链接上时选择
<a>
```

### 字体

> ```html
> <link href="https://fonts.font.im/css?family=Open+Sans" rel="stylesheet" type="text/css"> 
> /* Google font 添加到<head> */
> ```

```css
.class{
    font-family:'Open Sans',sans-serif;
    font-size:88px;
    text-align:center;
    /* 行高 */
    line-height: 2;
    /* 字间距 */
    letter-spacing: 1px;
}
```

### 布局

- `padding`：即内边距，围绕着内容（比如段落）的空间。
- `border`：即边框，紧接着内边距的线。
- `margin`：即外边距，围绕元素外部的空间。

```css
body {
  width: 600px;
  margin: 0 auto;
  background-color: #FF9500;
  padding: 0 20px 20px 20px;
  border: 5px solid black;
}
```

- `width: 600px;` —— 强制页面永远保持 600 像素宽。
- `margin: 0 auto;` —— 为 `margin` 或 `padding` 等属性设置两个值时，第一个值代表元素的上方**和**下方（在这个例子中设置为 `0`），而第二个值代表左边**和**右边（在这里，`auto` 是一个特殊的值，意思是水平方向上左右对称）。你也可以使用一个，三个或四个值，参考 [这里](https://developer.mozilla.org/zh-CN/docs/Web/CSS/margin#取值) 。
- `background-color: #FF9500;` —— 如前文所述，指定元素的背景颜色。我们给 body 用了一种略微偏红的橘色以与深蓝色的`html`元素形成反差，你也可以尝试其它颜色。
- `padding: 0 20px 20px 20px;` —— 我们给内边距设置了四个值来让内容四周产生一点空间。这一次我们不设置上方的内边距，设置右边，下方，左边的内边距为20像素。值以上、右、下、左的顺序排列。
- `border: 5px solid black;` —— 直接为 body 设置 5 像素的黑色实线边框。

!> 图片为内联元素，要控制图片的padding等块级行为要`display:block`