# php-blog
a light weight php blog system, no other frameworks, no composer dependencies
## usage
表结构和示例数据 -> blog_posts.sql
数据库配置 -> src/config.php
nignx 参考配置
``` bash
server {
        listen       80;
        server_name  www.blog.com;
        root /usr/local/var/www/blog/public;

        #charset koi8-r;

        #access_log  logs/host.access.log  main;

        location / {
            index index.php index.html;
            try_files $uri $uri/ /index.php?_url=$uri&$args;
        }

        #error_page  404              /404.html;

        # redirect server error pages to the static page /50x.html
        #
        error_page   500 502 503 504  /50x.html;
        location = /50x.html {
            root   html;
        }

        # proxy the PHP scripts to Apache listening on 127.0.0.1:80
        #
        #location ~ \.php$ {
        #    proxy_pass   http://127.0.0.1;
        #}

        # pass the PHP scripts to FastCGI server listening on 127.0.0.1:9000
        #

        location ~ \.php$ {
            fastcgi_pass   127.0.0.1:9000;
            fastcgi_index /index.php;

            include fastcgi_params;
            fastcgi_split_path_info       ^(.+\.php)(/.+)$;
            fastcgi_param PATH_INFO       $fastcgi_path_info;
            fastcgi_param PATH_TRANSLATED $document_root$fastcgi_path_info;
            fastcgi_param SCRIPT_FILENAME $document_root$fastcgi_script_name;
        }

        # deny access to .htaccess files, if Apache's document root
        # concurs with nginx's one
        #
        #location ~ /\.ht {
        #    deny  all;
        #}
    }
```
