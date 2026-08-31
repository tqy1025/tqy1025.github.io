---
layout: post
title: "Note：当我拿到 IP 后该从哪里入手（初步侦察）"
date: 2026-08-31 08:00:00 +0800
categories: [Web-security]
tags: [总结]
---

> 本文仅用于 CTF、个人靶场和经过授权的安全测试，并将随着学习持续更新。

## 版本信息

- 当前版本：`v1`
- 更新日期：`2026-08-31`

## 步骤一：访问目标 URL

首先访问目标，获取页面内容和 HTTP 响应头：

```bash
curl -i http://<目标IP>/
```

只查看响应头：

```bash
curl -I http://<目标IP>/
```

跟随重定向：

```bash
curl -iL http://<目标IP>/
```

访问 HTTPS：

```bash
curl -ik https://<目标IP>/
```

重点关注：

- HTTP 状态码
- `Server`
- `Location`
- `Set-Cookie`
- `Content-Type`
- 页面标题和注释
- 服务器或框架报错信息

## 步骤二：检查 Git 泄漏

检查 `.git` 目录：

```bash
curl -i http://<目标IP>/.git/
```

检查当前分支：

```bash
curl -i http://<目标IP>/.git/HEAD
```

检查 Git 配置：

```bash
curl -i http://<目标IP>/.git/config
```

判断依据：

1. `/.git/` 返回 `403`，说明目录可能存在，但禁止直接浏览。
2. `/.git/HEAD` 返回 `ref: refs/heads/master` 或 `ref: refs/heads/main`，说明 Git 元数据可以读取。
3. `/.git/config` 返回 `[core]`、`[remote "origin"]` 等配置，基本可以确认存在 Git 泄漏。

## 更新记录

| 版本 | 日期         | 内容               |
| -- | ---------- | ---------------- |
| v1 | 2026-08-31 | 增加目标访问与 Git 泄漏检查 |
