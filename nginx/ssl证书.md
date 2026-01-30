---
title: SSL证书
description: Nginx - SSL证书
published: true
date: 2026-01-30T06:48:15.738Z
tags: openssl, acme, ssl
editor: markdown
dateCreated: 2026-01-30T01:32:13.128Z
---

# SSL证书

> Nginx 相关的 SSL证书 问题收集
{.is-info}


---

## 公网环境

```bash
# 一行下载最新版 → 进入目录
curl -L https://github.com/freemankevin/acme-ssl-breeze/archive/refs/tags/latest.tar.gz | tar -xz && cd acme-ssl-breeze-latest

# 只需改 3 个变量，然后执行
nano renew-ssl-cert.sh    # 修改 DOMAIN / BASE_DIR / RELOAD_CMD
chmod +x renew-ssl-cert.sh
./renew-ssl-cert.sh
```

## 内网环境

如果需要 `.cert` 格式，用这一行命令：

```bash
openssl req -x509 -newkey rsa:2048 -keyout localhost.key -out localhost.cert -days 3650 -nodes -subj "/C=CN/ST=State/L=City/O=Org/CN=localhost"
```

这样就会生成 `cert.cert`（证书）和 `key.key`（私钥）。

或者如果已经有 `.pem` 格式的证书，可以转换：

```bash
openssl x509 -in localhost.pem -out localhost.cert
```

---

[返回 Nginx](/nginx)
