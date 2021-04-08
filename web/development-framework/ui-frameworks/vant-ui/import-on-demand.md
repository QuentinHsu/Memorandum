# 自动按需导入

手动导入啥的都太麻烦了，还是尽量自动化。  
虽然官方推荐的这个“自动按需导入”，也还是需要手动写入一些对应（少量）内容。

## 安装

### 安装 vant

```text
yarn add vant
```

### 安装 babel-plugin-import

```bash
yarn add babel-plugin-import -D
```

## 配置

* 在 babel-plugin-import 配置 vant

```javascript
// babel.config.js
module.exports = {
  plugins: [
    ['import', {
      libraryName: 'vant',
      libraryDirectory: 'es',
      style: true
    }, 'vant']
  ]
}
```

* 你需要啥相关组件，直接在下方的 import 中按需导入，并 Vue.use（可链式 use 🤣）。

```javascript
// main.js
import {
  Button,
  Tag
} from 'vant';
Vue.use(Button).use(Tag)
```

## 使用

这时，就可以在 HTML 模块中使用 vant 组件了。

