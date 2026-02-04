---
sidebar: false
outline: deep
next: false
navbar: false
---

# OpenClaw 部署教程

## 资源链接

| 类型 | 地址 |
|------|------|
| 项目地址 | https://github.com/openclaw/openclaw |
| Docker 镜像 | https://hub.docker.com/r/smanx/openclaw |
| 免费 API | https://platform.iflow.cn |
| 免费服务部署 | https://zeabur.com |

## Docker 部署

### 快速启动

```bash
docker run -d --name openclaw -p 18789:18789 -v openclaw:/root/.openclaw -e OPENCLAW_GATEWAY_TOKEN=token smanx/openclaw
```

### 部署前准备

| 配置项 | 说明 |
|--------|------|
| 镜像名称 | `smanx/openclaw` |
| 环境变量 | `OPENCLAW_GATEWAY_TOKEN` |
| 端口 | `18789` |
| 数据卷 | `/root/.openclaw` |

## 配置模板

```
{
  "models": {
    "providers": {
      "custom-openai": {
        "baseUrl": "https://apis.iflow.cn/v1",
        "apiKey": "sk-xxxxxxxxxxxxxxxxxxxxxx",
        "api": "openai-completions",
        "models": [
          {
            "id": "qwen3-coder-plus",
            "name": "qwen3-coder-plus",
            "reasoning": false,
            "input": [
              "text"
            ],
            "cost": {
              "input": 0,
              "output": 0,
              "cacheRead": 0,
              "cacheWrite": 0
            },
            "contextWindow": 128000,
            "maxTokens": 4096
          }
        ]
      }
    }
  },
  "agents": {
    "defaults": {
      "model": {
        "primary": "custom-openai/qwen3-coder-plus"
      },
      "maxConcurrent": 4,
      "subagents": {
        "maxConcurrent": 8
      }
    }
  },
  "commands": {
    "native": "auto",
    "nativeSkills": "auto"
  },
  "gateway": {
    "port": 18789,
    "mode": "local",
    "bind": "lan",
    "controlUi": {
      "allowInsecureAuth": true
    }
  }
}

```

