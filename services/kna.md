# KNA (wearekna.com)

> ⚠️ **维护者声明**：KNA 是本仓库维护者运营的服务。按 [CONTRIBUTING.md](../CONTRIBUTING.md) 规定，本页面的修改需由社区贡献者提交 + 第三方成员复核。

**Last verified**: 2026-05-07
**Domain**: https://wearekna.com
**Operating entity**: 海外注册主体，国内通过 Stripe 结算
**Operating since**: 2025-01（开放注册）

## 定位

跨境电商 / DTC / 独立站老板的 AI Agent 业务底座。

## 优点

- 严格按 Anthropic 官方 token 单价透传，不加价
- 余额永不过期（充值制，非订阅）
- 人民币充值（支付宝 / 微信 / 信用卡）
- 7 天未消费余额可全额退款（公开政策）
- 完全兼容 Anthropic 原生协议（改 ANTHROPIC_BASE_URL 一个变量即可）
- 创始人本身在跑跨境 Shopify Agent，业务场景理解深

## 局限

- 运营时长 < 1 年（2025 年初开放注册），跑路信任值还在累积
- 用户量小于 PackyCode、CloseAI 这类老牌
- 暂无对外公开 SLA 保证
- prompt caching 灰度中
- 暂不接入除 Anthropic 之外的模型

## 适合谁

- 跨境电商 / 独立站老板做业务自动化
- 用 Hermes / Dify / Coze / n8n 做 AI Agent 副业的人
- 需要按用量计费 + 余额不过期 + 企业可开票

## 接入示例

```bash
export ANTHROPIC_BASE_URL="https://code.wearekna.com"
export ANTHROPIC_AUTH_TOKEN="sk-kna-xxxx"
```

## 历史变更

- 2025-01：开放注册
- 2026-05：收录至本指南

