### apple m1安装mysql
```shell
docker pull mysql/mysql-server
```

### 启动mysql

```shell
docker run -itd --name mysql -p 3306:4873 -e MYSQL_ROOT_PASSWORD=123456 mysql/mysql-server
```

### 登陆mysql
```shell
docker exec -it mysql bash
mysql -u root -p root1234
```

### 授权
```shell
CREATE USER 'root'@'%' IDENTIFIED BY 'root';
GRANT ALL ON *.* TO 'root'@'%';
flush privileges;
ALTER USER 'root'@'%' IDENTIFIED WITH mysql_native_password BY 'root1234';
flush privileges;
```