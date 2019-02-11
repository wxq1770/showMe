
# 前端面试题
## 我们喜欢什么样的面试者 - [面试理念](https://github.com/fex-team/interview-questions)
- 基础扎实
    - 从多年的经验看，那些发展好的同学都具备扎实的基础知识
    - 比如只懂 jQuery 不懂 JavaScript 是不行的哦
    - 如果了解计算机基础会更好，因为我们将面临很多非前端技术的问题
- 主动思考
    - 被动完成任务的同学在这里进步会很慢
    - 你需要有自己的想法，而不是仅仅完成任务
- 爱学习
    - 前端领域知识淘汰速度很快，所以最好能经常学习和接触新东西
- 有深度
    - 遇到问题时多研究背后深层次的原因，而不是想办法先绕过去
    - 比如追踪某个 Bug 一直了解它本质的原因
- 有视野
    - 创新往往来自于不同学科的交集，如果你了解的领域越多，就越有可能有新想法
## 基础笔试题

#### HTML 前面面试题 HTML之标签

- 行内元素有哪些？块级元素有哪些？ 空(void)元素有那些？

    定义：CSS 规范规定，每个元素都有 display 属性，确定该元素的类型，每个元素都有默认的 display 值，如 div 的 display 默认值为“block”，则为“块级”元素；span 默认 display 属性值为“inline”，是“行内”元素。
    - 行内元素有：a b span img input select strong（强调的语气）
    - 块级元素有：div ul ol li dl dt dd h1 h2 h3 h4…p
    - 空元素
        1. 常见: br hr img input link meta
        2. 不常见: area base col command embed keygen param source track wbr

- HTML5 为什么只需要写 ``<!DOCTYPE HTML>``?
    - HTML5 不基于 **SGML 标准通用标记语言**，因此不需要对 DTD 进行引用，但是需要 doctype 来规范浏览器的行为（让浏览器按照它们应该的方式来运行）；
    - 而 HTML4.01 基于 SGML,所以需要对 DTD 进行引用，才能告知浏览器文档所使用的文档类型。

- html5 有哪些新特性、移除了那些元素？如何处理 HTML5 新标签的浏览器兼容问题？如何区分 HTML 和 HTML5？
    - HTML5 现在已经不是 **SGML 标准通用标记语言** 的子集，主要是关于**图像，位置，存储，多任务**等功能的增加
        - 绘画 canvas
        - 用于媒介回放的 video 和 audio 元素
        - 本地离线存储 localStorage 长期存储数据，浏览器关闭后数据不丢失
        - sessionStorage 的数据在浏览器关闭后自动删除
        - 语意化更好的内容元素，比如 article、footer、header、nav、section
        - 表单控件，calendar、date、time、email、url、search
        - 新的技术 webworker, websocket, Geolocation
    -  移除的元素：
        - 纯表现的元素：basefont，big，center，font, s，strike，tt，u;
        - 对可用性产生负面影响的元素：frame，frameset，noframes；
    - 低端浏览器 **支持 HTML5 新标签** 方式
        - IE8/IE7/IE6 支持通过 document.createElement 方法产生的标签，
        - 浏览器支持新标签后，还需要添加标签默认的样式。
        - 当然也可以直接使用成熟的框架、比如 html5shim;
        ```html
        <!--[if lt IE 9]>
            <script> src="http://html5shim.googlecode.com/svn/trunk/html5.js"</script>
        <![endif]-->
        ```
- 说出至少 4 种 vue 当中的指令和它的用法

    `v-if`(判断是否隐藏)、`v-for`(把数据遍历出来)、`v-bind`(绑定属性)、`v-model`(实现双向绑定)
#### CSS
- 介绍一下CSS的盒子模型？

    有两种， IE 盒子模型、标准 W3C 盒子模型；
    1. IE的content部分包含了 border 和 pading;
    2. 盒模型： 内容(content)、填充(padding)、边界(margin)、 边框(border).

- a 标签上四个伪类的执行顺序是怎么样的？
    ```
    link > visited > hover > active
    ```

- CSS选择符有哪些？哪些属性可以继承？优先级算法如何计算？内联和important哪个优先级高？
    - 标签选择符 类选择符 id选择符
    - 继承不如指定
    - 优先级就近原则，同权重情况下样式定义最近者为准
    - 载入样式以最后载入的为准
    - 优先级为: !important > id > class > tag important 比 内联优先级高
    ```css

    id 选择器（ # myid）
    类选择器（.myclassname）
    标签选择器（div, h1, p）
    相邻选择器（h1 + p）
    子选择器（ul > li）
    后代选择器（li a）
    通配符选择器（ * ）
    属性选择器（a[rel = "external"]）
    伪类选择器（a:hover, li:nth-child）

    以下是权重的规则：
    标签的    权重为1，
    class的  权重为10，
    id的     权重为100，

    以下例子是演示各种定义的权重值：
    权重为1    
        div{} 
    权重为10   
        .class1{}
    权重为100  
        #id1{}
    权重为100+1=101 
        #id1 div{} 
    权重为10+1=11    
        .class1 div{} 
    权重为10+10+1=21  
        .class1 .class2 div{} 

    如果权重相同，则最后定义的样式会起作用，但是应该避免这种情况出现
    ```
    
- 实现不使用 border 画出 1px 高的线，在不同浏览器的标准模式与怪异模式下都能保持一致的效果。
    ```html
     <div style="height:1px;overflow:hidden;background:red"></div>
    ```

- 谈谈浮动和清除浮动

    浮动的框可以向左或向右移动，直到他的外边缘碰到包含框或另一个浮动框的边框为止。由于浮动框不在文档的普通流中，所以文档的普通流的块框表现得就像浮动框不存在一样。浮动的块框会漂浮在文档普通流的块框上
    - 使用空标签清除浮动 **clear:both**（*理论上能清楚任何标签，增加无意义的标签*）
    - 使用 **overflow:auto**（*空标签元素清除浮动而不得不增加无意代码的弊端,,使用zoom:1用于兼容IE*）
    - 是用 **afert** 伪元素清除浮动（*用于非IE浏览器*） 
    
    <br/>

    1. 父级 div 定义伪类：after 和 zoom (推荐使用，建议定义公共类，以减少 CSS 代码)
        ```css
        .clearfloat:after{
            display:block;
            clear:both;
            content:"";
            visibility:hidden;
            height:0
        }
        .clearfloat{
            zoom:1
        }
        ```
    2. 在结尾处添加空 div 标签 clear:both
        ```html
        <div class="parent">
            <div class="left">Left</div>
            <div class="right">Right</div>
            <div class="clearfloat"></div>
        </div>

        <style>
            .left {float:left}
            .clearfloat{clear:both}
        </style>
        ```
    3. 父级 div 定义 height
    4. 父级 div 定义 overflow:auto
    5. 父级 div 定义 overflow:hidden
    6. 父级 div 也一起浮动
    7. 父级 div 定义 display:table
    8. 结尾处加 br 标签 clear:both

- 如何居中div？如何居中一个浮动元素？
    ```css
    div{ 
        width:200px; 
        margin:0 auto; 
    }

    div{ 
        Width:500px ; 
        height:300px; //高度可以不设 
        margin: -150px 0 0 -250px;
        position: relative; //相对定位 
        left:50%;
        top:50%;
    }

    ```

- 如何竖直居中一个元素
    - 绝对定位居中
    - 如果居中的是行内元素，可以设置父级 height 与 line-height 相等
    - 设置 margin/padding 居中
    - 相对位置偏移居中
    - flex 居中 设置 align-items:center 即可

- 列出 **display** 的值，说明他们的作用。
    1. **block** 象块类型元素一样显示
    2. **none** 缺省值
    3. **inline-block** 象行内元素一样显示,但其内容象块类型元素一样显示
    4. **list-item** 象块类型元素一样显示，并添加样式列表标记。
    5. table 此元素会作为块级表格来显示
    6. inherit 规定应该从父元素继承 display 属性的值

- **position** 的值， **relative** 和 **absolute**、 **fixed**、**static** 定位原点是？
    - **absolute**　生成绝对定位的元素，相对于 static 定位以外的第一个父元素进行定位。
    - **relative** 生成相对定位的元素，相对于其正常位置进行定位。
    - **fixed** （老IE不支持） 生成绝对定位的元素，相对于浏览器窗口进行定位。
    - **static** 默认值。没有定位，元素出现在正常的流中 * （忽略 top, bottom, left, right z-index 声明）。
    - **inherit** 规定从父元素继承 position 属性的值。

- display: none; 与 visibility: hidden; 的区别
    - 相同： 它们都能让元素不可见
    - display:none;会让元素完全从渲染树中消失，渲染的时候不占据任何空间；visibility: hidden;不会让元素从渲染树消失，渲染师元素继续占据空间，只是内容不可见
    - display: none;是非继承属性，子孙节点消失由于元素从渲染树消失造成，通过修改子孙节点属性无法显示；visibility:hidden;是继承属性，子孙节点消失由于继承了 hidden，通过设置 visibility: visible;可以让子孙节点显式
    - 修改常规流中元素的 display 通常会造成文档重排。修改 visibility 属性只会造成本元素的重绘
    - 读屏器不会读取 display: none;元素内容；会读取 visibility: hidden 元素内容

- css 选择器 hack：不同浏览器对选择器的支持不一样
    ```css
    /***** Selector Hacks ******/

    /* IE6 and below */
    * html #uno  { color: red }

    /* IE7 */
    *:first-child+html #dos { color: red }

    /* IE7, FF, Saf, Opera  */
    html>body #tres { color: red }

    /* IE8, FF, Saf, Opera (Everything but IE 6,7) */
    html>/**/body #cuatro { color: red }

    /* Opera 9.27 and below, safari 2 */
    html:first-child #cinco { color: red }

    /* Safari 2-3 */
    html[xmlns*=""] body:last-child #seis { color: red }

    /* safari 3+, chrome 1+, opera9+, ff 3.5+ */
    body:nth-of-type(1) #siete { color: red }

    /* safari 3+, chrome 1+, opera9+, ff 3.5+ */
    body:first-of-type #ocho {  color: red }

    /* saf3+, chrome1+ */
    @media screen and (-webkit-min-device-pixel-ratio:0) {
    #diez  { color: red  }
    }

    /* iPhone / mobile webkit */
    @media screen and (max-device-width: 480px) {
    #veintiseis { color: red  }
    }

    /* Safari 2 - 3.1 */
    html[xmlns*=""]:root #trece  { color: red  }

    /* Safari 2 - 3.1, Opera 9.25 */
    *|html[xmlns*=""] #catorce { color: red  }

    /* Everything but IE6-8 */
    :root *> #quince { color: red  }

    /* IE7 */
    *+html #dieciocho {  color: red }

    /* Firefox only. 1+ */
    #veinticuatro,  x:-moz-any-link  { color: red }

    /* Firefox 3.0+ */
    #veinticinco,  x:-moz-any-link, x:default  { color: red  }
    ```

- 属性 hack：不同浏览器解析 bug 或方法
    ```css
    /* IE6 */
    #once { _color: blue }

    /* IE6, IE7 */
    #doce { *color: blue; /* or #color: blue */ }

    /* Everything but IE6 */
    #diecisiete { color/**/: blue }

    /* IE6, IE7, IE8 */
    #diecinueve { color: blue\9; }

    /* IE7, IE8 */
    #veinte { color/*\**/: blue\9; }

    /* IE6, IE7 -- acts as an !important */
    #veintesiete { color: blue !ie; } /* string after ! can be anything */
    ```

- CSS3有哪些新特性？
    - 新增选择器 p:nth-child(n){color: rgba(255, 0, 0, 0.75)}
    - 弹性盒模型 display: flex;
    - 多列布局 column-count: 5;
    - 媒体查询 @media (max-width: 480px) {.box: {column-count: 1;}}
    - 个性化字体 @font-face{font-family: BorderWeb; src:url(BORDERW0.eot);}
    - 颜色透明度 color: rgba(255, 0, 0, 0.75);
    - 圆角 border-radius: 5px;
    - 渐变 background:linear-gradient(red, green, blue);
    - 阴影 box-shadow:3px 3px 3px rgba(0, 64, 128, 0.3);
    - 倒影 box-reflect: below 2px;
    - 文字装饰 text-stroke-color: red;
    - 文字溢出 text-overflow:ellipsis;
    - 背景效果 background-size: 100px 100px;
    - 边框效果 border-image:url(bt_blue.png) 0 10;
    - 平滑过渡 transition: all .3s ease-in .1s;
    - 动画 @keyframes anim-1 {50% {border-radius: 50%;}} animation: anim-1 1s;
    - 转换
        - 旋转 transform: rotate(20deg);
        - 倾斜 transform: skew(150deg, -10deg);
        - 位移 transform: translate(20px, 20px);
        - 缩放 transform: scale(.5);
    
- CSS3 新增伪类有那些？
    - p:first-of-type 选择属于其父元素的首个元素的每个元素。

    - p:last-of-type 选择属于其父元素的最后元素的每个元素。

    - p:only-of-type 选择属于其父元素唯一的元素的每个元素。

    - p:only-child 选择属于其父元素的唯一子元素的每个元素。

    - p:nth-child(2) 选择属于其父元素的第二个子元素的每个元素。

    - :after 在元素之前添加内容,也可以用来做清除浮动。

    - :before 在元素之后添加内容

    - :enabled 选择器匹配每个已启用的元素（大多用在表单元素上）。

    - :disabled 控制表单控件的禁用状态。

    - :checked 单选框或复选框被选中

- 描述css reset的作用和用途。

    Reset重置浏览器的css默认属性 浏览器的品种不同，样式不同，然后重置，让他们统一

- css 属性 content 有什么作用？

    content 属性专门应用在 before/after 伪元素上，用于插入额外内容或样式
    
- ::before 和 :after 中双冒号和单冒号有什么区别？
    - 在 CSS 中伪类一直用 : 表示，如 :hover, :active 等
    - 伪元素在 CSS1 中已存在，当时语法是用 : 表示，如 :before 和 :after
    - 后来在 CSS3 中修订，伪元素用 :: 表示，如 ::before 和 ::after，以此区分伪元素和伪类
    - 由于低版本 IE 对双冒号不兼容，开发者为了兼容性各浏览器，继续使使用 :after 这种老语法表示伪元素
    - 综上所述：::before 是 CSS3 中写伪元素的新语法； :after 是 CSS1 中存在的、兼容 IE 的老语法
#### JAVASCRIPT
- JS 的基本数据类型和引用数据类型
    - 基本数据类型：undefined、null、boolean、number、string、symbol
    - 引用数据类型：object、array、function

- 介绍 JS 有哪些内置对象？
    - 数据封装类对象：Object、Array、Boolean、Number、String
    - 其他对象：Function、Arguments、Math、Date、RegExp、Error
    - ES6 新增对象：Symbol、Map、Set、Promises、Proxy、Reflect

- 区分什么是“客户区坐标”、“页面坐标”、“屏幕坐标”？
    - 客户区坐标：鼠标指针在可视区中的水平坐标(clientX)和垂直坐标(clientY)
    - 页面坐标：鼠标指针在页面布局中的水平坐标(pageX)和垂直坐标(pageY)
    - 屏幕坐标：设备物理屏幕的水平坐标(screenX)和垂直坐标(screenY)

- offsetWidth/offsetHeight,clientWidth/clientHeight 与 scrollWidth/scrollHeight 的区别
    - offsetWidth/offsetHeight 返回值包含 content + padding + border，效果与 e.getBoundingClientRect()相同
    - clientWidth/clientHeight 返回值只包含 content + padding，如果有滚动条，也不包含滚动条
    - scrollWidth/scrollHeight 返回值包含 content + padding + 溢出内容的尺寸


- 如何获得一个 DOM 元素的绝对位置？
    - elem.offsetLeft：返回元素相对于其定位父级左侧的距离
    - elem.offsetTop：返回元素相对于其定位父级顶部的距离
    - elem.getBoundingClientRect()：返回一个 DOMRect 对象，包含一组描述边框的只读属性，单位像素
- JavaScript 如何实现一个类，怎么实例化这个类？

    - 构造函数法（this + prototype） -- 用 new 关键字 生成实例对象
        - 缺点：用到了 this 和 prototype，编写复杂，可读性差
            ```js
            function Mobile(name, price){
                this.name = name;
                this.price = price;
            }
            Mobile.prototype.sell = function(){
                alert(this.name + "，售价 $" + this.price);
            }
            var iPhone7 = new Mobile("iPhone7", 1000);
            iPhone7.sell();
            ```
    - Object.create 法 -- 用 Object.create() 生成实例对象
        - 缺点：不能实现私有属性和私有方法，实例对象之间也不能共享数据
            ```js
            var Person = {
                firstname: "Mark",
                lastname: "Yun",
                age: 25,
                introduce: function(){
                    alert('I am ' + Person.firstname + ' ' + Person.lastname);
                }
            };

            var person = Object.create(Person);
            person.introduce();

            // Object.create 要求 IE9+，低版本浏览器可以自行部署：
            if (!Object.create) {
            　   Object.create = function (o) {
            　　　 function F() {}
            　　　 F.prototype = o;
            　　　 return new F();
            　　};
            　}
            ```
    - 极简主义法（消除 this 和 prototype） -- 调用 createNew() 得到实例对象
        - 优点：容易理解，结构清晰优雅，符合传统的"面向对象编程"的构造

            ```js
             var Cat = {
                age: 3, // 共享数据 -- 定义在类对象内，createNew() 外
                createNew: function () {
                    var cat = {};
                    // var cat = Animal.createNew(); // 继承 Animal 类
                    cat.name = "小咪";
                    var sound = "喵喵喵"; // 私有属性--定义在 createNew() 内，输出对象外
                    cat.makeSound = function () {
                    alert(sound);  // 暴露私有属性
                    };
                    cat.changeAge = function(num){
                    Cat.age = num; // 修改共享数据
                    };
                    return cat; // 输出对象
                }
                };

                var cat = Cat.createNew();
                cat.makeSound();
            ```
    - ES6 语法糖 class -- 用 new 关键字 生成实例对象
        ```js
        class Point {
            constructor(x, y) {
                this.x = x;
                this.y = y;
            }
            toString() {
                return '(' + this.x + ', ' + this.y + ')';
            }
        }
        var point = new Point(2, 3);
        ```


- Javascript 如何实现继承？
    - 构造函数绑定：使用 call 或 apply 方法，将父对象的构造函数绑定在子对象上
        ```js
        function Cat(name,color){
        　Animal.apply(this, arguments);
        　this.name = name;
        　this.color = color;
        }
        ```
    - 实例继承：将子对象的 prototype 指向父对象的一个实例
        ```js
        Cat.prototype = new Animal();
        Cat.prototype.constructor = Cat;
        ```
    - 拷贝继承：如果把父对象的所有属性和方法，拷贝进子对象
        ```js
        function extend(Child, Parent) {
        　　　var p = Parent.prototype;
        　　　var c = Child.prototype;
        　　　for (var i in p) {
        　　　   c[i] = p[i];
        　　　}
        　　　c.uber = p;
        }
        ```
    - 原型继承：将子对象的 prototype 指向父对象的 prototype
        ``` js
        function extend(Child, Parent) {
            var F = function(){};
            　F.prototype = Parent.prototype;
            　Child.prototype = new F();
            　Child.prototype.constructor = Child;
            　Child.uber = Parent.prototype;
        }
        ```
    - ES6 语法糖 extends：class ColorPoint extends Point {}
        ```js
        class ColorPoint extends Point {
            constructor(x, y, color) {
                super(x, y); // 调用父类的constructor(x, y)
                this.color = color;
            }
            toString() {
                return this.color + ' ' + super.toString(); // 调用父类的toString()
            }
        }
        ```
- 事件的三个阶段 及 事件委托的优缺点 
    - 捕获、目标、冒泡
    - 事件委托是指将事件绑定目标元素的到父元素上，利用冒泡机制触发该事件
        - 可以减少事件注册，节省大量内存占用
        - 可以将事件应用于动态添加的子元素上
        - 缺点 ： 用不当会造成事件在不应该触发时触发

- 介绍 DOM0，DOM2，DOM3 事件处理方式区别
    ```js
    // DOM0 级事件处理方式：
    btn.onclick = func;
    btn.onclick = null;
    
    // DOM2 级事件处理方式：
    btn.addEventListener('click', func, false);
    btn.removeEventListener('click', func, false);
    btn.attachEvent("onclick", func);
    btn.detachEvent("onclick", func);
    
    //DOM3 级事件处理方式：
    //eventUtil 是自定义对象，textInput 是 DOM3 级事件
    eventUtil.addListener(input, "textInput", func);
    ```
- 在一个 DOM 上同时绑定两个点击事件：一个用捕获，一个用冒泡。事件会执行几次，先执行冒泡还是捕获？
    - 该 DOM 上的事件如果被触发，会执行两次（执行次数等于绑定次数）
    - 如果该 DOM 是目标元素，则按事件绑定顺序执行，不区分冒泡/捕获
    - 如果该 DOM 是处于事件流中的非目标元素，则先执行捕获，后执行冒泡

- IE 的事件处理和 W3C 的事件处理有哪些区别？(必考)

    ```js
    // 绑定事件
    W3C: targetEl.addEventListener('click', handler, false);
    IE: targetEl.attachEvent('onclick', handler);
    
    //删除事件
    W3C: targetEl.removeEventListener('click', handler, false);
    IE: targetEl.detachEvent(event, handler);
    
    //事件对象
    W3C: var e = arguments.callee.caller.arguments[0]
    IE: window.event
    
    //事件目标
    W3C: e.target
    IE: window.event.srcElement
    
    //阻止事件默认行为
    W3C: e.preventDefault()
    IE: window.event.returnValue = false'
    
    //阻止事件传播
    W3C: e.stopPropagation()
    IE: window.event.cancelBubble = true
    ```
- 闭包的特性：
    - 函数内再嵌套函数
    - 内部函数可以引用外层的参数和变量
    - 参数和变量不会被垃圾回收机制回收
- 如下代码的含义是？foo::bar(...arguments);

    函数绑定运算符是并排的两个冒号（::），双冒号左边是一个对象，右边是一个函数。该运算符会自动将左边的对象，作为上下文环境（即this对象），绑定到右边的函数上面。
    ```js
    foo::bar(...arguments);
    // 等同于
    bar.apply(foo, arguments);
    ```
- 编写一个方法 求一个字符串的字节长度
    ```js
    function GetBytes(str){
        var len = str.length;
        var bytes = len;
        for(var i=0; i<len; i++){
            if (str.charCodeAt(i) > 255) bytes++;
        }
        return bytes;
    }
    alert(GetBytes("你好,as"));
    ```
- 简单实现 Function.bind 函数？
    ```js
    if (!Function.prototype.bind) {
        Function.prototype.bind = function(that) {
        var func = this, args = arguments;
        return function() {
            return func.apply(that, Array.prototype.slice.call(args, 1));
        }
        }
    }
    // 只支持 bind 阶段的默认参数：
    func.bind(that, arg1, arg2)();

    // 不支持以下调用阶段传入的参数：
    func.bind(that)(arg1, arg2);
    ```
- Array.slice() 与 Array.splice() 的区别？
    - slice -- “读取”数组指定的元素，不会对原数组进行修改
        - 语法：arr.slice(start, end)
        - start 指定选取开始位置（含）
        - end 指定选取结束位置（不含）

    - splice
        - “操作”数组指定的元素，会修改原数组，返回被删除的元素
        - 语法：arr.splice(index, count, [insert Elements])
        - index 是操作的起始位置
        - count = 0 插入元素，count > 0 删除元素
        - [insert Elements] 向数组新插入的元素
- 请详细说下你对 vue 生命周期的理解？
    - 答：总共分为 8 个阶段创建前/后，载入前/后，更新前/后，销毁前/后。

    - 创建前/后： 在 beforeCreate 阶段，vue 实例的挂载元素 el 还没有。
    - 载入前/后：在 beforeMount 阶段，vue 实例的$el 和 data 都初始化了，但还是挂载之前为虚拟的 dom 节点，data.message 还未替换。在 mounted 阶段，vue 实例挂载完成，data.message 成功渲染。
    - 更新前/后：当 data 变化时，会触发 beforeUpdate 和 updated 方法。
    - 销毁前/后：在执行 destroy 方法后，对 data 的改变不会再触发周期函数，说明此时 vue 实例已经解除了事件监听以及和 dom 的绑定，但是 dom 结构依然存在
- 组件之间的传值？
    1. 父组件与子组件传值
        ```js
        //父组件通过标签上面定义传值
        <template>
            <Main :obj="data"></Main>
        </template>
        <script>
            //引入子组件
            import Main form "./main"

            exprot default{
                name:"parent",
                data(){
                    return {
                        data:"我要向子组件传递数据"
                    }
                },
                //初始化组件
                components:{
                    Main
                }
            }
        </script>


        //子组件通过props方法接受数据
        <template>
            <div>{{data}}</div>
        </template>
        <script>
            exprot default{
                name:"son",
                //接受父组件传值
                props:["data"]
            }
        </script>
        ```
        
    2. 子组件向父组件传递数据
        ```html
        <!-- 子组件通过$emit方法传递参数 -->
        <template>
            <div id="child" @click="$emit(sendparent,'hello',function(){return 'world'})"></div>
        </template>

        <!-- 父组件 -->
        <template>
        <div id="parent">
            <menu-left @sendparent="helloFn"></menu-left>
        </div>
        </template>
        
        <script>
        export default {
            name: 'App',
            methods: {
                helloFn: function (param1,param2) {
                    alert("hello world");
                    alert(param2());
                },
            }
        }
        </script>
        ```

    3. 兄弟间组件传值
        - 保持良好的团队命名规范，避免冲突，因为所有事件代码都保留在各个组件内部，发生冲突很难 debug。
        - 尽量减少不必要的通信，合理使用props传参。
        - 大型项目，应该一开始就选用vuex
        ```js
        //有时候非父子关系的组件也需要通信。在简单的场景下，使用一个空的 Vue 实例作为中央事件总线
        var bus = new Vue()
        // 触发组件 A 中的事件
        bus.$emit('event')
        // 在组件 B 创建的钩子中监听事件
        bus.$on('event', function () {
        // ...
        })
        ```
- vue 重定向、父子路由配置
    ```js
    import Vue from 'vue'
    import VueRouter from 'vue-router'
    Vue.use(VueRouter)

    //引入两个组件

    import home from "./home.vue"
    import game from "./game.vue"
    //定义路由
    const routes = [
        { path: "/", redirect: "/home" },//重定向,指向了home组件
        {
            path: "/home", component: home,
            //子路由
            children: [
                { path: "/home/game", component: game }
            ]
        }
    ]
    //创建路由实例
    const router = new VueRouter({routes})

    new Vue({
        el: '#app',
        data: {
        },
        methods: {
        },
        router
    })
    ```
- vue-router 有哪几种导航钩子?
    - 三种
    - 全局导航钩子
        - router.beforeEach(to, from, next),
        - router.beforeResolve(to, from, next),
        - router.afterEach(to, from ,next)
    - 组件内钩子
        - beforeRouteEnter,
        - beforeRouteUpdate,
        - beforeRouteLeave
    - 单独路由独享组件
        - beforeEnter
- 路由之间跳转？
    - 声明式（标签跳转） `<router-link :to="index">`
    - 编程式（ js 跳转）`router.push('index')`
- vuex 有哪几种属性
    - 有 5 种，分别是 `state、getter、mutation、action、module`
        - store
            - vuex 就是一个仓库，仓库里放了很多对象。其中 state 就是数据源存放地，对应于一般 vue 对象里面的 data
            - state 里面存放的数据是响应式的，vue 组件从 store 读取数据，若是 store 中的数据发生改变，依赖这相数据的组件也会发生更新
            - 它通过 mapState 把全局的 state 和 getters 映射到当前组件的 computed 计算属性
        - getter 特性是什么
            - getter 可以对 state 进行计算操作，它就是 store 的计算属性
            - 虽然在组件内也可以做计算属性，但是 getters 可以在多给件之间复用
            - 如果一个状态只在一个组件内使用，是可以不用 getters
        - mutation 特性是什么
            - action 类似于 muation, 不同在于：action 提交的是 mutation,而不是直接变更状态
            - action 可以包含任意异步操作
#### 浏览器/网络问题
- 常见的浏览器内核有哪些？
    ```
    Trident 内核：IE,MaxThon,TT,The World,360,搜狗浏览器等。[又称 MSHTML]

    Gecko 内核：Netscape6 及以上版本，FF,MozillaSuite/SeaMonkey 等

    Presto 内核：Opera7 及以上。 [Opera 内核原为：Presto，现为：Blink;]

    Webkit 内核：Safari,Chrome 等。 [ Chrome 的：Blink（WebKit 的分支）]
    ```

- 描述浏览器的渲染过程，DOM 树和渲染树的区别？
    - 浏览器的渲染过程：

        - 解析 HTML 构建 DOM(DOM 树)，并行请求 css/image/js
        - CSS 文件下载完成，开始构建 CSSOM(CSS 树)
        - CSSOM 构建结束后，和 DOM 一起生成 Render Tree(渲染树)
        - 布局(Layout)：计算出每个节点在屏幕中的位置
        - 显示(Painting)：通过显卡把页面画到屏幕上
    - DOM 树 和 渲染树 的区别：

        - DOM 树与 HTML 标签一一对应，包括 head 和隐藏元素
        - 渲染树不包括 head 和隐藏元素，大段文本的每一个行都是独立节点，每一个节点都有对应的 css 属性
- http 响应常见状态码
    - 100-199 : 表示成功接收请求, 要求客户端继续提交下一次请求才能完成整个处理过程
    - 200-299: 表示成果接收请求并已完成整个处理过程. 常用 200
    - 300-399: 为完成请求, 客户需进一步细化需求: 例如: 请求的资源已经移动一个新地址, 常用 302(重定向), 307 和 304(拿缓存)
    - 400-499: 客户端的请求有错误, 包含语法错误或者不能正确执行. 常用 404(请求的资源在 web 服务器中没有) 403(服务器拒绝访问, 权限不够)
    - 500-599: 服务器端出现错误
    
    - 常用：
        - 200 正常，表示一切正常, 返回的是正常请求结果
        - 302/307 临时重定向，指出请求的文档已被临时移动到别处, 此文档的新的 url 在 location 响应头中给出
        - 304 未修改，表示客户机缓存的版本是最新的, 客户机应该继续使用它
        - 403 禁止，服务器理解客户端请求, 但拒绝处理它, 通常用于服务器上文件或目录的权限设置所致
        - 404 找不到，服务器上不存在客户机所请求的资源
        - 500 服务器内部错误，服务器端的 cgi, asp, jsp 等程序发生错误
- HTTP 的几种请求方法用途
    - GET 方法：发送一个请求来取得服务器上的某一资源
    - POST 方法：向 URL 指定的资源提交数据或附加新的数据
    - PUT 方法：跟 POST 方法很像，也是想服务器提交数据。但是，它们之间有不同。PUT 指定了资源在服务器上的位置，而 POST 没有
    - HEAD 方法：只请求页面的首部
    - DELETE 方法：删除服务器上的某资源
    - OPTIONS 方法：它用于获取当前 URL 所支持的方法。如果请求成功，会有一个 Allow 的头包含类似“GET,POST”这样的信息
    - TRACE 方法：TRACE 方法被用于激发一个远程的，应用层的请求消息回路
    - CONNECT 方法：把请求连接转换到透明的 TCP/IP 通道

- Cookie
    Cookie 就是用来在本地缓存记住一些状态的，一个 Cookie 一般都包含 domin(所属域)、path、Expires(过期时间)等几个属性。服务端可以通过在响应头里的 set-cookies 来将状态写入客户端的 Cookie 里。下次客户端发起请求时可以将 Co

<br/>

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

- 前端需要注意哪些SEO
    - 合理的title、description、keywords：搜索对着三项的权重逐个减小，title值强调重点即可，重要关键词出现不要超过2次，而且要靠前，不同页面title要有所不同；description把页面内容高度概括，长度合适，不可过分堆砌关键词，不同页面description有所不同；keywords列举出重要关键词即可
    - 语义化的HTML代码，符合W3C规范：语义化代码让搜索引擎容易理解网页
    - 重要内容HTML代码放在最前：搜索引擎抓取HTML顺序是从上到下，有的搜索引擎对抓取长度有限制，保证重要内容一定会被抓取
    - 重要内容不要用js输出：爬虫不会执行js获取内容
    - 少用iframe：搜索引擎不会抓取iframe中的内容
    - 非装饰性图片必须加alt
    - 提高网站速度：网站速度是搜索引擎排序的一个重要指标

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

        //第二种方式
        function throttle(fn, gapTime) {
        let _lastTime = null;

        return function() {
            let _nowTime = +new Date();
            if (_nowTime - _lastTime > gapTime || !_lastTime) {
            fn();
            _lastTime = _nowTime;
            }
        };
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

 
- 函数防抖(debounce) 概念:在事件被触发 n 秒后再执行回调，如果在这 n 秒内又被触发，则重新计时。

```js
function debounce(fn, wait) {
  var timer = null;
  return function() {
    var context = this;
    var args = arguments;
    if (timer) {
      clearTimeout(timer);
      timer = null;
    }
    timer = setTimeout(function() {
      fn.apply(context, args);
    }, wait);
  };
}
```
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

- HTTP request报文结构是怎样的
    1. 首行是Request-Line包括：请求方法，请求URI，协议版本，CRLF
    2. 首行之后是若干行请求头，包括general-header，request-header或者entity-header，每个一行以CRLF结束
    3. 请求头和消息实体之间有一个CRLF分隔
    4. 根据实际请求需要可能包含一个消息实体 一个请求报文例子如下：

        ```
        GET /Protocols/rfc2616/rfc2616-sec5.html HTTP/1.1
        Host: www.w3.org
        Connection: keep-alive
        Cache-Control: max-age=0
        Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,*/*;q=0.8
        User-Agent: Mozilla/5.0 (Windows NT 6.1; WOW64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/35.0.1916.153 Safari/537.36
        Referer: https://www.google.com.hk/
        Accept-Encoding: gzip,deflate,sdch
        Accept-Language: zh-CN,zh;q=0.8,en;q=0.6
        Cookie: authorstyle=yes
        If-None-Match: "2cc8-3e3073913b100"
        If-Modified-Since: Wed, 01 Sep 2004 13:24:52 GMT

        name=qiu&age=25
        ```

- HTTP response报文结构是怎样的
    1. 首行是状态行包括：HTTP版本，状态码，状态描述，后面跟一个CRLF
    2. 首行之后是若干行响应头，包括：通用头部，响应头部，实体头部
    3. 响应头部和响应实体之间用一个CRLF空行分隔
    4. 最后是一个可能的消息实体 响应报文例子如下：
        ```
        HTTP/1.1 200 OK
        Date: Tue, 08 Jul 2014 05:28:43 GMT
        Server: Apache/2
        Last-Modified: Wed, 01 Sep 2004 13:24:52 GMT
        ETag: "40d7-3e3073913b100"
        Accept-Ranges: bytes
        Content-Length: 16599
        Cache-Control: max-age=21600
        Expires: Tue, 08 Jul 2014 11:28:43 GMT
        P3P: policyref="http://www.w3.org/2001/05/P3P/p3p.xml"
        Content-Type: text/html; charset=iso-8859-1

        {"name": "qiu", "age": 25}
        ```

- 如何进行网站性能优化
    - content方面
        - 减少HTTP请求：合并文件、CSS精灵、inline Image
        - 减少DNS查询：DNS查询完成之前浏览器不能从这个主机下载任何任何文件。方法：DNS缓存、将资源分布到恰当数量的主机名，平衡并行下载和DNS查询
        - 避免重定向：多余的中间访问
        - 使Ajax可缓存
        - 非必须组件延迟加载
        - 未来所需组件预加载
        - 减少DOM元素数量
        - 将资源放到不同的域下：浏览器同时从一个域下载资源的数目有限，增加域可以提高并行下载量
        - 减少iframe数量
        - 不要404
    - Server方面
        - 使用CDN
        - 添加Expires或者Cache-Control响应头
        - 对组件使用Gzip压缩
        - 配置ETag
        - Flush Buffer Early
        - Ajax使用GET进行请求
        - 避免空src的img标签
    - Cookie方面
        - 减小cookie大小
        - 引入资源的域名不要包含cookie
    - css方面
        - 将样式表放到页面顶部
        - 不使用CSS表达式
        - 使用不使用@import
        - 不使用IE的Filter
    - Javascript方面
        - 将脚本放到页面底部
        - 将javascript和css从外部引入
        - 压缩javascript和css
        - 删除不需要的脚本
        - 减少DOM访问
        - 合理设计事件监听器
    - 图片方面
        - 优化图片：根据实际颜色需要选择色深、压缩
        - 优化css精灵
        - 不要在HTML中拉伸图片
        - 保证favicon.ico小并且可缓存
    - 移动方面
        - 保证组件小于25k
        - Pack Components into a Multipart Document

- 从浏览器地址栏输入url到显示页面的步骤(以HTTP为例)
    1. 在浏览器地址栏输入URL
    2. 浏览器查看缓存，如果请求资源在缓存中并且新鲜，跳转到转码步骤
        - 如果资源未缓存，发起新请求
        - 如果已缓存，检验是否足够新鲜，足够新鲜直接提供给客户端，否则与服务器进行验证
        - 检验新鲜通常有两个HTTP头进行控制Expires和Cache-Control
            - HTTP1.0提供Expires，值为一个绝对时间表示缓存新鲜日期
            - HTTP1.1增加了Cache-Control: max-age=,值为以秒为单位的最大新鲜时间
    3. 浏览器解析URL获取协议，主机，端口，path
    4. 浏览器组装一个HTTP（GET）请求报文
    5. 浏览器获取主机ip地址，过程如下：
        - 浏览器缓存
        - 本机缓存
        - hosts文件
        - 路由器缓存
        - ISP DNS缓存
        - DNS递归查询（可能存在负载均衡导致每次IP不一样）
    6. 打开一个socket与目标IP地址，端口建立TCP链接，三次握手如下：
        - 客户端发送一个TCP的SYN=1，Seq=X的包到服务器端口
        - 服务器发回SYN=1， ACK=X+1， Seq=Y的响应包
        - 客户端发送ACK=Y+1， Seq=Z
    7. TCP链接建立后发送HTTP请求
    8. 服务器接受请求并解析，将请求转发到服务程序，如虚拟主机使用HTTP Host头部判断请求的服务程序
    9. 服务器检查HTTP请求头是否包含缓存验证信息如果验证缓存新鲜，返回304等对应状态码
    10. 处理程序读取完整请求并准备HTTP响应，可能需要查询数据库等操作
    11. 服务器将响应报文通过TCP连接发送回浏览器
    12. 浏览器接收HTTP响应，然后根据情况选择关闭TCP连接或者保留重用，关闭TCP连接的四次握手如下：
        - 主动方发送Fin=1， Ack=Z， Seq= X报文
        - 被动方发送ACK=X+1， Seq=Z报文
        - 被动方发送Fin=1， ACK=X， Seq=Y报文
        - 主动方发送ACK=Y， Seq=X报文
    13. 浏览器检查响应状态吗：是否为1XX，3XX， 4XX， 5XX，这些情况处理与2XX不同
    14. 如果资源可缓存，进行缓存
    15. 对响应进行解码（例如gzip压缩）
    16. 根据资源类型决定如何处理（假设资源为HTML文档）
    17. 解析HTML文档，构件DOM树，下载资源，构造CSSOM树，执行js脚本，这些操作没有严格的先后顺序，以下分别解释
    18. 构建DOM树：
        - Tokenizing：根据HTML规范将字符流解析为标记
        - Lexing：词法分析将标记转换为对象并定义属性和规则
        - DOM construction：根据HTML标记关系将对象组成DOM树
    19. 解析过程中遇到图片、样式表、js文件，启动下载
    20. 构建CSSOM树：
        - Tokenizing：字符流转换为标记流
        - Node：根据标记创建节点
        - CSSOM：节点创建CSSOM树
    21. 根据DOM树和CSSOM树构建渲染树:
        - 从DOM树的根节点遍历所有可见节点，不可见节点包括：1）script,meta这样本身不可见的标签。2)被css隐藏的节点，如display: none
        - 对每一个可见节点，找到恰当的CSSOM规则并应用
        - 发布可视节点的内容和计算样式
    22. js解析如下：
        - 浏览器创建Document对象并解析HTML，将解析到的元素和文本节点添加到文档中，此时document.readystate为loading
        - HTML解析器遇到没有async和defer的script时，将他们添加到文档中，然后执行行内或外部脚本。这些脚本会同步执行，并且在脚本下载和执行时解析器会暂停。这样就可以用document.write()把文本插入到输入流中。同步脚本经常简单定义函数和注册事件处理程序，他们可以遍历和操作script和他们之前的文档内容
        - 当解析器遇到设置了async属性的script时，开始下载脚本并继续解析文档。脚本会在它下载完成后尽快执行，但是解析器不会停下来等它下载。异步脚本禁止使用document.write()，它们可以访问自己script和之前的文档元素
        - 当文档完成解析，document.readState变成interactive
        - 所有defer脚本会按照在文档出现的顺序执行，延迟脚本能访问完整文档树，禁止使用document.write()
        - 浏览器在Document对象上触发DOMContentLoaded事件
        - 此时文档完全解析完成，浏览器可能还在等待如图片等内容加载，等这些内容完成载入并且所有异步脚本完成载入和执行，document.readState变为complete,window触发load事件
        - 显示页面（HTML解析过程中会逐步显示页面）
#### es6、7相关
- es6模板字符串的用法，includes() repeat() padStart()的含义
    ```js
        `abad ${num} asdf`
    ```
    - includes(); 返回布尔值，表示是否找到了参数字符串。
    - repeat(); 方法返回一个新字符串，表示将原字符串重复n次。
    - padStart(); 用于头部补全
- es6箭头函数 var sum = (num1, num2) => num1 + num2; let getTempItem = id => { id: id, name: "Temp" }; 翻译成普通函数
    ```js 
    var sum = function(num1, num2) {
        return num1 + num2;
    };

    // 报错
    let getTempItem = id => { id: id, name: "Temp" };

    // 不报错
    let getTempItem = id => ({ id: id, name: "Temp" });
    ```
- es6数组新增方法 
    - `console.log(1, ...[2, 3, 4], 5)`; 
    - `Array.from()`; 类似数组的对象（array-like object）和可遍历（iterable）的对象 转为真正的数组
    -` Array.of(3, 11, 8);` 将一组值，转换为数组
    - `Array.prototype.copyWithin(target, start = 0, end = this.length);` 在当前数组内部，将指定位置的成员复制到其他位置（会覆盖原有成员），然后返回当前数组。
        - `target（必需）`：从该位置开始替换数据。如果为负值，表示倒数。
        - `start（可选）`：从该位置开始读取数据，默认为 0。如果为负值，表示倒数。
        - `end（可选）`：到该位置前停止读取数据，默认等于数组长度。如果为负值，表示倒数。
    - `find();` 用于找出第一个符合条件的数组成员。然后返回该成员，否则返回undefined
    - `findIndex();` 返回第一个符合条件的数组成员的位置，如果所有成员都不符合条件，则返回-1
    - `fill();` 方法使用给定值，填充一个数组。
    - `keys()`是对键名的遍历、
    - `values()`是对键值的遍历，
    - `entries()`是对键值对的遍历。
    - `includes()` 表示某个数组是否包含给定的值，
    - `flat()` 用于将嵌套的数组“拉平”，变成一维的数组。该方法返回一个新数组，对原数据没有影响
    - `flatMap()`方法对原数组的每个成员执行一个函数然后对返回值组成的数组执行flat()方法。该方法返回一个新数组，不改变原数组。
- es6对象的扩展属性及方法
    - `super` this关键字总是指向函数所在的当前对象，ES6 又新增了另一个类似的关键字super，指向当前对象的原型对象。
    - `Object.is()` 它用来比较两个值是否严格相等
    - `Object.assign()` 方法用于对象的合并，将源对象（source）的所有可枚举属性，复制到目标对象（target）。
    - `Object.getOwnPropertyDescriptors()` ES5 的Object.getOwnPropertyDescriptor()方法会返回某个对象属性的描述对象（descriptor）。ES2017 引入了Object.getOwnPropertyDescriptors()方法，返回指定对象所有自身属性（非继承属性）的描述对象。
    - `Object.setPrototypeOf()` Object.setPrototypeOf方法的作用与__proto__相同，用来设置一个对象的prototype对象
    - `Object.getPrototypeOf()` 该方法与Object.setPrototypeOf方法配套，用于读取一个对象的原型对象
    - `Object.keys()`，

        ES5 引入了Object.keys方法，返回一个数组，成员是参数对象自身的（不含继承的）所有可遍历（enumerable）属性的键名。
        
        ES2017 引入了跟Object.keys配套的Object.values和Object.entries，作为遍历一个对象的补充手段，供for...of循环使用。

    - `Object.values()`，

        Object.values方法返回一个数组，成员是参数对象自身的（不含继承的）所有可遍历（enumerable）属性的键值。

    - `Object.entries()`

        Object.entries()方法返回一个数组，成员是参数对象自身的（不含继承的）所有可遍历（enumerable）属性的键值对数组。

    - `Object.fromEntries()` 

        Object.fromEntries()方法是Object.entries()的逆操作，用于将一个键值对数组转为对象。
- set map 数据结构 

    ES6 提供了新的数据结构 `Set`。它类似于数组，但是`成员的值都是唯一的`，`没有重复的值`。WeakSet 的成员只能是对象，而不能是其他类型的值。
    - `Set` 结构的实例有以下属性。
        - `Set.prototype.constructor：`构造函数，默认就是Set函数。
        - `Set.prototype.size：`返回Set实例的成员总数。

    - Set 实例的方法分为两大类：操作方法（用于操作数据）和遍历方法（用于遍历成员）。下面先介绍四个操作方法。
        - `add(value)：`添加某个值，返回 Set 结构本身。
        - `delete(value)：`删除某个值，返回一个布尔值，表示删除是否成功。
        - `has(value)：`返回一个布尔值，表示该值是否为Set的成员。
        - `clear()：`清除所有成员，没有返回值。
    - Set 结构的实例有四个遍历方法，可以用于遍历成员。
        - `keys()`：返回键名的遍历器
        - `values()`：返回键值的遍历器
        - `entries()`：返回键值对的遍历器
        - `forEach()`：使用回调函数遍历每个成员
    
    Map 数据结构。它类似于对象，也是键值对的集合，但是“键”的范围不限于字符串，各种类型的值（包括对象）都可以当作键。`WeakMap`只接受对象作为键名（null除外），不接受其他类型的值作为键名。`WeakMap`的键名所指向的对象，不计入垃圾回收机制。

    - `size 属性` 返回 Map 结构的成员总数。
    - `set(key, value) `set方法返回的是当前的Map对象，因此可以采用链式写法。
    - `get(key) `get方法读取key对应的键值，如果找不到key，返回undefined。
    - `has(key) `has方法返回一个布尔值，表示某个键是否在当前 Map 对象之中。
    - `delete(key)` delete方法删除某个键，返回true。如果删除失败，返回false。
    - `clear()` clear方法清除所有成员，没有返回值。

    - `keys()：`返回键名的遍历器。
    - `values()：`返回键值的遍历器。
    - `entries()：`返回所有成员的遍历器。
    - `forEach()：`遍历 Map 的所有成员。
- es6 Proxy 

    可以理解成，在目标对象之前架设一层“拦截”，外界对该对象的访问，都必须先通过这层拦截，因此提供了一种机制，可以对外界的访问进行过滤和改写。Proxy 这个词的原意是代理，用在这里表示由它来“代理”某些操作，可以译为“代理器”。
    - `get(target, propKey, receiver)：`拦截对象属性的读取，比如proxy.foo和proxy['foo']。
    - `set(target, propKey, value, receiver)：`拦截对象属性的设置，比如proxy.foo = v或proxy['foo'] = v，返回一个布尔值。
    - `has(target, propKey)：`拦截propKey in proxy的操作，返回一个布尔值。
    - `deleteProperty(target, propKey)：`拦截delete proxy[propKey]的操作，返回一个布尔值。
    - `ownKeys(target)：`拦截Object.getOwnPropertyNames(proxy)、Object.getOwnPropertySymbols(proxy)、Object.keys(proxy)、for...in循环，返回一个数组。该方法返回目标对象所有自身的属性的属性名，而Object.keys()的返回结果仅包括目标对象自身的可遍历属性。
    - `getOwnPropertyDescriptor(target, propKey)：`拦截Object.getOwnPropertyDescriptor(proxy, propKey)，返回属性的描述对象。
    - `defineProperty(target, propKey, propDesc)：`拦截Object.defineProperty(proxy, propKey, propDesc）、Object.defineProperties(proxy, propDescs)，返回一个布尔值。
    - `preventExtensions(target)：`拦截Object.preventExtensions(proxy)，返回一个布尔值。
    - `getPrototypeOf(target)：`拦截Object.getPrototypeOf(proxy)，返回一个对象。
    - `isExtensible(target)：`拦截Object.isExtensible(proxy)，返回一个布尔值。
    - `setPrototypeOf(target, proto)：`拦截Object.setPrototypeOf(proxy, proto)，返回一个布尔值。如果目标对象是函数，那么还有两种额外操作可以拦截。
    - `apply(target, object, args)：`拦截 Proxy 实例作为函数调用的操作，比如proxy(...args)、proxy.call(object, ...args)、proxy.apply(...)。
    - `construct(target, args)`：拦截 Proxy 实例作为构造函数调用的操作，比如new proxy(...args)。
- Promise 对象
    Promise 是异步编程的一种解决方案，ES6 将其写进了语言标准，统一了用法，原生提供了Promise对象。Promise 提供统一的 API，各种异步操作都可以用同样的方法进行处理。有三种状态：pending（进行中）、fulfilled（已成功）和rejected（已失败）。如果改变已经发生了,就不会再变了，会一直保持这个结果。
    - `Promise.prototype.then() `它的作用是为 Promise 实例添加状态改变时的回调函数。then方法的第一个参数是resolved状态的回调函数，第二个参数（可选）是rejected状态的回调函数。
        ```js 
        getJSON("/posts.json").then(function(json) {
            return json.post;
        }).then(function(post) {
        // ...
        });
        ```
    - `Promise.prototype.catch() `用于指定发生错误时的回调函数。
        ```js
        getJSON('/posts.json').then(function(posts) {
        // ...
        }).catch(function(error) {
        // 处理 getJSON 和 前一个回调函数运行时发生的错误
        console.log('发生错误！', error);
        });
        ```
    - `Promise.prototype.finally()` 用于指定不管 Promise 对象最后状态如何，都会执行的操作。该方法是 `ES2018` 引入标准的。
        ```js
        promise
        .then(result => {···})
        .catch(error => {···})
        .finally(() => {···});
        ```
    - `Promise.all()` Promise.all方法用于将多个 Promise 实例，包装成一个新的 Promise 实例。
        ```js 
        const p = Promise.all([p1, p2, p3]);
        ```
    - `Promise.race` 方法同样是将多个 Promise 实例，包装成一个新的 Promise 实例。
        ```js
        //只要p1、p2、p3之中有一个实例率先改变状态，p的状态就跟着改变。那个率先改变的 Promise 实例的返回值，就传递给p的回调函数。
        const p = Promise.race([p1, p2, p3]);
        ```
    - `Promise.resolve()`有时需要将现有对象转为 Promise 对象，Promise.resolve方法就起到这个作用。
        ```js
        const jsPromise = Promise.resolve($.ajax('/whatever.json'));
        ```
    - Promise.reject() 方法也会返回一个新的 Promise 实例，该实例的状态为rejected。
- Generator 函数 和 async 函数 
    - generator 函数是 ES6 提供的一种异步编程解决方案
        - 执行 generator 函数返回的是一个遍历器对象, 也就是说, 我们可以使用 next 方法, 来遍历 generator 函数内部的每一个状态,
        - 既然 generator 函数内部具有多个状态, 那么总该有一个标识来决定函数在遍历过程中应该在哪里停下来, 所以我们需要 yield， for...of
    - ES2017 标准引入了 async 函数，使得异步操作变得更加方便。async 函数属于 ES7 的语法, 需要 Babel 或 regenerator 转码后才能使用，将next方法自动化了