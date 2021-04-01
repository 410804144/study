### 中文乱码

修改 /etc/nginx/nginx.conf文件，在server节点增加【charset utf-8;】

```shell
    server {
        listen       80 default_server;
        listen       [::]:80 default_server;
        charset utf-8;
        server_name  _;
        root         /usr/share/nginx/html;

        # Load configuration files for the default server block.
        include /etc/nginx/default.d/*.conf;

        location / {
        }

        error_page 404 /404.html;
            location = /40x.html {
        }

        error_page 500 502 503 504 /50x.html;
            location = /50x.html {
        }
    }
```