---
layout: post
title:  如何在nginx下thinkphp配置pathinfo及相关错误的显示
---

###配置pathinfo
> fastcgi模块自带了一个fastcgi\_split\_path\_info指令专门用来解决此类问题的，
> 该指令会根据给定的正则表达式来分隔URL，从而提取出脚本名和path info信息，使用这个指令可以避免使用if语句

```
location ~ .+\.php($|/) {
	fastcgi_pass                127.0.0.1:9000;
	fastcgi_index               index.php;
	fastcgi_intercept_errors    on;
	#设置PATH_INFO，注意fastcgi_split_path_info已经自动改写了fastcgi_script_name变量，  
	#后面不需要再改写SCRIPT_FILENAME,SCRIPT_NAME环境变量，所以必须在加载fastcgi.conf之前设置  
	fastcgi_split_path_info  ^(.+\.php)(/.*)$;
	fastcgi_param  PATH_INFO $fastcgi_path_info;

	include /usr/local/etc/nginx/fastcgi.conf;
}
```


###错误显示

> 安装好php及nginx后，很多显示错误条件没开启，需要做如下配置。

> php.ini
> 
> ```
> display_errors
  	Default Value: On
 	;Development Value: On
 	;Production Value: Off
>
> error_reporting
	Default Value: E_ALL & ~E_NOTICE & ~E_STRICT & ~E_DEPRECATED
	;Development Value: E_ALL
	;Production Value: E_ALL & ~E_DEPRECATED & ~E_STRICT
> ```
> 
> php-fpm.conf
> 
>  `php_flag[display_errors] = on`
  