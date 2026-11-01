# StreamBridge 项目资料

这是我个人整理的 StreamBridge Docker 直播自动化项目资料仓库。这里保存上游源码、作者部署教程、Docker 镜像地址，以及自己的部署笔记；**本仓库不是上游项目的官方仓库，也不包含上游源码副本**。

## 上游项目的三个地址

| 类型 | 地址 | 用途 |
|---|---|---|
| GitHub 源码 | https://github.com/yyzq-cf/stream-bridge | 查看源代码、版本更新、项目说明 |
| 中文部署教程 | 待补充准确链接 | 暂不写入未经核实的地址 |
| Docker Hub 镜像 | https://hub.docker.com/r/ywsj/stream-bridge | 拉取镜像；镜像标签：`ywsj/stream-bridge:latest` |

## 项目用途

根据上游 GitHub README，StreamBridge 是一个直播流管理与转推工具，包含：

- 多平台直播状态监控和自动转推
- 视频文件、在线视频直链推流
- 视频循环播放
- RTMP 推流目标管理
- Docker 部署，支持 amd64 和 arm64
- Web 管理界面，默认端口为 5300

具体功能以[上游 README](https://github.com/yyzq-cf/stream-bridge)和实际部署版本为准。

## 本项目的部署目标

- 直播路数：1 路
- 使用场景：定时/计划直播（具体定时启动能力需部署后核实）
- 月预算：约人民币 150 元
- 计划环境：Linux VPS + Docker Compose
- 初步配置方向：2 vCPU、2 GB RAM；网络稳定性和持续上行带宽优先

## 文件说明

- [部署说明](docs/deployment.md)
- [VPS 配置建议](docs/vps-config.md)
- [YouTube 推流说明](docs/streaming.md)
- [上游地址清单](docs/source-links.md)

## 安全提醒

- 本仓库为公开仓库，**不要提交 YouTube Stream Key、VPS 密码、SSH 私钥、API Token、真实的 .env 文件或个人访问凭据**。
- 管理员密码和 Session 密钥必须自行设置强随机值。
- 首次部署后立即修改默认凭据，并限制管理端口访问；如使用公网访问，建议配置 HTTPS 和防火墙。
- 转推或循环播放的内容必须拥有相应版权或授权，并遵守 YouTube 等平台规则。
