# CoderPlan (coderplan.ai)

**Last verified**: 2026-06-02
**Domain**: https://coderplan.ai
**Operating entity**: CoderPlan AI
**Operating since**: 2025

## 定位

AI 编程工具用户的一站式 LLM API 网关，统一接入 Claude/GPT/Gemini 等主流模型。

## 优点

- 支持 Claude (Opus/Sonnet/Haiku) + GPT + Gemini 等多模型，一个 API Key 全搞定
- 完全兼容 Anthropic 原生协议 + OpenAI 兼容协议
- Claude Code / Cursor / Cline / Aider / Codex CLI 开箱即用
- 按官方价透明计费，无隐藏加价
- 充值制，余额永不过期
- 支持 prompt caching，长 session 成本更低

## 局限

- 运营时长相对较短
- 暂无公开 SLA 保证
- 国际用户为主，人民币支付渠道有限

## 适合谁

- 用 Claude Code / Cursor / Cline 等工具的开发者
- 需要同时使用多个 LLM 模型的 AI 应用开发者
- 想用一个统一 API 网关替代多个 API Key 的团队

## 接入示例

```bash
# Anthropic 原生协议
export ANTHROPIC_BASE_URL="https://api.coderplan.ai"
export ANTHROPIC_API_KEY="sk-xxx"

# OpenAI 兼容协议
export OPENAI_API_BASE="https://api.coderplan.ai/v1"
export OPENAI_API_KEY="sk-xxx"
```

## 实测数据

> 待补充。请按 [README.md 第六节](../README.md#六独立验证方法重要) 标准提供透传计费 / 延迟 / 工具兼容性 / 退款流程四项实测。

## 用户反馈

> 待社区贡献者补充。

## 历史变更

- 2026-06：提交收录申请
