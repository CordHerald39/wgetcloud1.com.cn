---
title: "代理环境变量怎么查：避免命令行继续使用旧端口"
category: "tutorials"
label: "实用教学"
description: "代理环境变量怎么查：避免命令行继续使用旧端口，按步骤核对条件、错误与恢复方法。"
date: "2026-10-04"
updated: "2026-10-04"
author: "WgetCloud中文资料编辑"
draft: false
---

## 先确认当前进程的设置
更换客户端后，终端可能仍保留旧的代理环境变量。PowerShell 可运行 `Get-ChildItem Env: | Where-Object Name -Match 'proxy'` 查看名称与当前值；输出可能包含认证信息，应留在本机，不粘贴到公开帖子。
## 区分 URL 和变量名
curl 文档介绍 http_proxy、HTTPS_PROXY、ALL_PROXY 和 NO_PROXY。HTTP 代理变量的大小写处理有特殊规则；不要把其他程序的行为直接套用到 curl。`NO_PROXY` 可使匹配目标绕过代理，因此同一终端中不同域名可能出现不同路径。
## 用临时命令验证
先通过[显式代理请求](/tutorials/curl-explicit-proxy/)指定实际端口，而非立即改系统永久设置。如果显式请求成功、原请求失败，就检查旧变量和绕过列表；如果两者都失败，回到本地监听与节点检查。
## 更改后重新打开终端
需要修改时记录原值，一次改一个变量，并按所用应用文档验证。永久变量变更未必自动进入已启动的进程。不要让截图带出密码、令牌或个人订阅 URL，也不要用不存在的统一端口覆盖所有应用。
## 依据
[curl 官方环境变量说明](https://curl.se/docs/manpage.html)。
