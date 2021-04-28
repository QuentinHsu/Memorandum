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

![](../../.gitbook/assets/image%20%2816%29.png)

仅仅安装了还不能直接使用，还需要在 PowerShell 中配置

* 找到 PowerShell 的配置文件 在 PowerShell 执行如下命令，以显示 PowerShell 配置文件路径

```bash
$Profile
```

![](../../.gitbook/assets/image%20%2814%29.png)

* 在该文件中配置如下内容

```bash
Import-Module posh-git # 引入 posh-git
Set-PSReadlineKeyHandler -Key Tab -Function Complete # 设置 Tab 键补全
```

重新打开以生效。

