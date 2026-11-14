---
layout: default
title: "Horizon Summary: 2026-11-14 (ZH)"
date: 2026-11-14
lang: zh
---

> 从 8 条内容中筛选出 2 条重要资讯。

---

**科技新闻**
1. [Lovable 构建的应用因不安全默认配置泄露护照及 20 万条私信](#item-tech-news-1) ⭐️ 7.0/10
2. [SpaceX 在第 15 次试飞中成功捕获星舰飞行器](#item-tech-news-2) ⭐️ 7.0/10

---

## 科技新闻

<a id="item-tech-news-1"></a>
### [Lovable 构建的应用因不安全默认配置泄露护照及 20 万条私信](https://www.crissyfield.de/research/lovable-en/) ⭐️ 7.0/10

安全研究披露，使用 AI 应用构建平台 Lovable 生成的应用程序因不安全的数据库默认配置，导致用户敏感护照数据与超过 20 万条私信遭到公开泄露。泄露主要源于客户端随站点公开的只读 API 密钥可直接访问未配置有效行级安全（Row-Level Security）策略的数据库表，普通用户仅通过审查浏览器网络请求即可读取数据。该问题反映出 AI 自动生成应用在缺乏严格安全默认设置时，极易规模化产生具备数据暴露隐患的在线服务。

hackernews · armcat · 11月14日 17:43 · [社区讨论](https://news.ycombinator.com/item?id=50499017)

**「背景」** Lovable 是一款允许用户通过自然语言提示词快速构建 Web 应用的 AI 开发平台，主要面向缺乏专业编程经验的构建者。该平台默认集成 Supabase 作为后端基础设施，用于自动配置数据库、身份认证和存储服务，因此所生成应用的数据安全性高度依赖底层服务与集成模板预设的权限访问策略。

**「安全风险与防范措施」** 该漏洞（追踪为 CVE-2025-48757）导致基于 Lovable 与 Supabase 构建的应用若未显式配置行级安全（RLS），攻击者便可利用前端暴露的 API 密钥未经认证直接拉取后端数据库。受影响的开发者需立即排查并启用 Supabase 表的 RLS 规则与访问控制策略，以防敏感生产数据持续外泄。

**「社区讨论」** 社区讨论指出，底层平台 Supabase 长期以来为了降低上手门槛而妥协了安全默认配置，是导致 AI 构建工具生成大量脆弱应用的结构性诱因之一。多位开发者强调，AI 编程与后端平台亟须引入“默认拒绝”机制、最小权限 API 及自动化权限校验，防止无安全背景的用户直接部署高危应用。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://docs.lovable.dev/integrations/supabase">Connect to Supabase - Lovable Documentation</a></li>
<li><a href="https://www.crissyfield.de/research/lovable-en/">Lovable : Many Apps Expose Sensitive Data — Crissy Field GmbH</a></li>
<li><a href="https://www.brinztech.com/breach-alerts/brinztech-alert-critical-row-level-security-rls-vulnerability-cve-2025-48757-exposed-lovable-supabase-applications/">Critical Row Level Security (RLS) Vulnerability (CVE-2025 ...</a></li>

</ul>
</details>

**标签**: `#security`, `#ai-generated code`, `#data leaks`, `#supabase`, `#app development`

---

<a id="item-tech-news-2"></a>
### [SpaceX 在第 15 次试飞中成功捕获星舰飞行器](https://x.com/i/broadcasts/2brajgZlOKRMka) ⭐️ 7.0/10

SpaceX 在第 15 次星舰试飞（Flight 15）结束时成功捕获了星舰飞行器本体。这一进展验证了超大尺度航天器的高精度实时制导与机械臂捕获回收能力，是推进全复用运载火箭系统的关键步骤。目前关于星舰隔热瓦在再入过程中的实际损耗程度及飞行器的复用状态，仍需等待官方进一步公布详细检测数据。

hackernews · ls612 · 11月14日 21:22 · [社区讨论](https://news.ycombinator.com/item?id=50500963)

**「背景」** SpaceX 的星舰系统旨在实现完全快速可重复使用，其方案采用发射塔上的机械臂在空中直接捕获返回的箭体。此前测试主要验证了超重型助推器（Super Heavy）的捕获回收，而第 15 次飞行测试（Flight 15）则进一步推进至飞船本体（Ship 42）重返大气层后的首次发射塔空中捕获尝试。

**「社区讨论」** 社区讨论普遍关注星舰隔热罩的耐受表现，指出若隔热层完好并实现助推器与星舰的“双重捕获”，将真正大幅摊薄轨道发射成本。此外，多位讨论者强调，在星舰如此庞大的物理尺度下完成高精度悬停与接引，展现了极高水平的机械与控制工程能力。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://www.youtube.com/watch?v=KqGPHd7XAbs">Watch Live! SpaceX Starship Flight 15 Reentry and Potential Catch ...</a></li>
<li><a href="https://www.space.com/space-exploration/launches-spacecraft/spacex-starship-flight-15-chopsticks-double-catch-super-heavy-ship">SpaceX launches Starship on ambitious 22-hour Flight 15 ... | Space</a></li>

</ul>
</details>

**标签**: `#aerospace`, `#hardware`, `#robotics`, `#spacex`

---