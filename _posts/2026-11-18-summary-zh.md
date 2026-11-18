---
layout: default
title: "Horizon Summary: 2026-11-18 (ZH)"
date: 2026-11-18
lang: zh
---

> 从 8 条内容中筛选出 2 条重要资讯。

---

**科技新闻**
1. [Nginx HTTP/2 模块曝出未授权远程代码执行漏洞](#item-tech-news-1) ⭐️ 8.0/10
2. [微软发布七款主打性价比的新 AI 模型](#item-tech-news-2) ⭐️ 7.0/10

---

## 科技新闻

<a id="item-tech-news-1"></a>
### [Nginx HTTP/2 模块曝出未授权远程代码执行漏洞](https://www.wiz.io/blog/nginx-http2-rce-vulnerabilities) ⭐️ 8.0/10

安全研究团队披露了 Nginx HTTP/2 模块中存在的未授权远程代码执行漏洞（涉及 CVE-2026-123633 与 CVE-2026-123007），并演示了结合 Linux 内核漏洞实现容器逃逸的攻击链。受影响实例若启用了 HTTP/2 支持，攻击者可在无需身份验证的情况下执行任意代码。管理员可通过更新至修复版本或临时禁用 HTTP/2 协议来规避风险。

hackernews · speedping · 11月18日 15:19 · [社区讨论](https://news.ycombinator.com/item?id=50547374)

**「漏洞背景」** CVE-2026-123633 与 CVE-2026-123007 是存在于 Nginx HTTP/2 模块中的严重内存损坏漏洞，由 Wiz Research、Ikotas Labs、Rapid7 及 Xint 等团队独立发现并向 F5 报告。攻击者无需身份验证，即可利用该模块在处理特定协议请求时的缺陷触发远程代码执行。

**「影响与应对」** 该漏洞直接影响所有启用了 HTTP/2（ngx\_http\_v2\_module）的 NGINX 开源版与 NGINX Plus 实例；鉴于其允许未授权远程代码执行的高危风险，系统管理员需立即排查配置并升级官方修复版本，或在完成补丁部署前临时关闭 HTTP/2 支持以规避攻击。

**「社区讨论」** 社区用户指出开源仓库在公开通告前约一周就已提交了修复补丁，容易被监控代码变更的攻击者提前利用，建议排查期间优先禁用 HTTP/2；也有讨论指出 HTTP/2 在 Nginx 中并非默认启用，同时攻击链中用于容器逃逸的 Linux SCTP 本地提权漏洞同样值得警惕。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://www.wiz.io/blog/nginx-http2-rce-vulnerabilities">Unauthenticated Remote Code Execution in NGINX: CVE-2026 ...</a></li>
<li><a href="https://cybersecuritynews.com/nginx-http-2-vulnerabilities/">NGINX HTTP/2 Flaws Could Allow Memory Corruption and Remote ...</a></li>
<li>NGINX ngx_http_v2_module vulnerability CVE-2026-123007</li>

</ul>
</details>

**标签**: `#nginx`, `#cybersecurity`, `#vulnerabilities`, `#http2`, `#infrastructure`

---

<a id="item-tech-news-2"></a>
### [微软发布七款主打性价比的新 AI 模型](https://microsoft.ai/news/microsoft-ignite-2026/) ⭐️ 7.0/10

微软宣布推出七款主打可扩展性价比（scalable price-performance）的全新 AI 模型，旨在提升基础模型的性价比与竞争力。官方尚未在此项初步消息中公开各模型的完整技术规范与详细可用性细则。

hackernews · gmays · 11月18日 16:08 · [社区讨论](https://news.ycombinator.com/item?id=50548021)

**「背景」** 微软近年来持续推进自主研发的 MAI 系列模型，旨在优化推理与部署成本的同时平衡模型性能。此次发布进一步扩展了该系列自研架构，涵盖网络安全与编程等专业应用场景。

**「影响」** 面向日常生产和高频编程任务的企业及开发者能够显著削减高阶模型调用成本；据微软测算，MAI Code 2 能以 Claude Opus 5.5 约 5% 的成本实现其 96% 的编码性能，为大规模工程化代码交付提供了更具性价比的直接替代选项。

**「社区讨论」** 有开发者表示在测试 MAI Code 2 后认为其实际编程表现能够媲美顶尖模型，但也有评论指出微软应提供开源或开放权重版本以争夺市场份额，同时部分从业者对过度依赖大语言模型带来的技能退化表达了担忧。

<details><summary>参考链接</summary>
<ul>
<li>HN digest: Hacker News, summarized</li>
<li><a href="https://microsoft.ai/models/mai-code-2/">MAI Code 2 | Microsoft AI</a></li>
<li><a href="https://forklog.com/en/microsoft-unveils-ai-models-for-coding-and-cybersecurity/">Microsoft unveils AI models for coding and cybersecurity | ForkLog</a></li>

</ul>
</details>

**标签**: `#artificial intelligence`, `#large language models`, `#microsoft`, `#software engineering`

---