# Amazon 00–06 Independent Skills

这是 Amazon 00–06 的 **7 个可独立安装 Skill** 版本。

与 `amazon-00-06-full-pipeline-plugin` 不同，本仓库不依赖插件 Router；每个目录都是一个自包含 Skill，可以单独安装、单独更新、单独测试。

## Skills

- `amazon-00/` — Governance / Product Truth / Policy / Orchestration / Final QA
- `amazon-01/` — Search Demand & Keywords
- `amazon-02/` — Listing Copy
- `amazon-03/` — Listing Images
- `amazon-04/` — A+ Content
- `amazon-05/` — Ads & PPC
- `amazon-06/` — Native Upload Template Compiler

## Self-contained structure

每个 Skill 目录包含：

```text
amazon-XX/
├── SKILL.md
├── skill.json
└── references/
```

`references/` 只包含该 Skill 真正需要的专业模块，因此把任意一个 `amazon-XX` 目录单独打包/上传时，不依赖仓库根目录的公共文件。

## 使用原则

- ChatGPT 可根据任务自动选择一个或多个已安装 Skill。
- 用户也可以明确调用某个 Skill，例如“调用 Amazon 02”。
- 00 仍保留完整新品全链路治理/编排职责；但七个 Skill 在 Standalone 模式下均必须独立完成自身 Owner 范围，不强迫用户先运行无关 Skill。
- Business Output First 不等于降低专业深度；Product Truth、Variation/Child Truth、当前 Amazon Hard Rule、Claim Evidence、真实 Final Asset、06 Workbook Reopen Validation 与 Final Release QA 继续保留。

## Source

本仓库来自已完成自检、试运行和漏洞修复的 Amazon 00–06 生产版本，并将原共享 Reference 重组为各 Skill 的本地依赖。
