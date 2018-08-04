---
layout: post
title: "跑通Node全栈(demo版本)(五)---Vue-cli请求后台数据"
date: 2018-8-05 
description: "跑通Node全栈(demo版本)(五)---Vue-cli请求后台数据"
tag: Vue
---   

  这一章我们带大家一起学习如何使用Vue向express后台发送请求,并将得到的MongoDB的数据返回

### 1.修改默认的Vue模板

* 首先,我们先写一个测试页面,看vue是否跑通。打开components文件夹中的HelloWord.vue组件,删除默认代码,并将该组件修改成test.vue。

  ![](/images/posts/vue/31.png)

* 前面我们讲过components中的组件需要和路由系统中的路径相对应,所以我们需要打开router文件夹中的index.js,修改相关代码。

  ![](/images/posts/vue/32.png)

* 运行npm start启动Vue服务。打开浏览器,运行localhost:8080看到效果

  ![](/images/posts/vue/33.png)

### 2.连接express到后台

* 测试成功后,我们就可以尝试向express后台发送数据了。首先,我们需要打开express后台服务(同npm start)

前面我们已经编写了一个testDB接口,也就是说我们现在只需要通过Vue发起请求调用testDB这个接口就可以了。

* 前面我们讲的是使用表单的方法发起请求,这次我们使用Vue中的axios插件。Axios 是一个基于 promise 的 HTTP 库，可以用在浏览器和 node.js 中。

* 首先安装axios

  ```
    cnpm install axios --save
  ```

* 为了可以全局的使用axios,我们还需要做如下配置
  (1)将axios在mian.js中引入
  ```
    import axios from 'axios'
  ```
  (2)将axios改写为Vue的原型属性
  ```
    Vue.prototype.$axios= axios
  ```

* 接着我们尝试用axios写一个自定义方法访问testDB接口,如下图

  ![](/images/posts/vue/34.png)

* 到浏览器中点击按钮"获取数据"按钮,浏览器会报错,错误如下。这是因为浏览器的同源策略限制,无法跨域请求3000端口的数据。故而我们还需要配置axios的跨域设置。

* 我们在config文件夹下的index.js中的proxyTable中加入如下代码
 
  ![](/images/posts/vue/35.png)

  注:前面一定要加http

* 解决了跨域问题后,我们就可以用api编写相关访问请求的代码了

  ![](/images/posts/vue/36.png)

* 点击请求,如果成功,则会将数据了中的测试数据全部打印在页面中了

  ![](/images/posts/vue/37.png)

### 3.总结

  麻雀虽小,五脏俱全。至此为止,我们用五章的篇幅跟大家介绍了如何使用Vue+express+mongodb跑通了一个前台加后台的小Demo。后面我们将持续更新完整的学生管理系统制作教程。



* 本章我们简单介绍了一下路由的基础配置,以后我们就可以按照这种格式编写其他业务逻辑的路由啦。

转载请注明原地址，房东惠的博客：[http://myPirlo.github.io](http://myPirlo.github.io) 谢谢！
