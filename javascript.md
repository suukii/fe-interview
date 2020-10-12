> 整理自 [front-end-interview-handbook](https://github.com/yangshun/front-end-interview-handbook)。注：并非该仓库的翻译版本。

#### 宿主对象(host objects)和原生对象(native objects)有什么不同？

原生对象是 JS 的一部分，在 ES 规范中有定义的，比如 `String`, `Math`, `RegExp`, `Object`, `Function` 等。

宿主对象是由运行环境提供的(浏览器/Node)，比如 `window`, `XMLHttpRequest` 等。

https://stackoverflow.com/questions/7614317/what-is-the-difference-between-native-objects-and-host-objects

#### `.call` 和 `.apply` 的区别？

`.call` 和 `.apply` 都是用来调用函数并修改 `this` 指向的，不同的只是它们接收其他参数的方式，`.call` 接收若干个参数，用逗号分隔开，`.apply` 接收一个数组。

#### 解释一下 `.bind`

`.bind` 会返回一个新函数并设定好 `this` 的指向。

一般是要把 class 的方法作为另一个函数的参数时（比如作为事件处理函数）会需要用到，避免函数在参数传递的过程中 `this` 发生意外的改变。

https://developer.mozilla.org/en/docs/Web/JavaScript/Reference/Global_objects/Function/bind

#### 解释一下 `document.write()`

当页面加载完毕之后再调用 `document.write()` 的话，它会调用 `document.open()` 方法，把整个页面都移除(`<head>` 和 `<body>` 都没了)，然后替换成参数字符串。

`document.open()` 会打开一个文档流(document stream)，`document.write()` 就往里面写入字符串。

在以前 `document.write()` 的确是有用途的，比如可以实现[“当浏览器支持 JS 时才应用某些样式”](https://www.quirksmode.org/blog/archives/2005/06/three_javascrip_1.html)的功能，或者实现[“并行加载 JS 文件并保证执行顺序”](https://github.com/paulirish/html5-boilerplate/wiki/Script-Loading-Techniques#documentwrite-script-tag)的功能。

但是在现在，这些功能也不一定非要依靠 `document.write()` 来实现了。

https://www.quirksmode.org/blog/archives/2005/06/three_javascrip_1.html

https://github.com/h5bp/html5-boilerplate/wiki/Script-Loading-Techniques#documentwrite-script-tag

#### 特性检测(feature detection)、特性推理(feature inference)和 UA 字符串的区别是什么？

-   特性检测是指检测浏览器是否支持某些功能，[Modernizr](https://modernizr.com/) 是一个用于特性检测的库。e.g. `'geolocation' in navigator`
-   特性推理和特性检测差不多，不过它是检查浏览器是否支持另一个方法，如果浏览器支持方法 A，特性推理就认为浏览器也支持方法 B。特性推理并非推荐的做法，还是用特性检测比较靠谱。
-   UA 字符串可以通过 `navigator.userAgent` 来获取。这是浏览器提供的一个属性，包含了程序类型、操作系统、软件厂商或者软件版本等信息。不过，这个信息并非完全可信，比如 Chrome 提供的 UA 字符串会说它自己时 Chrome 和 Safari。这个方法也应该避免。

https://developer.mozilla.org/en-US/docs/Learn/Tools_and_testing/Cross_browser_testing/Feature_detection

https://stackoverflow.com/questions/20104930/whats-the-difference-between-feature-detection-feature-inference-and-using-th

https://developer.mozilla.org/en-US/docs/Web/HTTP/Browser_detection_using_the_user_agent
