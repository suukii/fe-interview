# JS 部分

- [JS 部分](#js-部分)
  - [front-end-interview-handbook](#front-end-interview-handbook)
    - [解释一下事件代理](#解释一下事件代理)
    - [解释一下 `this` 的运行机制](#解释一下-this-的运行机制)
    - [解释一下原型链继承的运行机制](#解释一下原型链继承的运行机制)
    - [AMD vs CommonJS](#amd-vs-commonjs)
    - [如何区分 null, undefined, undeclared？](#如何区分-null-undefined-undeclared)
    - [什么是闭包？](#什么是闭包)
    - [宿主对象(host objects)和原生对象(native objects)有什么不同？](#宿主对象host-objects和原生对象native-objects有什么不同)
    - [`.call` 和 `.apply` 的区别？](#call-和-apply-的区别)
    - [解释一下 `.bind`](#解释一下-bind)
    - [解释一下 `document.write()`](#解释一下-documentwrite)
    - [特性检测(feature detection)、特性推理(feature inference)和 UA 字符串的区别是什么？](#特性检测feature-detection特性推理feature-inference和-ua-字符串的区别是什么)
    - [解释一下 Ajax](#解释一下-ajax)
    - [阐述一下 Ajax 的优点和缺点](#阐述一下-ajax-的优点和缺点)
    - [说一下 JSONP 的原理，为什么它不是 Ajax？](#说一下-jsonp-的原理为什么它不是-ajax)
    - [解释一下“变量/函数提升”(hoisting)](#解释一下变量函数提升hoisting)
    - [描述一下事件冒泡](#描述一下事件冒泡)
    - ["attribute" 和 "property" 的区别是什么？](#attribute-和-property-的区别是什么)
    - [为什么不推荐扩展 JS 的内置对象？](#为什么不推荐扩展-js-的内置对象)
    - [document 的 `load` 和 `DOMContentLoaded` 事件的区别是什么？](#document-的-load-和-domcontentloaded-事件的区别是什么)
    - [`==` 和 `===` 的区别是什么？](#-和--的区别是什么)
    - [解释一下同源策略(从 JS 相关的角度)](#解释一下同源策略从-js-相关的角度)
    - [`use strict;` 有什么用？它的优缺点是什么？](#use-strict-有什么用它的优缺点是什么)
    - [解释一下什么是 SPA 以及如何提高 SPA 的 SEO](#解释一下什么是-spa-以及如何提高-spa-的-seo)
    - [解释一下 Promise](#解释一下-promise)
    - [Promise 相对于回调的优缺点是什么？](#promise-相对于回调的优缺点是什么)
    - [用另外一门语言写代码再编译成 JS 这样做的优缺点是什么？](#用另外一门语言写代码再编译成-js-这样做的优缺点是什么)
    - [使用什么工具和技术来 debug](#使用什么工具和技术来-debug)
    - [如何遍历对象和数组？](#如何遍历对象和数组)
    - [解释一下 mutable 和 immutable 对象](#解释一下-mutable-和-immutable-对象)
    - [怎么实现 immutable？](#怎么实现-immutable)
    - [解释一下同步和异步函数的区别？](#解释一下同步和异步函数的区别)
    - [什么是事件循环？调用栈和任务队列的区别又是什么？](#什么是事件循环调用栈和任务队列的区别又是什么)
    - [`function foo() {}` 和 `var foo = function () {}` 有什么区别？](#function-foo--和-var-foo--function---有什么区别)
    - [`let`, `var`, `const` 的区别？](#let-var-const-的区别)
    - [ES6 class 和 ES5 的构造函数有什么区别？](#es6-class-和-es5-的构造函数有什么区别)
    - [说一下箭头函数的优点。](#说一下箭头函数的优点)
    - [在构造函数中使用箭头函数有什么好处？](#在构造函数中使用箭头函数有什么好处)
    - [高阶函数是什么？](#高阶函数是什么)
    - [什么是柯里化？](#什么是柯里化)
    - [文件间如何共享代码？](#文件间如何共享代码)
    - [为什么会需要 class 静态成员？](#为什么会需要-class-静态成员)
  - [JS 基础](#js-基础)
    - [谈谈你对闭包的理解](#谈谈你对闭包的理解)
    - [什么是原型和原型链？](#什么是原型和原型链)
    - [JS 中如何实现继承？](#js-中如何实现继承)
    - [谈谈你对 BigInt 的理解](#谈谈你对-bigint-的理解)
  - [JS 深入数组](#js-深入数组)
    - [数组扁平化的几种方法](#数组扁平化的几种方法)
    - [V8 的 `sort()` 用的是什么排序算法？](#v8-的-sort-用的是什么排序算法)
  - [JS API 原理](#js-api-原理)
    - [如何模拟实现一个 new 的效果？](#如何模拟实现一个-new-的效果)
    - [如何模拟实现一个 bind 的效果？](#如何模拟实现一个-bind-的效果)
    - [如何实现一个 call/apply 函数？](#如何实现一个-callapply-函数)
    - [JS 中浅拷贝的手段有哪些？](#js-中浅拷贝的手段有哪些)
    - [如何写一个完整的深拷贝？](#如何写一个完整的深拷贝)
  - [V8 引擎原理](#v8-引擎原理)
    - [JS 数据是怎么存储的？](#js-数据是怎么存储的)
    - [V8 引擎如何进行垃圾内存的回收？](#v8-引擎如何进行垃圾内存的回收)
    - [描述一下 V8 执行一段代码的过程](#描述一下-v8-执行一段代码的过程)
    - [如何理解 EventLoop？](#如何理解-eventloop)

<hr />

> 以下题目整理自 [front-end-interview-handbook](https://github.com/yangshun/front-end-interview-handbook)。

<hr />

## front-end-interview-handbook

### 解释一下事件代理

事件代理是指在一系列元素的祖先元素上绑定事件处理函数，而不是分别绑定在所有元素上。事件代理的原理是事件冒泡。

**优点**

1. 降低内存使用，因为只需要无论有多少个元素，都只需要在祖先元素上绑定一个处理函数，一定程度上降低了内存的使用。
2. 在新增/移除子元素的时候不需要给子元素绑定/解绑处理函数。

### 解释一下 `this` 的运行机制

`this` 的值取决于函数被调用的方式，它是在运行时确定的，属于动态作用域。

关于 `this` 的值，有以下几种可能（函数调用方式），当多种调用方式同时存在时，优先级从高到低：

1. new
2. apply、call、bind
3. obj.method()
4. 单独调用 func()（此时 this 是 window 或者 undefined）

### 解释一下原型链继承的运行机制

在 JS 中，每个对象都有一个 `.__proto__` 属性，指向另一个对象，也就是它的原型。如果我们访问一个对象属性，但这个属性不存在的时候，JS 就会沿着 `.__proto__` 去它的原型对象上找，原型对象也有自己的 `.__proto__` 属性，所以这个查找过程会持续到找到相应属性或者到达原型链尽头。这种行为一般称为代理而不是继承。

### AMD vs CommonJS

两者都是 ES6 之前的模块系统。

1. CommonJS 是同步的，AMD(Asynchronous Module Definition) 是异步的。
2. CommonJS 是设计用于服务端的，而 AMD 则倾向于浏览器，所以它支持异步加载模块。

在 ES6 提供原生模块系统支持后，两者都变得没有必要了。虽然 ES6 模块的支持还不全面，但这个问题可以用编译器来解决。

### 如何区分 null, undefined, undeclared？

1. null: 已声明已赋值
2. undefined: 已声明未赋值
3. undeclared: 未声明

**如何检测**

null 和 undefined 可以使用全等直接和值比较，undeclared 可以使用 try/catch 在严格模式中捕获 Reference Error。

### 什么是闭包？

闭包是指一个函数加上它被声明时所处的词法作用域。闭包函数可以访问它外层函数的作用域，即使是在外层函数已经执行完毕之后。

**有什么用**

1. 一般用于封装（模拟）私有属性和方法，常见于模块模式
2. 用于实现 partial 或 curry

### 宿主对象(host objects)和原生对象(native objects)有什么不同？

原生对象是 JS 的一部分，在 ES 规范中有定义的，比如 `String`, `Math`, `RegExp`, `Object`, `Function` 等。

宿主对象是由运行环境提供的(浏览器/Node)，比如 `window`, `XMLHttpRequest` 等。

https://stackoverflow.com/questions/7614317/what-is-the-difference-between-native-objects-and-host-objects

### `.call` 和 `.apply` 的区别？

`.call` 和 `.apply` 都是用来调用函数并修改 `this` 指向的，不同的只是它们接收其他参数的方式，`.call` 接收若干个参数，用逗号分隔开，`.apply` 接收一个数组。

### 解释一下 `.bind`

`.bind` 会返回一个新函数并设定好 `this` 的指向。

一般是要把 class 的方法作为另一个函数的参数时（比如作为事件处理函数）会需要用到，避免函数在参数传递的过程中 `this` 发生意外的改变。

https://developer.mozilla.org/en/docs/Web/JavaScript/Reference/Global_objects/Function/bind

### 解释一下 `document.write()`

当页面加载完毕之后再调用 `document.write()` 的话，它会调用 `document.open()` 方法，把整个页面都移除(`<head>` 和 `<body>` 都没了)，然后替换成参数字符串。

`document.open()` 会打开一个文档流(document stream)，`document.write()` 就往里面写入字符串。

在以前 `document.write()` 的确是有用途的，比如可以实现[“当浏览器支持 JS 时才应用某些样式”](https://www.quirksmode.org/blog/archives/2005/06/three_javascrip_1.html)的功能，或者实现[“并行加载 JS 文件并保证执行顺序”](https://github.com/paulirish/html5-boilerplate/wiki/Script-Loading-Techniques#documentwrite-script-tag)的功能。

但是在现在，这些功能也不一定非要依靠 `document.write()` 来实现了。

https://www.quirksmode.org/blog/archives/2005/06/three_javascrip_1.html

https://github.com/h5bp/html5-boilerplate/wiki/Script-Loading-Techniques#documentwrite-script-tag

### 特性检测(feature detection)、特性推理(feature inference)和 UA 字符串的区别是什么？

-   特性检测是指检测浏览器是否支持某些功能，[Modernizr](https://modernizr.com/) 是一个用于特性检测的库。e.g. `'geolocation' in navigator`
-   特性推理和特性检测差不多，不过它是检查浏览器是否支持另一个方法，如果浏览器支持方法 A，特性推理就认为浏览器也支持方法 B。特性推理并非推荐的做法，还是用特性检测比较靠谱。
-   UA 字符串可以通过 `navigator.userAgent` 来获取。这是浏览器提供的一个属性，包含了程序类型、操作系统、软件厂商或者软件版本等信息。不过，这个信息并非完全可信，比如 Chrome 提供的 UA 字符串会说它自己是 Chrome 和 Safari。这个方法也应该避免。

https://developer.mozilla.org/en-US/docs/Learn/Tools_and_testing/Cross_browser_testing/Feature_detection

https://stackoverflow.com/questions/20104930/whats-the-difference-between-feature-detection-feature-inference-and-using-th

https://developer.mozilla.org/en-US/docs/Web/HTTP/Browser_detection_using_the_user_agent

### 解释一下 Ajax

Ajax(asynchronous JavaScript and XML) 是实现异步程序的一系列技术，利用 Ajax，程序可以异步地向服务器发送请求、获取数据、更新页面，而不用刷新整个页面。现在一般都用 JSON 代替 XML 来进行数据传输了。常用到的 API 是 `XMLHttpRequest` 或者 `fetch`。

https://en.wikipedia.org/wiki/Ajax_(programming)

https://developer.mozilla.org/en-US/docs/AJAX

### 阐述一下 Ajax 的优点和缺点

**优点**

-   提高用户体验：可以局部更新网页内容，不用整个页面刷新。
-   减少 js 和 css 文件的下载次数：如果页面整个刷新，文档中的资源都要重新下载；而使用 ajax 的话，就只需要下载一次。
-   可以保持页面状态：因为页面没有刷新，所以状态也不会被重置。
-   其他 SPA 的优点。

**缺点**

-   动态网页对于添加书签并不友好。
-   必须运行在支持 js 的浏览器上。
-   对爬虫不友好，一些爬虫不会执行 js 脚本，也就爬不到内容。
-   首屏时间长，SPA 页面要等到 js 加载执行完才能看到页面内容。
-   SPA 的其他缺点。

### 说一下 JSONP 的原理，为什么它不是 Ajax？

JSONP(JSON with Padding) 是用来绕过浏览器同源策略的一个方法，因为 Ajax 请求会受到同源策略的限制。

它利用 `<script>` 来向跨域域名发起请求，一般同时会指定一个 `callback` 作为参数，比如 `https://example.com?callback=printData`，`printData` 需要在全局中定义。服务器收到请求后，会返回一个 js 文件，里面的内容类似：

```js
printData({ name: 'suukii' });
```

浏览器接收到这个文件后执行里面的代码，这样就实现了从跨域域名请求数据的功能。

但由于服务器返回的是一个 js 文件，`JSONP` 其实存在着不小的安全漏洞，所以除非请求域名是可信任的，不然不要轻易使用 `JSONP` 技术。另外，在 `CORS` 出现后，我们也基本不需要 `JSONP` 了。

https://stackoverflow.com/a/2067584/1751946

### 解释一下“变量/函数提升”(hoisting)

变量提升是用来解释“变量在声明前就可以被访问”这个现象的，简单地说就是把 `var` 声明语句“提升”到全局/模块/函数代码的顶端，但被提升的仅仅是声明语句，赋值语句并没有被提升。函数声明则是整个函数体都会被提升。

`let` 和 `const` 声明的变量也都会被提升，但存在一个“暂时性死区”，在 `let`，`const` 声明语句执行之前，这些变量都不能被访问到。

“提升”其实并不是真实存在的行为，只是为了容易理解而提出来的一个概念。实际上在代码执行之前，JS 引擎还会有一个编译的阶段，在这个过程中它会解析声明语句，确定哪些作用域里面存在哪些变量。

https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Grammar_and_Types#Variable_hoisting

https://stackoverflow.com/questions/31219420/are-variables-declared-with-let-or-const-not-hoisted-in-es6/31222689#31222689

### 描述一下事件冒泡

当一个 DOM 元素上触发了某个事件时，它会先检查有没有事件处理函数，然后再把事件传递给它的父元素，如此重复，一直到 `document` 元素。

事件冒泡是事件代理的原理。

### "attribute" 和 "property" 的区别是什么？

attribute 是定义在 HTML 文档中的，而 property 是定义在 DOM 元素上的。

https://stackoverflow.com/questions/6003819/properties-and-attributes-in-html

### 为什么不推荐扩展 JS 的内置对象？

因为如果直接在 `prototype` 上增加属性或者方法的话，很有可能会与第三方库或者将来的 JS 原生方法产生命名冲突。

除了提供 polyfill，最好不要直接拓展内置对象的 `prototype`。

http://lucybain.com/blog/2014/js-extending-built-in-objects/

### document 的 `load` 和 `DOMContentLoaded` 事件的区别是什么？

-   `DOMContentLoaded` 是在 HTML 文档下载解析完之后触发的，不用等待其他资源如样式、图片、subframe 完成加载。
-   `load` 事件则要等到 DOM 和所有其他资源都下载完成之后才会触发。

https://developer.mozilla.org/en-US/docs/Web/Events/DOMContentLoaded

https://developer.mozilla.org/en-US/docs/Web/Events/load

### `==` 和 `===` 的区别是什么？

-   `==` 在比较之前会进行类型转换。
-   `===` 在比较之前不会进行类型转换，如果两个操作数类型不一致就直接返回 false。

什么时候可以使用 `==`？一个小建议，在需要判断一个值是否等于 `null` 或者 `undefined` 的时候，为了方便，可以利用下 `==` 的类型转换。

https://stackoverflow.com/questions/359494/which-equals-operator-vs-should-be-used-in-javascript-comparisons

### 解释一下同源策略(从 JS 相关的角度)

同源策略限制了 JS 向跨域域名发送请求。同源指的是协议、hostname、端口名一致。

这样做是为了避免网页执行了恶意脚本，然后恶意脚本通过操作 DOM 来获取敏感信息。

https://en.wikipedia.org/wiki/Same-origin_policy

### `use strict;` 有什么用？它的优缺点是什么？

用来开启全局或者函数的严格模式。

**优点**

-   给未声明的变量赋值时会抛出错误而不是默默创建一个全局变量。
-   尝试删除不允许删除的对象属性时会报错而不是静默失败。
-   要求函数参数命名唯一。
-   单独调用函数时 `this` 的值是 `undefined` 而不是 `window`。
-   纠正了一些其他 JS 的缺陷。

**缺点**

-   不能访问 `function.caller` 和 `function.arguments` 了。
-   合并严格模式和非严格模式的代码可能会导致意想不到的问题。
-   禁用了一些非严格模式中的特性。

不过总的来说，还是推荐使用严格模式。

http://2ality.com/2011/10/strict-mode-hatred.html

http://lucybain.com/blog/2014/js-use-strict/

### 解释一下什么是 SPA 以及如何提高 SPA 的 SEO

传统的网站是，浏览器从服务器接收 HTML 文档并渲染，如果用户跳转到了另一个链接，服务器会返回一份新的 HTML 文档，浏览器会重新渲染，这样每次都要更新整个页面，这个就叫做服务端渲染。

但 SPA 用的是客户端渲染，浏览器会先下载一个文档，下载文档中包含的脚本(框架、库、源码)和样式，然后再开始执行脚本、渲染页面。当需要导航到另一个链接时，页面的 URL 会通过 HTML5 的 History API 来更新，然后程序通过 Ajax 从服务器下载新数据，更新到页面上。这种模式更接近原生程序。

**优点**

-   网站能更快地响应用户操作，不用一个操作一次全页面更新。
-   减少了 HTTP 请求，包含在文档中的 JS 和 CSS 文件等资源只需要在第一次加载文档时下载，因为此后页面不再更新，这些资源也不需要重复下载了。
-   更好实现了服务端和客服端的关注点分离。不同客户端上的网页应用可以对应同一套服务端代码，客户端和服务端通过约定好的 API 通信，各自技术栈不受对方约束。

**缺点**

-   首次加载需要加载的资源比较多，比如框架代码、程序代码、公用资源。
-   需要在服务端进行设置把客户端的所有路由都重定向到同一个入口，然后让客户端接手路由管理，避免客户端页面刷新。
-   SEO 不友好。SPA 要等 JS 加载完毕之后才会开始获取数据、渲染页面，但很多爬虫都不会执行 JS，所以就爬不到网页内容。如果需要考虑 SEO，可以考虑使用服务端渲染，或者使用 [Prerender](https://prerender.io/) 之类的服务。

https://github.com/grab/front-end-guide#single-page-apps-spas

http://stackoverflow.com/questions/21862054/single-page-app-advantages-and-disadvantages

http://blog.isquaredsoftware.com/presentations/2016-10-revolution-of-web-dev/

https://medium.freecodecamp.com/heres-why-client-side-rendering-won-46a349fadb52

### 解释一下 Promise

Promise 是一个对象，保存着一个结果，这个结果在将来某一时刻才会被确定。

它有 3 种状态：

1. 在结果确定之前，处于 pending 状态
2. 成功的结果，resolved，返回数据
3. 失败的结果，rejected，可能是报错了，返回错误信息

常见的 polyfill 有 `$.deferred`, Q 和 Blvebird，不过不是所有 polyfill 都完全遵循规范来实现的。

https://medium.com/javascript-scene/master-the-javascript-interview-what-is-a-promise-27fc71e77261

### Promise 相对于回调的优缺点是什么？

**优点**

1. 避免回调地狱。
2. 编写顺序异步程序更简单。
3. 有了 `Promise.all()`，写并行异步也更简单了。
4. 关于回调的几个问题：过早调用、过晚调用、调用次数过多/过少、参数缺失、吞并异常等问题都不会发生。

**缺点**

1. 兼容性，老浏览器可能不支持。

https://github.com/getify/You-Dont-Know-JS/blob/master/async%20%26%20performance/ch3.md

### 用另外一门语言写代码再编译成 JS 这样做的优缺点是什么？

**优点**

1. 新语言解决了一些 JS 的历史遗留问题，还会限制使用 anti-patterns。
2. 还可能提供一些语法糖，减少代码量。
3. 对于大项目，静态检查(TS)是很有必要的。

**缺点**

-   多了一个打包/编译的过程，因为浏览器只能执行 JS。
-   如果 sourcemap 没有对应到编译前的代码的话，debug 会变得很麻烦。
-   要考虑团队的学习成本。
-   社区可能会比较小，资源/教程/工具不多。
-   IDE 支持可能不足。
-   这些语言总会落后于最新的 JS 规范。

https://softwareengineering.stackexchange.com/questions/72569/what-are-the-pros-and-cons-of-coffeescript

### 使用什么工具和技术来 debug

-   React, Redux: [React Devtools](https://github.com/facebook/react-devtools), [Redux Devtools](https://github.com/gaearon/redux-devtools)
-   Vue: [Vue Devtools](https://github.com/vuejs/vue-devtools)
-   JavaScript: [Chrome Devtools](https://hackernoon.com/twelve-fancy-chrome-devtools-tips-dc1e39d10d9d), `debugger`, `console.log`

https://hackernoon.com/twelve-fancy-chrome-devtools-tips-dc1e39d10d9d

https://raygun.com/blog/javascript-debugging/

### 如何遍历对象和数组？

**遍历对象的键**

1. `for...in`
2. `Object.keys()`
3. `Object.getOwnPropertyNames()`

**遍历数组**

1. for loop
2. `for...of`，如果获取下标和值，可以用 `arr.entries()` 方法
3. `.forEach()` 等

http://2ality.com/2015/08/getting-started-es6.html#from-for-to-foreach-to-for-of

https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/entries

### 解释一下 mutable 和 immutable 对象

mutable 就是普通的 JS 对象。

immutable 指的是对象在创建之后，状态不能再修改。immutable 是函数式编程中一个很重要的原则。

**如何创建 immutable 对象？**

-   禁止改写属性：设置 `writable: false` 和 `configurable: false`。
-   禁止添加属性：`Object.preventExtensions(...)`。
-   `Object.seal()`：相当于 `Object.preventExtensions(...)` + `configurable: false`，但还可以修改属性值。
-   `Object.freeze()`：相当于 `Object.seal()` + `writable: false`

**immutability 的优缺点**

优点：

-   容易追踪修改。而且对象的比较可以直接比较引用，在 React 和 Redux 中很有用。
-   可预测，immutable 对象创建后状态就不会被修改了，不用担心某一个操作在将来会有什么影响。
-   不用因为担心不小心修改到原对象而每次操作都自己复制一份对象。
-   在多线程环境中也能放心使用，不用担心修改对象会相应其他线程。
-   使用类似 ImmutableJS 的库可以提升性能，减少内存消耗。

缺点：

-   原生实现的性能太差，所以需要借助库来实现。
-   如果对象很多的话，频繁的内存分配还是会影响性能。
-   存在循环引用的结构很难实现 immutable。（如果你有两个对象，它们初始化之后都不能再改变，那你要如何实现它们相互引用？）

https://github.com/yangshun/front-end-interview-handbook/blob/master/contents/en/javascript-questions.md

### 怎么实现 immutable？

1. 用库：immutablejs, mori, immer
2. 自己实现：用 `const` + 上面提到的冻结对象的方法。需要"修改"对象时，使用展开符、`Object.assign()`、`Array.concat()` 等方法来创建新的对象。

https://stackoverflow.com/questions/1863515/pros-cons-of-immutability-vs-mutability

https://www.sitepoint.com/immutability-javascript/

https://wecodetheweb.com/2016/02/12/immutable-javascript-using-es6-and-beyond/

### 解释一下同步和异步函数的区别？

-   同步函数会阻塞主线程，异步函数不会。
-   同步函数中，按顺序执行，上一个语句执行完才会执行下一个语句，如果执行时间过长，程序就会变成无法响应了。
-   异步函数则一般接收一个回调函数，等异步操作结束之后再调用回调。

### 什么是事件循环？调用栈和任务队列的区别又是什么？

事件循环是一个单线程的无限循环，它管着调用栈和任务队列，如果调用栈里面是空的，而任务队列中又有任务的话，事件循环就会从任务队列中出列一个任务，推入调用栈去执行。

https://2014.jsconf.eu/speakers/philip-roberts-what-the-heck-is-the-event-loop-anyway.html

https://2014.jsconf.eu/speakers/philip-roberts-what-the-heck-is-the-event-loop-anyway.html

http://theproactiveprogrammer.com/javascript/the-javascript-event-loop-a-stack-and-a-queue/

### `function foo() {}` 和 `var foo = function () {}` 有什么区别？

前一个是函数声明，后一个是函数表达式。关键区别在于函数声明中的函数体会被全部提升，所以可以在函数声明之前调用一个函数。而函数表达式中只有 `var` 声明语句被提升了，如果尝试在赋值钱调用函数，则会得到 TypeError。

https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/function

### `let`, `var`, `const` 的区别？

|          | `var`     | `let`/`const`                         |
| -------- | --------- | ------------------------------------- |
| 作用域   | 函数/全局 | 块级，花括号(函数、if-else、for-loop) |
| 提升     | 存在提升  | 存在提升，但存在暂时性死区            |
| 重复声明 | 覆盖      | 报错                                  |

https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/let

https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/var

https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/const

### ES6 class 和 ES5 的构造函数有什么区别？

最主要的是在写继承的时候提供了更简洁的语法糖，但是继承原理还是一样的。

https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Objects/Inheritance

https://eli.thegreenplace.net/2013/10/22/classical-inheritance-in-javascript-es5

### 说一下箭头函数的优点。

-   语法简洁。
-   提供词法作用域的 `this`，箭头函数的 `this` 在书写时就确定为它外层第一个普通函数的 `this`。

### 在构造函数中使用箭头函数有什么好处？

将实例方法作为事件处理函数回调时，不用担心 `this` 丢失。

在 React 的 class 组件中常用，可以省掉手动 bind 的步骤。

https://medium.com/@machnicki/handle-events-in-react-with-arrow-functions-ede88184bbb

https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/Arrow_functions

https://medium.com/@machnicki/handle-events-in-react-with-arrow-functions-ede88184bbb

### 高阶函数是什么？

接收函数作为参数，或者返回一个函数的函数。用来抽象一些操作，比如 `map`, `forEach`, `bind` 等

https://medium.com/javascript-scene/higher-order-functions-composing-software-5365cf2cbe99

https://hackernoon.com/effective-functional-javascript-first-class-and-higher-order-functions-713fde8df50a

https://eloquentjavascript.net/05_higher_order.html

### 什么是柯里化？

柯里化指的是讲一个接收**多个参数**的函数，变成多个接收**一个参数**的函数，每次调用都只传入一个参数。

这个技术是函数式编程中常见的，用于提高代码可读性和可组合性(compose)。

```js
function curry(fn) {
    if (fn.length === 0) {
        return fn;
    }

    function _curried(depth, args) {
        return function (newArgument) {
            if (depth - 1 === 0) {
                return fn(...args, newArgument);
            }
            return _curried(depth - 1, [...args, newArgument]);
        };
    }

    return _curried(fn.length, []);
}

function add(a, b) {
    return a + b;
}

var curriedAdd = curry(add);
var addFive = curriedAdd(5);

var result = [0, 1, 2, 3, 4, 5].map(addFive); // [5, 6, 7, 8, 9, 10]
```

https://hackernoon.com/currying-in-js-d9ddc64f162e

### 文件间如何共享代码？

取决于环境。

-   浏览器：全局(window)、AMD(requirejs)
-   Node.js：CommonJS

不过 ES6 的模块系统最终应该会取代 AMD 和 CommonJS，统一客户端和服务器的模块系统。

http://requirejs.org/docs/whyamd.html

https://nodejs.org/docs/latest/api/modules.html

http://2ality.com/2014/09/es6-modules-final.html

### 为什么会需要 class 静态成员？

-   保存配置
-   静态方法一般是纯函数

https://stackoverflow.com/questions/21155438/when-to-use-static-variables-methods-and-when-to-use-instance-variables-methods

<hr />

> 以下题目整理自[神三元的博客](http://47.98.159.95/my_blog/)。

<hr />

## JS 基础

### 谈谈你对闭包的理解

**概念**

闭包是指那些能够访问其他函数作用域中变量的函数，也有定义是说这样的函数加上它能访问的作用域就构成了闭包。

**本质/产生原因**

之所以会产生闭包，首先是因为 JS 中存在作用域链这样一个机制，每个函数在创建时就会在其环境变量中保存对其父级作用域的引用，即使是创建这个函数的上下文(父级函数)已经执行完毕并销毁了，这个作用域引用还是有效的。

作用域链：当要访问一个变量时，JS 解释器首先会在当前作用域进行查找，如果找不到就会顺着作用域链一级一级往上查找，直到找到想要的变量或者到达作用域链的尽头。

**表现形式**

1. 函数作为另一个函数的返回值
2. 函数作为另一个函数的参数进行传递
3. 定时器、Ajax、事件监听等异步操作中使用的回调函数
4. IIFE

其实从闭包的本质可以看出，只要函数保存了对其父级作用域的引用，就会产生闭包，不拘于以上所提到的表现形式。

### 什么是原型和原型链？

**原型**

在 JS 中，每个函数都有一个 `prototype` 属性，指向一个对象，当我们把这个函数当作构造函数来调用时，生成的实例对象都会跟函数的 `prototype` 对象关联起来，而 `prototype` 对象就是实例对象的原型，实例对象可以通过委托(也有说法是继承)来访问它的原型对象上的属性和方法。

**原型链**

在 JS 中，对象都有自己的原型对象，而原型对象本身也是一个对象，所以它也有自己的原型对象，就这样子串成了原型链。当访问一个对象的属性时，如果属性不存在，解释器会去该对象的原型上查找，如果还是找不到，则会去原型对象的原型上查找，重复这个步骤直到找到了需要访问的属性，或者到达了原型链的尽头。

### JS 中如何实现继承？

TODO

### 谈谈你对 BigInt 的理解

TODO

## JS 深入数组

### 数组扁平化的几种方法

**方法 1：递归 + reduce**

```js
const flatten = arr => {
    return arr.reduce((res, item) => {
        return Array.isArray(item)
            ? [...res, ...flatten(item)]
            : [...res, item];
    }, []);
};
```

**方法 2：序列化 + replace**

```js
const flatten = arr => {
    return JSON.stringify(arr).replace(/\[|\]/g, '').split(',');
};
```

**方法 3：调 API flat()**

```js
const flatten = arr => {
    return arr.flat(Infinity);
};
```

**方法 4：扩展运算符 + concat**

```js
const flatten = arr => {
    let res = [...arr];
    while (res.some(Array.isArray)) {
        res = [].concat(...res);
    }
    return res;
};
```

### V8 的 `sort()` 用的是什么排序算法？

[TODO](https://v8.dev/blog/array-sort)

## JS API 原理

### 如何模拟实现一个 new 的效果？

**new 做的几个事情：**

1. 创建一个空对象
2. 将构造函数中的 `this` 指向这个空对象
3. 运行构造函数代码
4. 如果函数返回值不是引用类型就返回第一步创建的对象

**我们要做的事：**

-   首先基于构造函数的原型新建一个空对象，实现实例可以访问原型对象属性的效果。
-   将新对象作为 `this` 调用构造函数。
-   判断构造函数的返回值，如果不是引用类型的值，就返回第一步创建的对象，否则直接返回构造函数返回值。

```js
const newFactory = (ctor, ...arg) => {
    if (typeof ctor != 'function') {
        throw TypeError('the first argument must be a function');
    }

    const thisObj = Object.create(ctor.prototype);
    const returnedValue = ctor.apply(thisObj, arg);

    return isObject(returnedValue) || isFunction(returnedValue)
        ? returnedValue
        : thisObj;

    // *******************************************
    function isObject(val) {
        return typeof returnedValue == 'object' && returnedValue;
    }

    function isFunction(val) {
        return typeof returnedValue == 'function';
    }
};
```

### 如何模拟实现一个 bind 的效果？

-   对于普通函数调用，绑定 `this` 就行。
-   对于构造函数调用，要将绑定后函数的原型对象指向原函数的原型。
-   由于 `new` 的优先级高于 `bind`，所以要保证用 `new` 调用绑定函数时要忽略之前传入的 `this` 而使用 new 出来的对象。

```js
Function.prototype.bind = function (thisArg, ...arg1) {
    if (typeof this != 'function')
        throw TypeError('cannot call bind on non-function');

    const func = this;

    const bound = function (...arg2) {
        const context = this instanceof func ? this : thisArg;
        return func.apply(context, [...arg1, ...arg2]);
    };

    bound.prototype = Object.create(func.prototype);
    return bound;
};
```

### 如何实现一个 call/apply 函数？

-   先把函数挂在传入的 `this` 对象上作为方法
-   调用该方法
-   从 `this` 对象上删掉该方法
-   使用了 Symbol 避免命名冲突

**call**

```js
Function.prototype.call = function (thisArg, ...arg) {
    if (typeof this != 'function')
        throw TypeError('cannot call call on non-function');

    const funcNameSymbol = Symbol('tempFunction');
    thisArg[funcNameSymbol] = this;

    const res = thisArg[funcNameSymbol](...arg);
    delete thisArg[funcNameSymbol];

    return res;
};
```

**apply**

```js
Function.prototype.call = function (thisArg, arg) {
    // 跟 call 一样的
};
```

### JS 中浅拷贝的手段有哪些？

**数组浅拷贝**

1. 展开运算符，`[...target]`
2. `target.slice(0)`
3. `[].concat(target)`
4. `for...in` + `hasOwnProperty` 自己实现

**对象浅拷贝**

1. 展开运算符，`{...target}`
2. `Object.assign({}, target)`
3. `for...in` + `hasOwnProperty` 自己实现

### 如何写一个完整的深拷贝？

**第一步：递归拷贝**

```js
const deepClone = target => {
    if (isArray(target) || isObject(target)) {
        const copy = isArray(target) ? [] : {};

        for (const prop in target) {
            if (target.hasOwnProperty(prop)) {
                const value = target[prop];
                copy[prop] =
                    isArray(value) || isObject(value)
                        ? deepClone(value)
                        : value;
            }
        }
        return copy;
    }
    return target;

    // *******************************************
    function isArray(target) {
        return Array.isArray(target);
    }

    function isObject(target) {
        return typeof target == 'object' && target;
    }
};
```

**第二步：解决循环引用，用 WeakMap 记录已经处理过的值**

```js
const deepClone = (target, map = new WeakMap()) => {
    if (map.has(target)) return target;

    if (isArray(target) || isObject(target)) {
        map.set(target, true);
        // ...
    }
    // ...
};
```

> 用 WeakMap 的弱引用避免内存泄漏。

**第三步：拷贝特殊对象**

TODO

## V8 引擎原理

### JS 数据是怎么存储的？

V8 的内存分为 `栈内存` 和 `堆内存`

-   存储在 `栈` 中的是不变的数据，包括 `函数调用栈`，`基础类型的值`，还有 `引用类型的引用地址`。
-   存储在 `堆` 中的是可变的数据，也就是引用类型的值，也是垃圾回收发生的地方。

**拓展：为什么不把所有数据都存在栈内存？**

因为系统栈除了存储变量，还有创建和切换执行上下文(栈帧)的功能。要实现快速切换上下文的功能，就需要每个栈帧的大小都是可预测的，这样才可以通过计算很快得出下个栈帧的内存地址，进行切换。如果在栈中放可变数据，可能需要将每个栈帧的大小设计得非常大，极大地增加了数据存储的空间复杂度，而且也提高了栈溢出的风险。

**拓展：为什么不把所有数据都存在堆内存？**

堆内存中数据杂乱，GC 算法复杂，会导致执行上下文切换开销极大。

### V8 引擎如何进行垃圾内存的回收？

**栈内存**

对于栈内存来说，当 ESP 指针下移进行上下文切换之后，栈顶的空间就会被自动回收了。

**堆内存**

对于堆内存，情况复杂一点。

V8 的堆内存分成 `新生代` 和 `老生代` 两个部分，刚新建出来的对象会先存在 `新生代` 内存中，如果对象存活时间比较久，就会被转移到 `老生代` 中。

**新生代**

而 `新生代` 又分成两个部分：`From` 和 `To`，`From` 表示正在使用的内存，`To` 表示暂时闲置的内存。

-   程序创建的对象会先被存在 `From` 内存中。
-   当进行垃圾回收的时候，V8 会检查 `From` 中的对象，将存活对象复制到 `To` 内存，将非存活对象回收。
-   然后两块内存的角色调换。

为什么新生代内存需要分成两部分？因为堆内存在使用上并不是连续的，所以会产生很多内存碎片，`From` 到 `To` 这一步就是为了清理内存碎片。

> 新生代垃圾回收算法叫做 Scavenge 算法。

**老生代**

`新生代` 中的对象如果经过多次回收依然存在，就会被转移到 `老生代` 内存中，这种现象叫做 `晋升`，晋升发生的情况有以下两种：

-   对象已经经历过一次 Scavenge 算法
-   `To` 内存的空间占用超过 25%

老生代中的内存回收采用的是 `标记-清除`，先遍历堆中所有对象，给它们做上标记，然后对于程序中 `使用的对象` 和 被 `强引用的对象` 取消标记，这个阶段称为标记阶段；接下来在清除阶段，对有标记的对象进行回收。

对于老生代中的内存碎片问题，V8 是直接在清除阶段把存活对象全部往一边靠，这个移动对象的过程也是最耗时间的。

由于垃圾回收是很耗时间的操作，而且会阻塞 JS 业务代码的执行。为了解决这个问题，V8 采用了 `增量标记` 的方案，也就是将上面说到的标记，清除，和处理内存碎片的阶段分成小段执行，而不是一口气执行到底。比如先用对一部分对象进行标记，然后暂停垃圾回收，执行业务代码，再回来继续标记对象。

### 描述一下 V8 执行一段代码的过程

TODO

### 如何理解 EventLoop？
