# 2019年计划
## vue重构 + ssr
-   [pwa教程](https://lavas.baidu.com/pwa)

    W3C 组织早在 2014 年 5 月就提出过 Service Worker 这样的一个 HTML5 API ，主要用来做持久的离线缓存。

    - `Service Worker` 是用 JavaScript 编写的 JS 文件，能够代理请求，并且能够操作浏览器缓存，通过将缓存的内容直接返回，让请求能够瞬间完成。开发者可以预存储关键文件，可以淘汰过期的文件等等，给用户提供可靠的体验。
        - 第一步，应该是安全，将全站 HTTPS 化，因为这是 PWA 的基础，没有 HTTPS，就没有 Service Worker
        - 第二步，应该是 Service Worker 来提升基础性能，离线提供静态文件，把用户首屏体验提升上来
        - 第三步，App Manifest，这一步可以和第二步同时进行
        后续，再考虑其他的特性，离线消息推送等


## 面试题
## 业务需求支持
## 会议记录、 知识库记录
## 前后端开发流程梳理
## 开发环境不断优化 docker 的运用

## 技术插件收藏

- [PDF预览](http://www.gjtool.cn/pdfh5/) 
    - 条件是上传的PDF命名必须是英文不能有中文。否则会报错
    - 文件大小5MB以内吧，我这插件自带的PDF文件 1.3Mb 23页。
    - 还有就是在模板页打开pdf了。因为将PDF转为image base64格式展，比较耗时间和性能。反复在dom操作中插入节点微信的webview会卡死。
    ```js
    var pdfh52 = new Pdfh5('.pdfjs2',{
        pdfurl: 'test.pdf'
    });
    
    // pdfh5.zoomChange 
    // pdfh5.renderPages 
    // pdfh5.renderEnd 
    // pdfh5.scroll 
    // pdfh5.show 
    // pdfh5.hide
    // pdfh5还有pdfh5开始初始化、pdfh5加载完成、PDF加载失败、PDF加载成功事件：   
    // pdfh5.start 
    // pdfh5.complete 
    // pdfh5.error 
    // pdfh5.success 
    // pdfh5还有还原事件、销毁事件（附带回调函数）：  
    // pdfh5.reset 
    // pdfh5.destroy 
    // pdfh5还有静态参数： 
    // pdf最外层div pdfh5.container
    // pdf第二层div pdfh5.viewerContainer
    // 所有包裹pdf的div的父div pdfh5.viewer
    // 所有包裹pdf的div pdfh5.pages
    // pdf加载完成状态 pdfh5.pdfLoaded
    // pdf总页数 pdfh5.totalNum
    // pdf当前页数 pdfh5.currentNum
    // pdfh5初始化的时间戳 pdfh5.initTime
    // pdfh5开始渲染距离初始化多少毫秒 pdfh5.startTime
    // pdfh5渲染完毕距离初始化多少毫秒  pdfh5.endTime
    // pdfh5渲染过程中时间戳   pdfh5.renderTime
    // pdfh5支持在线预览 http://www.gjtool.cn/pdfh5/pdf.html?file=http://xxx.xxx.xxx/xxx.pdf
    // 新增配置参数scrollEnable:false不允许pdf滚动,true允许pdf滚动
    var pdfh5 = new Pdfh5('.pdfjs', {
        scrollEnable:false,//是否允许pdf滚动
        pdfurl: url
    });
    // 新增方法pdfh5.scrollEnable(true)允许pdf滚动,pdfh5.scrollEnable(false)不允许pdf滚动
    // 新增on方法,监听各种事件
    pdfh5.on("start",function(str){
        console.log(str)
    })
    pdfh5.on("complete",function(str){
        pdfh5.scrollEnable(true)
    })

    ```

- [anime动画插件](https://github.com/juliangarnier/anime) [官网](https://animejs.com/)  [文档](https://animejs.com/documentation/#cssProperties)

