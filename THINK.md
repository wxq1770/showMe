## 思路面试题

#### HTML
- 简述一下你对 HTML 语义化的理解？
    ```
    用正确的标签做正确的事情。

    html 语义化让页面的内容结构化，结构更清晰，便于对浏览器、搜索引擎解析;

    即使在没有样式 CSS 情况下也以一种文档格式显示，并且是容易阅读的;

    搜索引擎的爬虫也依赖于 HTML 标记来确定上下文和各个关键字的权重，利于 ***SEO***;

    使阅读源代码的人对网站更容易将网站分块，便于阅读维护理解。
    ```
#### CSS

- 外边距折叠(collapsing margins)

    相邻的两个盒子（可能是兄弟关系也可能是祖先关系）的外边距可以结合成一个单独的外边距。 这种合并外边距的方式被称为折叠，结合而成的外边距称为折叠外边距

    折叠结果遵循下列计算规则：

    - 两个相邻的外边距都是正数时，折叠结果是它们两者之间较大的值
    - 两个相邻的外边距都是负数时，折叠结果是两者绝对值的较大值
    - 两个外边距一正一负时，折叠结果是两者的相加的和

- 用纯 CSS 创建一个三角形的原理是什么？
    ```CSS
    /* 把上、左、右三条边隐藏掉（颜色设为 transparent）*/
    #demo {
        width: 0;
        height: 0;
        border-width: 20px;
        border-style: solid;
        border-color: transparent transparent red transparent;
    }
    ```

- display:inline-block 什么时候会显示间隙？
    - 相邻的 inline-block 元素之间有换行或空格分隔的情况下会产生间距
    - 非 inline-block 水平元素设置为 inline-block 也会有水平间距
    - 可以借助 vertical-align:top; 消除垂直间隙
    - 可以在父级加 font-size：0; 在子元素里设置需要的字体大小，消除垂直间隙
    - 把 li 标签写到同一行可以消除垂直间隙，但代码可读性差

- display:inline-block 间隙问题怎么解决？
    ```CSS
    移除空格、
    使用 margin 负值、
    使用 font-size: 0、letter-spacing、word-spacing
    ```

- 请解释一下 CSS3 的 Flexbox（弹性盒布局模型）以及适用场景？
- 请写出多种等高布局
- 圣杯布局的实现原理？
- 什么是双飞翼布局？实现原理？
- reset.css 和 Normalize.css 理解
    - reset.css 意为重置默认样式。HTML 中绝大部分标签元素在网页显示中都有一个默认属性值，通常为了避免重复定义元素样式，需要进行重置默认样式
    - Normalize.css 只是一个很小的 css 文件,但它在默认的 HTML 元素样式上提供了跨浏览器的高度一致性。相比于传统的 css reset，Normalize.css 是一种现代的，为 HTML5 准备的优质替代方案。
        1. 保护有用的浏览器默认样式而不是完全去掉它们
        2. 一般化的样式：为大部分 HTML 元素提供
        3. 修复浏览器自身的 bug 并保证各浏览器的一致性
        4. 优化 CSS 可用性：用一些小技巧
        5. 解释代码：用注释和详细的文档来

- 介绍使用过的 CSS 预处理器？
    - CSS 预处理器基本思想：为 CSS 增加了一些编程的特性（变量、逻辑判断、继承嵌套、函数等）
    - 开发者使用这种语言进行进行 Web 页面样式设计，再编译成正常的 CSS 文件使用
    - 使用 CSS 预处理器，可以使 CSS 更加简洁、适应性更强、可读性更佳，无需考虑兼容性
    - 最常用的 CSS 预处理器语言包括：Sass（SCSS）和 LESS

- CSS 优化、提高性能的方法有哪些？
    - 多个 css 合并，尽量减少 HTTP 请求
    - 将 css 文件放在页面最上面
    - 移除空的 css 规则
    - 避免使用 CSS 表达式
    - 选择器优化嵌套，尽量避免层级过深
    - 充分利用 css 继承属性，减少代码量
    - 抽象提取公共样式，减少代码量
    - 属性值为 0 时，不加单位
    - 属性值为小于 1 的小数时，省略小数点前面的 0
    - css 雪碧图
    - base64 图片

- 元素竖向的百分比设定是相对于容器的高度吗？

    元素竖向的百分比设定是相对于容器的宽度，而不是高度

- 全屏滚动的原理是什么？ 用到了 CSS 的那些属性？
    - 原理类似图片轮播原理，超出隐藏部分，滚动时显示
    - 可能用到的 CSS 属性：overflow:hidden; transform:translate(100%, 100%); display:none;

- 如果需要手动写动画，你认为最小时间间隔是多久？

    16.7ms 多数显示器默认频率是 60Hz，即 1 秒刷新 60 次，所以理论上最小间隔: 1s / 60 * 1000 ＝ 16.7ms

#### JAVASCRIPT
- 常见排序算法的时间复杂度,空间复杂度
    
- 什么是 mvvm？

    MVVM 是 Model-View-ViewModel 的缩写。mvvm 是一种设计思想。Model 层代表数据模型，也可以在 Model 中定义数据修改和操作的业务逻辑；View 代表 UI 组件，它负责将数据模型转化成 UI 展现出来，ViewModel 是一个同步 View 和 Model 的对象。

    在 MVVM 架构下，View 和 Model 之间并没有直接的联系，而是通过 ViewModel 进行交互，Model 和 ViewModel 之间的交互是双向的， 因此 View 数据的变化会同步到 Model 中，而 Model 数据的变化也会立即反应到 View 上。

    ViewModel 通过双向数据绑定把 View 层和 Model 层连接了起来，而 View 和 Model 之间的同步工作完全是自动的，无需人为干涉，因此开发者只需关注业务逻辑，不需要手动操作 DOM, 不需要关注数据状态的同步问题，复杂的数据状态维护完全由 MVVM 来统一管理。

- vue 的双向绑定的原理是什么(常考)

    vue.js 是采用数据劫持结合发布者-订阅者模式的方式，通过 Object.defineProperty()来劫持各个属性的 setter，getter，在数据变动时发布消息给订阅者，触发相应的监听回调。

    具体步骤：

    第一步：需要 observe 的数据对象进行递归遍历，包括子属性对象的属性，都加上 setter 和 getter 这样的话，给这个对象的某个值赋值，就会触发 setter，那么就能监听到了数据变化

    第二步：compile 解析模板指令，将模板中的变量替换成数据，然后初始化渲染页面视图，并将每个指令对应的节点绑定更新函数，添加监听数据的订阅者，一旦数据有变动，收到通知，更新视图

    第三步：Watcher 订阅者是 Observer 和 Compile 之间通信的桥梁，主要做的事情是:

        - 在自身实例化时往属性订阅器(dep)里面添加自己
        - 自身必须有一个 update()方法
        - 待属性变动 dep.notice()通知时，能调用自身的 update() 方法，并触发 Compile 中绑定的回调，则功成身退。
    第四步：MVVM 作为数据绑定的入口，整合 Observer、Compile 和 Watcher 三者，通过 Observer 来监听自己的 model 数据变化，通过 Compile 来解析编译模板指令，最终利用 Watcher 搭起 Observer 和 Compile 之间的通信桥梁，达到数据变化 -> 视图更新；视图交互变化(input) -> 数据 model 变更的双向绑定效果。

- iOS safari 如何阻止“橡皮筋效果”？

    ```js
    $(document).ready(function(){
        var stopScrolling = function(event) {
            event.preventDefault();
        }
        document.addEventListener('touchstart', stopScrolling, false);
        document.addEventListener('touchmove', stopScrolling, false);
    });
    ```
    - 简单粗暴的解决法，阻止浏览器滑动的默认行为
        ```js
        document.body.addEventListener('touchmove', (e) => {
        e.preventDefault();
        });
        ```
    - 这里需要说明下，在IOS11.3下此写法不能达到预期效果，需要如下代码
        ```js
        document.body.addEventListener('touchmove', (e) => {
        e.preventDefault();
        }, { passive: false });
        ```
    ```js
    //默认都为false
    addEventListener(type, listener, {
        capture: false, //控制监听器是在捕获阶段执行还是在冒泡阶段执行
        passive: false,
        once: false, //表明该监听器是一次性的，执行一次后就被自动 removeEventListener 掉
    })
    // passive单独拿来讲
    // passive 监听器诞生了，passive 的意思是“顺从的”，表示它不会对事件的默认行为说 no，浏览器知道了一个监听器是 passive 的，它就可以在两个线程里同时执行监听器中的 JavaScript 代码和浏览器的默认行为了
    //为true时 调用 preventDefault() 无效
    ```

- 介绍 JavaScript 的原型，原型链？有什么特点？
    - 原型：
        - JavaScript 的所有对象中都包含了一个 [proto] 内部属性，这个属性所对应的就是该对象的原型
        - JavaScript 的函数对象，除了原型 [proto] 之外，还预置了 prototype 属性
        - 当函数对象作为构造函数创建实例时，该 prototype 属性值将被作为实例对象的原型 [proto]。
    - 原型链：
        - 当一个对象调用的属性/方法自身不存在时，就会去自己 [proto] 关联的前辈 prototype 对象上去找
        - 如果没找到，就会去该 prototype 原型 [proto] 关联的前辈 prototype 去找。依次类推，直到找到属性/方法或 undefined 为止。从而形成了所谓的“原型链”
    - 原型特点：
        - JavaScript 对象是通过引用来传递的，当修改原型时，与之相关的对象也会继承这一改变

- 解释 JavaScript 中的作用域与变量声明提升？
    - JavaScript 作用域：
        - 在 Java、C 等语言中，作用域为 for 语句、if 语句或{}内的一块区域，称为作用域；
        - 而在 JavaScript 中，作用域为 function(){}内的区域，称为函数作用域。
        - 全局函数无法查看局部函数的内部细节，但局部函数可以查看其上层的函数细节，直至全局细节
        - 如果当前作用域没有找到属性或方法，会向上层作用域查找，直至全局函数，这种形式就是作用域链
    - JavaScript 变量声明提升：
        - 在 JavaScript 中，函数声明与变量声明经常被 JavaScript 引擎隐式地提升到当前作用域的顶部。
        - 声明语句中的赋值部分并不会被提升，只有名称被提升
        - 函数声明的优先级高于变量，如果变量名跟函数名相同且未赋值，则函数声明会覆盖变量声明
        - 如果函数有多个同名参数，那么最后一个参数（即使没有定义）会覆盖前面的同名参数


- 谈谈 this 对象的理解
    - this 总是指向函数的直接调用者
    - 如果有 new 关键字，this 指向 new 出来的实例对象
    - 在事件中，this 指向触发这个事件的对象
    - IE 下 attachEvent 中的 this 总是指向全局对象 Window

- 什么是函数节流？介绍一下应用场景和原理？
    - 函数节流(throttle)是指阻止一个函数在很短时间间隔内连续调用。 只有当上一次函数执行后达到规定的时间间隔，才能进行下一次调用。 但要保证一个累计最小调用间隔（否则拖拽类的节流都将无连续效果）
    - 函数节流用于 onresize, onscroll 等短时间内会多次触发的事件
    - 函数节流的原理：
        - 使用定时器做时间节流。 当触发一个事件时，先用 setTimout 让这个事件延迟一小段时间再执行。 如果在这个时间间隔内又触发了事件，就 clearTimeout 原来的定时器， 再 setTimeout 一个新的定时器重复以上流程。
        ```js
        function throttle(method, context) {
            clearTimeout(methor.tId);
            method.tId = setTimeout(function(){
                method.call(context);
            }， 100); // 两次调用至少间隔 100ms
        }
        // 调用
        window.onresize = function(){
            throttle(myFunc, window);
        }
        ```

- 那些操作会造成内存泄漏？
    - 内存泄漏指任何对象在您不再拥有或需要它之后仍然存在
    - 垃圾回收器定期扫描对象，并计算引用了每个对象的其他对象的数量。如果一个对象的引用数量为 0（没有其他对象引用过该对象），或对该对象的惟一引用是循环的，那么该对象的内存即可回收
    - setTimeout 的第一个参数使用字符串而非函数的话，会引发内存泄漏
    - 闭包、控制台日志、循环（在两个对象彼此引用且彼此保留时，就会产生一个循环）
    - 未使用 var 声明的全局变量
    - 循环引用(两个对象相互引用)
    - 移除存在绑定事件的 DOM 元素(IE)

- JavaScript 对象生命周期的理解？ 
    - 当创建一个对象时，JavaScript 会自动为该对象分配适当的内存
    - 垃圾回收器定期扫描对象，并计算引用了该对象的其他对象的数量
    - 如果被引用数量为 0，或惟一引用是循环的，那么该对象的内存即可回收
- 为什么 JS 是单线程,而不是多线程 [常考]
    - 单线程是指 JavaScript 在执行的时候，有且只有一个主线程来处理所有的任务。
    - 目的是为了实现与浏览器交互。
    - 我们设想一下，如果 JavaScript 是多线程的，现在我们在浏览器中同时操作一个 DOM，一个线程要求浏览器在这个 DOM 中添加节点，而另一个线程却要求浏览器删掉这个 DOM 节点，那这个时候浏览器就会很郁闷，他不知道应该以哪个线程为准。所以为了避免此类现象的发生，降低复杂度，JavaScript 选择只用一个主线程来执行代码，以此来保证程序执行的一致性。



- vue 中 ajax 请求代码应该写在组件的 methods 中还是 vuex 的 action 中

    如果请求来的数据不是要被其他组件公用，仅仅在请求的组件内使用，就不需要放入 vuex 的 state 里

    如果被其他地方复用，请将请求放入 action 里，方便复用，并包装成 promise 返回

 
#### 浏览器/网络问题

- 浏览器debug工具与chrome插件的应用

- HTML5 的离线储存怎么使用，工作原理能不能解释一下<br/>
 
    在用户没有与因特网连接时，可以正常访问站点或应用，在用户与因特网连接时，更新用户机器上的缓存文件。<br/>

    原理：HTML5 的离线存储是基于一个新建的.appcache 文件的缓存机制(不是存储技术)，通过这个文件上的解析清单离线存储资源，这些资源就会像 cookie 一样被存储了下来。之后当网络在处于离线状态下时，浏览器会通过被离线存储的数据进行页面展示。

    如何使用：

    1. 页面头部像下面一样加入一个 manifest 的属性；
    2. 在 cache.manifest 文件的编写离线存储的资源

        ```
        CACHE MANIFEST
        #v1.0

        CACHE:
        js/app.js
        css/style.css

        NETWORK:
        assets/logo.png

        FALLBACK:
        /html5/ /404.html
        ```
    3. 在离线状态时，操作 window.applicationCache 进行需求实现。
    
        参考链接：- [HTML5 离线缓存-manifest 简介](https://chrome.google.com/webstore/detail/%E4%BA%8C%E7%BB%B4%E7%A0%81qr%E7%A0%81%E7%94%9F%E6%88%90%E5%99%A8qr-code-generato/pflgjjogbmmcmfhfcnlohagkablhbpmg, "HTML5 离线缓存-manifest 简介")

- 浏览器是怎么对 HTML5 的离线储存资源进行管理和加载的呢？

    ```
    在线的情况下，浏览器发现 html 头部有 manifest 属性，它会请求 manifest 文件，如果是第一次访问 app，那么浏览器就会根据 manifest 文件的内容下载相应的资源并且进行离线存储。如果已经访问过 app 并且资源已经离线存储了，那么浏览器就会使用离线的资源加载页面，然后浏览器会对比新的 manifest 文件与旧的 manifest 文件，如果文件没有发生改变，就不做任何操作，如果文件改变了，那么就会重新下载文件中的资源并进行离线存储。

    离线的情况下，浏览器就直接使用离线存储的资源。
    ```


- 如何最小化重绘(repaint)和回流(reflow)？

    - 需要要对元素进行复杂的操作时，可以先隐藏(display:"none")，操作完成后再显示
    - 需要创建多个 DOM 节点时，使用 DocumentFragment创建完后一次性的加入 document
    - 缓存 Layout 属性值，如：var left = elem.offsetLeft; 这样，多次使用 left 只产生一次回流
    - 尽量避免用 table 布局（table 元素一旦触发回流就会导致 table 里所有的其它元素回流）
    - 避免使用 css 表达式(expression)，因为每次调用都会重新计算值（包括加载页面）
    - 尽量使用 css 属性简写，如：用 border 代替 border-width, border-style, border-color 批量修改元素样式：elem.className 和 elem.style.cssText 代替 elem.style.xxx

- 请解释一下 JavaScript 的同源策略
    - 概念:同源策略是客户端脚本（尤其是 Javascript）的重要的安全度量标准。它最早出自 Netscape Navigator2.0，其目的是防止某个文档或脚本从多个不同源装载。这里的同源策略指的是：协议，域名，端口相同，同源策略是一种安全协议
    - 指一段脚本只能读取来自同一来源的窗口和文档的属性


- 从输入 URL 到页面加载发生了什么【必考】
    [详细](https://segmentfault.com/a/1190000006879700)
    - 总体来说分为以下几个过程:
        - DNS 解析
        - TCP 连接
        - 发送 HTTP 请求
        - 服务器处理请求并返回 HTTP 报文
        - 浏览器解析渲染页面
        - 连接结束
<br/>
、
- HTTP 长连接、短连接

    在 HTTP/1.0 中默认使用短连接。也就是说，客户端和服务器每进行一次 HTTP 操作，就建立一次连接，任务结束就中断连接。当客户端浏览器访问的某个 HTML 或其他类型的 Web 页中包含有其他的 Web 资源（如 JavaScript 文件、图像文件、CSS 文件等），每遇到这样一个 Web 资源，浏览器就会重新建立一个 HTTP 会话。

    而从 HTTP/1.1 起，默认使用长连接，用以保持连接特性。使用长连接的 HTTP 协议，会在响应头加入这行代码：

    `Connection:keep-alive`

    在使用长连接的情况下，当一个网页打开完成后，客户端和服务器之间用于传输 HTTP 数据的 TCP 连接不会关闭，客户端再次访问这个服务器时，会继续使用这一条已经建立的连接。Keep-Alive 不会永久保持连接，它有一个保持时间，可以在不同的服务器软件（如 Apache）中设定这个时间。实现长连接需要客户端和服务端都支持长连接。

    HTTP 协议的长连接和短连接，实质上是 TCP 协议的长连接和短连接。

- HTTP 的缓存机制(常考)

    Http 的缓存主要利用 header 里的两个字段来控制：
    - Cache-control主要包含以及几个字段：
        - private:则只有客户端可以缓存
        - public:客户端和代理服务器都可以缓存
        - max-age:缓存的过期时间
        - no-cache:需要使用对比缓存来验证缓存数据
        - no-store:所有内存都不会进行缓存
    - ETag:即用来进行对比缓存，Etag 是服务端资源的一个标识码
        - 当客户端发送第一次请求时服务端会下发当前请求资源的标识码 Etag，下次再请求时，客户端则会通过 header 里的 If-None-Match 将这个标识码 Etag 带上，服务端将客户端传来的 Etag 与最新的资源 Etag 做对比，如果一样，则表示资源没有更新，返回 304。
    - 通过 Cache-control 和 Etag 的配合来实现 Http 的缓存机制。


