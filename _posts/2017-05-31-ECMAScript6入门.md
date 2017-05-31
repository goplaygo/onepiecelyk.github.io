---
layout: post
title: ECMAScript6入门
date: 2017-05-31
tags: 博客   
---


最近几天在看阮一峰老师的《ES6 标准入门》这本书，初步学习了一下ES6的语法和与ES5之间的差别。同时也学习了慕课网新出版的ES6教程，然后尝试编写了一个彩票11选5的项目，后续会放到github上。

### ECMAScript6入门

ECMAScript6，也叫ECMAScript2015，简称ES6，是javascript的下一代标准，15年正式发布。ES6的变化是具有里程碑性的，他将改变我们编写javascript代码的方式。

### 块级作用域

在ES5是没有块级作用域的，作用域都是以函数划分的，定义的变量或函数都是在其上级作用域内作为局部变量或直接在全局变量作用域暴露作为全局变量（浏览器下为window的属性，Node环境下属于golbal对象）

```
var a= 1;
function test(){
    console.log('external');
}
function start(){
    var a = 10;
    if(a>1){
        function test(){
            console.log('internal');
        }
    }
    test();
}
start();
console.log(a);
```

对于以上例子，在es5环境下，输出的是‘internal’，在ES6环境运行下则输出‘external’

### let和const
#### let
ES6新增let命令，类似var来声明变量。不同的是，let声明的变量只存在let块级作用域内