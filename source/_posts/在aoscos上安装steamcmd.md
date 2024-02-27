---
title: 在AOSCOS上安装steamcmd
date: 2024-02-27 15:27:04
tags:
---

## 安装依赖

```bash
sudo oma install gcc+32
```

## 下载并解压缩适用于 Linux 的 SteamCMD

```bash
curl -sqL "https://steamcdn-a.akamaihd.net/client/installer/steamcmd_linux.tar.gz" | tar zxvf -
```

中国内地用户可使用以下命令以使用内地节点：

```bash
curl -sqL "https://media.st.dl.bscstorage.net/client/installer/steamcmd_linux.tar.gz" | tar zxvf -
```

## 运行

```bash
./steamcmd.sh
```

等待steamcmd更新完成，您就可以享用此应用了！

## 参考资料

[VALVE Developer Community](https://developer.valvesoftware.com/wiki/SteamCMD:zh-cn)
