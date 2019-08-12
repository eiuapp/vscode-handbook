---
date: 2019-01-08T21:07:13+01:00
title: 'ubuntu下安装code server'
weight: 10
keywords:
  - code-server
description: 'ubuntu下安装code server'
---

安装 [code server](https://github.com/cdr/code-server)

## env

### clond server

- cloud: tencent cloud:
- os: ubuntu
- memory: 1GB

### local server

- os: ubuntu
- memory: 16GB

## step

### docker

#### （可跳过）内存要大于2G

```
ubuntu@VM-0-12-ubuntu:~/code-server$ docker run -it -p 8443:8443 -v "${PWD}:/home/coder/project" codercom/code-server --allow-http --no-auth
(node:5) [DEP0005] DeprecationWarning: Buffer() is deprecated due to security and usability issues. Please use the Buffer.alloc(), Buffer.allocUnsafe(), or Buffer.from() methods instead.
INFO  code-server v1.1156-vsc1.33.1
INFO  Additional documentation: http://github.com/cdr/code-server
INFO  Initializing {"data-dir":"/home/coder/.local/share/code-server","extensions-dir":"/home/coder/.local/share/code-server/extensions","working-dir":"/home/coder/project","log-dir":"/home/coder/.cache/code-server/logs/20190811033659113"}
INFO  Starting shared process [1/5]...
INFO  Starting webserver... {"host":"0.0.0.0","port":8443}
WARN  No certificate specified. This could be insecure.
WARN  Documentation on securing your setup: https://github.com/cdr/code-server/blob/master/doc/security/ssl.md
WARN
WARN  Launched without authentication.
INFO
INFO  Started (click the link below to open):
INFO  http://localhost:8443/
INFO
WARN  stderr {"data":"(node:18) [DEP0005] DeprecationWarning: Buffer() is deprecated due to security and usability issues. Please use the Buffer.alloc(), Buffer.allocUnsafe(), or Buffer.from() methods instead.\n"}
internal/child_process.js:366
    throw errnoException(err, 'spawn');
    ^

Error: spawn ENOMEM
    at ChildProcess.spawn (internal/child_process.js:366:11)
    at Object.spawn [as _spawn] (child_process.js:538:9)
    at t.async (/src/packages/server/out/cli.js:504:34598)
    at e.exports (/src/packages/server/out/cli.js:504:34099)
    at e (/src/packages/server/out/cli.js:504:32722)
    at Timeout.u [as _onTimeout] (/src/packages/server/out/cli.js:504:33015)
    at ontimeout (timers.js:436:11)
    at tryOnTimeout (timers.js:300:5)
    at listOnTimeout (timers.js:263:5)
    at Timer.processTimers (timers.js:223:10)
ubuntu@VM-0-12-ubuntu:~/code-server$
```

报错了。

所以，我先尝试其它方式安装吧。

参考：https://github.com/cdr/code-server/issues/232

知道，要正常安装 code-server 必须要有 2GB 的内存。

而且因为，不支持 windows 平台，所以，这里先放弃在 云端 部署了。

尝试在内网的一台机器上运行吧

#### 内存大于2GB

内网机器内存 16GB, 所以执行：


```bash
cd
pwd
ubuntu@utuntu:~$ docker run -d --restart always -p 8443:8443 -v "${PWD}:/home/coder/project" codercom/code-server --allow-http --no-auth
```

本地 chrome 打开：http://192.168.168.137:8443/ 即可使用（没设置密码登录，要改进）

#### Todo 设置密码登录

### Binaries

https://blog.csdn.net/Granery/article/details/90415636

#### 启动

如果下载的是 2.0 以上版本

```
./code-server --auth="password"
```

如果下载的是 1.\* 版本

```
./code-server
```

