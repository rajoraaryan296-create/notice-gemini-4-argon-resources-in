---
layout: default
title: "通知：gemini-4-argon 资源紧缺，建议改用 Aistudio-Gemini-4 或 gemini-4-carbon"
description: "2026 年 11 月 20 日下午（截图约 17:56 看到时显示「2小时前」，大约 16:00 前后，Asia/Shanghai），第三方接口聚合站 momoAPIPro（tryallapi.com）的系统公告发出一条关于 的可用性通知："
---

# 通知：gemini-4-argon 资源紧缺，建议改用 Aistudio-Gemini-4 或 gemini-4-carbon

2026 年 11 月 20 日下午（截图约 17:56 看到时显示「2小时前」，大约 16:00 前后，Asia/Shanghai），第三方接口聚合站 momoAPIPro（[tryallapi.com](https://tryallapi.com/)）的系统公告发出一条关于 `gemini-4-argon` 的可用性通知：

> 通知：近期 gemini-4-argon 资源紧缺,低价分组请求失败率偏高,建议使用Aistudio-Gemini-4或者暂时切换到 gemini-4-carbon,目前可用性相对更好。argon 恢复后会另行通知。给您带来不便,敬请谅解。

需要按原文理解，不要自行加码：当前点名的是 `gemini-4-argon` 资源紧缺，尤其是低价分组请求失败率偏高。站点给出两条建议：一是继续调用 `gemini-4-argon`，但改用 **Aistudio-Gemini-4 分组**（这是 tryallapi 的分组名，不是 Google AI Studio 的官方产品）；二是暂时把模型换成 `gemini-4-carbon`，公告写的是目前可用性相对更好，并不是保证一定能打通，也不是承诺更快或更便宜。argon 何时恢复，公告只说会另行通知，本文不猜测恢复时间。

要在自己的项目或脚本里按量调用，可以从这个注册入口进入：[https://tryallapi.com/register?aff=5A6A](https://tryallapi.com/register?aff=5A6A)。

本文按 **2026 年 11 月 20 日（Asia/Shanghai，UTC+8）** 对公开页面、系统公告、官方文档和当日定价数据的复核来写。需要先说清楚：tryallapi.com / momoAPIPro 是**第三方 API 聚合站**，不是 Google、Google DeepMind、Gemini、Google AI Studio、Vertex AI 或 Gemini for business 的官网，也不是官方 API。文中出现的 Aistudio-Gemini-4、Vertex-Gemini-3 等，都是 tryallapi 的**分组名**，不是 Google AI Studio 或 Vertex 的官方产品。同一模型 ID 不等于官方直连，也不等于官方服务等级承诺。价格、分组和可用性都会变，请以当天控制台和模型广场为准。官方 Ultra / Pro 订阅门槛，以及「Free tier 不可用」这类限制，只适用于 Google 官方界面，**不要套到 tryallapi 上**。

## 官方怎么区分 Argon 和 Carbon

公告建议暂时切到 `gemini-4-carbon`，所以先对照官方对这两条模型的定位。两者官方 Standard 单价相同，但不等于一次调用的花费相同。

### Gemini 4 Argon

根据 Google 2026 年 10 月 13 日的 [GA 介绍](https://blog.google/innovation-and-ai/models-and-research/gemini-models/introducing-gemini-4-argon/)、同日发布的 [模型卡](https://deepmind.google/models/model-cards/gemini-4-argon/)、[开发者指南](https://aistudio.google.com/learn/gemini-4-argon-developer-guide)，以及 [AI Studio 更新日志](https://aistudio.google.com/docs/changelog)：

- 模型 ID：`gemini-4-argon`。对外开发者可用日以 2026 年 10 月 13 日 GA 为准（更早的 9 月 30 日还有过预告）。
- 官方定价页（2026 年 11 月 20 日核对 [Gemini API 定价](https://ai.google.dev/gemini-api/docs/pricing)）的说明是：高效的 Gemini 4 前沿推理模型，在复杂编码、智能体、数学和科学任务上，能提供 Gemini 4 级能力，同时比 Gemini 4 Carbon 响应更快、每轮消耗的 token 更少。
- GA 博文写明：面向编程、金融、法律、网络安全和科学等复杂实际工作；并写到它在 Vals Index 上排名第一。这里只转述官方表述，不另行补充其他分数。
- 模型卡写明：原生多模态推理模型，不是既有模型的微调；输入支持文本、图像、音频和视频，输出为文本；输入与输出合计的上下文窗口最高 100 万 token。
- 开发者指南写明：思考深度默认 `medium`，可在 `low` / `medium` / `high` 之间调节；输入和输出共用 100 万 token 上下文；并提供同一套 Gemini API 内置工具。
- 官方通道只适用于官方界面，包括 AI Studio / Android Studio 里的 Gemini API 付费档、Gemini for business、Google Antigravity（Ultra），以及 Gemini 应用和 Search 中的 AI Mode（10 月 13 日博文写 Argon 对应 Ultra 和 Pro）。这些门槛**不适用于** tryallapi。

官方 Standard 付费档标价（USD / 1M tokens，不是 Free tier；输出价格包含思考 token）是：

| 时段 | 输入 | 输出（含思考 token） | 上下文缓存 |
| --- | --- | --- | --- |
| 至 2026 年 11 月 30 日 | $2.00 | $10.00 | $0.10 |
| 2026 年 12 月 1 日起 | $4.00 | $20.00 | $0.20 |

官方页面写明目前只有隐式缓存（implicit caching），不支持显式缓存。Batch / Flex 等档位另有标价，这里不并入上表，以[官方定价页](https://ai.google.dev/gemini-api/docs/pricing)为准。官方还会对每一个 token 计费，包括思考 token，以及在使用 grounding 时的内部工具指令；Google Search grounding 另有官方费用，本文不编造 tryallapi 的 grounding 价格，需要时请直接看官方定价页。

### Gemini 4 Carbon

根据 Google 2026 年 11 月 10 日的 [上线介绍](https://blog.google/innovation-and-ai/models-and-research/gemini-models/gemini-4-carbon-now-available/)、同日发布的 [模型卡](https://deepmind.google/models/model-cards/gemini-4-carbon/)、[开发者指南](https://aistudio.google.com/learn/gemini-4-carbon-developer-guide) 和 [What's new](https://aistudio.google.com/docs/whats-new-gemini-4-carbon)：

- 模型 ID：`gemini-4-carbon`。对外可用日以 2026 年 11 月 10 日为准（更早的 10 月 28 日还有过预告）。
- 模型卡写明：Gemini 4 Carbon 基于 Gemini 4 Argon。
- 官方定价页的说明是：能力最强的推理模型，面向复杂软件工程、深层数学和科学问题、高事实准确性、自主多步智能体，以及最高 100 万 token 的长解码生成。
- 11 月 10 日博文写明：Carbon 是他们目前最强的模型；Argon 仍是大多数软件工程和知识工作的更合适选择，而 Carbon 面向会把模型智力推向极限的任务，例如复杂、多步的编码和调试，以及开放式的科学研究和发现——它会比 Argon 使用更多 token，以便更充分地探索、更深入地推理，并跑更长的验证循环。
- 这一点很关键：**官方单价相同，不代表一次调用更便宜。** Carbon 可能消耗更多思考 token，即使每 100 万 token 的标价一样，账单也可能更高。不要把「暂时切到 carbon」理解成免费或自动降价。
- 上下文窗口、思考档位（默认 `medium`，可选 `low` / `medium` / `high`）和内置工具，与 Argon 相同；官方 Standard 导入价同样是 11 月 30 日前 $2 / $10，12 月 1 日起 $4 / $20，同样不在 Free tier，同样只有隐式缓存。
- 11 月 10 日博文还写到 Carbon 在 CursorBench 4.0、Perplexity 的 WANDR 和 Zapier 的 AutomationBench 上排名第一，并称相较「次优外部模型」，每项任务成本不到其一半。这些都是官方博文的表述，不能当成 tryallapi 的价格。
- 消费端上线范围也不要和 Argon 混写：11 月 10 日博文写的是 Google AI Ultra（Gemini 应用 / AI Mode / Antigravity），比 Argon 在 10 月 13 日博文里「Ultra 和 Pro」的表述更窄。这些同样只适用于官方界面，不适用于 tryallapi。

## 渠道：tryallapi.com（momoAPIPro）按量 API

- **站点：** [https://tryallapi.com/](https://tryallapi.com/)
- **注册入口：** [https://tryallapi.com/register?aff=5A6A](https://tryallapi.com/register?aff=5A6A)

这一条面向要在自己的项目、脚本或客户端里调用模型的人，不是 Google 官方网页或官方订阅。站点品牌是 **momoAPIPro**，定位是按量计费的 API 聚合。

![momoAPIPro 系统公告：gemini-4-argon 资源紧缺，建议改用 Aistudio-Gemini-4 或暂时切换到 gemini-4-carbon](https://upload.maynor1024.live/file/1795168901075_01-announcement.png)

> 图注：2026 年 11 月 20 日约 17:56（Asia/Shanghai）系统公告截图。其中关于 `gemini-4-argon` 的条目当时标注为「2小时前」。同板按时间从新到旧还能看到：Vertex-Gemini-1、Aistudio-Gemini-1 分组将于北京时间当天 20 点下线；`gemini-embedding-001`、`gemini-embedding-2-preview` 暂时下架；`scribe_v2`、`scribe_v3` 上架；Gemini 原生调用新增 `/v1` 路径支持；以及此前的 `doubao-seedance-2-5-flash-261115`、`qwen4-max` 上架通知。上架或目录里还有模型，不等于所有分组一直可用。

2026 年 11 月 20 日大约 17:57–17:58（Asia/Shanghai）的公开定价目录里，这两条模型的厂商标注都是 Google（vendor_id 67），计费类型为按量（quota_type 0），状态为可用，标签为「对话,识图,工具」，模型类型为对话。支持的接点类型都是 `gemini` 和 `openai`。两条模型的定价数据里都没有给出 5 分钟或 1 小时的缓存创建倍率，所以这里只列出输入、补全和缓存命中，不补写未见的数字。

站点上的模型说明（按站点原文引用，不等同于上文的官方定位）分别是：

- `gemini-4-argon`：Gemini 4 Argon (gemini-4-argon) 是我们的旗舰推理模型，专为复杂的软件工程、深奥的数学和科学问题解决、自主多步代理以及长达 100 万个令牌的长解码而打造。
- `gemini-4-carbon`：Gemini 4 Carbon（gemini-4-carbon）是我们推理能力最强的模型，专为复杂软件工程、数学与科学问题求解、高事实准确性、自主多步骤智能体场景打造，支持最高 100 万 token 的超长输出。

公开目录里的创建时间分别是：`gemini-4-argon` 为 2026-10-13 15:25:35（与官方 GA 同一天），`gemini-4-carbon` 为 2026-11-11 15:31:34（官方 11 月 10 日上线后的第二天）。

优先使用主线 [https://tryallapi.com](https://tryallapi.com/)；主机名本身不是完整的调用路径。OpenAI 兼容 Base URL 常见写法是 `https://tryallapi.com/v1`。同日公告还提到 Gemini 原生调用新增 `/v1` 路径支持，例如 `/v1/models/{model}:generateContent`（以及 `streamGenerateContent`），请以当天文档确认实际路径，不要把它理解成现在必须改走这条路径，也不要指望它能解决 argon 的失败率问题。备用主机 `https://api.maynorai.asia` 此前被说明为备用线路且已被封禁，这里只如实记录，不提供绕过方法。

### 分组价格（2026-11-20 约 17:57 公开定价数据）

单位是 **USD / 1M Tokens**，按量计费。计算公式与此前复核过的公开目录一致：输入 = `2 × model_ratio × group_ratio`，输出 = `model_ratio × completion_ratio × 2 × group_ratio`，缓存命中 = `2 × model_ratio × cache_ratio × group_ratio`。两条模型当日都是 `model_ratio = 1`、`completion_ratio = 5`、`cache_ratio = 0.05`。下表按 2026 年 11 月 20 日大约 17:57–17:58（Asia/Shanghai）的公开定价数据计算，使用前请回到模型广场或定价页核对。

先说一条硬界限：公告写的是低价分组失败率偏高，但当天公开目录里 `gemini-4-argon` 的 `enable_groups` **只列出了 Aistudio-Gemini-4 和 Vertex-Gemini-3**。站点分组倍率表里确实还有更低倍率的 Gemini 分组（例如 Anti-Gemini-1、Cli-Gemini-1、Discounted-Gemini-1、Aistudio-Gemini-1、Vertex-Gemini-1、Aistudio-Gemini-2 等），但它们当时并没有出现在 argon 的 `enable_groups` 里，本文不把这些分组写成 argon 的现行价，也不计算对应数字。

**gemini-4-argon**（当日仅下列两个分组）

| 分组 | 输入 | 补全 | 缓存命中 | 相对官方导入价（$2 / $10） |
| --- | --- | --- | --- | --- |
| Aistudio-Gemini-4 | $4.2059 | $21.0296 | $0.2103 | 约 2.103 倍 |
| Vertex-Gemini-3 | $3.9600 | $19.8000 | $0.1980 | 1.980 倍 |

当前列出的两个 argon 分组，都高于官方 Standard 导入价（至 11 月 30 日的 $2 / $10）。**不要默认所有分组都比官方便宜。** 公告建议优先使用的是 Aistudio-Gemini-4 分组；Vertex-Gemini-3 当天也在公开目录里，但公告并没有点名这个分组。12 月 1 日起，官方标价会变成 $4 / $20，和这两个分组的价格已经接近，但这不等于 tryallapi 会或不会在 12 月 1 日调价。

**gemini-4-carbon**（作为临时切换的对照）

| 分组 | 输入 | 补全 | 缓存命中 | 相对官方导入价（$2 / $10） |
| --- | --- | --- | --- | --- |
| Aistudio-Gemini-2 | $1.1647 | $5.8236 | $0.0582 | 0.582 倍 |
| Vertex-Gemini-2 | $1.3200 | $6.6000 | $0.0660 | 0.660 倍 |
| Aistudio-Gemini-3 | $1.9412 | $9.7060 | $0.0971 | 0.971 倍 |
| Vertex-Gemini-3 | $3.9600 | $19.8000 | $0.1980 | 1.980 倍 |
| Aistudio-Gemini-4 | $4.2059 | $21.0296 | $0.2103 | 约 2.103 倍 |

carbon 当天开放的分组里，有的低于官方导入价，有的高于官方导入价。切到 carbon **不会自动落到更便宜的分组**；官方单价相同，再加上 Carbon 可能消耗更多思考 token，账单并不必然更低。更便宜的分组，也正是 argon 这则公告里提到失败率偏高的那一类——不要据此承诺 carbon 的低价分组一定更稳。公告说的是可用性「相对更好」，不是保证。Anti / Cli / Discounted / \*-Gemini-1 等分组当天同样不在 carbon 的 `enable_groups` 里，本文也不为 carbon 补写这些分组的价格。此前（11 月 19 日）公告板上曾出现过 gemini-4-carbon 的 Anti 资源暂时下架的说明；就当天目录来看，Anti 分组仍未进入 carbon 的 `enable_groups`，这里只作为背景，不把它当作今天的头条。

### 同板其他公告（仅作背景，不是这篇文章的主题）

同一张 17:56 的系统公告截图里，按时间从新到旧还能看到这些条目，这里只作背景，避免把本文写成公告汇总：

- 「Vertex-Gemini-1, Aistudio-Gemini-1分组将于北京时间11月20日20点下线，恢复时间等待通知」，截图时标注「34分钟前」（大约 17:22）。就 17:56 的截图而言，这是即将发生的下线。这两个 `-1` 分组当天并不在 argon 的 `enable_groups` 里，不要理解成 argon 本身会在 20 点下线。它提醒的是：上架或目录里还有模型，不等于所有分组一直可用。
- 「近期 gemini-embedding-001, gemini-embedding-2-preview 资源紧缺，请求失败率偏高，暂时下架，恢复后会另行通知」，标注「1小时前」。复核公开目录时，324 个模型里没有这两个 ID。
- 「模型上架：scribe_v2、scribe_v3」，标注「3小时前」。这里只记录公告写过这两个 ID，不展开评测。
- 「Gemini 原生调用新增 /v1 路径支持，如 /v1/models/{model}:generateContent（/v1/models/{model}:streamGenerateContent）」，同样标注「3小时前」。请以当天文档确认路径；本文不把它写成现在必须改走的接口，也不把它写成可以修复 argon 失败率的办法。
- 截图底部仍能看到「模型上架：doubao-seedance-2-5-flash-261115、qwen4-max」（时间被裁切）。只作为同板背景。

## 怎么切换

1. 打开 [https://tryallapi.com/register?aff=5A6A](https://tryallapi.com/register?aff=5A6A) 注册并登录。
2. 在控制台创建令牌（API Key）。不要把密钥发到聊天、截图或文章里。
3. 若按公告继续使用 argon：在控制台允许的前提下选择 **Aistudio-Gemini-4** 分组，`model` 填写 `gemini-4-argon`。当天公开目录里 Vertex-Gemini-3 也在 argon 的开放分组中，这里只如实记录；公告点名建议的分组是 Aistudio-Gemini-4，并没有点名 Vertex-Gemini-3。
4. 若按公告做临时切换：把模型改成 `gemini-4-carbon`。官方单价与 Argon 相同，但实际消耗的 token，以及 tryallapi 上命中的分组，都可能不同。
5. 当日支持的接点类型是 `gemini` 和 `openai`。OpenAI 兼容 Base URL 常见写法是 `https://tryallapi.com/v1`；原生 Gemini 的 generateContent 路径以当天文档为准。优先走主线 [https://tryallapi.com](https://tryallapi.com/)，不要把主机名当成完整路径。
6. 实际扣费以控制台账单和当时命中的分组为准。

## 需要记住的几点

- 这是第三方按量通道，不是 Google、Google DeepMind、Gemini、Google AI Studio、Vertex AI 或 Gemini for business 的官方订阅，也不能替代官方账号。Aistudio-Gemini-4、Vertex-Gemini-3 只是 tryallapi 的分组名。
- 官方 Ultra / Pro 门槛和「Free tier 不可用」只适用于官方界面，不要套到这条通道上。
- 官方模型和 tryallapi 目录里的同名模型 ID 一致，但不等于官方直连，也不等于官方服务等级承诺。
- 公告建议的是：继续用 argon 时优先走 Aistudio-Gemini-4 分组，或暂时改用 `gemini-4-carbon`。argon 恢复时间以后续通知为准，本文不猜测。
- 切到 Carbon 不是自动降价，也不是免费更换。官方单价相同，但 Carbon 可能用掉更多思考 token；tryallapi 上既有低于官方导入价的分组，也有更高的分组，低价分组也不等于更稳。
- 当天公开目录里，argon 只列出了 Aistudio-Gemini-4 和 Vertex-Gemini-3，这两个分组都高于官方导入价。未出现在该模型 `enable_groups` 里的更低倍率分组，不能写成 argon 的现行价。
- 价格、分组和可用性都会变，请以 2026 年 11 月 20 日之后的当天页面为准。
