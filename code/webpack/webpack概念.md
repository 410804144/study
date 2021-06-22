### 入口(entry)
- 指示webpack使用那个模块作为依赖图的入口起点，默认【./src/index.ts】
```javascript
module.exports = {
    entry: './src/index.ts',
}
```

### 输出(output)
- 告诉webpack在哪里输出所创建的bundle，以及如何命名这些文件
```javascript
const path = require('path')

module.exports = {
    entry: './src/index.ts',
    output: {
        path: path.resolve(__dirname, 'dist'),
        filename: 'test.bundle.js',
    },
}
```

### 解析(loader)
- webpack只能理解JavaScript和JSON文件， 其他类型文件需要loader去处理
- 以下代码是当引入.txt文件时，使用row-loader解析文件
```javascript
const path = require('path')

module.exports = {
    entry: './src/index.ts',
    output: {
        path: path.resolve(__dirname, 'dist'),
        filename: 'test.bundle.js',
    },
    module: {
        rules: [
            {
                test: /\.txt$/,
                use: 'raw-loader',
            },
        ],
    },
}
```
- 执行顺序，从后往前，限制性sass-loader，再执行css-loader，最后执行style-loader
```javascript
modules.exports = {
    module: {
        rules: [
            {
                test: /\.css$/,
                use: [
                    { loader: 'style-loader' },
                    {
                        loader: 'css-loader',
                        options: {
                            modules: true,
                        },
                    },
                    { loader: 'sass-loader' },
                ],
            },
        ],
    },
}
```

### 插件(plugin)
-- 插件可以执行更广的任务，包括打包优化，资源管理，注入环境变量
-- 以下配置为应用程序生产一个HTML文件，并注入所有bundle
```shell
npm install --save-dev html-webpack-plugin
```
```javascript
const HtmlWebpackPlugin = require('html-webpack-plugin')
const webpack = require('webpack')

module.exports = {
    module: {
        rules: [
            {
                test: /\.txt$/,
                use: 'raw-loader',
            },
        ],
    },
    plugins: [
        new HtmlWebpackPlugin({ template: './src/index.html'}),
    ],
}
```

### 模式(mode)
- 通过选择development, production, none之中的一个，来设置参数，可以启用webpack内置在相应环境下的优化，默认值为production
```javascript
module.exports = {
    mode: 'production',
}
```

### 浏览器兼容性
- webpack支持所有符合ES5标准的浏览器（不支持IE8及以下版本），webpack的import()和require.ensure()需要Promise，如果想要支持旧版本浏览器，需要提前加载polyfill

### 环境
- webpack5 运行于Node.js v10.13.0+