#### 安装依赖
```shell
yum install -y curl policycoreutils-python openssh-server
```

### 下载软件包
```shell
wget https://mirrors.tuna.tsinghua.edu.cn/gitlab-ce/yum/el7/gitlab-ce-10.2.2-ce.0.el7.x86_64.rpm
```

### 安装gitlab
```shell
rpm -ivh gitlab-ce-10.2.2-ce.0.el7.x86_64.rpm
```

### 修改配置文件 /etc/gitlab/gitlab.rb，可以配置ip或者域名
```shell
external_url 'http://ip'
```

### 初始化配置，该配置需要比较长时间（上线后，不能执行该指令，不然会把配置文件重置）
```shell
gitlab-ctl reconfigure
```

### 配置访问端口号 /var/opt/gitlab/gitlab-rails/etc/gitlab.yml
```shell
gitlab:
  host: ip或者域名
  port: 端口号
  https: false
```

### 配置nginx端口号，需要配置跟上面的端口号一致 /var/opt/gitlab/nginx/conf/gitlab-http.conf
```shell
server {
  listen *: 端口号
}
```

### 修改后台服务端口（可以不配置） /var/opt/gitlab/gitlab-rails/etc/unicorn.rb
```shell
listen "127.0.0.1:端口号", :tcp_nopush => false
```

### 修改gitlab端口号，与上面端口一致（可以不配置） /var/opt/gitlab/gitlab-shell/config.yml
```shell
gitlab_url: "http://127.0.0.1:端口号"
```

### 常用指令
```shell
# 启动
gitlab-ctl start

# 停止
gitlab-ctl stop

# 重启
gitlab-ctl restart

# 查看服务状态
gitlab-ctl status

# 初始化配置
gitlab-ctl reconfigure

# 查看服务日志
gitlab-ctl tail 名称
```