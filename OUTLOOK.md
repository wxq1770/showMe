## 技术展望与项目经验及工作流

#### HTML
- PWA之离线缓存 Service Worker

#### CSS
- 抽离样式模块怎么写，说出思路？

    CSS 可以拆分成 2 部分：公共 CSS 和 业务 CSS：
    - 网站的配色，字体，交互提取出为公共 CSS。这部分 CSS 命名不应涉及具体的业务
    - 对于业务 CSS，需要有统一的命名，使用公用的前缀。可以参考面向对象的 CSS

- 什么是响应式设计？响应式设计的基本原理是什么？如何兼容低版本的 IE？
    - 响应式设计就是网站能够兼容多个终端，而不是为每个终端做一个特定的版本
    - 基本原理是利用 CSS3 媒体查询，为不同尺寸的设备适配不同样式
    - 对于低版本的 IE，可采用 JS 获取屏幕宽度，然后通过 resize 方法来实现兼容：
        ```js
        $(window).resize(function () {
            screenRespond();
        });

        screenRespond();

        function screenRespond(){

            var screenWidth = $(window).width();

            if(screenWidth <= 1800){
                $("body").attr("class", "w1800");
            }

            if(screenWidth <= 1400){
                $("body").attr("class", "w1400");
            }

            if(screenWidth > 1800){
                $("body").attr("class", "");
            }
        }
        ```
- 让页面里的字体变清晰，变细用 CSS 怎么做？（IOS 手机浏览器字体齿轮设置）
    ```css
    -webkit-font-smoothing: antialiased;
    ```

- 如何修改 Chrome 记住密码后自动填充表单的黄色背景？
    - 产生原因：由于 Chrome 默认会给自动填充的 input 表单加上 input:-webkit-autofill 私有属性造成的
    - 解决方案 1：在 form 标签上直接关闭了表单的自动填充：autocomplete="off"
    - 解决方案 2：input:-webkit-autofill { background-color: transparent; }

- 怎么让 Chrome 支持小于 12px 的文字？
    ```css
    .shrink{
        -webkit-transform:scale(0.8);
        -o-transform:scale(1);
        display:inline-block;
    }
    ```

- input [type=search] 搜索框右侧小图标如何美化？
    ```CSS
    input[type="search"]::-webkit-search-cancel-button{
        -webkit-appearance: none;
        height: 15px;
        width: 15px;
        border-radius: 8px;
        background:url("images/searchicon.png") no-repeat 0 0;
        background-size: 15px 15px;
    }
    ```
- 请问为何要使用 transform 而非 absolute positioning，或反之的理由？为什么？
    - 使用 transform 或 position 实现动画效果时是有很大差别。
    - 使用 transform 时，可以让 GPU 参与运算，动画的 FPS 更高。
    - 使用 position 时，最小的动画变化的单位是 1px，而使用 transform 参与时，可以做到更小（动画效果更加平滑）
    - 功能都一样。但是 translate 不会引起浏览器的重绘和重排，这就相当 nice 了。
    <br/><br/>
    反之

    - tranform 改变 fixed 子元素的定位对象
    - transform 改变元素层叠顺序 transform 的副作用

- 你熟悉 SVG 样式的书写吗？
    <table>
    <thead>
    <tr>
    <th>SVG</th>
    <th>等效的 CSS</th>
    </tr>
    </thead>
    <tbody>
    <tr>
    <td>fill</td>
    <td>background-color 或 color</td>
    </tr>
    <tr>
    <td>fill-opacity</td>
    <td>background-color 或 color 设置 rgba/hsla</td>
    </tr>
    <tr>
    <td>opacity</td>
    <td>opacity</td>
    </tr>
    <tr>
    <td>stroke</td>
    <td>border-color</td>
    </tr>
    <tr>
    <td>stroke-width</td>
    <td>border-thickness</td>
    </tr>
    <tr>
    <td>stroke-opacity</td>
    <td>border-color 设置 rgba</td>
    </tr>
    <tr>
    <td>rx, ry</td>
    <td>border-radius</td>
    </tr>
    </tbody>
    </table>

    - 下面的属性在 SVG 和 CSS 中是一样的，只是在 SVG 的 transformations 和 dimensions 中稍有区别：

        - font-family, font-size, font-style, font-variant 和 font-weight
        - width 和 height 
        - scale, rotate, skew

- 如果设计中使用了非标准的字体，你该如何去实现？
    - 用图片代替
    - web fonts 在线字库
    - @font-face
    
#### JAVASCRIPT
- 渐进增强和优雅降级
    - 渐进增强 ：针对低版本浏览器进行构建页面，保证最基本的功能，然后再针对高级浏览器进行效果、交互等改进和追加功能达到更好的用户体验。
    - 优雅降级 ：一开始就构建完整的功能，然后再针对低版本浏览器进行兼容
- Javascript 垃圾回收方法
    - 标记清除（mark and sweep）
        - 这是 JavaScript 最常见的垃圾回收方式，当变量进入执行环境的时候，比如函数中声明一个变量，垃圾回收器将其标记为“进入环境”，当变量离开环境的时候（函数执行结束）将其标记为“离开环境”
        - 垃圾回收器会在运行的时候给存储在内存中的所有变量加上标记，然后去掉环境中的变量以及被环境中变量所引用的变量（闭包），在这些完成之后仍存在标记的就是要删除的变量了

    - 引用计数(reference counting)
        - 在低版本 IE 中经常会出现内存泄露，很多时候就是因为其采用引用计数方式进行垃圾回收。引用计数的策略是跟踪记录每个值被使用的次数，当声明了一个 变量并将一个引用类型赋值给该变量的时候这个值的引用次数就加 1，如果该变量的值变成了另外一个，则这个值得引用次数减 1，当这个值的引用次数变为 0 的时 候，说明没有变量在使用，这个值没法被访问了，因此可以将其占用的空间回收，这样垃圾回收器会在运行的时候清理掉引用次数为 0 的值占用的空间
- 说说严格模式的限制
    - 严格模式主要有以下限制：
    - 变量必须声明后再使用
    - 函数的参数不能有同名属性，否则报错
    - 不能使用 with 语句
    - 不能对只读属性赋值，否则报错
    - 不能使用前缀 0 表示八进制数，否则报错
    - 不能删除不可删除的属性，否则报错
    - 不能删除变量 delete prop，会报错，只能删除属性 - elete global[prop]
    - eval 不会在它的外层作用域引入变量
    - eval 和 arguments 不能被重新赋值
    - arguments 不会自动反映函数参数的变化
    - 不能使用 arguments.callee
    - 不能使用 arguments.caller
    - 禁止 this 指向全局对象
    - 不能使用 fn.caller 和 fn.arguments 获取函数调- 用的堆栈
    - 增加了保留字（比如 protected、static 和 interface）

#### 浏览器/网络问题
- Http 2.0 与 http1.x 相比有什么优点(常考)
    - 二进制格式:http1.x 是文本协议，而 http2.0 是二进制以帧为基本单位，是一个二进制协议，一帧中除了包含数据外同时还包含该帧的标识：Stream Identifier，即标识了该帧属于哪个 request,使得网络传输变得十分灵活。
    - 多路复用: 一个很大的改进，原先 http1.x 一个连接一个请求的情况有比较大的局限性，也引发了很多问题，如建立多个连接的消耗以及效率问题。
        - http1.x 为了解决效率问题，可能会尽量多的发起并发的请求去加载资源，然而浏览器对于同一域名下的并发请求有限制，而优化的手段一般是将请求的资源放到不同的域名下来突破这种限制。
        - 而 http2.0 支持的多路复用可以很好的解决这个问题，多个请求共用一个 TCP 连接，多个请求可以同时在这个 TCP 连接上并发，一个是解决了建立多个 TCP 连接的消耗问题，一个也解决了效率的问题。那么是什么原理支撑多个请求可以在一个 TCP 连接上并发呢？基本原理就是上面的二进制分帧，因为每一帧都有一个身份标识，所以多个请求的不同帧可以并发的无序发送出去，在服务端会根据每一帧的身份标识，将其整理到对应的 request 中。
    - header 头部压缩:主要是通过压缩 header 来减少请求的大小，减少流量消耗，提高效率。因为之前存在一个问题是，每次请求都要带上 header，而这个 header 中的数据通常是一层不变的。
    - 支持服务端推送
