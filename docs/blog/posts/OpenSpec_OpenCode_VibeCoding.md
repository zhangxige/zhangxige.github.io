---
icon: lucide/gamepad-directional
title: OpenSpec_OpenCode_VibeCoding
date: 2026-05-31
authors:
  - name: zx
    email: daxuekanshijie@sina.cn
categories:
  - Rust
---

# 用 OpenSpec \+ OpenCode 实现高效 Vibe Coding：从理念到落地

这里提供**两种最简单的方法**，把上面的内容保存为 `\.md` 文件，Windows WSL / 纯 Windows 都能用，一步步照着操作即可。

# 方法一：终端内直接创建（推荐，你当前环境）

你现在用的是 WSL 终端，操作最便捷：

1. 在终端进入你想保存文件的目录（比如桌面）

```bash
# 进入 Windows 桌面（WSL 通用路径）
cd /mnt/c/Users/你的用户名/Desktop
```

> 替换 `你的用户名` 为你电脑实际用户名，不知道可以先执行 `ls /mnt/c/Users/` 查看
> 
> 

2. 新建空白 Markdown 文件

```bash
touch VibeCoding-OpenSpec-OpenCode.md
```

3. 用编辑器打开粘贴内容

### 方式 1：nano（终端自带，不用额外安装）

```bash
nano VibeCoding-OpenSpec-OpenCode.md
```

- 进入编辑页后，**全选我上文完整文案 → 复制 → 在终端里右键粘贴**

- 粘贴完成后，按 `Ctrl \+ O` 保存，回车确认文件名

- 按 `Ctrl \+ X` 退出编辑器

### 方式 2：用 Windows 记事本 / VS Code 打开编辑

```bash
# 调用 Windows 默认记事本打开
notepad.exe VibeCoding-OpenSpec-OpenCode.md

# 如果你装了 VS Code，直接用这个（推荐）
code VibeCoding-OpenSpec-OpenCode.md
```

打开后粘贴全文，`Ctrl\+S` 保存即可。

---

# 方法二：浏览器纯手动保存（零命令，新手首选）

1. 把我上一轮发给你的**全部文案完整复制**

2. 在桌面右键 → 新建 → 文本文档

3. 双击打开文本文档，粘贴所有内容

4. 点击左上角 **文件 → 另存为**

    - 编码选择：**UTF\-8**（避免中文乱码）

    - 文件名处填写：`VibeCoding\-OpenSpec\-OpenCode\.md`

    - **保存类型** 选择：所有文件

5. 点击保存，文件就变成标准 Markdown 格式了。

---

# 补充：完整原文（直接复制使用）

```markdown
# 用 OpenSpec + OpenCode 实现高效 Vibe Coding：从理念到落地
Vibe Coding（氛围编程）是2025年由Andrej Karpathy提出的AI原生开发模式，核心是**用自然语言描述需求，凭直觉快速迭代，让AI主导代码生成**，彻底摆脱繁琐语法与流程束缚。而 **OpenSpec + OpenCode** 组合，正是把“随性创作”升级为**规范可控、高效落地**的Vibe Coding最佳实践——既保留“心流开发”的流畅感，又通过规范驱动（Spec-Driven）解决AI输出不可预测、难以维护的痛点。

## 一、核心概念：Vibe Coding × OpenSpec × OpenCode
### 1. Vibe Coding：跟着感觉走的AI开发
Vibe Coding 是一种**“重创意、轻流程”**的开发范式：
- ✅ 核心：**人类说需求，AI写代码**，用自然语言描述“要什么”，而非“怎么写”；
- ✅ 特点：快速原型、直觉驱动、流畅心流、低门槛，适合创意验证与快速迭代；
- ✅ 痛点：需求模糊、输出不可控、难以审计、后期维护成本高。

### 2. OpenSpec：给Vibe Coding装“规范刹车”
OpenSpec 是 **Fission-AI 推出的轻量级规范驱动开发工具**，专为AI编程设计，解决Vibe Coding“太随性”的问题：
- ✅ 核心：**先定规范，再写代码**，开发前与AI对齐“要构建什么”，锁定意图；
- ✅ 能力：生成标准化提案（`proposal.md`）、设计文档（`design.md`）、任务清单（`tasks.md`），变更可追溯、可审查；
- ✅ 价值：让Vibe Coding **“自由不混乱，高效不失控”**，适配新项目与存量项目迭代。

### 3. OpenCode：强大的AI编程Agent
OpenCode 是**开源终端AI编程助手**，支持75+大模型（含Claude、Gemini、GLM等免费模型），是Vibe Coding的核心执行引擎：
- ✅ 核心：**多模型并行、会话隔离、终端原生交互**，直接在命令行与AI结对编程；
- ✅ 能力：理解代码库架构、生成/调试/重构代码、集成Git与终端工具、支持插件扩展（如Oh-My-OpenCode）；
- ✅ 价值：**零成本享受顶级AI编程能力**，搭配OpenSpec实现“规范+自由”的完美平衡。

### 三者关系
**Vibe Coding = 理念（怎么开发）**
**OpenSpec = 规则（开发边界）**
**OpenCode = 工具（执行落地）**
→ 组合效果：**随性创作不翻车，AI编码可控可维护**。

## 二、环境准备：一键搭建Vibe Coding工作站
### 1. 系统要求
- Node.js ≥ 20.19.0（必须，OpenSpec/OpenCode强依赖）；
- 终端：WSL（Windows）、Git Bash、iTerm2（Mac）；
- 可选：Bun（更快的包管理器，推荐）。

### 2. 安装步骤（复制即用）
#### ① 安装 OpenCode（AI编程核心）
```bash
# 全局安装OpenCode CLI
npm install -g opencode-ai@latest
# 验证安装（输出版本即成功）
opencode --version
```

#### ② 安装 OpenSpec（规范驱动核心）

```bash
# 全局安装OpenSpec CLI
npm install -g @fission-ai/openspec@latest
# 验证安装（输出版本即成功）
openspec --version
```

#### ③ 安装增强插件（可选但推荐）

```bash
# 安装Oh-My-OpenCode（Claude/Gemini认证+增强能力）
npx oh-my-openagent install
# 安装Antigravity认证插件（Google/Gemini免API Key）
opencode plugin install opencode-antigravity-auth
```

#### ④ 认证模型（Claude/Gemini 免费使用）

```bash
# 启动认证流程
opencode auth login
# 按提示选择：
# Anthropic → Claude Pro/Max（浏览器登录授权）
# Google → Gemini（OAuth授权，无需API Key）
```

## 三、实战流程：5 步完成 Vibe Coding 全链路

### 1\. 初始化项目：绑定 OpenSpec 与 OpenCode

```bash
# 进入你的项目目录
cd my-vibe-project
# 初始化OpenSpec（生成.openspec目录与AGENTS.md）
openspec init
```

初始化后生成核心文件：

- `\.openspec/`：规范与变更存储目录；

- `AGENTS\.md`：给 AI 的行为准则（定义 Vibe 风格与项目规则）；

- `project\.md`：项目全局上下文（技术栈、架构、约束）。

### 2\. 发起需求：用自然语言创建变更提案

在 OpenCode 中输入斜杠命令，开启 Vibe Coding：

```bash
# 启动OpenCode
opencode
# 创建新功能提案（自然语言描述需求）
/opsx:propose 实现用户登录模块，支持手机号验证码登录，风格简洁现代
```

AI 自动生成 3 个核心文档（在`\.openspec/changes/\[提案名\]/`下）：

- `proposal\.md`：需求背景、目标、范围（对齐意图）；

- `design\.md`：技术方案、架构设计、依赖关系（明确实现路径）；

- `tasks\.md`：拆分任务、优先级、预估工时（可执行清单）。

### 3\. 审查规范：快速确认或迭代需求

打开生成的文档（如`design\.md`），快速审查：

- 需求是否符合预期？

- 技术方案是否合理？

- 任务拆分是否清晰？

**修改方式**：直接编辑文档，或在 OpenCode 中用自然语言调整：

```bash
/opsx:update 调整登录UI，增加记住密码选项，验证码60秒倒计时
```

### 4\. 执行开发：AI 按规范生成代码（Vibe 时刻）

规范确认后，一键让 AI 执行所有任务：

```bash
# 应用变更，AI自动生成代码、提交Git
/opsx:apply
```

**Vibe Coding 体验**：

- AI 全程自主编码、调试、修复错误；

- 你只需**专注 “感觉”**：运行效果是否符合预期？交互是否流畅？

- 不满意直接用自然语言反馈：`/opsx:fix 登录按钮点击无响应`，AI 自动修复。

### 5\. 迭代优化：快速循环，直到 “感觉对了”

Vibe Coding 的核心是**快速迭代**：

1. 运行代码，体验效果；

2. 用自然语言描述调整需求（如 “颜色调浅一点”“动画更快”）；

3. 执行`/opsx:apply`，AI 自动更新代码；

4. 循环直到 \\*\\*“vibe 匹配”\\*\\*（效果符合直觉）。

## 四、核心优势：为什么选 OpenSpec\+OpenCode 做 Vibe Coding

### 1\. 自由与规范平衡

- ✅ 保留 Vibe Coding 的**流畅心流**：自然语言驱动，无需逐行编码；

- ✅ 解决 “随性混乱”：OpenSpec 锁定意图，变更可追溯、可审查。

### 2\. 低成本高效率

- ✅ 免费使用顶级模型：Claude、Gemini、GLM 等，**无需 API Key**；

- ✅ 全流程自动化：提案→设计→编码→提交，AI 一站式完成；

- ✅ 开发效率提升 5\-10 倍：专注创意，摆脱机械编码。

### 3\. 可控可维护

- ✅ 规范即文档：所有变更留痕，新人快速上手；

- ✅ 任务可追踪：每个功能对应清晰任务清单，进度可视化；

- ✅ 适配存量项目：不重构现有代码，渐进式迭代。

### 4\. 零门槛上手

- ✅ 无需深厚编程基础：**会说话就能开发**；

- ✅ 终端原生交互：无需复杂 IDE，命令行直接搞定；

- ✅ 插件化扩展：按需安装能力（如认证、多模型支持）。

## 五、适用场景：谁需要这套组合？

- ✅ 创意开发者：快速验证想法、原型开发、黑客松项目；

- ✅ 全栈工程师：高效迭代功能、减少重复编码、专注架构设计；

- ✅ 非技术创始人：无需雇开发，自己用自然语言搭建产品；

- ✅ 团队协作：统一 AI 输出规范，降低沟通成本，提升交付质量。

## 六、总结：开启你的 AI 原生开发时代

Vibe Coding 不是 “不专业”，而是**AI 时代的新专业**—— 把人类从机械编码中解放，专注创意与体验。而 **OpenSpec \+ OpenCode** 正是这套理念的最佳落地工具：

- **OpenCode** 让你**随性创作**，享受 AI 编码的流畅心流；

- **OpenSpec** 让你**规范可控**，避免自由创作的混乱与风险。

现在，无需纠结语法、无需搭建复杂环境，只需**说清楚你的想法**，剩下的交给 AI—— 这就是 Vibe Coding 的魅力，也是 OpenSpec\+OpenCode 的价值。

