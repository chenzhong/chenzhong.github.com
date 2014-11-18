---
layout: post
title: 做一个属于自己的blog

---


记录下部署jekyll的一些点滴。

首先先搭建起jekyll博客，具体可以参照这篇文章进行搭建——[blogging\_with\_jekyll]("http://www.ruanyifeng.com/blog/2012/08/blogging_with_jekyll.html", "blogging_with_jekyll")。

搭建起来之后，样式不是特别的美观，阅读体验也相对一般，大家可以根据自己喜欢的博客样式，进行配置。
以下以我的博客为例，我是参考了这个[博客]('http://chloerei.com/','blog')。

首先clone代码

```
git clone https://github.com/chloerei/scribble.git
```
修改下CNAME(将你的域名写入,如chenzhong.cc)

修改下_config.yml, baseurl置为/, 其余信息替换成自己的个人信息即可。

配置自己的dns, 创建两个A纪录

	192.30.252.153
	192.30.252.154

创建一个CNAME的记录指向(github用户名).github.com


最后，提交代码到github上, 等待10分钟即可。这样博客就搞定了，非常简单。
