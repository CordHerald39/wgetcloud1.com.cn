---
title: "HTTP、SOCKS 和 mixed 端口怎么分辨"
category: "tutorials"
label: "实用教学"
description: "HTTP、SOCKS 和 mixed 端口怎么分辨，按步骤核对条件、错误与恢复方法。"
date: "2026-10-04"
updated: "2026-10-04"
author: "WgetCloud中文资料编辑"
draft: false
---

## 看监听功能，不靠端口数字猜
Mihomo 可分别配置 HTTP、SOCKS 与 mixed 监听。mixed 端口同时接收 HTTP 和 SOCKS 请求；端口数字本身没有固定含义。先在实际客户端查看当前有效配置，而非从教程推断你的设备必定使用 7890。
## 请求方案要与监听匹配
应用填 HTTP 代理时，需要一个接受 HTTP 的端口；SOCKS 请求则需要相应支持。填错可能导致协议错误，即便客户端处于运行状态。若端口已被其他程序占用，检查启动日志，先确认哪个程序在监听。
## 建立一张本机对照表
记录用途、绑定地址和端口，只保存本人机器信息。示意：浏览器手动代理对应 HTTP，curl SOCKS 测试对应 SOCKS，支持 mixed 的入口可按文档复用。此表不是 WgetCloud 服务端节点地址，不能用它代替订阅配置。
## 完成后检查接管范围
同一网页分别在浏览器和命令行验证，注明每次使用的方案。不要为了修本机连接把监听地址随意改成所有网卡；局域网访问属于另一项配置，需要单独评估访问权限。
## 依据与下一步
[Mihomo 代理端口文档](https://wiki.metacubex.one/config/inbound/port/)；[curl 手册](https://curl.se/docs/manpage.html)。参阅[显式代理检查](/tutorials/curl-explicit-proxy/)。
