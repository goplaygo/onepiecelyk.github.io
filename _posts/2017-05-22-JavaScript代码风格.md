---
layout: post
title: JavaScript代码风格
date: 2017-05-22 
tags: 博客   
---

因为最近一直在准备毕业论文和答辩的事情，一直没有更新自己的博客网站，但是也一直在有道笔记了记录自己平时的学习，今天我就来写一下关于JavaScript代码风格规范的问题。主要是看了[Airbnb](https://github.com/airbnb/javascript)的JavaScript Style Guide.

### 命名约定

 - 命名具有描述性


```
    //bab
    function q(){
        //body
    };
    //good
    function query(){
        //body
    } 
```
 - 驼峰式的命名对象、函数、实例

```
//bad
var OBJTaaaa ={};
var this_is_my_demo = {};
var o = {};
function c(){};
//good
var thisIsMyDemo = {};
function thisIsMyFunction(){}; 
```

 - 构造函数时首字母大写
```
//bad
function user(key){
    this.name = key.name;
} 
var bad = new user({
    name:'ysl'
});
//good
function User(key){
    this.name = key.name;
}
var good = new User({
    name:'ysl'
});
```

 - 定义私有属性时以下横线_开头
 ```
 //bad 
 this.__name='ysl';
 this.name_='ysl';
 //good
 this._name='ysl';
```
 - 使用self来保存this引用
 ```
 //bad
 function (){
     var _this = this;
     return function (){
         console.log(_this);
     };
 }
 //good
 function (){
     var self = this;
     return function(){
         console.log(self);
     }
 }
 ```

 - 尽可能的使用命名函数
 ```
 //bad
 var log = function (msg){
     console.log(msg)
 };
 //good
 var log = function log(msg){
     console.log(msg);
 }
 ```
 ### 变量