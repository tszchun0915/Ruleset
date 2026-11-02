# Ruleset

域名規則集（Clash `.yaml`／小火箭 `.list`／Loon `.lsr`）。主配置同訂閱唔放呢度。完整 Loon 配置先用 `.lcf`。

## 思路

按用途拆主題：國際／地區限定／本地直連／安全／防洩漏。配置用 `RULE-SET` 引用；策略喺主配置度定，唔寫死喺呢個 README。主題夾保持分開。同一策略可以順住引用，見 `groups.md`。

本地點餐、支付、CN-Local、AlipayHK 一類，客戶端預期用 DIRECT。

## 主題（簡述）

| 主題 | 用途 |
|---|---|
| AI | 港澳未開放嘅 AI 服務 |
| AI-Leak | DNS／WebRTC 等洩漏相關 |
| Github | GitHub **下載**網域 |
| AniGamer | 動畫瘋 |
| AppleService | Apple 相關補充 |
| Bank(HK) | 香港銀行 |
| CN | 中國常用網域 |
| Global | 日常國際 App |
| CN-Local | 深圳通、KoolCenter |
| Direct | 適合直連嘅網域 |
| Discord | Discord |
| Emby | Emby／媒體 |
| HK | 香港媒體等 |
| HKJC-Extra | 馬會補充 |
| HKTR / KTR | 港／韓跑相關 |
| Line | LINE |
| LineTV-Extra | LINE TV |
| Rule | 封鎖／P2P 等 |
| TW | 台灣相關 |
| Tiktok | TikTok |
| USA | 美國相關 |
| bilibili | B 站 |
| DianPing | 大眾點評 |
| Taobao-Extra | 淘寶／天貓補充 |
| QQ-Tencent-Lite | QQ／支付安全頁（精簡） |
| DouYin-Extra | 抖音（非國際 TikTok） |
| QR-Order-CN | 大陸掃碼點餐 SaaS |
| QR-Order-HKTW | 港台掃碼點餐 |
| AlipayHK | AlipayHK |
| Pay-HK-Direct | PayMe／FPS |
| DNS-Leak-Test | DNS 洩漏檢測 |
| MapleStory-Worlds | 楓之谷世界 |
| Dcard | Dcard |
| Bing-Extra | Bing 補充 |
| BiliBili-Extra | B 站漫畫／貓耳補充 |
| TikTok-Extra | TikTok CDN 補充 |
| Line-Extra | LINE 補充 |
| Emby-Extra | Emby 點播補充 |

格式：`<主題>/<主題>.yaml` · `.list` · `.lsr`

最後更新：2026-11-02（Asia/Hong_Kong）

<!-- Maintained with Grok Bot -->
