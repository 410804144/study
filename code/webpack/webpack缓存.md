### 缓存输出文件
- 修改配置文件
```javascript
module.exports = {
    ...
    output: {
        ...
        filename: '[name].[contenthash].js'
    },
    optimization: {
        moduleIds: 'deterministic',
        runtimeChunk: 'single',
        splitChunks: {
            cacheGroups: {
                test: /[\\/]node_modules[\\/]/,
                name: 'vendors',
                chunks: 'all',
            },
        },
    },
}
```
- contenthash 
  配置根据文件内容生成hash名称输出，如果文件内容不改，输出的文件名就不变
- optimization.runtimeChunk
  提取引导模版出来，不跟自己写的代码放一起
- optimization.splitChunks
  自定义将node_modules提取出来，这部分代码经常不会改动
- optimization.moduleIds
  防止因为不同文件import，导致所有文件的module.id变化，而导致hash值变化