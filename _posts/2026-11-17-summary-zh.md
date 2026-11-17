---
layout: default
title: "Horizon Summary: 2026-11-17 (ZH)"
date: 2026-11-17
lang: zh
---

> 从 10 条内容中筛选出 5 条重要资讯。

---

**科技新闻**
1. [OpenAI 推出 GPT-6.2 Astra 与 Sol 并上线 API](#item-tech-news-1) ⭐️ 8.0/10
2. [vLLM 发布 v0.34.0：全量切换至 Model Runner V2 并默认启用可扩展 KV 缓存](#item-tech-news-2) ⭐️ 7.0/10
3. [Simon Willison 与 Prime Radiant 推出编程智能体外部沙箱模式](#item-tech-news-3) ⭐️ 7.0/10
4. [Datasette Lite 重写：利用 Service Worker 与 Pyodide 在浏览器运行服务端 Python](#item-tech-news-4) ⭐️ 7.0/10

**财经新闻**
1. [英国法庭驳回针对索尼 PlayStation 商店近 20 亿英镑诉讼](#item-finance-news-1) ⭐️ 7.0/10

---

## 科技新闻

<a id="item-tech-news-1"></a>
### [OpenAI 推出 GPT-6.2 Astra 与 Sol 并上线 API](https://openai.com/index/introducing-gpt-6-2-astra-sol/) ⭐️ 8.0/10

OpenAI 正式推出了 GPT-6.2 Astra 与 GPT-6.2 Sol 两款新模型，并已在 API 中分别以 gpt-6.2-astra 和 gpt-6.2-sol 开放调用。定位为前沿模型的 6.2 Astra 输入与输出定价降至每百万 Token 8 美元和 40 美元，缓存价格降至 0.40 美元；面向日常工作的 6.2 Sol 维持每百万 Token 2 美元输入与 10 美元输出。测试显示两款模型在分析和代码生成任务上展现出更快的执行速度并减少了工具调用，但在部分复杂 3D 动画生成及长任务协作表现上仍存在局限。

hackernews · jasondavies · 11月17日 17:46 · [社区讨论](https://news.ycombinator.com/item?id=50535230)

**「背景」** OpenAI 在其模型体系中将 Astra 定位为处理高难度任务的前沿旗舰模型，Sol 则为主打日常通用任务的高效模型。在此次迭代前，上一代 GPT-6 Astra 的 API 价格为每百万 Token 输入 10 美元、输出 50 美元，而 GPT-6 与 6.1 版本的 Sol 则将轻量级定价维持在每百万 Token 2 美元与 10 美元。

**「使用影响」** Astra 的缓存价格较上一代的每百万 Token 1 美元大幅降至 0.40 美元，直接降低了长时间运行的智能体（agentic）会话以及多轮对话调用的累积成本。

**「社区讨论」** 基准测试者指出新模型在数据分析考核中速度极快且调用开销显著下降，但偶有未得出答案即提前结束运行的情况。同时有开发者反映，Astra 在长时间处理复杂目标并拆分子任务时，偶尔会中断流程向用户询问难以理解的底层实现细节。

**标签**: `#artificial intelligence`, `#large language models`, `#openai`, `#benchmarks`

---

<a id="item-tech-news-2"></a>
### [vLLM 发布 v0.34.0：全量切换至 Model Runner V2 并默认启用可扩展 KV 缓存](https://github.com/vllm-project/vllm/releases/tag/v0.34.0) ⭐️ 7.0/10

开源大模型推理引擎 vLLM 正式发布 v0.34.0 版本，彻底移除了旧版 Model Runner V1，并将 Model Runner V2 作为唯一的 GPU 运行环境。该版本在 CUDA 和 ROCm 上默认启用可扩展 KV 缓存机制，改为依据预热及 CUDA 图捕获后实际空闲显存分配空间，以换取更大的并发缓存容量与吞吐表现，但在部分硬件的高并发场景下可能导致解码延迟上升 6% 至 18%。同时，默认注意力块大小由 16 调整为 64，并新增了对 Mistral Large 4 等 10 款新模型的支持以及面向 NVIDIA Blackwell 与 AMD MI355X 的硬件加速内核。

github · khluu · 11月16日 23:22

**「背景」** Model Runner 是 vLLM 负责 GPU 模型推理执行的核心组件。为了解决早期架构积累的技术债务并提升运行效率，开发团队重新设计推出了更模块化的 Model Runner V2，并在 0.30 版本中将其设为默认运行器，随后逐步推进旧版 V1 的废除计划。

**「影响与迁移建议」** 使用旧架构或定制组件的服务存在启动失败风险：设置 \`VLLM\_USE\_V2\_MODEL\_RUNNER=0\` 将在启动时直接报错，现有的 V1 Logits 处理器需迁移至新模块路径；此外，运行环境必须升级至 \`huggingface\_hub &gt;= 2.0.0\`，且 AMD 平台构建全面弃用 ROCm 7.2 改为仅支持 ROCm 10.0。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://github.com/vllm-project/vllm">GitHub - vllm-project/vllm: A high-throughput and memory ... Model Runner V2 Design Document - vLLM vLLM changelog — v0.34.0, Nov 16, 2026 · What&#x27;s New Model Runner V2 Design Document - vLLM vLLM 0.30 Upgrade: Model Runner V2 and Breaking Changes Model Runner V2: A Modular and Faster Core for vLLM</a></li>

</ul>
</details>

**标签**: `#vLLM`, `#LLM Inference`, `#Machine Learning`, `#Open Source`, `#GPU Computing`

---

<a id="item-tech-news-3"></a>
### [Simon Willison 与 Prime Radiant 推出编程智能体外部沙箱模式](https://simonwillison.net/2026/Nov/17/external-sandboxes-for-coding-agents/) ⭐️ 7.0/10

Simon Willison 与 AI 研究机构 Prime Radiant 合作提出了“外部沙箱”（external sandbox）模式，使编程智能体本体保持在隔离环境之外，仅将待执行的代码调度至独立沙箱中运行以防范系统破坏与提示注入风险。团队同步开源了三款提供统一本地 API 的参考实现：基于 v86 与 WebAssembly 运行 Alpine Linux 的 Node.js 服务、基于 Apple Containers 的 Python 服务，以及借助微软 Quicksand（集成 QEMU）的 Python 服务。该架构可供 Claude Code、Codex 或 Pi 等工具接入，并支持 HTTP/HTTPS 允许列表网络代理与免密凭据替换机制。

rss · Simon Willison · 11月17日 22:52

**「背景」** 代码编写类 AI 智能体在协助开发时通常拥有在宿主系统直接运行代码的权限，但在解析不可信输入时面临提示词注入攻击及破坏本地环境的安全风险。为了在保障安全的同时保留自动化能力，开发者持续探索环境隔离机制，例如微软开源的 Quicksand 库便通过封装 QEMU 虚拟机来为智能体提供轻量级的代码执行沙盒。

**「实际影响」** 开发人员在测试本地模型或自主编程智能体时，可以通过标准本地接口直接将代码执行限制在轻量虚拟机或容器内，在不向智能体暴露宿主机系统权限与真实认证密钥的前提下隔离不可信代码。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://github.com/microsoft/quicksand">GitHub - microsoft / quicksand : Quickly sandbox your AI agent. · GitHub</a></li>

</ul>
</details>

**标签**: `#AI agents`, `#sandboxing`, `#security`, `#prompt injection`

---

<a id="item-tech-news-4"></a>
### [Datasette Lite 重写：利用 Service Worker 与 Pyodide 在浏览器运行服务端 Python](https://simonwillison.net/2026/Nov/17/datasette-lite/) ⭐️ 7.0/10

Simon Willison 发布了 Datasette Lite 的全面重构版本，改用 Service Worker 结合 Pyodide 和 WebAssembly，直接在浏览器端完整运行服务端 Datasette Python 应用。新版本替代了 2022 年依赖 Web Worker 及 innerHTML 注入、导致 JavaScript 插件无法运行的旧架构，表现与真实服务端几乎无异。用户现可通过特定 URL 参数加载 CORS 开放的 SQLite、JSON 或 CSV 数据，自由指定 PyPI 版本或 GitHub 分支，挑选超过 100 种 SQLite 版本，并动态安装支持客户端 JS 可视化的第三方插件。

rss · Simon Willison · 11月17日 16:48

**「背景」** Datasette Lite 最初于 2022 年推出，旨在通过 WebAssembly 和 Pyodide 在浏览器中直接运行 Python 版 Datasette。早期版本依赖 Web Worker 模拟请求并将生成的 HTML 注入页面，导致页面无法正常执行 script 标签，也无法运行依赖 JavaScript 的交互插件与可视化功能。

**「实际影响」** 开发者与数据分析师无需搭建或部署独立的 Web 服务器，仅凭构造特定 URL 即可在浏览器内快速复现分页 Bug、演示分支新特性或直接分享交互式数据可视化效果。

**标签**: `#webassembly`, `#pyodide`, `#sqlite`, `#python`, `#service-workers`

---

## 财经新闻

<a id="item-finance-news-1"></a>
### [英国法庭驳回针对索尼 PlayStation 商店近 20 亿英镑诉讼](https://www.reuters.com/world/sony-defeats-2-billion-uk-claim-over-playstation-store-pricing-2026-11-17/) ⭐️ 7.0/10

英国竞争上诉法庭驳回了一项针对索尼约 19.7 亿英镑的集体诉讼，认定其并未滥用市场支配地位抬高 PlayStation 商店的数字内容价格。该诉讼代表约 1220 万名英国消费者，但法庭裁定主机硬件之间的市场竞争已有效限制了索尼的定价空间。

telegram · zaihuapd · 11月17日 16:02

**「背景」** 该集体诉讼由消费者代表发起，指控索尼利用对数字游戏分发渠道的控制强制抽取 30% 佣金，导致英国玩家多年来承担了过高的购买成本。

**「影响」** 该裁决消除了索尼近 20 亿英镑的潜在赔偿责任，诉讼涉及的约 1220 万名英国消费者也因此无法获得数字游戏及内购的差价退款。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://topdisputes.com/disputes/playstation-store-class-action">Alex Neill v. Sony class action: status and timeline — TopDisputes</a></li>
<li><a href="https://www.brickcourt.co.uk/news/detail/competition-appeal-tribunal-dismisses-2-billion-playstation-class-action-against-sony">Competition Appeal Tribunal dismisses £2 billion PlayStation ...</a></li>

</ul>
</details>

**标签**: `#Sony`, `#Antitrust`, `#Gaming Industry`, `#Litigation`

---