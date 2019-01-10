# 前端开发配置记录

<br/>

## chrome相关插件列表

----

#### 前端页面对比设计图工具：

- [1px](https://chrome.google.com/webstore/detail/gebccnmciopflhcdihopmphapifkkfdh, "1px")

- [AlloyDesigner](https://chrome.google.com/webstore/detail/alloydesigner/ojooeaohlmgpcjajikhmibcnbebfenid, "AlloyDesigner")

- [Visual Inspector](https://chrome.google.com/webstore/detail/visual-inspector%E5%89%8D%E7%AB%AF%E9%87%8D%E6%9E%84%20%E8%A7%86%E8%A7%89%E8%B5%B0%E6%9F%A5/jgimcbonbekgeahallgcmiibdidjeeim, "Visual Inspector")

#### 接口测试工具：

- [Postman](https://chrome.google.com/webstore/detail/postman/fhbjgbiflinjbdggehcddcbncdddomop, "Postman")

- [ApiDebug](https://chrome.google.com/webstore/detail/apidebug-%E6%8E%A5%E5%8F%A3%E8%B0%83%E8%AF%95%E6%8F%92%E4%BB%B6/ieoejemkppmjcdfbnfphhpbfmallhfnc, "ApiDebug")

- [Tabbed Postman](https://chrome.google.com/webstore/detail/tabbed-postman-rest-clien/coohjcphdfgbiolnekdpbcijmhambjff, "Tabbed Postman ")

- [Advanced REST client](https://chrome.google.com/webstore/detail/advanced-rest-client/hgmloofddffdnphfgcellkdfbfbjeloo, "Advanced REST client")

- [Web Server for Chrome 模拟本地静态文件插件](https://chrome.google.com/webstore/detail/web-server-for-chrome/ofhbbkphhbklhfoeikjpcbhemlocgigb, "Web Server for Chrome")

#### 数据转换工具

- [二维码(QR码)生成器](https://chrome.google.com/webstore/detail/%E4%BA%8C%E7%BB%B4%E7%A0%81qr%E7%A0%81%E7%94%9F%E6%88%90%E5%99%A8qr-code-generato/pflgjjogbmmcmfhfcnlohagkablhbpmg, "二维码(QR码)生成器")

- [Smeagol的二维码插件](https://chrome.google.com/webstore/detail/%E4%BA%8C%E7%BB%B4%E7%A0%81qr%E7%A0%81%E7%94%9F%E6%88%90%E5%99%A8qr-code-generato/pflgjjogbmmcmfhfcnlohagkablhbpmg, "Smeagol的二维码插件")

- [WEB前端助手(FeHelper)](https://chrome.google.com/webstore/detail/web%E5%89%8D%E7%AB%AF%E5%8A%A9%E6%89%8Bfehelper/pkgccpejnmalmdinmhkkfafefagiiiad?hl=zh-CN, "WEB前端助手(FeHelper)")

- [工具喵 - Unix时间戳、URL编码/解码、IP地址查询、MD5加密、BASE64编码/解码、随机字符串](https://chrome.google.com/webstore/detail/%E5%B7%A5%E5%85%B7%E5%96%B5/coppgeobilocdhiclhgmadabblhfjgpm, "工具喵")

- [JSON Editor](https://chrome.google.com/webstore/detail/json-editor/lhkmoheomjbkfloacpgllgjcamhihfaj, "JSON Editor")


#### 图片压缩网址


- [tinypng.com](https://tinypng.com/, "tinypng.com")

- [智图](https://tinypng.com/, "智图")


#### 图标网站


- [bootcss](http://www.bootcss.com/p/font-awesome/, "bootcss")


#### markdown 语法：
- [markdown](http://xianbai.me/learn-md/article/syntax/paragraphs-and-line-breaks.html, "markdown")

<br/>

## webpack打包工具列表

---

图片自动化压缩插件


```javascript
//引入插件
var ImageminPlugin = require('imagemin-webpack-plugin').default;

//配置
plugins: [
    new ImageminPlugin({
      disable: process.env.NODE_ENV !== 'production', // 开发时不启用
      pngquant: {//图片质量
        quality: '95-100'
      }
    })
]
```

- [imagemin-webpack-plugin](https://github.com/Klathmon/imagemin-webpack-plugin, "imagemin-webpack-plugin")

