### 你好,我是 Yang / Hi, I'm Yang

**我设计并验证 AI coding 评测任务——题面、检查点、硬门槛、自动判分链,并把这套工作流做成工具。**
I design and verify AI coding evaluation tasks — task specs, checkpoints, hard gates, scoring pipelines — and turn the workflow itself into tools.

- 🎯 最新作品:[Grader Lab](https://yange0793-dot.github.io/grader-lab/) — 在浏览器里给编码任务判分,纯前端,点开即用
- 🧰 日常:AI 辅助开发重度实践者,Claude Code / Codex / ZCode 混合工作流
- 📍 中国 · 正在承接 AI 训练 / 评测类项目

## 主张 → 证据

每条能力主张都挂一个**现在就能点开验证**的链接:

| 主张 | 证据 |
| --- | --- |
| 会设计可判分的编码任务:检查点 / 硬门槛 / 权重 | [grader-lab 判分模型](https://github.com/yange0793-dot/grader-lab/blob/main/src/engine/scoring.ts) · [4 道内置示例题](https://github.com/yange0793-dot/grader-lab/blob/main/src/samples.ts) |
| 会把出题质量检查规则化,拦住套路化出题 | [grader-lab 出题 lint](https://github.com/yange0793-dot/grader-lab/blob/main/src/engine/lint.ts) |
| 判分逻辑可离线复现、可测试 | grader-lab 引擎层 22 项单测,CI 强制绿 |
| 会写带真测试的 CLI 工具 | [prompt-lint](https://github.com/yange0793-dot/prompt-lint)(9 规则 / 16 测试 / py3.10–3.14 矩阵)· [novel-toolchain](https://github.com/yange0793-dot/novel-toolchain)(53 项自测) |
| 懂 LLM 应用协议层 | [mixrouter](https://github.com/yange0793-dot/mixrouter) — 本地 Anthropic 协议模型路由器 |
| 能写原生 macOS 应用 | [CodexContextBar](https://github.com/yange0793-dot/CodexContextBar) — 306 行 Objective-C,零依赖零网络 |

## 精选项目

**🎯 [grader-lab](https://github.com/yange0793-dot/grader-lab) — 编码任务判分台**
浏览器内运行候选代码、按检查点判分:行为断言 / 输出正则 / 源码检查 / 性能预算,硬门槛短路 + 加权 Rubric。
React 19 · TypeScript(strict)· Web Worker · 22 项单测 · [在线 demo](https://yange0793-dot.github.io/grader-lab/)

**🔍 [prompt-lint](https://github.com/yange0793-dot/prompt-lint) — 提示词体检 CLI**
规则式检查模糊表述、全角字符、矛盾指令等 9 类问题;离线确定性,零依赖。
Python · 16 项测试 · 30 秒上手:`pipx install promptlint && promptlint -p "帮我优化一下这个函数,让它快点"`

**✍️ [novel-toolchain](https://github.com/yange0793-dot/novel-toolchain) — 长篇写作命令行工具链**
章节编号、伏笔追踪、情节线矩阵、时间线校对、码字日志。纯 Python 标准库,53 项自测。

**🔀 [mixrouter](https://github.com/yange0793-dot/mixrouter) — 本地 Anthropic 协议模型路由器**
按模型名路由到不同上游,仿 cc-switch 控制台,本地模型接入 Claude Code 生态。

**📊 [CodexContextBar](https://github.com/yange0793-dot/CodexContextBar) — macOS 菜单栏上下文窗口监控**
306 行 Objective-C,Cocoa only,无网络权限。

## 我怎么工作

- 需求先拆成可验收的小块,每块想清楚怎么检查(断言 / 测试 / 可点开的 demo),再动手;
- commit 按主题切分,测试和 CI 是交付物的一部分,不是事后补;
- 文档写「为什么」和「不能做什么」,不只写「是什么」——参考 [grader-lab 的设计说明](https://github.com/yange0793-dot/grader-lab/blob/main/DESIGN.md)。

## 技术栈(诚实分级)

- **熟练**:Python · TypeScript · React · Git / GitHub Actions · AI 编程工具链(Claude Code / Codex / ZCode)
- **能用**:Objective-C · Vite · vitest / pytest · Playwright
- **了解**:Go · Rust
