### 加载css
- 安装style-loader和css-loader
```shell
npm install style-loader css-loader --save-dev
```
- 修改配置信息(webpack-config.js)
```javascript
module.exports = {
  ...
  module: {
    ...
    {
      test: /\.css$/i,
      use: ['style-loader', 'css-loader'],
    }
  }
}
```
### 加载图片
- 修改配置信息(webpack-config.js)
```javascript
module.exports = {
  ...
  module: {
    ...
    {
      test: /\.(png|svg|jpg|jpeg|gif)$/i,
      type: 'asset/resource',
    }
  }
}
```
### 加载字体文件
- 修改配置信息(webpack-config.js)
```javascript
module.exports = {
  ...
  module: {
    ...
    {
      test: /\.(woff|woff2|eot|ttf|otf)$/i,
      type: 'asset/resource',
    }
  }
}
```
- 定义@font-face
```css
@font-face {
    font-family: 'yuanti';
    src: url('./xxx.ttf') format('truetype');
    font-weight: 600;
    font-style: normal;
}
```
- 样式中使用
```css
.hello {
    font-family: 'yuanti';
}
```
### 加载csv tsv
- 安装csv-loader
```shell
npm install csv-loader --save-dev
```
- 修改配置信息(webpack-config.js)
```javascript
module.exports = {
    ...
        module: {
...
    {
        test: /\.(csv|tsv)$/i,
            type: ['csv-loader'],
    }
}
}
```
### 加载xml
- 安装xml-loader
```shell
npm install xml-loader --save-dev
```
- 修改配置信息(webpack-config.js)
```javascript
module.exports = {
  ...
  module: {
    ...
    {
      test: /\.xml$/i,
      type: ['xml-loader'],
    }
  }
}
```
### 自定义parser(toml,yaml,json5)
- 安装依赖
```shell
npm install toml yamljs json5 --save-dev
```
- 修改配置信息(webpack-config.js)
```javascript
const toml = require('toml')
const yaml = require('yamljs')
const json5 = require('json5')

module.exports = {
  ...
  module: {
    ...
    {
      test: /\.toml$/i,
      type: 'json',
      parser: {
        parse: toml.parse
      }
    },
    {
      test: /\.yaml$/i, 
      type: 'json',
      parser: {
        parse: yaml.parse
      }
    },
    {
      test: /\.json5$/i,
      type: 'json',
      parser: {
        parse: json5.parse
      }
    },
  }
}

```

