
安装 [code server](https://github.com/cdr/code-server)

## env

- cloud: tencent cloud:
- os: ubuntu

## step

### docker

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

### Binaries

https://blog.csdn.net/Granery/article/details/90415636


