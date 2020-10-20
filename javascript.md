> 整理自 [front-end-interview-handbook](https://github.com/yangshun/front-end-interview-handbook)。注：非该仓库的翻译版本。都是一些比较简单的题目。

#### 解释一下事件代理

事件代理是指在一系列元素的祖先元素上绑定事件处理函数，而不是分别绑定在所有元素上。事件代理的原理是事件冒泡。

**优点**

1. 降低内存使用，因为只需要无论有多少个元素，都只需要在祖先元素上绑定一个处理函数，一定程度上降低了内存的使用。
2. 在新增/移除子元素的时候不需要给子元素绑定/解绑处理函数。

#### 解释一下 `this` 的运行机制

`this` 的值取决于函数被调用的方式，它是在运行时确定的，属于动态作用域。

关于 `this` 的值，有以下几种可能（函数调用方式），当多种调用方式同时存在时，优先级从高到低：

1. new
2. apply、call、bind
3. obj.method()
4. 单独调用 func()（此时 this 是 window 或者 undefined）

#### 解释一下原型链继承的运行机制

在 JS 中，每个对象都有一个 `.__proto__` 属性，指向另一个对象，也就是它的原型。如果我们访问一个对象属性，但这个属性不存在的时候，JS 就会沿着 `.__proto__` 去它的原型对象上找，原型对象也有自己的 `.__proto__` 属性，所以这个查找过程会持续到找到相应属性或者到达原型链尽头。这种行为一般称为代理而不是继承。

#### AMD vs CommonJS

两者都是 ES6 之前的模块系统。

1. CommonJS 是同步的，AMD(Asynchronous Module Definition) 是异步的。
2. CommonJS 是设计用于服务端的，而 AMD 则倾向于浏览器，所以它支持异步加载模块。

在 ES6 提供原生模块系统支持后，两者都变得没有必要了。虽然 ES6 模块的支持还不全面，但这个问题可以用编译器来解决。

#### 如何区分 null, undefined, undeclared？

1. null: 已声明已赋值
2. undefined: 已声明未赋值
3. undeclared: 未声明

**如何检测**

null 和 undefined 可以使用全等直接和值比较，undeclared 可以使用 try/catch 在严格模式中捕获 Reference Error。

#### 什么是闭包？

闭包是指一个函数加上它被声明时所处的词法作用域。闭包函数可以访问它外层函数的作用域，即使是在外层函数已经执行完毕之后。

**有什么用**

1. 一般用于封装（模拟）私有属性和方法，常见于模块模式
2. 用于实现 partial 或 curry

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
-   UA 字符串可以通过 `navigator.userAgent` 来获取。这是浏览器提供的一个属性，包含了程序类型、操作系统、软件厂商或者软件版本等信息。不过，这个信息并非完全可信，比如 Chrome 提供的 UA 字符串会说它自己是 Chrome 和 Safari。这个方法也应该避免。

https://developer.mozilla.org/en-US/docs/Learn/Tools_and_testing/Cross_browser_testing/Feature_detection

https://stackoverflow.com/questions/20104930/whats-the-difference-between-feature-detection-feature-inference-and-using-th

https://developer.mozilla.org/en-US/docs/Web/HTTP/Browser_detection_using_the_user_agent

#### 解释一下 Ajax

Ajax(asynchronous JavaScript and XML) 是实现异步程序的一系列技术，利用 Ajax，程序可以异步地向服务器发送请求、获取数据、更新页面，而不用刷新整个页面。现在一般都用 JSON 代替 XML 来进行数据传输了。常用到的 API 是 `XMLHttpRequest` 或者 `fetch`。

https://en.wikipedia.org/wiki/Ajax_(programming)

https://developer.mozilla.org/en-US/docs/AJAX

#### 阐述一下 Ajax 的优点和缺点

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

#### 说一下 JSONP 的原理，为什么它不是 Ajax？

JSONP(JSON with Padding) 是用来绕过浏览器同源策略的一个方法，因为 Ajax 请求会受到同源策略的限制。

它利用 `<script>` 来向跨域域名发起请求，一般同时会指定一个 `callback` 作为参数，比如 `https://example.com?callback=printData`，`printData` 需要在全局中定义。服务器收到请求后，会返回一个 js 文件，里面的内容类似：

```js
printData({ name: 'suukii' });
```

浏览器接收到这个文件后执行里面的代码，这样就实现了从跨域域名请求数据的功能。

但由于服务器返回的是一个 js 文件，`JSONP` 其实存在着不小的安全漏洞，所以除非请求域名是可信任的，不然不要轻易使用 `JSONP` 技术。另外，在 `CORS` 出现后，我们也基本不需要 `JSONP` 了。

https://stackoverflow.com/a/2067584/1751946

#### 解释一下“变量/函数提升”(hoisting)

变量提升是用来解释“变量在声明前就可以被访问”这个现象的，简单地说就是把 `var` 声明语句“提升”到全局/模块/函数代码的顶端，但被提升的仅仅是声明语句，赋值语句并没有被提升。函数声明则是整个函数体都会被提升。

`let` 和 `const` 声明的变量也都会被提升，但存在一个“暂时性死区”，在 `let`，`const` 声明语句执行之前，这些变量都不能被访问到。

“提升”其实并不是真实存在的行为，只是为了容易理解而提出来的一个概念。实际上在代码执行之前，JS 引擎还会有一个编译的阶段，在这个过程中它会解析声明语句，确定哪些作用域里面存在哪些变量。

https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Grammar_and_Types#Variable_hoisting

https://stackoverflow.com/questions/31219420/are-variables-declared-with-let-or-const-not-hoisted-in-es6/31222689#31222689

#### 描述一下事件冒泡

当一个 DOM 元素上触发了某个事件时，它会先检查有没有事件处理函数，然后再把事件传递给它的父元素，如此重复，一直到 `document` 元素。

事件冒泡是事件代理的原理。

#### "attribute" 和 "property" 的区别是什么？

attribute 是定义在 HTML 文档中的，而 property 是定义在 DOM 元素上的。

https://stackoverflow.com/questions/6003819/properties-and-attributes-in-html

#### 为什么不推荐扩展 JS 的内置对象？

因为如果直接在 `prototype` 上增加属性或者方法的话，很有可能会与第三方库或者将来的 JS 原生方法产生命名冲突。

除了提供 polyfill，最好不要直接拓展内置对象的 `prototype`。

http://lucybain.com/blog/2014/js-extending-built-in-objects/

#### document 的 `load` 和 `DOMContentLoaded` 事件的区别是什么？

-   `DOMContentLoaded` 是在 HTML 文档下载解析完之后触发的，不用等待其他资源如样式、图片、subframe 完成加载。
-   `load` 事件则要等到 DOM 和所有其他资源都下载完成之后才会触发。

https://developer.mozilla.org/en-US/docs/Web/Events/DOMContentLoaded

https://developer.mozilla.org/en-US/docs/Web/Events/load

#### `==` 和 `===` 的区别是什么？

-   `==` 在比较之前会进行类型转换。
-   `===` 在比较之前不会进行类型转换，如果两个操作数类型不一致就直接返回 false。

什么时候可以使用 `==`？一个小建议，在需要判断一个值是否等于 `null` 或者 `undefined` 的时候，为了方便，可以利用下 `==` 的类型转换。

https://stackoverflow.com/questions/359494/which-equals-operator-vs-should-be-used-in-javascript-comparisons

#### 解释一下同源策略(从 JS 相关的角度)

同源策略限制了 JS 向跨域域名发送请求。同源指的是协议、hostname、端口名一致。

这样做是为了避免网页执行了恶意脚本，然后恶意脚本通过操作 DOM 来获取敏感信息。

https://en.wikipedia.org/wiki/Same-origin_policy

#### `use strict;` 有什么用？它的优缺点是什么？

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

#### 解释一下什么是 SPA 以及如何提高 SPA 的 SEO

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

#### 解释一下 Promise

Promise 是一个对象，保存着一个结果，这个结果在将来某一时刻才会被确定。

它有 3 种状态：

1. 在结果确定之前，处于 pending 状态
2. 成功的结果，resolved，返回数据
3. 失败的结果，rejected，可能是报错了，返回错误信息

常见的 polyfill 有 `$.deferred`, Q 和 Blvebird，不过不是所有 polyfill 都完全遵循规范来实现的。

https://medium.com/javascript-scene/master-the-javascript-interview-what-is-a-promise-27fc71e77261

#### Promise 相对于回调的优缺点是什么？

**优点**

1. 避免回调地狱。
2. 编写顺序异步程序更简单。
3. 有了 `Promise.all()`，写并行异步也更简单了。
4. 关于回调的几个问题：过早调用、过晚调用、调用次数过多/过少、参数缺失、吞并异常等问题都不会发生。

**缺点**

1. 兼容性，老浏览器可能不支持。

https://github.com/getify/You-Dont-Know-JS/blob/master/async%20%26%20performance/ch3.md

#### 用另外一门语言写代码再编译成 JS 这样做的优缺点是什么？

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

#### 使用什么工具和技术来 debug

-   React, Redux: [React Devtools](https://github.com/facebook/react-devtools), [Redux Devtools](https://github.com/gaearon/redux-devtools)
-   Vue: [Vue Devtools](https://github.com/vuejs/vue-devtools)
-   JavaScript: [Chrome Devtools](https://hackernoon.com/twelve-fancy-chrome-devtools-tips-dc1e39d10d9d), `debugger`, `console.log`

https://hackernoon.com/twelve-fancy-chrome-devtools-tips-dc1e39d10d9d

https://raygun.com/blog/javascript-debugging/

#### 如何遍历对象和数组？

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

#### 解释一下 mutable 和 immutable 对象

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

#### 怎么实现 immutable？

1. 用库：immutablejs, mori, immer
2. 自己实现：用 `const` + 上面提到的冻结对象的方法。需要"修改"对象时，使用展开符、`Object.assign()`、`Array.concat()` 等方法来创建新的对象。

https://stackoverflow.com/questions/1863515/pros-cons-of-immutability-vs-mutability

https://www.sitepoint.com/immutability-javascript/

https://wecodetheweb.com/2016/02/12/immutable-javascript-using-es6-and-beyond/

#### 解释一下同步和异步函数的区别？

-   同步函数会阻塞主线程，异步函数不会。
-   同步函数中，按顺序执行，上一个语句执行完才会执行下一个语句，如果执行时间过长，程序就会变成无法响应了。
-   异步函数则一般接收一个回调函数，等异步操作结束之后再调用回调。

#### 什么是事件循环？调用栈和任务队列的区别又是什么？

事件循环是一个单线程的无限循环，它管着调用栈和任务队列，如果调用栈里面是空的，而任务队列中又有任务的话，事件循环就会从任务队列中出列一个任务，推入调用栈去执行。

https://2014.jsconf.eu/speakers/philip-roberts-what-the-heck-is-the-event-loop-anyway.html

https://2014.jsconf.eu/speakers/philip-roberts-what-the-heck-is-the-event-loop-anyway.html

http://theproactiveprogrammer.com/javascript/the-javascript-event-loop-a-stack-and-a-queue/

#### `function foo() {}` 和 `var foo = function () {}` 有什么区别？

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

#### ES6 class 和 ES5 的构造函数有什么区别？

最主要的是在写继承的时候提供了更简洁的语法糖，但是继承原理还是一样的。

https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Objects/Inheritance

https://eli.thegreenplace.net/2013/10/22/classical-inheritance-in-javascript-es5

#### 说一下箭头函数的有点。

-   语法简洁。
-   提供词法作用域的 `this`，箭头函数的 `this` 在书写时就确定为它外层第一个普通函数的 `this`。
