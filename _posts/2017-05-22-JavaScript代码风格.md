---
layout: post
title: JavaScript代码风格
date: 2017-05-22 
tags: 博客   
---

因为最近一直在准备毕业论文和答辩的事情，一直没有更新自己的博客网站，但是也一直在有道笔记了记录自己平时的学习情况，今天我就来写一下关于JavaScript代码风格规范的问题。主要是看了[Airbnb](https://github.com/airbnb/javascript)的JavaScript Style Guide.

### 命名约定

- 命名具有描述性

```
//bab
function q() {
//body
};
//good
function query() {
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
function user(key) {
    this.name = key.name;
} 
var bad = new user({
    name:'ysl'
});
//good
function User(key) {
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
function () {
    var _this = this;
    return function () {
    console.log(_this);
    };
}
//good
function () {
var self = this;
return function() {
    console.log(self);
    }
}
```
- 尽可能的使用命名函数
```
//bad
var log = function (msg) {
    console.log(msg)
};
//good
var log = function log(msg) {
    console.log(msg);
}
```
### 变量
- 永远使用var关键字来声明变量
```
//bad
superMsg = new SuperMsg();
//good
var superMsg = new superMsg();
```
- 对每一个变量单独使用var声明
```
//bad
var items = getItems();
goSportSteam = true;
dragonball = 'y';
//good
var itrems = getItems();
var goSportsTeam = true;
var dragonball = 'z';   
```
- 未赋值变量最后声明
```
//bad
var i,
len,
dragonball,
items = getItems(),
goSportsTeam = true;
//bad
var i;
var items = getItems();
var dragonball;
var goSportsTeam = true;
var len;
//good
var items = getItems();
var goSportTeam = true;
var dragonball;
var length;
var i;
```
- 在作用域顶部声明变量
```
//bad
function () {
    test();
    console.log('do something');
    // other 
    var name = getName();
    if(name =='test') {
        return name;
    }
}
//good
function () {
    var name = getName();
    test();
    console.log('do something');
    //other
    if(name =='test') {
        return false;
    }
    return name;
}
//bad
function () {
    var name = getName();
    if(!argument.length) {
        return false;
    }
    this.setFirstName(name);
    return true;
}
//good
function () {
    var name;
    if(!arguments.length) {
        return false;
    }
    name = getName();
    this.setFirstName(name);
    return true;    
}
```
### 对象
- 使用对象字面量创建对象
```
//bad 
var Person = new Object();
//good
var person = {};
```
- 不使用保留字做对象属性
```//bad
var person = {
    nama:'style',
    private:true;
}
//good
var person = {
    name:'style',
    self:true;
}
```
- 使用可读性的同义词代替保留字
```
//bad
var person = {
    class:'guide'
};
//bad
var person = {
    klass:'guide'
};
//good
var person = {
    type:'guide'
}
```
### 属性
- 用点号访问属性
```
var lu =  {
    jjj:true,
    name:24
};
//bad
var isjj:lu['jjj'];
//good
var isjj:lu.jjj; 
```
- 通过变量访问对象属性时使用中括号
```
var luke = { 
    jed:true,
    age:24
};
function getProp(prop) {
    return luke[prop];
}
var isJed = getProp('jed');
```
### 数组
- 使用字面量创建数组
```
//bad
var a= new Array();
//good
var a = [];
```
- 使用push方法添加数组项
```
var a =[];
//bad
a[a.length] = 'style guide';
//good
a.push('style guide');
```
- 使用slice方法复制数组
```
var a = [1,3,5,7,9];
var copyA= [];
var len = a.length;
var i ;
//bad
for(i =0;i<leng;i++) {
    copyA[i] = a[i];
}
//good
copyA = a.splice();
```
- 使用slice方法将类数组转换成数组
```
function trigger() {
    var args=Array.prototype.sloce.call(arguments);
}
```
### 字符串使用单引号
```
//bad
var name = "bob";
var fullname = "bob"+this.lastName;
//good
var fullName='jack'
var fullName = 'jack'+this.lastName;
```
- 长字符串应该通过字符串链接多行书写
```
//bad
var Msg = 'abcdefghijklmnopqrstuvwxyzzyxwvutsrqponmlkjihgfedcba';
//good
var Msg = 'abcdefghijklmnopqrstuvwxyz'+'abcdefghijklmnopqrstuvwxyz'
```
- 当以编程方式创建字符串时，应该使用join方法而不是使用字符串连接
```
var items;
var messages;
var length;
var i;
message = [{
    state:'success',
    message:'this one worked'
},{
state:'success',
    message:'this one worked as well,'
},{
state:'error',
    message:'this one did not work.'
}];
length = message.length;
//bad
function inbox(message) {
    items = '<ul>';
    for(i = 0;i<length;i++) {
        items +='<li>' + messages[i].message +'</li>';
}
    return items+'</ul>';
}
//good
function inbox(message) {
    items =[];
    for(i =0;i<length;i++) {
        items[i] = '<li>' + messages[i].message + '</li>';
}
    return '<ul>' + items.join('') + '</ul>';
}
```
### 函数
- 永远不要在非函数中使用函数声明，而可以使用命名函数表达式
```
//bad
if (currentUser) {
    function test() {
        console.log('yup');
    }
}
//good
var test;
if(currentUser) {
    test = function test() {
        console.log('yup');
    }
}
```
- 不要把参数命名为arguments
```
//bad
function nope(name,option,arguments) {
    //body
}
//good
function yup(name,optios,args) {
    //body
}
```
### 代码块
- 所有的多行代码块使用花括号
```
//bad
if(test)
    return false;
//good
if(test) return false;
if(test) {
    return false;
}
//bad
function () {return false;}
//good
function () {
    return false;
}
```
### 比较符号
- 优先使用===和！==,最后使用==和！=
- 使用快捷方式判断
### 注释
- 多行推荐使用/**...*/，不要使用//
- 单行注释使用//
- 使用//FIXME:声明问题
```
function ASD() {
    //FIXME: shouldn't use a global here
    total = 0;
    return this;
}
```
- 使用//TODO:声明需要实现
```
function ASD() {
    //TODO:total should 
    this.total = 0;
    return this;
}
```
### 空格
- 设置tab键为2个空格或4个空格
- 在花括号前加一个空格
```
//bad
function test(){
    console.log('test');
}
person.set('att',{
    age:20,
    name:'liu'
});
//good
function test() {
    console.log('test');
}
person.set('att', {
    age:22,
    name:'li'
})
```
- 在包含表达式的括号前加一个空格 
```
//bad
if(isjj) {
    fight();
}
//good
if (isjj) {
    fight();
}
```
- 包含函数参数列表的括号前不加空格
```
//bad
function fight () {
    console.log ('aaa');
}
//good
function fight() {
    console.log('aaa');
}
```
- 运算符前后需要加空格
```
//bad 
var x=y+5;
//good
var x = y + 5;
```
- 在文件末尾加单一分行符
- 在代码块和下一代码语句之间留一空行

```
//bad
if (foo) {
    return bar;
}
return bar;

//good
if(foo){
    return bar;
}

return bar;
```

### 分号

- 自执行函数后加分号
```
//bad
(function (){
    var name = 'sky';
    return name
})()

//good
(function(){
    var name = 'sky';
    return name;
})();
```

- 每条代码语句后加分号

```
//bad
var name ='style'
//good
var name ='style';
```

### 强制转换

- 类型转换放在代码语句前面

```
// => this.reviewScore = 9;

//bad
var totalScore = this.reviewScore + '';
//good
var totalScore = '' + this.reviewScore;
//bad
var totalScore = '' + this.reviewScore + 'total score';
//good
var totalScore = this.reviewScore + 'totel score';
```

- 使用parsetInt数值转换时，总是声明转换进制

```
var value = '4';
//bad
var val = new Number(value);
var val = +value;
var val = value >> 0;
var val = parsetInt(value);

//good
var val = Number(value);
var val = parsetInt(value,10);

```
- Boolean值转换

```
var age = 0;
//bad 
var hasAge = new Boolean(age);

//good
var hasAge = Boolean(age);
var noAge = !!age;
```

### 存取器

- 使用存取器的方法存取值
```
//bad 
dog.name();
dog.name('wang');

//good
dog.getName();
god.setName('wang');
```

- 返回boolean值的方法用isVal()或hasVal()形式

```
//bad
if(!dog.name) {
    return false;
}
if(!dog.hasName()) {
    return false;
}
```

- 不要重写构造函数原型

```
function fran() {
    console.log('new fr');
}

//bad
fran.prototype = {
    fight: function fight() {
        console.log('fight');
    },

    block: function block() {
        console.log('block');
    }
};

//good
fran.prototype.fight = function fight() {
    console.log('fight');
};

fran.prototype.block = function block() {
    console.log('block');
}
```

### Jquery

- Jquery对象变量前加前缀$

```
//bad
var sidebar = $('.sidebar');

//good
var $sidebar = $('.sidebar');
```

- 混存DOM查询

```
//bad
function setSidebar() {
    $('.sidebar).hide();
    //some
    $('.sidebar).css({
        'color':'blue'
    });
}
//good
function setSidebar() [
    var $sidebar = $('.sidebar');
    $sidebar.hide();
    //some
    $sidebar.css({
        'color':'blue';
    })
]
```