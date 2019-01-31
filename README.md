# 前端开发配置记录

<br/>

## chrome相关插件列表

----

#### 前端页面对比设计图工具：

- [1px](https://chrome.google.com/webstore/detail/gebccnmciopflhcdihopmphapifkkfdh, "1px")

- [AlloyDesigner](https://chrome.google.com/webstore/detail/alloydesigner/ojooeaohlmgpcjajikhmibcnbebfenid, "AlloyDesigner")

- [Visual Inspector](https://chrome.google.com/webstore/detail/visual-inspector%E5%89%8D%E7%AB%AF%E9%87%8D%E6%9E%84%20%E8%A7%86%E8%A7%89%E8%B5%B0%E6%9F%A5/jgimcbonbekgeahallgcmiibdidjeeim, "Visual Inspector")

- [cssrem css转rem sublime 3插件](https://github.com/flashlizi/cssrem)


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
----
图片自动化压缩插件

- [imagemin-webpack-plugin](https://github.com/Klathmon/imagemin-webpack-plugin, "imagemin-webpack-plugin")


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

## gulp打包工具

- [gulp-cdn-replace gulp cdn 打包工具](https://github.com/JiangJie/gulp-cdn-replace, "gulp-cdn-replace gulp cdn 打包工具")


## 前端日志
----
- [badjs-report](https://github.com/BetterJS/badjs-report/blob/master/README.md, "badjs-report")


## 路径通配符

```
匹配package.josn 的name字段文件夹下的src文件夹下的所有以.js后缀名结尾的文件
src:['<%= pkg.name %>src/**/*.js']  

注意：
* 匹配任意数量任意字符,但不包括'/'
？只匹配一个字符,但不包括'/'
** 匹配任意数量任意字符,且包括'/'
{ } 匹配枚举文件;示例{main,app}.js,匹配main.js或app.js
! 不匹配后面的文件
```

## 前端组件

### lodash
Lodash 通过降低 array、number、objects、string 等等的使用难度从而让 JavaScript 变得更简单。
Lodash 的模块化方法 非常适用于：
[lodash](http://lodash.think2011.net/, "lodash")

- 遍历 array、object 和 string
- 对值进行操作和检测
- 创建符合功能的函数

### [lodash](http://lodash.think2011.net/, "lodash")


### vue-skeleton-webpack-plugin 骨架页面的组件












## nuxt.js vue服务器端渲染
----

### nuxt简介
#### 请求到渲染的流程

```
1，请求进入
2，服务器入口
3，中间件层
  3.1：NUXT.CONFIG.JS解析
  3.2：匹配样式
  3.3：匹配页面及子组件
4，验证页面及组件
5，异步获取数据及拉取数据
6，渲染
7，根据渲染中的NUXT-LINK标签再次跳转到第3部继续甄别。

```

#### 相关命令
```
// 启动服务器端渲染程序
nuxt

// 启动Spa模式
nuxt --spa 

// vue程序静态化命令，可以将每一个路由下的文件静态化为HTML文件
nuxt generate


```

#### vue-server-renderer 热加载及服务器渲染的开发服务器模块

<br/>
<br/>
<br/>

### 安装

#### create-nuxt-app 手脚架工具

```javascript
// npx 可以安装 create-nuxt-app 依赖包，并在创建项目后，将依赖包删除 
npx create-nuxt-app <项目名>

// 依赖选项
Koa
Vuetify
Spa
axios
Eslint
Prettier （如下注解）

// 启动开发环境
npm run dev

// 启动生产环境
npm run build
npm start
```

#### Prettier 代码格式化工具
- [Prettier](https://www.jianshu.com/p/d6a69eb08f07, "Prettier")

使用Prettier在code review时不需要再讨论代码样式,如果你已经在你的项目中使用ESLint并且想要只通过单独一条命令来执行你的所有的代码检查的话，你可以使用ESLint来为你运行Prettier。

```javascript
// eslint中集成prettier
//yarn add --dev prettier eslint-plugin-prettier
{
  "plugins": ["prettier"],
  "rules": {
    "prettier/prettier": "error"
  }
}

// 解决 eslint和prettier 格式规则重叠问题
//yarn add --dev eslint-config-prettier
{
  "extends": ["prettier"]
}

```

<br/>
<br/>
<br/>

### 目录结构

```javascript
- assets //资源目录用于组织未编译的静态资源如 LESS、SASS 或 JavaScript。

- components //组件目录，vue.js的组件，nuxt不会修改vue.js组件，不会有异步渲染方法的特性。

- layouts //布局目录，布局组件相关，目录不可更改

- middleware //中间件

- pages //页面目录，用于组织应用的路由及视图，nuxt.js读取目录下的.vue文件并自动生成路由配置，目录不可更改。不可更改。

- plugins //插件目录 根vue.js应用 实例化之前需要运行的javascript插件。不可更改。

- static //静态文件目录，目录下的文件会映射到根路径 / 下，不会被nuxt调用webapck做处理

- Store //用于组织VUEX状态树文件，NUXT集成了VUEX相关功能配置，在store目录下创建index.js可激活配置。不可更改。

- nuxt.config.js //用于组织Nuxt.js 应用的个性化配置，以便覆盖默认配置。

```

<br/>
<br/>
<br/>

### 别名 
提示: 在您的 vue 模板中, 如果你需要引入 assets 或者 static 目录, <BR/>使用 ~/assets/your_image.png 和 ~/static/your_image.png方式。
```javascript
~ 或 @  //src目录
~~ 或 @@ //根目录
```

<br/>
<br/>
<br/>

### 配置文件 nuxt.config.js 
可通过 nuxt.config.js 来覆盖默认的配置。不同环境下可以建立多个，属性描述如下
- [配置项相关细节](https://zh.nuxtjs.org/guide/configuration, "配置项相关细节")

```javascript
//Nuxt.js 允许你在自动生成的 vendor.bundle.js 文件中添加一些模块，以减少应用 bundle 的体积
//https://zh.nuxtjs.org/api/configuration-build
- build //扩展webapck的配置

- cache //该配置项让你开启组件缓存策略以提升渲染性能。

- css //该配置项用于定义应用的全局（所有页面均需引用的）样式文件、模块或第三方库。

- dev //该配置项用于配置 Nuxt.js 应用是开发还是生产模式。

- env //该配置项用于定义应用客户端和服务端的环境变量。

- generate //定义每个动态路由的参数，Nuxt.js 依据这些路由配置生成对应目录结构的静态文件。

- head //该配置项用于配置应用默认的meta标签。

- loading //该配置项用于个性化定制 Nuxt.js 使用的加载组件。

- modules //该配置项允许您将Nuxt模块添加到项目中。

- modulesDir //您定义Nuxt.js应用程序的node_modules文件夹。

- plugins //该配置项用于配置那些需要在 根vue.js应用 实例化之前需要运行的 Javascript 插件。

- rootDir //设置Nuxt.js 应用的根目录。

- router //该配置项可用于覆盖 Nuxt.js 默认的 vue-router 配置。

- srcDir //该配置项用于配置应用的源码目录路径。

- transition //该配置项用于个性化配置应用过渡效果属性的默认值。

```

<br/>
<br/>
<br/>

### 路由
Nuxt.js 依据 pages 目录结构自动生成 vue-router 模块的路由配置。
```javascript
//要在页面之间使用路由，我们建议使用<nuxt-link> 标签。
<template>
  <nuxt-link to="/">首页</nuxt-link>
</template>


基础路由
//假设 pages 的目录结构如下：
pages/
--| user/
-----| index.vue
-----| one.vue
--| index.vue

//那么，Nuxt.js 自动生成的路由配置如下：
router: {
  routes: [
    {
      name: 'index',
      path: '/',
      component: 'pages/index.vue'
    },
    {
      name: 'user',
      path: '/user',
      component: 'pages/user/index.vue'
    },
    {
      name: 'user-one',
      path: '/user/one',
      component: 'pages/user/one.vue'
    }
  ]
}



动态路由

//在 Nuxt.js 里面定义带参数的动态路由，需要创建对应的以下划线作为前缀的 Vue 文件 或 目录。

//你会发现名称为 users-id 的路由路径带有 :id? 参数，表示该路由是可选的。如果你想将它设置为必选的路由，需要在 users/_id 目录内创建一个 index.vue 文件。

pages/
--| users/
-----| _id.vue//可选参数路由
--| _slug //必选参数路由
-----| comments.vue
-----| index.vue


//Nuxt.js 生成对应的路由配置表为：
router: {
  routes: [
    {
      name: 'users-id',
      path: '/users/:id?', //可选参数路由
      component: 'pages/users/_id.vue'
    },
    {
      name: 'slug',
      path: '/:slug', //必选参数路由
      component: 'pages/_slug/index.vue'
    },
    {
      name: 'slug-comments',
      path: '/:slug/comments', //必选参数路由
      component: 'pages/_slug/comments.vue'
    }
  ]
}



路由参数校验
//Nuxt.js 可以让你在动态路由组件中定义参数校验方法。
// pages/users/_id.vue
export default {
  validate ({ params }) {
    // 必须是number类型
    //如果校验方法返回的值不为 true或Promise中resolve 解析为false或抛出Error ， Nuxt.js 将自动加载显示 404 错误页面或 500 错误页面。
    return /^\d+$/.test(params.id)
  }
}



嵌套路由
//创建内嵌子路由，你需要添加一个 Vue 文件，同时添加一个与该文件同名的目录用来存放子视图组件
//Warning: 别忘了在父组件(.vue文件) 内增加 <nuxt-child/> 用于显示子视图内容。
pages/
--| users/ //子视图组件
-----| _id.vue
-----| index.vue
--| users.vue //父级组件

//Nuxt.js 自动生成的路由配置如下：
router: {
  routes: [
    {
      path: '/users',
      component: 'pages/users.vue',//父级组件
      children: [
        {
          path: '',
          component: 'pages/users/index.vue',//子视图组件
          name: 'users'
        },
        {
          path: ':id',
          component: 'pages/users/_id.vue',//子属兔组件并且ID参数为可选参数
          name: 'users-id'
        }
      ]
    }
  ]
}



动态嵌套路由
//在动态路由下配置动态子路由~可以解决不同平台如微信公众号，app，wap端功能不同时的页面组件加载问题
pages/
--| _category/ //必选参数
-----| _subCategory/ //必选参数子集视图
--------| _id.vue   //可选参数子集子集的视图
--------| index.vue 
-----| _subCategory.vue //必选参数的子集父级视图
-----| index.vue
--| _category.vue //必选参数父级视图


router: {
  routes: [
    {
      path: '/:category',
      component: 'pages/_category.vue', //父级视图必选参数:
      children: [
        {
          path: '',
          component: 'pages/_category/index.vue',//子路由
          name: 'category'
        },
        {
          path: ':subCategory',
          component: 'pages/_category/_subCategory.vue',//子路由的父级路由比选参数:subCategory
          children: [
            {
              path: '',
              component: 'pages/_category/_subCategory/index.vue',//子子路由
              name: 'category-subCategory'
            },
            {
              path: ':id',
              component: 'pages/_category/_subCategory/_id.vue',//子子路由可选参数
              name: 'category-subCategory-id'
            }
          ]
        }
      ]
    }
  ]
}




SPA fallback
//为动态路由启动SPA fallback，在spa模式下NUXT.JS将输出一个与index.html相同的额外的文件，如果没有文件匹配，大多数静态托管服务可配置为使用spa模板，




过渡动效
//Nuxt.js 使用 Vue.js 的<transition>组件来实现路由切换时的过渡动效。
提示 :Nuxt.js 默认使用的过渡效果名称为 page
//如果想让每一个页面的切换都有淡出 (fade) 效果，我们需要创建一个所有路由共用的 CSS 文件。所以我们可以在 assets/ 目录下创建这个文件：

//在全局样式文件 assets/main.css 里添加一下样式：

.page-enter-active, .page-leave-active {
  transition: opacity .5s;
}
.page-enter, .page-leave-active {
  opacity: 0;
}

//然后添加到 nuxt.config.js 文件中：
module.exports = {
  css: [
    'assets/main.css'
  ]
}

// 如果想给某个页面自定义过渡特效的话，只要在该页面组件中配置 transition 字段即可：

// 在全局样式 assets/main.css 中添加一下内容：
.test-enter-active, .test-leave-active {
  transition: opacity .5s;
}
.test-enter, .test-leave-active {
  opacity: 0;
}

//然后我们将页面组件中的 transition 属性的值设置为 test 即可：
export default {
  transition: 'test'
}





中间件
// 自定义函数运行在一个或者一组页面渲染之前
放置在 middleware/ 目录。 文件名的名称将成为中间件名称(middleware/auth.js将成为 auth 中间件)。一个中间件将接收context作为第一个参数
// 更多中间件栗子：https://github.com/nuxt/example-auth0

执行顺序
1.nuxt.config.js
2.匹配布局
3.匹配页面

// 如下中间件操作
export default function (context) {
  context.userAgent = process.server ? context.req.headers['user-agent'] : navigator.userAgent
}


//中间件可以异步执行,只需要返回一个 Promise 或使用第2个 callback 作为第一个参数：
// Promise栗子
import axios from 'axios'
export default function ({ route }) {
  return axios.post('http://my-stats-api.com', {
    url: route.fullPath
  })
}

// 然后在你的 nuxt.config.js 、 layouts 或者 pages 中使用中间件:
// nuxt.config.js stats 中间件将在每个路由改变时被调用。
module.exports = {
  router: {
    middleware: 'stats'
  }
}


```
<br/>
<br/>
<br/>


### 视图
本章节的内容阐述了如何在 Nuxt.js 应用中为指定的路由配置数据和视图，包括应用模板、页面、布局和HTML头部等内容。

#### 模板
应用模板，订制化默认html模板，应用根目录下创建一个 app.html 的文件。
```html
<!DOCTYPE html>
<!--[if IE 9]><html lang="en-US" class="lt-ie9 ie9" {{ HTML_ATTRS }}><![endif]-->
<!--[if (gt IE 9)|!(IE)]><!--><html {{ HTML_ATTRS }}><!--<![endif]-->
  <head>
    {{ HEAD }}
  </head>
  <body {{ BODY_ATTRS }}>
    {{ APP }}
  </body>
</html>
```
<br/>
<br/>

#### 布局
Nuxt.js 允许你扩展默认的布局，或在 layout 目录下创建自定义的布局。

<br/>
<br/>

#### 默认布局
可通过添加 layouts/default.vue 文件来扩展应用的默认布局。

别忘了在布局文件中添加 <nuxt/> 组件用于显示页面的主体内容。

默认布局的源码如下：
```html
<template>
  <nuxt/>
</template>
```

<br/>
<br/>

#### 错误页面
你可以通过编辑 layouts/error.vue 文件来定制化错误页面.

这个布局文件不需要包含 <nuxt/> 标签。你可以把这个布局文件当成是显示应用错误（404，500等）的组件。

```javascript
举一个个性化错误页面的例子 layouts/error.vue:
<template>
  <div class="container">
    <h1 v-if="error.statusCode === 404">页面不存在</h1>
    <h1 v-else>应用发生错误异常</h1>
    <nuxt-link to="/">首 页</nuxt-link>
  </div>
</template>

<script>
export default {
  props: ['error'],
  layout: 'blog' // 你可以为错误页面指定自定义的布局
}
</script>
```
<br/>
<br/>

#### 个性化布局
layouts 根目录下的所有文件都属于个性化布局文件，可以在页面组件中利用 layout 属性来引用。

请确保在布局文件里面增加 <nuxt/> 组件用于显示页面非布局内容。

```html
举个例子 layouts/blog.vue:
<template>
  <div>
    <div>这里是博客导航</div>
    <nuxt/>
  </div>
</template>

在 pages/posts.vue 里， 可以指定页面组件使用 blog 布局。
<script>
export default {
  layout: 'blog'
}
</script>
```

<br/>
<br/>

#### 页面
页面组件就是vue组件，nuxt.js为这些组件添加了配置项，以便开发通用应用

```javascript
//Nuxt.js 为页面提供的特殊配置项：如下
asyncData	//最重要的一个键, 支持 异步数据处理，另外该方法的第一个参数为当前页面组件的 上下文对象。
fetch	//与 asyncData 方法类似，用于在渲染页面之前获取数据填充应用的状态树（store）。不同的是 fetch 方法不会设置组件的数据。详情请参考 关于fetch方法的文档。
head	//配置当前页面的 Meta 标签, 详情参考 页面头部配置API。
layout	//指定当前页面使用的布局（layouts 根目录下的布局文件）。详情请参考 关于 布局 的文档。
loading	//如果设置为false，则阻止页面自动调用this.$nuxt.$loading.finish()和this.$nuxt.$loading.start(),您可以手动控制它,请看例子,仅适用于在nuxt.config.js中设置loading的情况下。请参考API配置 loading 文档。
transition	//指定页面切换的过渡动效, 详情请参考 页面过渡动效。
scrollToTop	//布尔值，默认: false。 用于判定渲染页面前是否需要将当前页面滚动至顶部。这个配置用于 嵌套路由的应用场景。
validate	//校验方法用于校验 动态路由的参数。
middleware	//指定页面的中间件，中间件会在页面渲染之前被调用， 请参考 路由中间件。
```

```html
<template>
  <h1 class="red">Hello {{ name }}!</h1>
</template>

<script>
export default {
  asyncData (context) {
    // 每次在加载组件之前调用
    return { name: 'World' }
  },
  fetch () {
    // fetch方法用于在呈现页面之前填充存储
  },
  head () {
    // 为这个页面设置元标记
  },
  // and more functionality to discover
  ...
}
</script>

<style>
.red {
  color: red;
}
</style>
```
<br/>
<br/>

#### html头部
nuxt.js使用了vue-meta更新应用的头部标签和html标签属性
```JAVA
//配置vue-meta
{
  keyName: 'head', // 设置 meta 信息的组件对象的字段，vue-meta 会根据这 key 值获取 meta 信息
  attribute: 'n-head', // vue-meta 在监听标签时所添加的属性名
  ssrAttribute: 'n-head-ssr', // 让 vue-meta 获知 meta 信息已完成服务端渲染的属性名
  tagIDKeyName: 'hid' // 让 vue-meta 用来决定是否覆盖还是追加 tag 的属性名
}
```


<br/>
<br/>

#### 默认 Meta 标签
在nuxt.config.js中定义所有默认的meta标签。

```javascript
//一个使用自定义 viewport 和 谷歌字体 的配置示例：
head: {
  meta: [
    { charset: 'utf-8' },
    { name: 'viewport', content: 'width=device-width, initial-scale=1' }
  ],
  link: [
    { rel: 'stylesheet', href: 'https://fonts.googleapis.com/css?family=Roboto' }
  ]
}
```


<br>
<br>

#### 个性化特定页面的 Meta 标签
```
关于个性化特定页面的 Meta 标签，请参考 页面头部配置API。

注意：为了避免子组件中的meta标签不能正确覆盖父组件中相同的标签而产生重复的现象，建议利用 hid 键为meta标签配一个唯一的标识编号。请阅读关于 vue-meta 的更多信息。
```


<br>
<br>

### 异步数据
Nuxt.js 扩展了 Vue.js，增加了一个叫 asyncData 的方法，使得我们可以在设置组件的数据之前能异步获取或处理数据。

#### asyncData 方法
将在页面组件加载前调用，会在服务端或者路由更新前被调用，第一个参数为上下文对象，利用asyncData方法来获取数据，nuxt.js会将asyncData返回的数据融合组件data方法返回的数据，一并返回给当前组件。
```java
asyncData方法是在组件初始化前调用的，所以方法是没办法通过this来获取组件实例对象的

//使用方法
1.返回一个promise，待promise解析后才会设置组件数据，然后渲染组件
2.使用async或await
3.为第二个参数指定回调函数，//该回调函数需符合通用的 NodeJs 回调函数的形式: callback(err, data)
我们使用 axios 重构 HTTP 请求, 我们 强烈建议您 使用 axios 模块 用于您的Nuxt项目中。



//栗子Promise
export default {
  asyncData ({ params }) {
    return axios.get(`https://my-api/posts/${params.id}`)
    .then((res) => {
      return { title: res.data.title }
    })
  }
}

//使用 async或await
export default {
  async asyncData ({ params }) {
    let { data } = await axios.get(`https://my-api/posts/${params.id}`)
    return { title: data.title }
  }
}

//使用回调函数
export default {
  asyncData ({ params }, callback) {
    axios.get(`https://my-api/posts/${params.id}`)
    .then((res) => {
      callback(null, { title: res.data.title }) //该回调函数需符合通用的 NodeJs 回调函数的形式: callback(err, data)
    })
  }
}

//静态默认方式
export default {
  data () {
    return { foo: 'bar' }
  }
}

```

```HTML
//数据的展示
//asyncData 方法返回的数据在融合 data 方法返回的数据后，一并返回给模板进行展示，如：
<template>
  <h1>{{ title }}</h1>
</template>
```
<br>
<br>

#### 上下文对象
可通过 API context 来了解该对象的所有属性和方法。

```javascript
//在服务器端调用asyncData时，您可以访问用户请求的req和res对象。
export default {
  async asyncData ({ req, res }) {
    // 请检查您是否在服务器端
    // 使用 req 和 res
    if (process.server) {
     return { host: req.headers.host }
    }

    return {}
  }
}
```

#### 访问动态路由数据
```java
您可以使用注入 asyncData 属性的 context 对象来访问动态路由数据。例如，可以使用配置它的文件或文件夹的名称访问动态路径参数。所以，如果你定义一个名为 _slug.vue 的文件，您可以通过 context.params.slug 来访问它。

export default {
  async asyncData ({ params }) {
    const slug = params.slug // When calling /abc the slug will be "abc"
    return { slug }
  }
}
```



#### 监听 query 参数改变
```
默认情况下，query的改变不会调用asyncData方法。如果要监听这个行为，例如，在构建分页组件时，您可以设置应通过页面组件的watchQuery属性监听参数。了解更多有关API watchQuery的信息。
```


#### 错误处理
nuxt.js的上下文对象 context 中提供了一个 error的方法 
```java
//Nuxt.js 在上下文对象context中提供了一个 error(params) 方法，你可以通过调用该方法来显示错误信息页面。params.statusCode 可用于指定服务端返回的请求状态码。
export default {
  asyncData ({ params, error }) {
    return axios.get(`https://my-api/posts/${params.id}`)
    .then((res) => {
      return { title: res.data.title }
    })
    .catch((e) => {
      error({ statusCode: 404, message: 'Post not found' })
    })
  }
}
```

有一个值得注意的问题是，如果我们在另外一个页面内也引用了 axios，那么在应用打包发布的时候 axios 会被打包两次，而实际上我们只需要打包一次。这个问题可以通过在 nuxt.config.js 里面配置 build.vendor 来解决：

```JAVA
//经过如下的配置后，我们可以在任何页面里面引入 axios 而不用担心它会被重复打包。
module.exports = {
  build: {
    vendor: ['axios']
  }
}
```

<br>
<br>
<br>

## docker
----

### docker命令
- docker build 创建镜像 
```javascript
// -t 指定创建镜像后的名字和标签 name:tag 
// -f 指定要使用的Dockerfile路径；
// . 当前目录
docker build -t egg-nuxt/node:v1 -f Dockerfile .

// 将代码直接copy到容器中
docker cp ~/myproject/. container_name:/home/myname/myproject

//将代码挂在到容器目录下
docker run -v /mnt/temp/myproject/:/home/myname/myproject ...

```