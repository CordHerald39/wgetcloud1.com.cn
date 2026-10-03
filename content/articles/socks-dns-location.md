---
title: "SOCKS5 与 SOCKS5H 的区别：域名由谁解析"
category: "tutorials"
label: "实用教学"
description: "SOCKS5 与 SOCKS5H 的区别：域名由谁解析，按步骤核对条件、错误与恢复方法。"
date: "2026-10-04"
updated: "2026-10-04"
author: "WgetCloud中文资料编辑"
draft: false
---

## 区别在域名解析的位置
curl 的 socks5 代理方式由本地解析目标域名，socks5h 则让代理解析。两者是请求方式区别，不表示某一种方式一定更快或更安全；实际效果还取决于应用、配置与网络。
## 比较时只换代理方案
确认本人客户端提供 SOCKS 监听后，以其真实端口请求同一网址。示意为 `curl.exe --proxy socks5://127.0.0.1:7891 --max-time 20 -I https://example.com/`；再把方案改成 `socks5h://`。端口 7891 是示例，不代表 WgetCloud 的固定配置。
## 结果能说明什么
本地解析失败而代理解析成功时，可把调查范围缩到 DNS 路径；仍不能据此保证所有应用都遵循代理 DNS。若两次都连接拒绝，先修正监听端口，不必继续改 DNS。不要用 IP 直接替换 HTTPS 域名来“解决”证书问题。
## 与浏览器分开核对
浏览器可能还有自己的加密 DNS 设置，不能从 curl 结果推断浏览器一定采用相同路径。记录应用、代理方案、错误信息，再按对应客户端文档查配置。继续阅读[系统与应用请求检查](/tutorials/connection-check/)。
## 来源
[curl 官方 SOCKS 参数说明](https://curl.se/docs/manpage.html)。
