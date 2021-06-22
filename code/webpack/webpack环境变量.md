### webpack命令后可以配置--env参数，出入任意数量的环境变量
- webpack.config.js配置
```javascript
const path = require('path')

module.exports = (env) => {
    console.log('Goal: ', env.goal) // 'local'
    console.log('Production:', env.production) // true
    
    return {
        entry: './src/index.js',
        output: {
            filename: 'bundle.js',
            path: path.resolve(__dirname, 'dist'),
        },
    }
}
```
- 执行指令
```shell
npx webpack --env goal=local --env production --progress
```
