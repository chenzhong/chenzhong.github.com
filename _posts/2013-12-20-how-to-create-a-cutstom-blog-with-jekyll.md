---
layout: post
title: 做一个属于自己的blog

---


最近把博客搞了一下，记录下部署jekyll的一些点滴。

首先先搭建起jekyll博客，具体可以参照这篇文章进行搭建——[blogging\_with\_jekyll]("http://www.ruanyifeng.com/blog/2012/08/blogging_with_jekyll.html", "blogging_with_jekyll")。

搭建起来之后，样式不是特别的美观，阅读体验也相对一般，大家可以根据自己喜欢的博客样式，进行配置。
以下以我的博客为例，我是参考了这个[博客]('http://chloerei.com/','blog')。

首先clone代码

```
git clone git clone git@github.com:insraq/insraq.github.com.git
```


第二步，将css, js复制黏贴到自己的blog项目中，并同时将_layout的文件夹进行替换。

第三步，修改default.html文件的一些相关信息。

```html
<div class="header">
	<h1><a href="/">Cedric</a></h1>
	<h2>Coding is my life style</h2>   
</div>
```

替换about.html的信息。配置CAME，将里面的配置信息修改成自己的信息。

最后，提交代码到github上。这样博客就搞定了，非常简单。
