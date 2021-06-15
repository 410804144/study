### 安装
```shell
mkdir webpack-demo
cd webpack-demo
npm init -y
npm install webpack webpack-cli --save-dev
```
### 防止意外发布代码(操作package.json)
- 删除以下属性
```shell
"main": "index.js"
```
- 增加以下属性
```shell
"private": true
```

### 快速查看代码实现情况
- 增加./dist/index.html文件
```html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8" />
    <title>起步</title>
  </head>
  <body>
    <script src="main.js"></script>
  </body>
</html>
```
- 执行npx webpack，将会生成dist/main.js
- 浏览器打开dist/index.html，就可以查看页面执行效果

### 使用配置文件
- 创建配置文件：webpack.config.js
```javascript
const path = require('path')
module.exports = {
  entry: './src/index.js',
  output: {
    filename: 'main.js',
    path: path.resolve(__dirname, 'dist'),
  },
}
```
- 使用配置文件打包（默认情况下读取webpack.config.js，参数可以省略）
```shell
npx webpack --config webpack.config.js
```

### 创建脚本
- 在package.json中增加
```javascript
{
    ...
    "script": {
        ...
        "build": "webpack"
    }
    ...
}
```
- 执行打包指令
```shell
# 等效于npx webpack
npm run build
```

### 定义多入口、自动生成index.html文件
- 引入插件
```shell
npm install html-webpack-plugin --save-dev
```
- 修改配置文件webpack.config.js
```javascript
const path = require('path')
const HtmlWebpackPlugin = require('html-webpack-plugin')

module.exports = {
    entry: {
        index: './src/index.js',
        print: './src/print.js',
    },
    plugins: [
      new HtmlWebpackPlugin({
          title: '管理输出',
      }),
    ],
    output: {
        filename: '[name].bundle.js',
        path: path.resolve(__dirname, 'dist'),
        clean: true,
    },
}
```