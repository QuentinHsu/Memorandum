# About package-lock

## 按照 package-lock 文件内容安装 package

### npm

当项目根目录下存在文件 package-lock.json 时，就可以使用下述命令

```text
npm ci
```

该命令，还可以当作 `npm install --force` 命令来使用。因为它会在安装包之前，自动删除原有的 node\_modules 文件夹下所有内容。

### yarn

当项目根目录下存在文件 yarn-lock.json 时，直接使用下述命令即可

```bash
yarn
// 等效于
yarn install
```



