# TeapotRouter（teapotrouter.com）

> ⚠️ **利益相关声明**：本条目由 TeapotRouter 运营方提交，尚未经第三方验证。按 [CONTRIBUTING.md](../CONTRIBUTING.md) 的反自我吹捧规则，建议由社区贡献者复核后再合并；后续对本页的修改同样欢迎社区监督。

**Last verified**: 2026-10-27 by [@anmutu](https://github.com/anmutu)
**Domain**: https://teapotrouter.com
**Operating entity**: 官网未披露注册主体（自我描述为独立中转服务；联系邮箱 support@teapotrouter.com）
**Operating since**: 未公开（Terms of Service 生效日 2026-09-29）

## 定位

预充值、按量计费的双协议网关：一把 Key 同时接 Claude Code（Anthropic 协议）与 OpenAI 系工具，主打每笔请求成本可对账。

## 优点

- 双协议单 Key：`ANTHROPIC_BASE_URL` 指向网关跑 Claude Code；OpenAI SDK 将 `base_url` 改为网关 `/v1` 即可
- 价格公开：站内价格表 + 免登录价格接口（https://teapotrouter.com/api/pricing）
- workspace 内每笔请求有模型、token 用量、费用与时间戳流水
- 支持组织级发 Key 与审计日志
- 可配置多条上游信道，单条失败时按配置改走其他路由
- 充值门槛低：$1 起，支持支付宝与国际卡

## 局限

- 运营时间短，官网未公开运营主体 / 注册信息
- 未找到公开退款政策页（Terms 称退款以订单 / 计费记录为准）
- Terms 明示不提供正常运行时间（uptime）保证
- 截至提交日暂无公开的第三方用户反馈
- 只提供 GPT 与 Claude 两条模型通道，无多模型集市

## 适合谁

需要同一把 Key 兼跑 Claude Code 与 OpenAI SDK、且要求逐笔请求成本可核对的小团队 / 组织。

## 实测数据

> 以下为运营方提交时（2026-10-26 22:03 UTC 前后）按本指南第六节方法自测的原始记录，建议第三方复核。
> 验证 Key（余额上限 $0.3，供本指南维护者 / 社区测试）：`sk-b7f4f5167934bdf9fbda43df563f88bad807579a7a8a75db`

### 6.1 透传计费验证

提供的测试 Key 在提交时点鉴权失败，未能完成扣费对账：

```
$ curl -s https://api.teapotrouter.com/v1/messages \
    -H "Authorization: Bearer sk-b7f4…75db" \
    -H "anthropic-version: 2023-06-01" \
    -H "content-type: application/json" \
    -d '{"model":"claude-sonnet-4-20250514","max_tokens":100,"messages":[{"role":"user","content":"Repeat exactly: hello world"}]}'
{"error":{"code":"","message":"Invalid token (request id: 202610262203254106863458268d9d6c68wCzIz)","type":"new_api_error"}}
```

免登录价格接口实测可用：

```
$ curl -s https://teapotrouter.com/api/pricing | jq -r '.pricing[].model_name'
gpt-6-astra
gpt-6.1-sol
```

### 6.2 延迟（10 次平均 / 中位数 / p95）

- 无有效 Key，只能测到网关鉴权层 RTT（请求被拒，不代表推理延迟）：
  - avg: 577 ms
  - median: 511 ms
  - p95: 595 ms
- 推理延迟待有效 Key 后按 6.2 标准补测

### 6.3 工具兼容性

| 工具 | 支持 | 备注 |
|---|---|---|
| Claude Code | ⚠️ | 官网提供 ANTHROPIC_BASE_URL 接入脚本；`/v1/messages` 路径可达，待有效 Key 实测 |
| Anthropic Python SDK | ⚠️ | 同上 |
| Cursor | 未测 | OpenAI 兼容路径 `/v1/chat/completions` 可达 |
| Cline | 未测 | |
| Aider | 未测 | |
| Hermes / Dify / Coze / n8n | 未测 | |

### 6.4 退款流程

- 退款窗口期：未公开
- 实测申请到到账：未实测
- 退款链接 / 政策页面：未找到独立退款页；Terms 第 3 条写明退款、折扣、税费等以订单 / 计费记录为准（https://teapotrouter.com/en/terms）

## 用户反馈

> 截至提交日暂无公开独立反馈，待社区补充（本条目为运营方提交，不自评）。

## 历史变更

- 2026-10-27：运营方提交收录申请（本 PR）
