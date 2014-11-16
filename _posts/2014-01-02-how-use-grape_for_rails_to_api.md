---
layout: post
title: 如何使用grape快速开发api
---



相信不久的将来会给西瓜社开发移动端的产品，这次先尝试写下API，使用的gem是grape，记录下使用的一些心得。而选择grape的原因是比rails自身的api更加轻量级，而且我觉得更加简单易懂。


首先 加入相应的gem

```
gem 'grape', git: 'https://github.com/intridea/grape.git'
bundle install
```

		

之后创建一个目录在app目录下，

```
api
|- acme
	|- activity.rb
|- api.rb
```
	

api.rb

```
class API < Grape::API
	prefix 'api'
   mount Acme::ActivityAPI
end
```

activity.rb
	
```
class ActivityAPI < Grape::API
 format :json
 
 resource :activities do
   params do
     requires :id, type: String, desc: "id"
   end
   
   get :index do
     @activities = Activity.all
   end
   
   get :show do
     @activity = Activity.find params[:id]
   end
 end
end
```



配置application.rb

```
config.paths.add "app/api", :glob => "\*\*/\*.rb"
config.autoload_paths += Dir["#{Rails.root}/app/api/*"]
```

    
最后配置路由,routes.rb

```
mount API => "/"
```

	
