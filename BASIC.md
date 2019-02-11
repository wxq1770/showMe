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
