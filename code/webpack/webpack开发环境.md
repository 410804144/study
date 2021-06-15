### 配置开发环境
- 修改配置文件
```javascript
module.exports = {
    mode: 'development',
    devtool: 'inline-source-map',
    ...
}
```
### 观察模式
- 修改package.json
```shell
{
  ...
  "scripts": {
    "watch": "webpack --watch",
    ...
  }
}
```
- 执行指令
```shell
npm run watch
```
- 接下来，修改文件并保存后，会自动编译代码，刷新页面就能看到编译后的效果

## webpack-dev-server
- 修改webpack.config.js
```javascript
module.exports = {
    ...
    devServer: {
        contentBase: './dist',
    }
}
```
- 修改package.json
```shell
{
  ...
  "scripts": {
    "start": "webpack serve --open",
    ...
  }
}
```
- 执行指令
```shell
npm run start
```
- 接下来，修改文件并保存后，会自动编译代码，并自动刷新网页
# webpack-dev-middleware
- 安装依赖
```shell
npm install --save-dev express webpack-dev-middleware
```
- 修改配置文件
```javascript
module.exports = {
    ...
    output: {
        ...
        publicPath: '/',
    }
}
```
- 新建server.js
```javascript
const express = require('express')
const webpack = require('webpack')
const webpackDevMiddleware = require('webpack-dev-middleware')

const app = express()
const config = require('./webpack.config')
const compiler = webpack(config)

// 告知 express 使用 webpack-dev-middleware，以及将 webpack.config.js 配置文件作为基础设置。
app.use(
    webpackDevMiddleware(compiler, {
        publicPath: config.output.publicPath,
    })
)

// 将文件 serve 到 port 3000。
app.listen(3000, function() {
    console.log('Example app listening on port 3000!\n')
})
```
- 修改package.json
```shell
{
  ...
  "scripts": {
    "server": "node server.js",
    ...
  }
}
```
- 执行指令
```shell
npm run server
```
- 接下来，修改文件并保存后，会自动编译代码，并自动刷新网页