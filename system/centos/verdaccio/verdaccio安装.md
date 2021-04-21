### 安装nodejs
```shell
yum install -y nodejs
```
### 安装verdaccio
```shell
npm install -g verdaccio
```
### 配置
```shell
# 修改config.yaml，在最后一行添加内容，使其可以在外网访问
# 该文件正常在（/root/.config/verdaccio/config.yaml）
# 可输入之情verdaccio启动服务，就能看到路径
listen: 0.0.0.0:4873
```

### 使用pm2启动verdicco（pm2托管的进程可以保证进程永远是活着的，尝试通过kill -9去杀verdaccio的进程发现杀了之后又自动启起来）
### 全局安装pm2
```shell
npm install -g pm2

```

### 使用pm2启动verdicco
```shell
pm2 start `which verdaccio`
```