---
title: vscode报错
---

## 故障现象

vscode在登陆


## 使用gnome-keyring

1. 安装`gnome-keyring`

```bash
sudo oma install gnome-keyring
```
2. 在`vscode`中启用`gnome-keyring`

* 方式一：编辑`～/.vscode/argv.json`，在最后一个配置项后添加以下内容：

```json
	"password-store": "gnome-libsecret",
```

* 方式二：在`vscode`中，使用快捷键`CTRL + shift + P`，打开命令面板，找到以下命令并打开：

![](../img/)

在打开的配置文件中，添加以下项，并重启`vscode`.
```json
	"password-store": "gnome-libsecret",
```
注意：配置文件的每一项配置应以`,`结尾。