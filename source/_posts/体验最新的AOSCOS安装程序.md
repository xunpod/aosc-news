---
title: 体验最新的AOSCOS系统安装器
date: 2024-02-27 16:20:31
tags:
hide: false
---

AOSCOS系统安装器分为前端[deploykit-gui](https://github.com/AOSC-Dev/deploykit-gui)和后端[deploykit-backend](https://github.com/AOSC-Dev/deploykit-backend)


## 更新系统并安装依赖

```bash
sudo oma upgrade
sudo oma install devel-base llvm parted rustc yarn
```
## 编译`deploykit-gui`

```bash
git clone https://github.com/AOSC-Dev/deploykit-gui.git
cd deploykit-gui
yarn && yarn tauri build

```

## 编译`deploykit-backend`

```bash
git clone https://github.com/AOSC-Dev/deploykit-backend
cd deploykit-backend
cargo build --release
```
完成编译后，将`deploykit-backend/deploykit-dbus.conf.debug`重命名为`deploykit-dbus.conf`，将以下编译成果存放到其他介质上，确保下文启动的`livekit`环境能访问到它们：

```bash
deploykit-gui/src-tauri/target/release/deploykit-gui 
deploykit-backend/deploykit-dbus.conf
deploykit-backend/target/release/deploykit-backend
```

## 启动livekit环境

1. 在官网下载[livekit]()镜像，并刻盘启动。

在启动

## 故障处理

1. `cargo build --release`报错，需要更新版本的`rustc`：

```bash
error: package `zvariant_derive v4.0.0` cannot be built because it requires rustc 1.75 or newer, while the currently active rustc version is 1.74.0
Either upgrade to rustc 1.75 or newer, or use
cargo update zvariant_derive@4.0.0 --precise ver
where `ver` is the latest version of `zvariant_derive` supporting rustc 1.74.0

```
使用`sudo oma topic`打开测试源，按`Enter`或空格键选中`rustc 1.75`或者更高版本。而后按`ESC`应用更改，等待`oma`刷新信息后，审阅并安装新版本`rustc`，再执行`cargo build --release`

2. 编译`deploykit-gui`时报错，提示生成deb失败：

```bash
Bundling deploykit-gui_0.0.0_amd64.deb (deploykit-gui/src-tauri/target/release/bundle/deb/deploykit-gui_0.0.0_amd64.deb)
       Error failed to bundle project: Failed to build data folders and files
error Command failed with exit code 1.
info Visit https://yarnpkg.com/en/docs/cli/run for documentation about this command.
```
不用担心，这是正常现象，忽略即可。