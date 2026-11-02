# Ruleset additions — region-model fill (2026-11-02)

補地區模型窿窿：國際 Default／陸港台直連或地區 VPN／Safe／AI／動畫瘋／TikTok→台。

三個主題喺 repo 根目錄，佈局同其他一樣（`<Name>/<Name>.yaml`、`.list`、`.lsr`）。原有規則集冇刪。

Clash / Loon / Shadowrocket:

`https://raw.githubusercontent.com/tszchun0915/Ruleset/refs/heads/main/<Name>/<Name>.{yaml|lsr|list}`

## New sets this wave

| Set | Policy | Why |
|-----|--------|-----|
| CN-Local | 🇨🇳 China | 深圳通、KoolCenter／酷友社 |
| HKJC-Extra | 🇭🇰 HongKong | 馬會域名補充（HK 已有 keyword） |
| LineTV-Extra | 🇹🇼 Taiwan | LINE TV；唔包 line-cdn 免誤傷 LINE |

## Also wired in finals (bm7, no new folder)

- YouTube → 🚀 Default
- Google → 🚀 Default
- Apple → 🚀 Default（FaceTime 仍靠 `IP-CIDR,17.0.0.0/8,DIRECT`）
- TVB／myTV SUPER → 🇭🇰 HongKong
- TikTok → 🇹🇼 Taiwan（已有）
- Bahamut／動畫瘋 → 🎮 AniGamer（組只留 DIRECT／港／台）
- Bank(HK) → 🔒 Safe；AI-Leak → 🛡️ Leak（已有）

## Privacy

- 呢個 repo／呢啲集：**只域名規則，可 public**
- **主配置 YAML／conf 同訂閱 Link：唔好 push 去公開 GitHub**

<!-- Maintained with Grok Bot -->
