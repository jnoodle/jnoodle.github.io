---
layout: post
title: 一个轻量级的JS路由库——fd-router
---

fd-router是一个简单轻量的JS路由库，主要用于一些简单的单页面应用。

[源码在这里](https://github.com/jnoodle/fd-router) 喜欢记得给个Star~

<!--more-->

fd-router中包含了详细的注释，目的主要不在于生产环境使用，而是希望用户通过对于源码的研究和扩展，可以快速搭建适合自己项目的路由库。

fd-router主要包含如下方法：

## init(options)

初始化路由，设置路由模式（`history`或`hash`）和根目录。

```javascript
Router.init({
    mode: 'history',
    root: '/'
});
```


## add(route)

增加路由（注册路由）

```javascript
Router.add({
    path: /about\/(.*)/, //可以使用正则表达式，每一个()匹配将会作为参数传入enterHandler、handler和exitHandler
    params: [1, 2],  //初始参数，enterHandler、handler和exitHandler的参数包含params和path中匹配的参数
    enterHandler: function () {  
        //路由进入时触发的回调，如果返回false，则handler不触发
        console.log('enter about');
    },
    handler: function () {
    		//路由回调
        console.log('do about');
    },
    exitHandler: function () {
        //路由退出时触发的回调
        console.log('exit about');
    }
});
```


## remove(routeArray)

移除路由。只需要有path即可。

```javascript
Router.remove([
    {path: /about/}, 
    {path: /info/}
]);
```

## listen()

开始监听路由。

## go（path）

导航到路由。

```javascript
Router.go('/about/');
```
