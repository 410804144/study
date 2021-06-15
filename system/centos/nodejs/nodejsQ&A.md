#### npm安装的全局命令无法执行

修改 /etc/profile 文件，在末尾加入
```shell
# 后面是nodejs的安装路径
export PATH="$PATH:/usr/local/node-v8.11.3-linux-x64/bin"
```

刷新配置
```shell
source /etc/profile
```


### chromedriver@2.46.0 install `node install.js`
```shell
npm install chromedriver --chromedriver_cdnurl=http://cdn.npm.taobao.org/dist/chromedriver
# 如果不行，则运行下面指令
npm install --ignore-scripts
npm install
```