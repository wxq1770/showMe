
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

- CSS选择符有哪些？哪些属性可以继承？优先级算法如何计算？内联和important哪个优先级高？
    - 标签选择符 类选择符 id选择符
    - 继承不如指定
    - Id > class > 标签选择
    - important 优先级高
    ```css
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

- 清除浮动的几种方式，各自的优缺点
    - 使用空标签清除浮动 **clear:both**（*理论上能清楚任何标签，增加无意义的标签*）
    - 使用 **overflow:auto**（*空标签元素清除浮动而不得不增加无意代码的弊端,,使用zoom:1用于兼容IE*）
    - 是用 **afert** 伪元素清除浮动（*用于非IE浏览器*）
        ```css
        .clear{
            clear:both;
            height:0;
            overflow:hidden;
        }
        .clearfix:after{
            content:".";
            display:block;
            height:0;
            clear:both;
            visibility:hidden
        }
        .clearfix{
            *+height:1%;
        }
        .clearfix {
            overflow: auto;
            zoom: 1;
        }
        ```

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
- 列出 **display** 的值，说明他们的作用。
    1. **block** 象块类型元素一样显示
    2. **none** 缺省值
    3. **inline-block** 象行内元素一样显示,但其内容象块类型元素一样显示
    4. **list-item** 象块类型元素一样显示，并添加样式列表标记。

- **position** 的值， **relative** 和 **absolute**、 **fixed**、**static** 定位原点是？
    - **absolute**　生成绝对定位的元素，相对于 static 定位以外的第一个父元素进行定位。
    - **relative** 生成相对定位的元素，相对于其正常位置进行定位。
    - **fixed** （老IE不支持） 生成绝对定位的元素，相对于浏览器窗口进行定位。
    - **static** 默认值。没有定位，元素出现在正常的流中 * （忽略 top, bottom, left, right z-index 声明）。
    - **inherit** 规定从父元素继承 position 属性的值。

- CSS3有哪些新特性？
    ```css
    CSS3实现圆角
    border-radius:8px

    阴影
    box-shadow:10px

    对文字加特效 
    text-shadow

    线性渐变
    gradient

    旋转
    transform 
    transform:rotate(9deg) scale(0.85,0.90)
    translate(0px,-30px) skew(-9deg,0deg);

    旋转,缩放,定位,倾斜 
    增加了更多的CSS选择器 多背景 rgba

    ```
- 描述css reset的作用和用途。

    Reset重置浏览器的css默认属性 浏览器的品种不同，样式不同，然后重置，让他们统一

- 解释css sprites，如何使用。

    Css 精灵 把一堆小的图片整合到一张大的图片上，减轻服务器对图片的请求数量
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

## 技术展望与工作流

#### HTML
- PWA之离线缓存 Service Worker
#### CSS
#### JAVASCRIPT
#### 浏览器
