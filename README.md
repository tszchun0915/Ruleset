# tszchun0915 規則整合包（2026-10-31，Asia/Taipei）

每個主題一個資料夾：`<主題>.yaml`（Clash/Mihomo rule-provider，classical）、`<主題>.list`（Shadowrocket）、`<主題>.lsr`（Loon）。
每個檔頭都寫咗來源、日期、改動。範圍太闊或者有問題嘅規則**冇刪走**，改為放喺檔尾做註解，需要嘅話自己開返。

## 數量
| 主題 | 條數 (.yaml / .list / .lsr) | 停用(檔尾註解) |
|---|---|---|
| AI | 117 / 117 / 117 | 19 |
| Github | 39 / 39 / 39 | 0 |
| AI-Leak | 68 / 68 / 68 | 5 |
| AniGamer | 7 / 8 / 8 | 2 |
| AppleService | 69 / 88 / 88 | 0 |
| Bank(HK) | 194 / 196 / 196 | 50 |
| CN | 143 / 143 / 143 | 0 |
| Direct | 294 / 298 / 298 | 0 |
| Discord | 65 / 65 / 65 | 0 |
| Emby | 61 / 61 / 61 | 0 |
| HK | 18 / 18 / 18 | 0 |
| HKTR | 7 / 7 / 7 | 0 |
| KTR | 23 / 23 / 23 | 0 |
| Line | 38 / 38 / 38 | 0 |
| Rule | 69 / 73 / 73 | 2 |
| TW | 7 / 7 / 7 | 0 |
| Tiktok | 61 / 62 / 62 | 0 |
| USA | 26 / 26 / 26 | 0 |
| WishRunner | 8 / 8 / 8 | 0 |
| bilibili | 130 / 134 / 134 | 0 |

.yaml 少過 .list：Clash/Mihomo 唔支援 USER-AGENT / URL-REGEX，所以自動略過。.lsr 已經將 DST-PORT 轉做 Loon 用嘅 DEST-PORT，UDP 用 PROTOCOL,UDP。

## 特別處理
- **AI**：只放港澳**未開放**嘅服務：OpenAI/ChatGPT/Sora、Anthropic/Claude、Gemini API/AI Studio、Gemini Notebook(NotebookLM)、Google Labs/Jules/Antigravity，加埋 AI 圖片/影片/音樂工具。
  已移除港澳用得到嘅：Gemini 網頁/App（2026-03 起香港開放）、Copilot、Meta AI、Perplexity、Grok、Apple Intelligence、Adobe Firefly。
  亦都修正咗 Clash AI.yaml 第 166–202 行嘅全形空格，呢啲空格會令成個 YAML 解析失敗。
- **Github**：只放「下載」用嘅網域，github.com 網頁同 API 唔包括。
  新加入 **release-assets.githubusercontent.com**：而家 Release 下載會 302 轉去呢度，你原本冇呢個網域，所以先會慢。
  電腦版用 PROCESS-NAME git / git-remote-https，令 git clone 都行 VPN。
- **Bank(HK)**：以 SR 2026-09-29 修訂版做基礎。Clash 舊版多出嘅 50 條放咗喺檔尾註解。
- **Rule**：停用 `DOMAIN-KEYWORD,gov`，因為會中 gov.hk，改為 `DOMAIN-SUFFIX,gov.cn`；亦停用 `DST-PORT,10000-65535`。
- **AI-Leak**：停用 `DOMAIN-KEYWORD,stun/turn/cloudflare` 同 `DOMAIN-SUFFIX,1.1.1.1/1.0.0.1`（IP 唔係域名）。
- 修正咗幾類格式錯誤：
  - 行內 `# 註解`，SR/Loon 會當成無效規則
  - `DOMAIN-SUFFIX, x` 逗號後多咗空格
  - IP 冇 /32
  - 兩個 app 版本唔一致嘅地方，已合併

## 直接用人哋（更新更勤）嘅規則
全部 2026-10-31 實測 HTTP 200。
| 用途 | Clash/Mihomo | Shadowrocket | Loon |
|---|---|---|---|
| Telegram (blackmatrix7) | https://raw.githubusercontent.com/blackmatrix7/ios_rule_script/master/rule/Clash/Telegram/Telegram.yaml | https://raw.githubusercontent.com/blackmatrix7/ios_rule_script/master/rule/Shadowrocket/Telegram/Telegram.list | https://raw.githubusercontent.com/blackmatrix7/ios_rule_script/master/rule/Loon/Telegram/Telegram.list |
| Netflix (blackmatrix7) | https://raw.githubusercontent.com/blackmatrix7/ios_rule_script/master/rule/Clash/Netflix/Netflix.yaml | https://raw.githubusercontent.com/blackmatrix7/ios_rule_script/master/rule/Shadowrocket/Netflix/Netflix.list | https://raw.githubusercontent.com/blackmatrix7/ios_rule_script/master/rule/Loon/Netflix/Netflix.list |
| Disney (blackmatrix7) | https://raw.githubusercontent.com/blackmatrix7/ios_rule_script/master/rule/Clash/Disney/Disney.yaml | https://raw.githubusercontent.com/blackmatrix7/ios_rule_script/master/rule/Shadowrocket/Disney/Disney.list | https://raw.githubusercontent.com/blackmatrix7/ios_rule_script/master/rule/Loon/Disney/Disney.list |
| Apple (blackmatrix7) | https://raw.githubusercontent.com/blackmatrix7/ios_rule_script/master/rule/Clash/Apple/Apple.yaml | https://raw.githubusercontent.com/blackmatrix7/ios_rule_script/master/rule/Shadowrocket/Apple/Apple.list | https://raw.githubusercontent.com/blackmatrix7/ios_rule_script/master/rule/Loon/Apple/Apple.list |
| ChinaMax (blackmatrix7) | https://raw.githubusercontent.com/blackmatrix7/ios_rule_script/master/rule/Clash/ChinaMax/ChinaMax.yaml | https://raw.githubusercontent.com/blackmatrix7/ios_rule_script/master/rule/Shadowrocket/ChinaMax/ChinaMax.list | https://raw.githubusercontent.com/blackmatrix7/ios_rule_script/master/rule/Loon/ChinaMax/ChinaMax.list |
| Advertising (blackmatrix7) | https://raw.githubusercontent.com/blackmatrix7/ios_rule_script/master/rule/Clash/Advertising/Advertising.yaml | https://raw.githubusercontent.com/blackmatrix7/ios_rule_script/master/rule/Shadowrocket/Advertising/Advertising.list | https://raw.githubusercontent.com/blackmatrix7/ios_rule_script/master/rule/Loon/Advertising/Advertising.list |
| Privacy (blackmatrix7) | https://raw.githubusercontent.com/blackmatrix7/ios_rule_script/master/rule/Clash/Privacy/Privacy.yaml | https://raw.githubusercontent.com/blackmatrix7/ios_rule_script/master/rule/Shadowrocket/Privacy/Privacy.list | https://raw.githubusercontent.com/blackmatrix7/ios_rule_script/master/rule/Loon/Privacy/Privacy.list |
| Hijacking (blackmatrix7) | https://raw.githubusercontent.com/blackmatrix7/ios_rule_script/master/rule/Clash/Hijacking/Hijacking.yaml | https://raw.githubusercontent.com/blackmatrix7/ios_rule_script/master/rule/Shadowrocket/Hijacking/Hijacking.list | https://raw.githubusercontent.com/blackmatrix7/ios_rule_script/master/rule/Loon/Hijacking/Hijacking.list |
| Lan (blackmatrix7) | https://raw.githubusercontent.com/blackmatrix7/ios_rule_script/master/rule/Clash/Lan/Lan.yaml | https://raw.githubusercontent.com/blackmatrix7/ios_rule_script/master/rule/Shadowrocket/Lan/Lan.list | https://raw.githubusercontent.com/blackmatrix7/ios_rule_script/master/rule/Loon/Lan/Lan.list |
| OpenAI (blackmatrix7) | https://raw.githubusercontent.com/blackmatrix7/ios_rule_script/master/rule/Clash/OpenAI/OpenAI.yaml | https://raw.githubusercontent.com/blackmatrix7/ios_rule_script/master/rule/Shadowrocket/OpenAI/OpenAI.list | https://raw.githubusercontent.com/blackmatrix7/ios_rule_script/master/rule/Loon/OpenAI/OpenAI.list |
| Claude (blackmatrix7) | https://raw.githubusercontent.com/blackmatrix7/ios_rule_script/master/rule/Clash/Claude/Claude.yaml | https://raw.githubusercontent.com/blackmatrix7/ios_rule_script/master/rule/Shadowrocket/Claude/Claude.list | https://raw.githubusercontent.com/blackmatrix7/ios_rule_script/master/rule/Loon/Claude/Claude.list |
| GitHub (blackmatrix7) | https://raw.githubusercontent.com/blackmatrix7/ios_rule_script/master/rule/Clash/GitHub/GitHub.yaml | https://raw.githubusercontent.com/blackmatrix7/ios_rule_script/master/rule/Shadowrocket/GitHub/GitHub.list | https://raw.githubusercontent.com/blackmatrix7/ios_rule_script/master/rule/Loon/GitHub/GitHub.list |
| BiliBili (blackmatrix7) | https://raw.githubusercontent.com/blackmatrix7/ios_rule_script/master/rule/Clash/BiliBili/BiliBili.yaml | https://raw.githubusercontent.com/blackmatrix7/ios_rule_script/master/rule/Shadowrocket/BiliBili/BiliBili.list | https://raw.githubusercontent.com/blackmatrix7/ios_rule_script/master/rule/Loon/BiliBili/BiliBili.list |
| TikTok (blackmatrix7) | https://raw.githubusercontent.com/blackmatrix7/ios_rule_script/master/rule/Clash/TikTok/TikTok.yaml | https://raw.githubusercontent.com/blackmatrix7/ios_rule_script/master/rule/Shadowrocket/TikTok/TikTok.list | https://raw.githubusercontent.com/blackmatrix7/ios_rule_script/master/rule/Loon/TikTok/TikTok.list |
| Discord (blackmatrix7) | https://raw.githubusercontent.com/blackmatrix7/ios_rule_script/master/rule/Clash/Discord/Discord.yaml | https://raw.githubusercontent.com/blackmatrix7/ios_rule_script/master/rule/Shadowrocket/Discord/Discord.list | https://raw.githubusercontent.com/blackmatrix7/ios_rule_script/master/rule/Loon/Discord/Discord.list |
| Line (blackmatrix7) | https://raw.githubusercontent.com/blackmatrix7/ios_rule_script/master/rule/Clash/Line/Line.yaml | https://raw.githubusercontent.com/blackmatrix7/ios_rule_script/master/rule/Shadowrocket/Line/Line.list | https://raw.githubusercontent.com/blackmatrix7/ios_rule_script/master/rule/Loon/Line/Line.list |
| Bahamut (blackmatrix7) | https://raw.githubusercontent.com/blackmatrix7/ios_rule_script/master/rule/Clash/Bahamut/Bahamut.yaml | https://raw.githubusercontent.com/blackmatrix7/ios_rule_script/master/rule/Shadowrocket/Bahamut/Bahamut.list | https://raw.githubusercontent.com/blackmatrix7/ios_rule_script/master/rule/Loon/Bahamut/Bahamut.list |
| YouTube (blackmatrix7) | https://raw.githubusercontent.com/blackmatrix7/ios_rule_script/master/rule/Clash/YouTube/YouTube.yaml | https://raw.githubusercontent.com/blackmatrix7/ios_rule_script/master/rule/Shadowrocket/YouTube/YouTube.list | https://raw.githubusercontent.com/blackmatrix7/ios_rule_script/master/rule/Loon/YouTube/YouTube.list |
| Google (blackmatrix7) | https://raw.githubusercontent.com/blackmatrix7/ios_rule_script/master/rule/Clash/Google/Google.yaml | https://raw.githubusercontent.com/blackmatrix7/ios_rule_script/master/rule/Shadowrocket/Google/Google.list | https://raw.githubusercontent.com/blackmatrix7/ios_rule_script/master/rule/Loon/Google/Google.list |

其他（Clash/Mihomo 為主）：
- 廣告（domainset）：Sukka https://ruleset.skk.moe/Clash/domainset/reject.txt ；Surge/SR 格式：https://ruleset.skk.moe/List/domainset/reject.conf
- 廣告：anti-AD https://anti-ad.net/clash.yaml ；Loyalsoldier https://raw.githubusercontent.com/Loyalsoldier/clash-rules/release/reject.txt
- 中國 IP：https://raw.githubusercontent.com/Loyalsoldier/clash-rules/release/cncidr.txt ；MetaCubeX mrs：https://raw.githubusercontent.com/MetaCubeX/meta-rules-dat/meta/geo/geoip/cn.mrs
- Telegram / OpenAI / Anthropic mrs：https://raw.githubusercontent.com/MetaCubeX/meta-rules-dat/meta/geo/geosite/{telegram,openai,anthropic}.mrs
- 注意：Sukka 嘅 ai.conf 同大部分 AI 規則都包括 Gemini/Copilot，**唔啱你「港澳用到就唔走代理」嘅要求**，所以 AI 用返本包嘅版本。

## Loon 插件（全部實測 HTTP 200）
| 插件 | 用途 | URL | 最後更新 |
|---|---|---|---|
| Sub-Store | 訂閱轉換/節點管理 | https://raw.githubusercontent.com/sub-store-org/Sub-Store/master/config/Loon.plugin | 2026-08-27 |
| Script-Hub | 將 Surge/QX 模組轉做 Loon 用 | https://raw.githubusercontent.com/Script-Hub-Org/Script-Hub/main/modules/script-hub.loon.plugin | 2026-10-03 |
| BoxJs | 腳本設定面板 | https://raw.githubusercontent.com/chavyleung/scripts/master/box/rewrite/boxjs.rewrite.loon.plugin | 2023-02（舊但仍係官方） |
| fmz200 廣告攔截合集 | 多個 App 去廣告 | https://raw.githubusercontent.com/fmz200/wool_scripts/main/Loon/plugin/blockAds.plugin | 2026-10-31 |
| fmz200 YouTube | YouTube 去廣告 | https://raw.githubusercontent.com/fmz200/wool_scripts/main/Loon/plugin/split/partY/YouTube.lpx | 2025-10-18 |
| fmz200 小紅書 | 去廣告/淨化 | https://raw.githubusercontent.com/fmz200/wool_scripts/main/Loon/plugin/split/partX/Xiaohongshu.lpx | 2026-10-01 |
| fmz200 Spotify | Spotify 淨化 | https://raw.githubusercontent.com/fmz200/wool_scripts/main/Loon/plugin/split/partS/Spotify.lpx | 2026-04-26 |
| fmz200 Reddit | Reddit 去廣告 | https://raw.githubusercontent.com/fmz200/wool_scripts/main/Loon/plugin/split/partR/Reddit.lpx | 2025-10-18 |
| fmz200 微博 | 微博去廣告 | https://raw.githubusercontent.com/fmz200/wool_scripts/main/Loon/plugin/weibo.plugin | 2025-12-16 |
| DualSubs YouTube | YouTube 雙語字幕/翻譯 | https://github.com/DualSubs/YouTube/releases/latest/download/DualSubs.YouTube.plugin | v1.6.0 2026-10-11 |
| DualSubs Universal | Netflix/Disney+/Prime 等雙語字幕 | https://github.com/DualSubs/Universal/releases/latest/download/DualSubs.Universal.plugin | v1.8.2 2026-10-20 |
| Biliverse ADBlock | B 站去廣告 | https://github.com/Biliverse/ADBlock/releases/latest/download/BiliBili.ADBlock.plugin | v0.7.5 2026-10-17 |
| Biliverse Global | B 站港澳台番劇自動換區 | https://github.com/Biliverse/Global/releases/latest/download/BiliBili.Global.plugin | v0.9.3 2026-10-17 |
| Biliverse Enhanced | B 站介面自訂 | https://github.com/Biliverse/Enhanced/releases/latest/download/Biliverse.Enhanced.plugin | v0.6.2 2026-10-17 |
| iRingo WeatherKit | Apple 天氣增強（空氣質素等） | https://github.com/NSRingo/WeatherKit/releases/latest/download/iRingo.WeatherKit.lpx | v3.3.2 2026-08-29 |
| iRingo TestFlight | TestFlight 跨區 | https://github.com/NSRingo/TestFlight/releases/latest/download/iRingo.TestFlight.plugin | v3.4.0 2024-12（舊） |

可莉 kelee 插件：喺官方索引 https://hub.kelee.one/list.json 有，大部分 2026-10-02 更新。不過 kelee.one 擋咗我呢邊嘅網絡，所以未能直接下載驗證檔案。建議喺 Loon 內用可莉插件中心安裝：
- https://kelee.one/Tool/Loon/Lpx/Block_HTTPDNS.lpx（kelee 去廣告插件需要配合佢用）
- https://kelee.one/Tool/Loon/Lpx/Remove_ads_by_keli.lpx
- https://kelee.one/Tool/Loon/Lpx/YouTube_remove_ads.lpx
- https://kelee.one/Tool/Loon/Lpx/Bilibili_remove_ads.lpx
- https://kelee.one/Tool/Loon/Lpx/RedPaper_remove_ads.lpx
- https://kelee.one/Tool/Loon/Lpx/Spotify_remove_ads.lpx
- https://kelee.one/Tool/Loon/Lpx/HongKongToolbar_remove_ads.lpx
- https://kelee.one/Tool/Loon/Lpx/TestFlightRegionUnlock.lpx
- https://kelee.one/Tool/Loon/Lpx/Node_detection_tool.lpx
- https://kelee.one/Tool/Loon/Lpx/Prevent_DNS_Leaks.lpx

## 未確定 / 要留意
- AI 圖片/影片/音樂工具（Midjourney、Runway、Suno、Udio、Pika 等）冇公開國家名單，所以沿用你原本嘅判斷。
- Google Labs、Jules、Antigravity、Gemini CLI 喺香港用唔用到未完全確定。如果你發現直連用到，可以喺 AI 剷走嗰一段。
- PROCESS-NAME 同 AND 規則只喺電腦版（Clash Verge、Loon macOS）有效，iOS 會略過。
- Loon/TszChun.conf 入面 tszchun0915/Loon/... 嘅連結，要你開咗 Loon repo、上傳咗 .lsr 先用得。
