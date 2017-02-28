---
layout: post
title: 【译】CSS五种方式实现Footer置底
date: 2017-02-25 
tags: 博客   
---

### 随笔

页脚置底（sticky footer）字面意思就是将网页的footer部分始终在浏览器窗口的底部。

具体就是当网页内容足够长以致超出浏览器可视高度时，页脚会随着内容被推到网页底部；但是如果网页内容不够长时，置底的页脚则会保持在浏览器窗口底部。

![](/images/posts/Sticky Footer.png)


### 实现方法
#### 1.将内容部分的底部外边距设为负数

这是一种比较主流的写法，把内容部分最小高度设置为100%，然后利用部分的负底部外边距值来达到当高度不满时，页脚保持在窗口底部，当高度超出时随之推出的效果

```html
<html>
<body>
	<div class="wrapper">
		我是内容
		<div class="push"></div>
	</div>
	<div class="footer"></div>
</body>
</html>
```
```css
html,body{
	height:100%;
	margin:0;
}
.wrapper{min-height:100%;margin-bottom:-50px;/* 等于footer的高度 */}
.footer,.push{height:50px;}
```
**这个方法需要有额外的占位元素`如.puds`**
`.wraper`的margin-bottom的值需要和`.footer`的值保持一致，所以导致十分不友好
 
#### 2.将页脚的顶部外边距设置为负数

既然能在容器上使用负的margin-bottom，那么是否使用负的margin-top吗？答案当然是可以啦

给内容外增加父元素，并让内容分的底部内边距与页脚高度的值**相等**
```html
<html>
	<body>
		<div class="content">
			<div class="content-inside">
				我是内容
			</div>
		</div>
		<footer class="footer"></footer>
	</body>
</html>
```
```css
html,body{height:100%;margin:0;}
.content{min-height:100%}
.content .content-inside{padding:20px;padding-bottom:50px;}
.footer{height:50px;margin-top:-50px;}
```
当然因为也是添加了不必要的元素，造成不友好


#### 3.使用calc()设置内容高度

还有一种方法就是我们可以使用c3的新方法calc()计算函数

这样的话就不会有元素间的重叠发生了，也不需要控制内外边距

```html
<html>
	<body>
		<div class="content">
			我是内容
		</div>
		<div class="footer"></div>
	</body>
</html>
```
```css
min-height:calc(100%-(50px+元素间距离));
footer{height:50px}
```

#### 4.使用flexbox弹性盒布局 

因为以上三种方法都是固定的，通常是不利于网页布局的，因为内容可能会改变，一旦内容超出固定高度就会破坏布局，所以给footer使用flexbox吧，让他们的高度可大可小变的更灵活
```html
<html>
	<body>
		<div class="content">
			这是内容
		</div>
		<div class="footer"></div>
	</body>
</html>
```
```css
html{height:100%;}
body{min-height:100%;
display:flex;
flex-direction:column}
.content{
	flex:1;
	//或margin-top:auto;
}
```
PS：如果不是很理解，我们还有[Flex布局教程](http://www.ruanyifeng.com/blog/2015/07/flex-grammar.html?utm_source=tuicool)呢。
#### 5.使用grid网格布局
grid比flexbox布局还要新颖一些，并且更加简洁
```html
<html>
	<body>
		<div class="content">
			这是内容
		</div>
		<div class="footer"></div>
	</body>
</html>
```
```css
html{height:100%;}
body{min-height:100%;
display:grid;
grid-template-rows:1px auto;}
.footer{grid-row-start:2;
grid-row-end:3;}
```
PS：如果不是很理解，我们还有[Grid布局教程](http://www.w3cplus.com/css3/line-base-placement-layout.html)呢。
十分遗憾的是目前网格布局仅仅只有火狐浏览器和谷歌浏览器支持

##总结
其实这种页脚置底的布局随处可见，我们大家都会用，但是有时候用一些新的方式来编写相信也是一种提高。