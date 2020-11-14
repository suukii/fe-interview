# HTML 部分

- [HTML 部分](#html-部分)
  - [HTML5 和 HTML4 究竟有哪些不同？](#html5-和-html4-究竟有哪些不同)
  - [meta 标签的属性有哪些？](#meta-标签的属性有哪些)
  - [`href` 和 `src` 的区别？](#href-和-src-的区别)
  - [`script` 标签中的 defer 和 async 有什么区别？](#script-标签中的-defer-和-async-有什么区别)

<hr/>

> 以下部分整理自[神三元的博客](http://47.98.159.95/my_blog/)。

<hr/>

## HTML5 和 HTML4 究竟有哪些不同？

1. 声明方面：HTML5 文件的声明语句变成了 `<!DOCTYPE html>`。
2. 标准方面：形成了自己的标准，不再基于 SGML 标准进行文档解析。
3. 标签方面：
    1. 新增语义化标签如 `<header>`, `<article>`。
    2. 删除一些样式标签如 `<big>`, `<center>` 等，更彻底实现结构和样式的分离。
4. 属性方面：
    1. 增加了一些表单属性，主要是 `input` 的属性，`type` 属性新增了 `email`, `url`, `date` 等值。
    2. 新增了其他标签属性，如 `meta` 标签的 `charset` 属性，`script` 标签的 `async` 属性。
5. 存储方面：
    1. 新增了 webStorage, 包括 localStorage 和 sessionStorage。
    2. 新增了 IndexedDB，允许在客户端创建数据库存储数据。
    3. 新增了应用程序缓存器(application cache)，可以对 Web 进行缓存，为 PWA 提供了底层的技术支持。

## meta 标签的属性有哪些？

meta 标签一般用来定义网页说明、关键字及其他元数据，这些元数据一般用于浏览器(指示如何布局或重载页面)、搜索引擎和其他网络服务。

1. `charset`：用于指定字符集，合法值只能是 `utf-8`。
2. `name` + `content`：
3. `http-equiv` + `content`: 相当于设置 HTTP 头部，支持的值有 `content-security-policy`, `content-type`, `default-style`(默认 CSS 文件名), `x-ua-compatible`(`content` 必须是 `IE=edge`), `refresh`(指定页面自动刷新的时间、或者指定页面自动重定向的时间和地址)。

## `href` 和 `src` 的区别？

-   `href`, Hypertext Reference，指定网络资源的位置，定义的是当前元素(anchor)或文档(`<a>`, `<link>`)与指定资源的关系，资源下载不会阻塞浏览器解析 HTML 文档(这也是为什么建议使用 `<link>` 而不是 `@import` 引入 CSS)。
-   `src`, source，目的是要把文件下载到 HTML 页面中去，替换当前标签内容，比如 `<img>`, `<script>`, `<iframe>`，资源下载会阻塞浏览器解析 HTML 文档(这也是建议把 `<script>` 标签放到文档底部而非头部的原因)。

## `script` 标签中的 defer 和 async 有什么区别？

**没有 defer 和 async 的情况下：**

脚本的下载和执行顺序是根据 `script` 在文档中的书写顺序来的，而且这个下载和执行的过程还会阻塞(TODO: 了解一下 preloader, prescanner 什么的，现在应该是提前加载了吧?) HTML 文档的解析。

**defer 和 async 的区别**

两个属性都是告诉浏览器：立即下载 JS 资源，稍后执行，但与此同时，不要暂停 HTML 文档的解析。

不同的是稍后执行的时机：

-   `defer` 是等文档解释完毕之后(DOMContentLoaded)执行，多个 JS 文件按照 `<script>` 的书写顺序来执行。
-   `async` 是等 JS 文件下载完毕之后立即执行，不管 HTML 文档是否解析结束，所以会阻塞文档解析。另外，多个 JS 文件执行顺序不确定，哪个先下载完就执行哪一个。

当两个属性同时存在时，async 优先级更高。

<hr/>

> 以下部分整理自[qiu-deqing/FE-interview](https://github.com/qiu-deqing/FE-interview)。

<hr/>
