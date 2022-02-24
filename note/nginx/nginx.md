# Nginx

- 修改完配置文件之后检查配置文件是否有误

  ```bash
  nginx -t
  ```

  

- 修改配置文件之后,需要重启才能生效

  ```
  nginx -s reload
  ```

  

##### 设置允许跨域

```bash
# 在server下的location中添加
add_header 'Access-Control-Allow-Origin' '*';
add_header 'Access-Control-Allow_Credentials' 'true';
add_header 'Access-Control-Allow-Headers' 'Authorization,Accept,Origin,DNT,X-CustomHeader,Keep-Alive,User-Agent,X-Requested-With,If-Modified-Since,Cache-Control,Content-Type,Content-Range,Range';
add_header 'Access-Control-Allow-Methods' 'GET,POST,OPTIONS,PUT,DELETE,PATCH';

if ($request_method = 'OPTIONS') {
    add_header 'Access-Control-Max-Age' 1728000;
    add_header 'Content-Type' 'text/plain charset=UTF-8';
    add_header 'Content-Length' 0;
    return 204;
}
```



##### 配置https

```bash
server {
		# 端口后添加ssl，开启https服务
        listen       7770 ssl;
        #server_name  somename;
        #配置https服务
        ssl_certificate   /home/ssl/crt.crt;
        ssl_certificate_key  /home/ssl/key.key;
        ssl_session_cache  shared:SSL:1m;
        ssl_session_timeout 5m;
        ssl_protocols TLSv1 TLSv1.1 TLSv1.2;
        ssl_prefer_server_ciphers on;

        location / {
        	#设置允许跨域
        	add_header 'Access-Control-Allow-Origin' '*';
        	add_header 'Access-Control-Allow_Credentials' 'true';
        	add_header 'Access-Control-Allow-Headers' 'Authorization,Accept,Origin,DNT,X-CustomHeader,Keep-Alive,User-Agent,X-Requested-With,If-Modified-Since,Cache-Control,Content-Type,Content-Range,Range';
        	add_header 'Access-Control-Allow-Methods' 'GET,POST,OPTIONS,PUT,DELETE,PATCH';

        	if ($request_method = 'OPTIONS') {
                add_header 'Access-Control-Max-Age' 1728000;
                add_header 'Content-Type' 'text/plain charset=UTF-8';
                add_header 'Content-Length' 0;
                return 204;
        	}
            #代理的项目路径
            root   /usr/share/nginx/js/Delta;
            index  DeltaMock.js;
            try_files $uri $uri/ /DeltaMock.js;
        }
  }

```

