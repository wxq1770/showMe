
# 前端面试题

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
#### 浏览器
- 常见的浏览器内核有哪些？
    ```
    Trident 内核：IE,MaxThon,TT,The World,360,搜狗浏览器等。[又称 MSHTML]

    Gecko 内核：Netscape6 及以上版本，FF,MozillaSuite/SeaMonkey 等

    Presto 内核：Opera7 及以上。 [Opera 内核原为：Presto，现为：Blink;]

    Webkit 内核：Safari,Chrome 等。 [ Chrome 的：Blink（WebKit 的分支）]
    ```
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

#### 浏览器

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

<br/>

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
#### 浏览器
