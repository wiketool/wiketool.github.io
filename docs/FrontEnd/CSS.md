# CSS - Cascading Style Sheets

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
p
选择 <p>
```

#### ID选择器

```css
#my-id
```

#### 类选择器

```css
.class
```

#### 属性选择器

```
img[xxxx] 
选择 <img src="xxxx"> 而不是 <img>
```

#### 伪（Pseudo）类选择器

特定状态下的特定元素（比如鼠标指针悬停）

```
a:hover
仅在鼠标指针悬停在链接上时选择
<a>
```

