---
date: 2019-08-08T21:07:13+01:00
title: 'win10下安装Remote-SSH'
weight: 11
keywords:
  - code-server
description: 'win10下安装Remote-SSH'
---

本文主要讨论 [VS Code Remote Development](https://code.visualstudio.com/docs/remote/remote-overview) 中的 [Remote Development using SSH](https://code.visualstudio.com/docs/remote/ssh) 的安装

## env

- os: win10
- os-remote: ubuntu@192.168.168.137
- 

## 为什么要使用 remote

https://zhuanlan.zhihu.com/p/64505333


## 安装与配置


### 主要参考

- https://zhuanlan.zhihu.com/p/68577071
- https://blog.csdn.net/sixdaycoder/article/details/89947893
- https://www.cnblogs.com/xiaoqi/p/vs-code-remote.html

### 操作

安装完 `remote-ssh` 插件后，点`左下角 深绿色 图标`，选择 `remote-ssh Open Configuration file`

### 配置 Configuration file

然后选择 `C:\ProgramData\ssh\ssh_config`。不选择 `C:\Users\a\.ssh\config`。

参数的含义分别为：

- Host 连接的主机的名称，可自定
- Hostname 远程主机的IP地址
- User 用于登录远程主机的用户名
- Port 用于登录远程主机的端口
- IdentityFile 本地的id_rsa的路径

#### `Identifier "C:\Users\a\.ssh\id_rsa"` 会出错

配置过程中，指定`Identifier "C:\Users\a\.ssh\id_rsa"`也会出错，具体原因，不清楚。

#### 最终配置

如下：

```
# Read more about SSH config files: https://linux.die.net/man/5/ssh_config
Host u137
    HostName 192.168.168.137
    User ubuntu
    Port 2222
    #Identifier "C:\Users\a\.ssh\id_rsa"
```

### 为什么不选择 `C:\Users\a\.ssh\config`？

不选择 `C:\Users\a\.ssh\config`的原因如下：

- `C:\Users\a\.ssh\config` 已被 wsl 用户 u 使用，且，用于 wsl用户u 与 github.com 通信。如果在这里修改了 `C:\Users\a\.ssh\config` 就会破坏  wsl用户u 与 github.com 通信。导致出现下面的提示：

```bash
DESKTOP-APB1HCJ% git clone git@github.com:eiuapp/vscode-handbook.git
Cloning into 'vscode-handbook'...
Bad owner or permissions on /mnt/c/Users/a/.ssh/config
fatal: Could not read from remote repository.

Please make sure you have the correct access rights
and the repository exists.
DESKTOP-APB1HCJ% pwd
```

