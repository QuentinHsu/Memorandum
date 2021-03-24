# Chocolate

## 安装

Chocolate 官方安装文档：[https://chocolatey.org/install](https://chocolatey.org/install)

### Windows

**务必使用管理员权限打开 Power Shell 程序**，然后再执行下列安装命令

```bash
Set-ExecutionPolicy Bypass -Scope Process -Force; [System.Net.ServicePointManager]::SecurityProtocol = [System.Net.ServicePointManager]::SecurityProtocol -bor 3072; iex ((New-Object System.Net.WebClient).DownloadString('https://chocolatey.org/install.ps1'))
```

