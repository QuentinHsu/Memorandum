# Vue CLI 2

## Build

### 取消 Source Map 文件

所谓的 Source Map 文件，是指在打包后 dist 文件夹下 JavaScript，CSS 打包文件相对应的 Map 文件，Source Map 文件是未经加密压缩过的文件，且在生产环境使用能方便看到报错。所以相对于加密压缩过的文件，Source Map 文件体积是有点大的，比如可能是 1:8 的差距。

假如生产环境不会使用该类型文件，那么我们很有必要不在 Build 的时候不去生产该类文件！以减少编译时间和减小整个文件体积。

/config/index.js

```javascript
build: {
    // ……
    /**
     * 该选项控制打包时 Source Map 文件输出
     * true：生成
     * false：不生成
     */
    productionSourceMap: true,
    // ……
}
```

