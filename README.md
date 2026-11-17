# qhb-cdn-pool

QHB CDN 加密成品池，由私有仓 `cdn-sentinel` 每轮自动推送。只存密文 `cdn.json.enc`。

## 拉取地址

```
https://raw.githubusercontent.com/Ablefengy/qhb-cdn-pool/main/cdn.json.enc
```

客户端（`sync_cdn_local.bat`）拉到本地后由 `tools/cdn_crypto.py` 解密、家宽复验，再写入配置。
密文为四态判定明细（`schema=2`），非完整可用池。
