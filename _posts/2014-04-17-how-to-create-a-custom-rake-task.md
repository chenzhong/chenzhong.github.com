---
layout: post
title: 如何做一个自定义的rake
---

这次给[西瓜社](http://www.xiguashe.com, 'xiguashe')写了一个后端自动抓取豆瓣数据的task。

贴一下部分代码用来做说明：

```
namespace douban do
   desc "douban async"
   task async: :environment do
       include ProductsHelper
       p "async start"
       //coding
       p "async end"
   end

   def method
   end
end
```

先在lib/task/下新建一个文件，如：product.rake。

namespace: 命名空间，用于将特定的任务放在一个分类中，便于区分。

desc: 用来描述task，当rake -T 便可以知道这个任务是用于做什么的。

:enviroment 调用项目中的实例。

include 可以include helper，调用相应的helper方法。


