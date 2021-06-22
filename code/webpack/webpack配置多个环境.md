### 配置多个环境
- 安装依赖
```shell
npm install --save-dev webpack-merge
```
- 配置共通属性webpack.config.js
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
          title: '不同的环境配置',
      }),
    ],
    output: {
        filename: '[name].bundle.js',
        path: path.resolve(__dirname, 'dist'),
        clean: true,
    },
}
```

- 配置webpack.dev.js
```javascript
const { merge } = require('webpack-merge')
const config = require('./webpack.config')

module.exports = merge(config, {
    mode: 'development',
    devtool: 'inline-source-map',
    devServer: {
        contentBase: './dist',
    },
})
```
- 配置webpack.prod.js
```javascript
const { merge } = require('webpack-merge')
const config = require('./webpack.config')

module.exports = merge(config, {
    mode: 'production',
})
```

- 配置启动项package.json

```json
{
  ...
  "scripts": {
    ...
    "start": "webpack serve --open --config webpack.dev.js",
    "build": "webpack --config webpack.prod.js"
  },
  ...
}
```