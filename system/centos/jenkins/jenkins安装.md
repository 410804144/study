### 安装jdk
```shell
yum install java-1.8.0-openjdk-devel
```

### 启用Jenkins存储库
```shell
wget -O /etc/yum.repos.d/jenkins.repo http://pkg.jenkins-ci.org/redhat-stable/jenkins.repo
rpm --import https://pkg.jenkins.io/redhat/jenkins.io.key
```

### 安装jenkins
```shell
yum install jenkins
```

### 启动Jenkins服务并启用它以在系统引导时启动
```shell
systemctl start jenkins
systemctl enable jenkins
```

### 检查Jenkins是否正在运行
```shell
systemctl status jenkins
```

### 输出应类似如下所示
```shell
Loaded: loaded (/etc/rc.d/init.d/jenkins; generated)
Active: active (running) since Thu 2019-11-05 21:31:36 UTC; 3s ago
```

### 访问jenkins
```shell
http://ip:8080
```

### 第一次访问需要输入管理员密码，输入以下指令查看（32个字符长度的密码）
```shell
cat /var/lib/jenkins/secrets/initialAdminPassword
```

### 输入后，继续页面操作安装插件，然后设置用户即可完成安装