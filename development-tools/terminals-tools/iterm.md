# iTerm

## 错误解决

### Problem Running git

在更新 macOS 版本后，会遇到 iTerm 低栏显示 Git 出现了问题，点击其⚠️图标就会弹出如下图的提示信息：

![](../../.gitbook/assets/image%20%287%29.png)

可 Git 功能是正常的。

### 解决方案

任意终端执行如下命令

```text
xcode-select --install
```

并同意安装执行命令后弹出来的内容。  
体积有点大，需耐心等待，可能需要科学上网。

安装完成后，即可恢复正常显示。

