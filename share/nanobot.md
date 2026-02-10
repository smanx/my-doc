---
sidebar: false
outline: deep
next: false
navbar: false
---

# nanobot 部署教程


## 资源链接

| 类型 | 地址 |
|------|------|
| 项目地址 | https://github.com/HKUDS/nanobot |
| Docker 镜像 | https://hub.docker.com/r/smanx/nanobot |
| 免费 API | https://platform.iflow.cn |
| 免费服务部署 | https://zeabur.com |
| QQ接入 | https://q.qq.com |


## Docker 部署

### 快速启动

```bash
docker run -d --name nanobot -v nanobot:/root smanx/nanobot
```

### 部署前准备

| 配置项 | 说明 |
|--------|------|
| 镜像名称 | `smanx/nanobot` |
| 数据卷 | `/root` |

### 环境变量

| 环境变量 | 说明 |
|----------|------|
| `NANOBOT_DEFAULT_MODEL` | 默认使用的模型名称 |
| `OPENAI_API_BASE` | OpenAI API 基础地址 |
| `OPENAI_API_KEY` | OpenAI API 密钥 |

```
NANOBOT_DEFAULT_MODEL=openai/qwen3-max
OPENAI_API_BASE=https://apis.iflow.cn/v1
OPENAI_API_KEY=
```

### 测试命令

```bash
nanobot agent -m "What is 2+2?"
```
