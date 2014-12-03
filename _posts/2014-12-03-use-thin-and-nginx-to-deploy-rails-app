---
layout: post
title: 使用thin和nginx部署rails应用
---


###Nginx的安装和配置

- 安装：google

- 配置

> 进入/usr/local/nginx目录后，找到conf/vhost目录,创建xx.conf，通过
> nginx.conf include *.conf进行站点配置，配置文件如下：

> ```
> #app 与下面proxy_pass 名称保持一致
> upstream app {
>  server 127.0.0.1:8000;
>  server 127.0.0.1:8001;
>  server 127.0.0.1:8002;
> }

> server {
>  listen       80;
>  server_name  xxx.dev.com ;

>  root /data/htdocs/xxx.dev.com;
  
>  #处理assets静态资源，nginx直接处理
>  location ~* /.*\.(png|jpg|ico|jpeg|css|js|eot|ttf|woff|svg|otf) {
>   root /data/htdocs/xxx.dev.com/public;
>  }

>  location / {
>    proxy_set_header  X-Real-IP  $remote_addr;
>    proxy_set_header  X-Forwarded-For $proxy_add_x_forwarded_for;
>    proxy_set_header Host $http_host;
>    proxy_redirect off;
>    if (-f $request_filename/index.html) {
>      rewrite (.*) $1/index.html break;
>    }
>    if (-f $request_filename.html) {
      rewrite (.*) $1.html break;
>    }
>    #转发rails请求
>    if (!-f $request_filename) {
>      proxy_pass http://app; 
>      break;
>    }
>  }
  
>  location ~ .*\.(gif|jpg|jpeg|png|bmp|swf)$
>  {
>    expires      30d;
>  }

>  location ~ .*\.(js|css)?$
>  {
>    expires      1h;
>  }
  
>  #站点日志
>  access_log  logs/xxx.dev.com.log  access;
> }
> ```
> 
> 配置完成后，nginx -t命令涌来测试nginx配置文件是否正确，
> nginx -s reload命令来重新加载配置文件

### rails

> 1 从远程仓库获取到项目
> 
> 2 bundle install
> 
> 3 rake db:create RAILS_ENV=production
> 
> 4 rake db:migrate RAILS_ENV=production
> 
> 5 rake assets:precompile RAILS_ENV=production
>
> 6 创建thin.yml在config目录下
> 
> > thin.yml 配置文件如下：
> > ```
> > #thin config
> > #user: www #指定项目运行用户
> > #group: www #指定项目运行用户组
> > pid: tmp/pids/thin.pid
> > timeout: 30
> > wait: 30
> > log: log/thin.log
> > max_conns: 1024
> > require: []
> > environment: production
> > #environment: development 指定运行环境
> > max_persistent_conns: 512
> > servers: 3 #指定服务数，比如指定8000端口，那么会起8000-8002端口服务
> > threaded: false
> > daemonize: true #是否后台运行
> > #socket: tmp/sockets/thin.sock
> > chdir: /data/htdocs/xxx.dev.com
> > tag: thin-server #ps命令搜索标签名称
> > ```
> 
> 7 thin start -p 8000 -C config/thin.yml #启动thin服务
> 
> 8 thin stop -p 8000 -C config/thin.yml #停止thin服务