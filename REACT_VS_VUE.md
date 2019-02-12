# react VS vue

本文记录react vue技术相关功能，以及使用差异、性能测试等调研文档

- [vue 星数 126k](https://eggjs.org/zh-cn/intro/quickstart.html) 

- [react 星数 120k](https://zh.nuxtjs.org/guide/installation)

## 手脚架工具地址

- [vue cli 2.0-手脚架工具](https://www.jeffjade.com/2018/05/20/140-vue-webpack-boilerplate-template/) 
[vue cli 2.0-github地址 ](https://github.com/nicejade/vue-boilerplate-template) 

- [vue cli 3.0-手脚架工具](https://github.com/nicejade/awesome-vue-cli3-example) 
[vue cli 3.0-github地址 ](https://vue-cli3.lovejade.cn/) 



## 项目功能扩展及插件和使用效果要求
- i18n
- vuex Redux
- router
- less sass
- webpack 打包 cdn添加
- mocker 测试数据的编写
- test 自动化测试
- 前端监控log
- 代码注释
- es6支持情况
- 开发环境、测试环境、线上环境
- ssr
- prop-types 或者 typescript应用扩展配置方案
- lodash
- axios 或其它支持nodejs端和前端的ajax组件

- 生命周期
- 数据双向绑定方法方式 增删改
- 父子兄弟组件传值
- vuex Redux 赋值 取值 渲染 过滤
- router 验证过滤 路由模式
- 虚拟dom性能对比
- 开发目录 css js 组件 应用等层级目录划分
- cli 手脚架工具创建 vue cli 3.0  添加依赖组件方式

## 问题和ssr和spa结合使用方案。后端node 框架选型。
- 方案一：vue2.0、vue cli 3、nuxt、egg

----

<br>

## awesome-vue-cli3项目手脚架分析
### 命令行
```javascript
//打开开发环境 如下是可配置参数
npm run serve || npm run start || yarn start

`--open`    //在服务器启动时打开浏览器
`--copy`    //在服务器启动时将 URL 复制到剪切版
`--mode`    //指定环境模式 (默认值：development)
`--host`    //指定 host (默认值：0.0.0.0)
`--port`    //指定 port (默认值：8080)
`--https`   //使用 https (默认值：false)

//打包 如下可配置参数
npm run build

`--mode`        //指定环境模式 (默认值：production)
`--dest`        //指定输出目录 (默认值：dist)
`--modern`      //面向现代浏览器不带自动回退地构建应用,使用现代模式构建应用，为现代浏览器交付原生支持的 ES2015 代码，并生成一个兼容老浏览器的包用来自动回退。
`--target`      //app | lib | wc | wc-async (默认值：app)
`--name`        //库或 Web Components 模式下的名字 (默认值：package.json 中的 "name" 字段或入口文件名)
`--no-clean`    //在构建项目之前不清除目标目录
`--report`      //生成 report.html 以帮助分析包内容
`--report-json` //生成 report.json 以帮助分析包内容
`--watch`       //监听文件变化

//lint 检查代码格式
npm run lint

//修复代码格式
npm run eslint-fix

//格式化代码结构
npm run format-code

//build包构建结构分析
npm run analyz

//打包配置部署命令 打包加git推送
npm run deploy

//清空所有提交信息！危险操作。不知道用途是啥
npm run clear-commit-msg

//预览打包后静态文件
npm run preview

//自动化测试检查,
npm run test:unit

```

### webapck引用插件分析
- prerender-spa-plugin 预渲染 通过预编译器将指定路由组件生成静态文件，引用对应组件的样式和js。

    缺点
    - 不适用与路由太多的页面，会导致构建build的过程，等待的时间是超长
    - 对于一些经常发生变化的页面，如体育比赛等，会导致编译后的数据不是实时更新的
    - 不同的用户看都会不同的页面，这种类型的页面不适用预渲染

    注意
    - 如果没有对应路由或者拼写错误的话，build也会报错
    - webpack中配置的route需要与router一直，注意/符号
    - 需要注意Apache等配置，如果访问static的静态文件，都是统一访问到dist/static/目录下的，而不是dist/about/static这种


### 目录结构
```javascript
├── .circleci       //docker配置文件夹
│   └── config.yml  //docker-compose 容器依赖文件
├── .env            //环境变量
├── .git            //git文件
├── .gitignore      //git排除文件
├── README.md       //简介
├── commands        //脚本文件夹
│   ├── clear-commit-msg.sh     //删除所有提交信息脚本，
│   ├── deploy.sh               //打包后提交添加变更提交build后代码
│   └── preview.js              //启动express服务器预览打包后文件
├── dist            //打包后文件夹
├── jest.config.js  //单元测试配置文件
├── package.json    //依赖文件
├── public          //静态文件chunk入口
│   ├── favicon.ico //页面图标
│   ├── img         //pwa应用的图片
│   ├── index.html  //chunk入口文件
│   ├── manifest.json   //pwa入口文件
│   ├── robots.txt
│   └── service-worker.js   //pwa js文件
├── src         //程序主代码
│   ├── App.vue     //vue根文件
│   ├── assets      //静态资源
│   │   ├── icons   //icon
│   │   ├── images  //图片
│   │   └── styles  //样式
│   │       ├── common.scss     //全局样式
│   │       ├── element.scss    //饿了么样式
│   │       ├── mixins.scss     //混合样式 可配置参数
│   │       ├── style.scss      //统一加载
│   │       └── variables.scss  //变量样式
│   ├── components  //组件
│   │   ├── Advertisement.vue   //底部广告组件
│   │   ├── EditDialog.vue
│   │   ├── Icon.vue            //icon父组件
│   │   ├── Instruction.vue     //主内容区域，应用了marked markdown语法转样式
│   │   ├── icons   //图标组件文件夹
│   │   │   └── Arrow.vue       //图标组件 可以做图标样式切换等状态交互
│   │   └── markdown //markdown组件 
│   │       ├── Index.vue  //组件入口父级 有i18n国际化应用
│   │       ├── MarkdownPreview.vue     //绘制marked 语法
│   │       └── markdown.css   //组件css
│   ├── filters.js      //转值过滤等场景用的文件
│   ├── global.js       //全局方法的加载 包含helper文件夹下的方法，filters.js中的方法。还有其它全局性vue组件的注册，ElementUI、Markdown、VueMeta、Icon、Arrow
│   ├── helper          //扩展 api utils pluns等extends 等全局组件应用
│   │   ├── apis        //
│   │   │   └── index.js    //提取各组件下的非index.js文件的default modules
│   │   ├── ajax.js     //应用axios 全局设定ajax get post
│   │   ├── auth.js     //获取isLogin cookie 
│   │   ├── document.js //dom操作交互实现方法
│   │   ├── index.js    //导出各种全局设定方法
│   │   ├── lodash.js   //lodash相关数据结构的功能
│   │   └── utils.js    //程序公共功能文件
│   ├── i18n.js     //国际化方案
│   ├── locales     //国家化文件夹
│   │   └── en.json     //中文json文件
│   ├── main.js     //vue创建对象文件 导入了全局设置、vuex、国际化 
│   ├── mixins      //混合变量文件夹
│   │   └── metaMixin.js    //html vue-meta组件配置项
│   ├── pages   //页面文件夹
│   │   ├── ExploreMore.vue
│   │   ├── Homepage.vue    //首页
│   │   └── partials        //404等页面文件夹
│   │       └── NotFound.vue    //404页面
│   ├── registerServiceWorker.js    //启动程序生命周期
│   ├── router  //前端路由
│   │   ├── beforeEachHooks.js  //路由前置检查
│   │   ├── commonRoutes.js     //路由配置项
│   │   ├── index.js            //路由首页 history模式 并挂在路由前置检查功能
│   │   └── routes              //路由配置
│   │       ├── index.js        //遍历非index.js文件
│   │       └── main.js         //不太明白
│   └── store   //VUEX
│       ├── index.js            //创建vue对象
│       └── modules             //多模块vuex分类
│           ├── demo            //测试vuex功能
│           │   ├── actions.js  //触发过滤修改mutations方法
│           │   ├── getters.js  //获取state值
│           │   ├── index.js    //初始化当前模块vuex数据
│           │   └── mutations.js //注册修改state值
│           └── index.js        //遍历非index.js文件
├── tests
│   ├── coverage //生成测试报告
│   └── unit     //测试断言编写
│       ├── .eslintrc.js    //eslint配置
│       └── Arrow.spec.js   //Arrow.vue文件组件的断言编写
├── vue.config.js   //webapck配置，跨域、国际化、pwa
└── yarn.lock   //安装依赖
```

