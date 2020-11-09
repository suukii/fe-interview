# CSS 部分

- [CSS 部分](#css-部分)
  - [让元素水平垂直居中的方法有多少种？](#让元素水平垂直居中的方法有多少种)
  - [浮动布局的优缺点以及如何清除浮动布局？](#浮动布局的优缺点以及如何清除浮动布局)
  - [使用 `display: inline-block;` 会产生什么问题？解决方法是什么？](#使用-display-inline-block-会产生什么问题解决方法是什么)
  - [布局题：div 垂直居中，左右 10px，高度始终为宽度一半](#布局题div-垂直居中左右-10px高度始终为宽度一半)
  - [什么是 BFC？什么条件下会触发？应用场景有哪些？](#什么是-bfc什么条件下会触发应用场景有哪些)

> 以下部分整理自[神三元的博客](http://47.98.159.95/my_blog/)。

## 让元素水平垂直居中的方法有多少种？

**水平**

-   行内元素：
    -   `text-align: center;`
-   宽度已知的块级元素：
    -   `width` + `margin: 0 auto;`
    -   绝对定位 + `width` + `margin-left` 设为宽度的一半的负值
-   宽度未知的块级元素：
    -   `display: flex;` + `justify-content: center`
    -   绝对定位 + `transform: translateX(x);`
    -   父级元素 `display: table;`，居中元素 `margin: 0 auto;`
    -   变成行内元素 `display: inline-block;` + `text-align: center;`

**垂直**

-   `line-height` 设置为 `height`
-   `display: flex;` + `align-items: center`
-   绝对定位 + `transform: translateY(y);`
-   父元素 `display: table-cell; vertical-align: middle;`

**水平垂直**

-   `display: flex;` + `justify-content: center` + `align-items: center`
-   绝对定位 + `transform: translate(x, y);`
-   绝对定位 + 负 margin
-   父元素 `display: table-cell; vertical-align: middle;`，块级居中元素 `margin: 0 auto`；行内居中元素则在父元素上再设置 `text-align: center;`

## 浮动布局的优缺点以及如何清除浮动布局？

**优点**

实现文字环绕图片效果时可以用。

**缺点**

浮动元素脱离了正常的文档流，会导致父元素高度塌陷。

**清除浮动**

1. 在浮动元素后增加一个元素，再用 `clear` 属性。
2. 父元素添加 `overflow: hidden;`，原理是新建一个 BFC，BFC 在计算高度时会把浮动元素考虑进来。
3. 用 `::after` 伪类在父级添加一个子元素，再用 `clear` 属性。

另外要注意的是，浮动元素有块级元素的特性，比如 `inline` 元素浮动之后，它的 `display` 属性会被计算为 `block`，就可以设置宽高等属性了。

## 使用 `display: inline-block;` 会产生什么问题？解决方法是什么？

**问题**

两个 inline-block 元素并排一行时中间会有空白间隙。这是因为 HTML 中的换行被处理成了一个空白符。

**解决方法**

1. 设置父级元素 `font-size: 0;`
2. 删掉 HTML 中的换行
3. 两个并排的元素都设置 `float: left;`

## 布局题：div 垂直居中，左右 10px，高度始终为宽度一半

```
问题描述: 实现一个div垂直居中, 其距离屏幕左右两边各10px, 其高度始终是宽度的50%。同时div中有一个文字A，文字需要水平垂直居中。
```

居中就不多说了，说一下高度保持为宽度一半怎么实现。

-   `height: 0; padding-bottom: 50%;`，padding 如果设置为百分值，它的计算是基于元素的宽度的。
-   `calc()` + `vw`，`width: calc(100vw - 20px); height: calc(50vw - 10px);`

> 延申：子元素的宽度设置为百分比的话，如果子元素是绝对定位，则宽度计算基于父元素的 `content` + `padding`，如果不是绝对定位，则基于父元素的 `content`(标准盒模型) 或者 `content` + `padding` + `border`(IE 盒模型)。

## 什么是 BFC？什么条件下会触发？应用场景有哪些？

简单地说，BFC 就是页面渲染中的一个组成部分。在 BFC 中，块级元素 (block element) 会按流式布局 (normal flow) 进行排列。

**应用场景**

-   可以防止浮动导致父元素高度坍塌，因为 BFC 计算元素高度的时候会把浮动元素也计算在内。
-   可以避免外边距折叠 (margin collapse)，因为外边距折叠只会发生在同一个 BFC 中，所以新建一个 BFC 可以避免这种情况出现。
-   可以阻止文字环绕，文字会围绕着浮动元素排列，如果想要阻止这种行为，可以给文字的容器生成一个 BFC。

**哪些情况会触发 BFC？**

-   `float` 非 `none`
-   `position` 非 `static` 和 `relative`
-   `overflow` 非 `visible`
-   `display` 是 `flow-root`
-   `display` 是 `table-cell`, `table-caption`, `table-row`, `table-row-group`, `table-header-group`, `table-footer-group`, `inline-tale`
-   `display` 是 `flex`, `inline-flex`, `grid`, `inline-grid`, 或者是设置了这些属性的元素的直接子元素
-   设置了 `contain` 属性
