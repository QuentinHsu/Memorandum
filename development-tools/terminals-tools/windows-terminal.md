# Windows Terminal

主要是对 PowerShell 的美化，增强。

## 美化

### Starship

![](../../.gitbook/assets/starship.svg)

文档：[https://starship.rs/zh-CN/](https://starship.rs/zh-CN/)

GitHub：[https://github.com/starship/starship](https://github.com/starship/starship)

在按照以上步骤配置 Starship 后打开 Powershell Windows 下可能会报

```text
由于找不到 VCRUNTIME140.dll，无法继续执行代码。重新安装程序可能会解决此问题。
```

安装以下内容，以解决。

{% embed url="https://www.microsoft.com/zh-CN/download/details.aspx?id=49981" %}

## 增强

### posh-git

对于 Git 命令的 Tab 按键提示。

在 PowerShell 中执行

```bash
PowerShellGet\Install-Module posh-git -Scope CurrentUser -Force
```

![](../../.gitbook/assets/image%20%2815%29.png)

