---
layout: post
title: Jekyll搭建个人博客
date: 2017-01-14 
tags: 博客   
---

哈喽，大家好，我是刘御锟，是一名初入前端的菜鸟，大学时读的计算机科学与技术专业，因为机缘巧合，发现前端很有意思，日新月异的变化给我很强烈的冲击，从此进入到前端的世界里！
俗话说的好，自己学习好并不算真正的学好，你给大家讲解清楚才算真的好，所以我根据github和jekyll建造的个人网站的过程告诉大家。

### 介绍

 　Jekyll 是一个简单的博客形态的静态站点生产机器。它有一个模版目录，其中包含原始文本格式的文档，通过 Markdown （或者 Textile） 以及 Liquid 转化成一个完整的可发布的静态网站，你可以发布在任何你喜爱的服务器上。Jekyll 也可以运行在 GitHub Page 上，也就是说，你可以使用 GitHub 的服务来搭建你的项目页面、博客或者网站，而且是完全免费的

　使用 Jekyll 搭建博客之前要确认下本机环境，Git 环境（用于部署到远端）、[Ruby](http://www.ruby-lang.org/en/downloads/) 环境（Jekyll 是基于 Ruby 开发的）、包管理器 [RubyGems](http://rubygems.org/pages/download)                
　　如果你是 Mac 用户，你需要安装 Xcode 和 Command-Line Tools了。下载方式 Preferences → Downloads → Components。

　　Jekyll 是一个免费的简单静态网页生成工具，可以配合第三方服务例如： Disqus（评论）、多说(评论) 以及分享 等等扩展功能，Jekyll 可以直接部署在 Github（国外） 或 Coding（国内） 上，可以绑定自己的域名。[Jekyll中文文档](http://jekyll.bootcss.com/)、[Jekyll英文文档](https://jekyllrb.com/)、[Jekyll主题列表](http://jekyllthemes.org/)。


### Jekyll 环境配置

安装 jekyll

```     
$ gem install jekyll     
```    

创建博客

```    
$ jekyll new myBlog    
```   

进入博客目录

```
$ cd myBlog  
```

启动本地服务

```
$ jekyll serve
```

在浏览器里输入： [http://localhost:4000](http://localhost:4000)，就可以看到你的博客效果了。



so easy !

### 目录结构
　
　Jekyll 的核心其实是一个文本转换引擎。它的概念其实就是： 你用你最喜欢的标记语言来写文章，可以是 Markdown，也可以是 Textile,或者就是简单的 HTML, 然后 Jekyll 就会帮你套入一个或一系列的布局中。在整个过程中你可以设置URL路径, 你的文本在布局中的显示样式等等。这些都可以通过纯文本编辑来实现，最终生成的静态页面就是你的成品了。

 一个基本的 Jekyll 网站的目录结构一般是像这样的：

```
.
├── _config.yml
├── _includes
|   ├── footer.html
|   └── header.html
├── _layouts
|   ├── default.html
|   ├── post.html
|   └── page.html
├── _posts
|   └── xxxx-xx-xx-welcome-to-jekyll.markdown
├── _sass
|   ├── _base.scss
|   ├── _layout.scss
|   └── _syntax-highlighting.scss
├── about.md
├── css
|   └── main.scss
├── feed.xml
└── index.html

```

这些目录结构以及具体的作用可以参考 [官网文档](http://jekyll.com.cn/docs/structure/) 

进入 _config.yml 里面，修改成你想看到的信息，重新 jekyll server ，刷新浏览器就可以看到你刚刚修改的信息了。

到此，博客初步搭建算是完成了，

### 博客部署到远端 

　我这里讲的是部署到 Github Page 创建一个 github 账号，然后创建一个跟你账户名一样的仓库，如我的 github 账户名叫 [onepiecelyk](https://github.com/onepiecelyk)，我的 github 仓库名就叫 [onepiecelyk.github.io](https://github.com/onepiecelyk/onepiecelyk.github.io)，创建好了之后，把刚才建立的 myBlog 项目 push 到 username.github.io仓库里去（username指的是你的github用户名），检查你远端仓库已经跟你本地 myBlog 同步了，然后你在浏览器里输入 username.github.io ，就可以访问你的博客了。


### 编写文章

　　所有的文章都是 _posts 目录下面，文章格式为 mardown 格式，文章文件名可以是 .mardown 或者 .md。

　　编写一篇新文章很简单，你可以直接从 _posts/ 目录下复制一份出来 `2016-10-16-welcome-to-jekyll副本.markdown` ，修改名字为 2016-10-16-article1.markdown ，注意：文章名的格式前面必须为 2016-10-16- ，日期可以修改，但必须为 年-月-日- 格式，后面的 article1 是整个文章的连接 URL，如果文章名为中文，那么文章的连接URL就可能会出现一些乱码， 所以建议文章名最好是英文的或者阿拉伯数字。 双击 2016-10-16-article1.markdown 打开

```

---
layout: post
title:  "Welcome to Jekyll!"
date:   2017-01-14 15:29:08 +0800
categories: jekyll update
---

正文...

```


title: 显示的文章名， 如：title: 我的第一篇文章                    
date:  显示的文章发布日期，如：date: 2016-10-16                          
categories: tag标签的分类，如：categories: 随笔            

注意：文章头部格式必须为上面的，.... 就是文章的正文内容。

我写文章使用的是 Sublime Text3 编辑器，如果你对 markdown 语法不熟悉的话，可以看看[作业部落的教程](https://www.zybuluo.com/) 
 

```
$ jekyll server   
```

### 如果你本机没配置过任何jekyll的环境，可能会报错

```
/Users/xxxxxxxx/.rvm/rubies/ruby-2.2.2/lib/ruby/site_ruby/2.2.0/rubygems/core_ext/kernel_require.rb:54:in `require': cannot load such file -- bundler (LoadError)
	from /Users/xxxxxxxx/.rvm/rubies/ruby-2.2.2/lib/ruby/site_ruby/2.2.0/rubygems/core_ext/kernel_require.rb:54:in `require'
	from /Users/xxxxxxxx/.rvm/gems/ruby-2.2.2/gems/jekyll-3.3.0/lib/jekyll/plugin_manager.rb:34:in `require_from_bundler'
	from /Users/xxxxxxxx/.rvm/gems/ruby-2.2.2/gems/jekyll-3.3.0/exe/jekyll:9:in `<top (required)>'
	from /Users/xxxxxxxx/.rvm/gems/ruby-2.2.2/bin/jekyll:23:in `load'
	from /Users/xxxxxxxx/.rvm/gems/ruby-2.2.2/bin/jekyll:23:in `<main>'
	from /Users/xxxxxxxx/.rvm/gems/ruby-2.2.2/bin/ruby_executable_hooks:15:in `eval'
	from /Users/xxxxxxxx/.rvm/gems/ruby-2.2.2/bin/ruby_executable_hooks:15:in `<main>'

```

原因： 没有安装 bundler ，执行安装 bundler 命令

```

$ gem install bundler

```


提示： 

```
Fetching: bundler-1.13.5.gem (100%)
Successfully installed bundler-1.13.5
Parsing documentation for bundler-1.13.5
Installing ri documentation for bundler-1.13.5
Done installing documentation for bundler after 5 seconds
1 gem installed

```

再次执行 $ jekyll server  ，提示

```

Could not find proper version of jekyll (3.1.1) in any of the sources
Run `bundle install` to install missing gems.

```

跟着提示运行命令

```
$ bundle install
```

这个时候你可能会发现 bundle install 运行卡主不动了。

如果很长时间都没任何提示的话，你可以尝试修改 gem 的 source

```
$ gem sources --remove https://rubygems.org/
$ gem sources -a https://gems.ruby-china.org/
$ gem sources -l
*** CURRENT SOURCES ***

https://gems.ruby-china.org

```

再次执行命令 $ bundle install，发现开始有动静了

```
Fetching gem metadata from https://rubygems.org/...........
Fetching version metadata from https://rubygems.org/..
Fetching dependency metadata from https://rubygems.org/.
。。。
Installing jekyll-watch 1.3.1
Installing jekyll 3.1.1
Bundle complete! 3 Gemfile dependencies, 17 gems now installed.
Use `bundle show [gemname]` to see where a bundled gem is installed.

```

bundler安装完成，后再次启动本地服务 

```
$ jekyll server

```

继续报错

```
Configuration file: /Users/tendcloud-Caroline/Desktop/onepiecelyk.github.io/_config.yml
  Dependency Error: Yikes! It looks like you don't have jekyll-sitemap or one of its dependencies installed. In order to use Jekyll as currently configured, you'll need to install this gem. The full error message from Ruby is: 'cannot load such file -- jekyll-sitemap' If you run into trouble, you can find helpful resources at http://jekyllrb.com/help/! 
jekyll 3.1.1 | Error:  jekyll-sitemap

```
表示 当前的 jekyll 版本是 3.1.1 ，无法使用 jekyll-sitemap 

解决方法有两个

> 1、打开当前目录下的 _config.yml 文件，把 gems: [jekyll-paginate,jekyll-sitemap] 换成 gems: [jekyll-paginate] ，也就是去掉jekyll-sitemap。

> 2、升级 jekyll 版本，我当前的是 jekyll 3.1.2 。

修改完成后保存配置，再次执行

```
$ jekyll server

```
提示

```
 Incremental build: disabled. Enable with --incremental
      Generating... 
                    done in 0.901 seconds.
 Auto-regeneration: enabled for '/Users/ky/study/onepiecelyk.github.io'
Configuration file: /Users/ky/study/onepiecelyk.github.io/_config.yml
    Server address: http://127.0.0.1:4000/
  Server running... press ctrl-c to stop.

```
可能有时候也会出现

```
WARN: Unresolved specs during Gem::Specification.reset:
      jekyll-watch (~> 1.1)
      rouge (~> 1.7)
WARN: Clearing out unresolved specs.
Please report a bug if this causes problems.
/Library/Ruby/Gems/2.0.0/gems/bundler-1.14.4/lib/bundler/runtime.rb:40:in `block in setup': You have already activated colorator 1.1.0, but your Gemfile requires colorator 0.1. Prepending `bundle exec` to your command may solve this. (Gem::LoadError)
	from /Library/Ruby/Gems/2.0.0/gems/bundler-1.14.4/lib/bundler/runtime.rb:25:in `map'
	from /Library/Ruby/Gems/2.0.0/gems/bundler-1.14.4/lib/bundler/runtime.rb:25:in `setup'
	from /Library/Ruby/Gems/2.0.0/gems/bundler-1.14.4/lib/bundler.rb:100:in `setup'
	from /Library/Ruby/Gems/2.0.0/gems/jekyll-3.4.0/lib/jekyll/plugin_manager.rb:36:in `require_from_bundler'
	from /Library/Ruby/Gems/2.0.0/gems/jekyll-3.4.0/exe/jekyll:9:in `<top (required)>'
	from /usr/local/bin/jekyll:22:in `load'
	from /usr/local/bin/jekyll:22:in `<main>'
```

这时候你可以输入

```
$ bundle exec jekyll server 

```
就会成功了。

表示本地服务部署成功。

在浏览器输入 [127.0.0.1:4000](127.0.0.1:4000) ， 就可以看到[onepiecelyk.github.io](onepiecelyk.github.io)博客效果了。

### 修改成你自己的博客

>* 如果你想使用我的模板请把 _posts/ 目录下的文章都去掉。
>* 修改 _config.yml 文件里面的内容为你自己的。

然后使用 git push 到你自己的仓库里面去，检查你远端仓库，在浏览器输入 username.github.io 就会发现，你有一个漂亮的主题模板了。      



### 为什么要是用 Jekyll

使用了 Jekyll 你会发现如果你想使用多台电脑发博客都很方便，只要把远端 github 仓库里的博客 clone 下来，写文章后再提交就可以了.比起来HEXO要相对简单一点。当然有比较喜欢HEXO的也是可以的。












