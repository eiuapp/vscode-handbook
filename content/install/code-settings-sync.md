---
date: 2019-08-12T10:07:13+01:00
title: 'code-settings-sync设置'
weight: 13
keywords:
  - code-settings-sync
  - sync
description: '通过code-settings-sync同步vscode的配置'
---


## code-settings-sync

- https://github.com/shanalikhan/code-settings-sync

## 安装

其实只要 简单浏览一下 https://github.com/shanalikhan/code-settings-sync 的 README.md 文件就可以知道安装了。

重复摘抄如下

### Configure Settings Sync


Settings Sync Configuration page will be opened automatically on code start and requires two things to setup:

1. Github Token
2. Github Gist Id

Github Token needs to be retrived by your Github account while Settings Sync creates GIST if you are first time user.

Following are the steps you need to perform to configure.

- Click on `Login with Github` .
- Login Github on Browser and close the browser tab once you get Success message.
- If you are using Settings Sync first time GIST will be created automatically when you upload your settings.
- If you already have Github Gist, new window will be opened to allow you to select the Github Gist or `Skip` to create new Gist.



![Login with GitHub](https://shanalikhan.github.io/img/login-with-github.png)


![Existing Gist](https://shanalikhan.github.io/img/existing-gist.png)


You can always **verify created gist** by going to `https://gist.github.com` and checking for a gist named `cloudSettings`

---

有点像 https://www.whidy.net/visual-studio-code-settings-sync-introduction.html 这里的程序。

### （可跳过）如果英文不好

先简单看浏览下面的网站，实际操作，不同

https://gitee.com/hjm100/codes/oi5nuevyl82zp3hdtc19g18

https://www.cnblogs.com/kenz520/p/7416836.html

https://www.jianshu.com/p/a08219737291

## 同步的内容

通过去查看 https://gist.github.com/${githubAccountName}/ 知道 会有一个 cloudSettings 的 gist. 这个gist就是我们的vscode配置啦！

在 extensions.json 部分，通过搜索`metadata`, 得知，显示的只是 Enable 状态的 extensions. 

如果您安装了extensions, 但是，并没有 Enable, 则不会上传。

### 哪里看同步了哪些内容？

#### vscode 输出

来一个示例：

```
CODE SETTINGS SYNC UPLOAD SUMMARY
Version: 3.4.1
--------------------
GitHub Token: GitHubTTTTTTTTTTTTTTTTTTTTTTTToken
GitHub Gist: GitHubGGGGGGGGGGGGGGGist => 这个就是 gist的编号 https://gist.github.com/eiuapp/GitHubGGGGGGGGGGGGGGGist
GitHub Gist Type: Secret

Restarting Visual Studio Code may be required to apply color and file icon theme.
--------------------
Files Uploaded:
  extensions.json > extensions.json
  settings.json > settings.json

Extensions Ignored:
  No extensions ignored.

Extensions Removed:
  No extensions removed.

Extensions Added:
  remote-ssh v0.45.4
  remote-ssh-edit v0.45.4
  remote-ssh-explorer v0.45.4
  remote-wsl v0.39.2
--------------------
Done.
```

#### gist的revisions

1. 找开 gist 后点击 `Code` 边上的 `Revisions` 。或者
2. 在 gist url 地址后 手工加上 `/revisions`, 回车。即，形如： https://gist.github.com/$account/$gistHash/revisions

## 问题

### 如何使用历史某次vscode配置

多次上传后，如果我想使用某一次commit的gist下的vscode配置，应该怎么办？