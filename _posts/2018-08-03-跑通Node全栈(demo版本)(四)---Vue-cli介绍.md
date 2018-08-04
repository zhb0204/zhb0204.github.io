---
layout: post
title: "跑通Node全栈(demo版本)(四)---Vue-cli介绍"
date: 2018-8-03 
description: "跑通Node全栈(demo版本)(四)---Vue-cli介绍"
tag: Vue
---   
   
  前面我们已经跟大家一起打通了后台express的结构逻辑,本章我们将和大家一起学习使用Vue作为前端向后端发起请求。

### 1.准备阶段

* 首先我们使用vue-cli指令创建一个vuepage文件夹,并补齐依赖(文件夹与studentM同级),指令如下

  ```
    vue init webpack vuepage
    cd  vue  vuepage
    cnpm  install
  ```

  ![](/images/posts/vue/11.png)

### 2.vue-cli目录结构

* 一个vue-cli的项目结构如下，其中src文件夹是需要掌握的，所以本文也重点讲解其中的文件，至于其他相关文件，了解一下即可。

  ![](/images/posts/vue/21.png)

### 3.vue-cli目录结构细分

* (1).build——[webpack配置]

  build文件主要是webpack的配置，主要启动文件是dev-server.js，当我们输入npm run dev首先启动的就是dev-server.js，它会去检查node及npm版本，加载配置文件，启动服务。

  ![](/images/posts/vue/22.png)

* (2)config——[vue项目配置]

  config文件主要是项目相关配置，我们常用的就是当端口冲突时配置监听端口，打包输出路径及命名等

  ![](/images/posts/vue/23.png)

* (3)node_modules——[依赖包]

  node_modules里面是项目依赖包，其中包括很多基础依赖，自己也可以根据需要安装其他依赖。安装方法为打开cmd，进入项目目录，输入npm install [依赖包名称],回车。

在两种情况下我们会自己去安装依赖：

  ①项目运行缺少该依赖包：例如项目加载外部css会用到的css-loader，路由跳转vue-loader等（安装方法示例：npm install css-loader）

  ②安装插件：如vux（基于WEUI的移动端组件库），vue-swiper（轮播插件

  注：有时会安装指定依赖版本，需在依赖包名称后加上版本号信息，如安装11.1.4版本的vue-loader，输入npm install vue-loader@11.1.4

* (4)src——[项目核心文件]

  项目核心文件前面已经进行了简单的说明，接下来重点讲解main.js，App.vue,及router的index.js

* (5)index.html——[主页] 

  index.html如其他html一样，但一般只定义一个空的根节点，在main.js里面定义的实例将挂载在根节点下，内容都通过vue组件来填充

  ![](/images/posts/vue/24.png)

* (6)App.vue——[根组件] 

  一个vue页面通常由三部分组成:模板(template)、js(script)、样式(style)

  ![](/images/posts/vue/25.png)

  【template】

  其中模板只能包含一个父节点，也就是说顶层的div只能有一个（例如下图，父节点为#app的div，其没有兄弟节点）

  <router-view></router-view>是子路由视图，后面的路由页面都显示在此处

  打一个比喻吧,<router-view>类似于一个插槽，跳转某个路由时，该路由下的页面就插在这个插槽中渲染显示

  【script】

  vue通常用es6来写，用export default导出，其下面可以包含数据data，生命周期(mounted等)，方法(methods)等，具体语法请看vue.js文档，在后面我也会通过例子来说明。

  【style】

  样式通过style标签<style></style>包裹，默认是影响全局的，如需定义作用域只在该组件下起作用，需在标签上加scoped，<style scoped></style>

  如要引入外部css文件，首先需给项目安装css-loader依赖包，打开cmd，进入项目目录，输入npm install css-loader,回车。安装完成后，就可以在style标签下import所需的css文件，例如：

  ![](/images/posts/vue/26.png)

* (7) main.js——[入口文件]

  main.js主要是引入vue框架，根组件及路由设置，并且定义vue实例，下图中的

  components:{App}就是引入的根组件App.vue

  后期还可以引入插件，当然首先得安装插件。

  ![](/images/posts/vue/27.png)

* (8) main.js——[入口文件]

  router文件夹下，有一个index.js，即为路由配置文件

  ![](/images/posts/vue/28.png)

  这里定义了路径为'/'的路由，该路由对应的页面是Hello组件，所以当我们在浏览器url访问http://localhost:8080/#/时就渲染的Hello组件

  类似的，我们可以设置多个路由，‘/index’,'/list'之类的，当然首先得引入该组件，再为该组件设置路由。 
 
 

转载请注明原地址，房东惠的博客：[http://myPirlo.github.io](http://myPirlo.github.io) 谢谢！
