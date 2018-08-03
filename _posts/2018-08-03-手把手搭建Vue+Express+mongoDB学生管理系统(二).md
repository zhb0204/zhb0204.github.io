---
layout: post
title: "手把手搭建Vue+Express+mongoDB学生管理系统(二)"
date: 2018-8-03 
description: "手把手搭建Vue+Express+mongoD学生管理系统(二)"
tag: Vue
---   
   

  上一章我们已经利用express创建了一个简单的后台,本章我们一起研究express中路由的使用。

### 1.准备阶段

* 首先我们打开routes文件夹,会发现里面有index.js和user.js两个文件。因为本次案例咱们只在index.js中编写路由,所以首先我们删除uers.js,并在app.js中删除关于user的对应代码。

![](/images/posts/vue/11.png)

### 2.编写自己的第一个路由 

* 打开index.js会看到其中的代码包括下图所示的三个部分

![](/images/posts/vue/12.png)

-----第一个部分表示该页面引入了两个模块   express模块以及express的路由模块
-----第二个部分则开始路由的正式编写,回调函数中的三个参数req,res,next分别表示浏览器发出的请求,服务器返回的请求,以及请求完成后将要做的事情 
-----第三个部分则表示将该页面的路由模块整体暴露出去,以供浏览器调用,res.render默认使用的是jade的模板进行输出,不了解语法的同学可以暂时删掉这句话改用res.send()进行输出

* 接着我们就创建自己的第一个路由,并在浏览器中进行测试
```
    router.get('/test', function(req, res, next) {
       res.send("这是我的第一个路由测试")
    });
```

* 运行成功后的截图如下所示

![](/images/posts/vue/13.png)


* 本章我们简单介绍了一下路由的基础配置,以后我们就可以按照这种格式编写其他业务逻辑的路由啦。

转载请注明原地址，房东惠的博客：[http://myPirlo.github.io](http://myPirlo.github.io) 谢谢！
