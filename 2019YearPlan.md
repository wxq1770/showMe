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
