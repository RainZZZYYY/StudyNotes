---
aliases:
  - 多API配置
  - 多模型Agent
created: 2026-05-11
tags:
  - tools
  - reference
---

- [ ] 开头已确认
# Claude 多模型配置

Claude Code 的 `settings.json` 支持在 `env` 中为三种模型级别分别指定模型名，但共用同一个 API key 和 base URL。

## 关键点

- **多模型 ✅ 原生支持**：`ANTHROPIC_DEFAULT_HAIKU_MODEL`、`ANTHROPIC_DEFAULT_SONNET_MODEL`、`ANTHROPIC_DEFAULT_OPUS_MODEL` 分别指定不同模型名，Agent 通过 `model` 参数选择
- **多厂商 ❌ 不原生支持**：`ANTHROPIC_API_KEY` 和 `ANTHROPIC_BASE_URL` 只有一套，无法直连多个不同后端
- **跨厂商方案**：本地跑 API 代理（如 [LiteLLM](https://github.com/BerriAI/litellm)、[One API](https://github.com/songquanpeng/one-api)），根据模型名路由到不同厂商，settings.json 只需指向本地代理地址
- **项目级隔离**：不同项目目录可以放各自的 `.claude/settings.json`，实现不同项目用不同 key/后端，但同一会话内各 Agent 仍走同一配置

## 怎么用

代理路由示意（LiteLLM）：

```yaml
# litellm proxy config
model_list:
  - model_name: deepseek-v4-pro
    litellm_params:
      model: deepseek/deepseek-chat
      api_key: sk-deepseek-xxx
  - model_name: claude-sonnet-4-6
    litellm_params:
      model: anthropic/claude-sonnet-4-6
      api_key: sk-anthropic-xxx
```

settings.json 统一指向代理：

```json
{
  "env": {
    "ANTHROPIC_BASE_URL": "http://localhost:4000/anthropic",
    "ANTHROPIC_API_KEY": "sk-litellm-proxy-key"
  }
}
```

Agent 使用时选模型名，代理层自动路由到对应厂商。

## 关联

- [[Claude技能开发]]
- [[Claude技能清单]]

- [ ] 结尾已确认
