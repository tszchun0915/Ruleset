# 分組

主題夾保持獨立，唔合併檔案。下面只係邊啲可以順住用同一策略，等主配置少幾行註解。策略喺主配置度定。

`https://raw.githubusercontent.com/tszchun0915/Ruleset/main/<主題>/<主題>.yaml` · `.list` · `.lsr`

## 次序

- `AI-Leak`（AI）→ `AI-HK-Allow`（Default）→ `AI`（AI）→ `AppleService`（Default）→ `Direct` → `Global`；`Global` 放 `CN` 之前
- `AppleService` 係國際媒體／新聞／TestFlight／國際地圖瓦片，另加香港 Apple ID 登入（`albert`、`gsa`、`gsa-ws`、`idmsa`、`appleid.apple.com`、`id.apple.com`、`account.apple.com`、`iforgot.apple.com`、`setup.icloud.com` 同 `pNN-setup.icloud.com` 分區）。`17.0.0.0/8` 已唔喺 Direct；Direct 只留 APNs 官方細段。AppleService 仍要排喺 Direct 前面：Direct 有 `DOMAIN-SUFFIX,icloud.com`，排反會把 setup 分區直連
- `HKTR`（👟 HKTR）放 `KTR`（🇰🇷 Korea）之前；兩者都放 GEOIP、Direct 兜底之前。唔好併入 Default
- 韓跑域名、IP、PROCESS-NAME 只寫入 `KTR`。`HKTR` 只收港跑
- `MapleStory-Worlds`（Default）放 `KTR`（Korea）之前
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
  - RULE-SET,AppleService,🚀 Default
  - RULE-SET,Direct,DIRECT
  - RULE-SET,Global,🚀 Default
  - RULE-SET,CN,🇨🇳 China
  - RULE-SET,DianPing,🇨🇳 China
  - RULE-SET,DouYin-Extra,🇨🇳 China
  - RULE-SET,QQ-Tencent-Lite,🇨🇳 China
  - RULE-SET,QR-Order-CN,🇨🇳 China
  - RULE-SET,Taobao-Extra,🇨🇳 China
```

Loon：`https://raw.githubusercontent.com/tszchun0915/Ruleset/main/CN/CN.lsr,policy=🇨🇳 China`
