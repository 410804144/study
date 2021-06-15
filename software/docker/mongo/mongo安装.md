### 安装
```shell
docker pull mongo
```

### 启动
```shell
docker run -itd --name mymongo -p 27017:27017 mongo
```

### 连接
```shell
docker exec -it mymongo mongo
```
### 创建数据库
```shell
use xxx
db.createUser({user:"root",pwd:"root1234",roles:[{role:"dbOwner",db:"xxx"}]})
```