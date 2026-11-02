# 分組

主題夾保持獨立，唔合併檔案。下面只係邊啲可以順住用同一策略，等主配置少幾行註解。策略喺主配置度定。

`https://raw.githubusercontent.com/tszchun0915/Ruleset/main/<主題>/<主題>.yaml` · `.list` · `.lsr`

## 次序

- `AI-Leak`（AI）→ `AI-HK-Allow`（Default）→ `AI`（AI）
- `MapleStory-Worlds`（Default）放 `KTR`（Korea）之前
- `Direct`、`AI` 放 `Global` 之前；`Global` 放 `CN` 之前
- 唔好併：`LineTV-Extra` 入 `Line`；`DNS-Leak-Test` 入 `AI-Leak`；`Dcard` 入 `TW`；`BiliBili-Extra` 入 `bilibili`；`TikTok-Extra` 入 `Tiktok`

## 同一策略

| 策略 | 順住寫 |
|---|---|
| China | CN、DianPing、DouYin-Extra、QQ-Tencent-Lite、QR-Order-CN、Taobao-Extra |
| DIRECT | Direct、CN-Local、AlipayHK、Pay-HK-Direct、QR-Order-HKTW、BiliBili-Extra |
| Default | Global、AppleService、Bing-Extra、Discord、Discord_Plus、Line、Line-Extra、MapleStory-Worlds |
| HongKong | HK、HKJC-Extra |
| Taiwan | AniGamer、LineTV-Extra、TW、TikTok-Extra |

`CN-Local`、`AlipayHK` 檔頭仍寫 China；公開說明預期 DIRECT。`Emby` 可以改指定策略，同 `Emby-Extra` 一樣用 Default 先至接埋。`Bank(HK)`、`Dcard` 都叫 Safe，唔係同一組。

## Clash

```yaml
rule-providers:
  CN:
    type: http
    behavior: classical
    format: yaml
    url: https://raw.githubusercontent.com/tszchun0915/Ruleset/main/CN/CN.yaml
    path: ./ruleset/CN.yaml
    interval: 86400
  # 同策略其餘主題照呢個寫，url 換 <主題>/<主題>.yaml

rules:
  - RULE-SET,AI-Leak,🧠 AI
  - RULE-SET,AI-HK-Allow,🚀 Default
  - RULE-SET,AI,🧠 AI
  - RULE-SET,Global,🚀 Default
  - RULE-SET,CN,🇨🇳 China
  - RULE-SET,DianPing,🇨🇳 China
  - RULE-SET,DouYin-Extra,🇨🇳 China
  - RULE-SET,QQ-Tencent-Lite,🇨🇳 China
  - RULE-SET,QR-Order-CN,🇨🇳 China
  - RULE-SET,Taobao-Extra,🇨🇳 China
```

Loon：`https://raw.githubusercontent.com/tszchun0915/Ruleset/main/CN/CN.lsr,policy=🇨🇳 China`
