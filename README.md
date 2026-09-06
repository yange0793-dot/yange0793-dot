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
| 判分逻辑可离线复现、可测试、可挂 CI | [grader-lab 命令行判分](https://github.com/yange0793-dot/grader-lab/blob/main/cli/grade.mts) —— 同一套引擎在终端跑,退出码即门;51 项测试在 Node 22/24 两版 CI 上跑 |
| 出题自检不是口号,是 CI 门 | [示例题自检测试](https://github.com/yange0793-dot/grader-lab/blob/main/src/engine/samples.test.ts) —— 参考解必须满分、起始代码必须被硬门槛判 0、题目自身必须过出题 lint |
| 会把判分标准沉淀成题库,且题库本身持续被验证 | [task-bank](https://github.com/yange0793-dot/task-bank) —— 10 道题按 grader-lab 规格设计,每道附考察点/迷惑项/判分设计说明;CI 逐题自检:参考解满分、起始代码被硬门槛拦、出题 lint 零告警 |
| 会写带真测试的 CLI 工具 | [prompt-lint](https://github.com/yange0793-dot/prompt-lint)(9 规则 / 24 测试 / py3.10·3.12·3.14 三版矩阵 / 可挂 pre-commit)· [novel-toolchain](https://github.com/yange0793-dot/novel-toolchain)(53 项自测,其中 43 项在 CI 上可复现,另 10 项是本机环境检查) |
| 独立交付解决真实需求的工具,零依赖可审计 | [agent-bill](https://github.com/yange0793-dot/agent-bill) —— 从本地会话日志统计 Claude Code / Codex 的 token 用量与成本,`npx` 直跑零安装零上传;正确处理两家互斥的缓存 token 语义,未知名模型不计费只点名 |
| 懂 LLM 应用协议层 | [mixrouter](https://github.com/yange0793-dot/mixrouter) — 本地 Anthropic 协议模型路由器 |
| 能写原生 macOS 应用 | [CodexContextBar](https://github.com/yange0793-dot/CodexContextBar) — 388 行 Objective-C,零依赖零网络;解析逻辑用 fixture 会话在 CI 上断言,不只验能编译 |
| 会给"手感类"交付上自动验证:无头测试 + 可复现构建 | [canvas-games 无头物理测试](https://github.com/yange0793-dot/canvas-games/blob/main/slingshot/build/test.js) —— 9 项断言不开浏览器跑物理(开局不塌 / 弹道可达 / 命中真伤害);CI 重拼单文件成品后 `git diff --exit-code`,成品与源码漂移就红 |

## 精选项目

**🎯 [grader-lab](https://github.com/yange0793-dot/grader-lab) — 编码任务判分台**
浏览器内运行候选代码、按检查点判分:行为断言 / 输出正则 / 源码检查 / 性能预算,硬门槛短路 + 加权 Rubric;
同一套引擎另有命令行入口,`--min` 决定退出码,可直接当 CI 的门。
React 19 · TypeScript(strict)· Web Worker(浏览器)/ 子进程 + 超时(命令行)· 51 项测试 · Node 22/24 双版 CI · 推 main 自动部署 · 可从 task-bank 题库一键导入 · [在线 demo](https://yange0793-dot.github.io/grader-lab/)

**🗂 [task-bank](https://github.com/yange0793-dot/task-bank) — 编码评测题库(与 grader-lab 配套)**
12 道题按 grader-lab 规格设计成完整任务包(题面/ground truth/verifier/难度标注),基础→困难覆盖递归、原型链污染、闭包缓存、LRU 新鲜度、二分变体;附 reward hacking 判据设计手册(六类作弊手法→可执行判据);
每道题的 DESIGN.md 写清考察点、迷惑项设计与判分理由——判分标准可解释,自动判分才值得被信任;
CI 钉死 grader-lab commit 逐题跑三关自检,判分引擎升级会不会打碎题库,推送即知。

**💳 [agent-bill](https://github.com/yange0793-dot/agent-bill) — AI 编程工具用量账单(独立工具)**
从本地会话日志统计 Claude Code 与 Codex 的 token 用量、按模型/天/项目分解与估算成本,`npx` 直跑;
零 npm 依赖、零网络请求,数据不出本机。两家工具互斥的缓存 token 语义(Codex 缓存是子集、
Claude 缓存是独立计数)在解析层归一化并有测试钉住;未计价模型照常计 token、不计费、报告点名。
Node 18/22/24 三版 CI · 14 项测试 · [定价表](https://github.com/yange0793-dot/agent-bill/blob/main/pricing.json)欢迎 PR 校准

**🔍 [prompt-lint](https://github.com/yange0793-dot/prompt-lint) — 提示词体检 CLI**
规则式检查模糊表述、全角字符、矛盾指令等 9 类问题;离线确定性,零依赖,`--max-warn` 可把草稿气味也拦在 CI 外。
Python · 24 项测试(含两条挡文档漂移的:README 里贴的真实输出必须仍然真实、README 写的测试数必须等于真实收集数)· 30 秒上手:
`pipx install git+https://github.com/yange0793-dot/prompt-lint` 然后 `promptlint -p "帮我优化一下这个函数,让它快点"`

**✍️ [novel-toolchain](https://github.com/yange0793-dot/novel-toolchain) — 长篇写作命令行工具链**
章节编号、伏笔追踪、情节线矩阵、时间线校对、码字日志。纯 Python 标准库,53 项自测——43 项与环境无关、CI 上跑,另 10 项检查本机 Typora/launchd 接线,在别的 checkout 上自动跳过而不是报假失败。

**🔀 [mixrouter](https://github.com/yange0793-dot/mixrouter) — 本地 Anthropic 协议模型路由器**
按模型名路由到不同上游,仿 cc-switch 控制台,本地模型接入 Claude Code 生态。

**📊 [CodexContextBar](https://github.com/yange0793-dot/CodexContextBar) — macOS 菜单栏上下文窗口监控**
388 行 Objective-C,Cocoa only,无网络权限。读 `~/.codex/sessions` 的 jsonl 算上下文占用;`CODEX_CONTEXT_BAR_ROOT` 可指向 fixture,CI 每次推送都断言百分比与模型名。

**🎮 [canvas-games](https://github.com/yange0793-dot/canvas-games) — 两款单文件 Canvas 游戏**
弹弓物理(仿 Angry Birds 练习作:Matter.js 物理、木/玻璃/石三材质、三种鸟)与俯视角割草生存,双击 `.html` 即玩零安装;
游戏逻辑有 9 项无头测试——Node 直跑物理断言,不开浏览器;单文件成品由源码块拼接生成,CI 重拼一次 `git diff` 保证拼接可复现。

## 我怎么工作

- 需求先拆成可验收的小块,每块想清楚怎么检查(断言 / 测试 / 可点开的 demo),再动手;
- commit 按主题切分,测试和 CI 是交付物的一部分,不是事后补;
- 文档写「为什么」和「不能做什么」,不只写「是什么」——参考 [grader-lab 的设计说明](https://github.com/yange0793-dot/grader-lab/blob/main/DESIGN.md)。

## 技术栈(诚实分级)

- **熟练**:Python · TypeScript · React · Git / GitHub Actions · AI 编程工具链(Claude Code / Codex / ZCode)
- **能用**:Objective-C · Matter.js · Vite · vitest / pytest · Playwright
- **了解**:Go · Rust
