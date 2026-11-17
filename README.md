# qhb-cdn-pool

QHB CDN 成品池公开快照，由私有仓 `Ablefengy/cdn-sentinel` 的 `scan-cdn` 工作流每轮自动推送。

## 这是什么

- `cdn.json`（`schema=2`）：四平台 6686 / 1717 / 333 / 3377 的 CDN 判定明细，四态口径：
  - `alive`：云端两步全过，可新增
  - `waf_alive`：TLS 证活、但抢包路径被云端出口 WAF 拦，**需家宽复验后才能用**
  - `dead` / `unknown`：按原因分组，不直接删池
- `CDN.md`：人看的看板。

⚠️ 本文件**不是完整可用池**，请勿直接覆盖本地 `data/cdn_config.json`，务必经过家宽抢包路径复验。

## 客户端怎么用

`D://ai//qhb//sync_cdn_local.bat`（双击即可）默认从本仓 raw 拉取：

```
https://raw.githubusercontent.com/Ablefengy/qhb-cdn-pool/main/cdn.json
```

免 gh、免登录，任何电脑都能跑。流程：raw 拉取 → 家宽复验 → 写 `cdn_config.json`（写前备份）→ 触发健康检测刷新 state。
重名冲突/换源可用 `python tools/sync_from_cdn_json.py --source gh`（走私有仓，需 gh 登录态）。

本仓只放成品快照，不含任何脚本或凭据。
