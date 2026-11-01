# Docker 部署说明

本仓库提供的是部署模板，实际功能和环境变量以[上游项目](https://github.com/yyzq-cf/stream-bridge)当前版本为准。

## 1. 准备

- 一台 Linux VPS
- 已安装 Docker Engine 和 Docker Compose Plugin
- 开放/放行 TCP 5300（如果需要直接通过公网访问管理页面）
- 准备强管理员密码和随机 Session 密钥

## 2. 准备环境变量

在仓库目录中复制示例文件：

```bash
cp .env.example .env
nano .env
```

把 `ADMIN_PASS` 和 `SECRET_KEY` 替换成自己的随机值。不要把真实的 `.env` 上传到 GitHub。

可使用以下命令生成随机 Session 密钥：

```bash
openssl rand -hex 32
```

## 3. 启动容器

```bash
docker compose pull
docker compose up -d
docker compose ps
docker compose logs -f streambridge
```

管理页面默认端口为：

```text
http://服务器公网IP:5300
```

生产环境建议通过 HTTPS 反向代理访问，并用防火墙限制管理页面的来源 IP。不要把管理页面和默认密码直接暴露在公网。

## 4. 更新

```bash
docker compose pull
docker compose up -d
```

## 5. 数据目录

Compose 将宿主机当前目录下的 `./data` 映射到容器内 `/app/data`。该目录用于持久化数据。升级前建议先备份。

## 重要安全事项

- 不要使用上游示例中的默认密码 `admin123`。
- 不要将真实 Stream Key、密码、私钥或 `.env` 文件提交到公开仓库。
- 首次部署后立即确认管理员密码、端口暴露范围和 HTTPS 配置。
- 在实际开播前先用测试直播验证画面、声音、循环和断线恢复。
