![审稿式论文精读](./assets/reviewer-paper-reader-cover.png?raw=true)

# 审稿式论文精读

Reviewer Paper Reader · v1.1

用于个人科研学习的论文阅读 skill，适合阅读 AI、机器学习、多模态、智能体和机器人领域的论文。帮助你读懂作者做了什么、增加了什么认识，以及哪些问题值得接着研究。提供一篇论文就能开始，也可以只问某个方法、公式或实验。

下文提供 Claude、Claude Code、WorkBuddy、Codex、Cursor 和 OpenCode 的安装说明。

[下载 v1.1](downloads/reviewer-paper-reader-v1.1.zip) · [选择安装方式](#安装) · [开始阅读](#开始阅读)

## 读完能得到什么

一份中文阅读笔记，主要回答下面几个问题：

- 作者解决的是什么问题，为什么值得研究？
- 方法到底改了什么，为什么这样做，用一个例子能否说明白？
- 论文发现了什么关系或规律，在什么条件下成立，有哪些例外？
- 与已有工作相比，方法和认识分别新在哪里，贡献有多大？
- 实验说明了什么，哪些是直接结果，哪些仍是解释或推测？
- 对自己的研究有什么启发，下一步值得先验证什么？

方法论文、现象分析和定量研究都可以读。论文没有建立新规律时，会说明它实际带来了什么方法、能力或资源，不会为了凑结论硬提炼一条规律。

如果你正准备选题，可以补充自己的研究方向。阅读结果会围绕这个方向给出一个值得优先考虑的问题，说明它可能增加什么认识、先做什么验证，以及什么结果意味着应该换个方向。暂时找不到合适的问题时，也会直接说明。

## 安装

先[下载 v1.1 技能包](downloads/reviewer-paper-reader-v1.1.zip)，再按自己使用的平台安装。上传技能时选择这个 ZIP；手动安装时，先解压，再复制整个 `reviewer-paper-reader` 文件夹。

### Claude 网页版 / 桌面版

1. 在设置中开启文件创建与代码执行能力（Create and edit files / Code execution and file creation）。
2. 进入 **Customize → Skills**，点击 **+ → Create skill → Upload a skill**。
3. 上传下载的 `reviewer-paper-reader-v1.1.zip`，在技能列表中启用它。
4. 回到对话，上传论文，发送下方的阅读请求。

无需解压 ZIP。团队账号若没有上传入口，请联系管理员确认技能权限。[Claude 官方说明](https://support.claude.com/en/articles/12512180-use-skills-in-claude)

### WorkBuddy

1. 在左侧打开 **专家·技能·连接器 → 技能**。
2. 点击 **添加技能 → 上传技能**，选择 `reviewer-paper-reader-v1.1.zip`。
3. 在“已安装”中确认技能已启用，然后在对话中上传论文并发出阅读请求。

本包通过“上传技能”导入，不需要先在技能市场搜索。[WorkBuddy 官方说明](https://www.codebuddy.cn/docs/workbuddy/From-Beginner-to-Expert-Guide/Function-Description/Skills-Market)

### Claude Code

将解压得到的文件夹放入 `~/.claude/skills/`。在解压后的目录运行：

```bash
mkdir -p ~/.claude/skills
cp -R reviewer-paper-reader ~/.claude/skills/
```

在 Claude Code 中输入 `/reviewer-paper-reader`，再附上论文与阅读要求。只想在当前项目使用，可改放到项目内的 `.claude/skills/`。[Claude Code 官方说明](https://code.claude.com/docs/en/skills)

### Codex

将解压得到的文件夹放入 `~/.agents/skills/`：

```bash
mkdir -p ~/.agents/skills
cp -R reviewer-paper-reader ~/.agents/skills/
```

在 Codex 中输入 `$reviewer-paper-reader` 调用，或从技能选择器选中它。只想在当前项目使用，可放到项目内的 `.agents/skills/`。未识别到新技能时，重启 Codex 后再试。[Codex 官方说明](https://learn.chatgpt.com/docs/build-skills)

### Cursor

将解压得到的文件夹放入 `~/.cursor/skills/`：

```bash
mkdir -p ~/.cursor/skills
cp -R reviewer-paper-reader ~/.cursor/skills/
```

在 Agent 对话中输入 `/`，搜索并选择 `reviewer-paper-reader`。只想在当前项目使用，可放到项目内的 `.cursor/skills/`。以上是本地 Agent 的安装方式；云端使用方式见 [Cursor 官方说明](https://cursor.com/docs/skills)。

### OpenCode

将解压得到的文件夹放入 `~/.config/opencode/skills/`：

```bash
mkdir -p ~/.config/opencode/skills
cp -R reviewer-paper-reader ~/.config/opencode/skills/
```

在对话中说明“请使用 reviewer-paper-reader 阅读这篇论文”。只想在当前项目使用，可放到项目内的 `.opencode/skills/`。[OpenCode 官方说明](https://docs.opencode.ai/docs/skills/)

上面的命令适用于 macOS / Linux。Windows 用户可在文件资源管理器中打开 `%USERPROFILE%`，按 `~` 后面的目录层级放置文件夹。例如，Claude Code 对应 `%USERPROFILE%\.claude\skills\reviewer-paper-reader\SKILL.md`。

安装时请保留整个文件夹，勿只复制 `SKILL.md`，也不要额外嵌套一层同名目录。

从 v1.0 升级时，先将旧的 `reviewer-paper-reader` 文件夹移到技能目录之外，再放入新版。通过 ZIP 导入的平台，可先移除旧项再上传 v1.1。安装后仍使用 `reviewer-paper-reader` 这个名称。

安装入口按各平台官方文档整理，尚未逐个平台实测。本 skill 使用当前 Agent 已有的 PDF 阅读、检索和文件工具；工具是否可用会影响全文获取、查新和笔记保存。

## 开始阅读

上传 PDF 后，直接发送：

```text
请使用 reviewer-paper-reader 阅读我上传的论文。
```

也可以提供论文链接、DOI、arXiv 编号，或当前项目中可访问的 PDF 路径。无需先填写背景资料。

如果有具体目标，可以一起说清楚：

```text
请使用 reviewer-paper-reader 阅读这篇论文：[论文链接]。
我的研究方向是多模态智能体。
请重点讲清核心思想、论文发现的规律及其适用条件，
判断创新和实验，再找一个值得先验证的问题。
```

## 常用读法

### 先看看值不值得精读

```text
请使用 reviewer-paper-reader 速读这篇论文：[论文]。
先告诉我它做了什么、主要结果如何，以及哪些部分值得仔细看。
```

### 方法没看懂

```text
请使用 reviewer-paper-reader 解释这篇论文的[方法或公式]。
请用一个具体例子讲清楚，必要的基础知识也一起解释。
```

### 想知道论文增加了什么认识

```text
请使用 reviewer-paper-reader 阅读[论文]。
它试图寻找什么规律，实际验证到了哪一步？
请讲清成立条件、例外，以及哪些原因解释还需要证据。
```

### 想判断创新是否成立

```text
请使用 reviewer-paper-reader 比较[论文A]和[论文B]。
它们的关键区别是什么？新增的部分是否有价值？
请给出相关工作的依据。
```

### 想从论文中找研究问题

```text
请使用 reviewer-paper-reader 阅读[论文]。
结合我的[研究方向]，找一个值得先验证的问题。
说清楚这个问题可能增加什么认识、先做什么验证、
出现什么结果时应该继续，什么结果时应该停止。
```

### 阅读 Zotero 中的论文

```text
请使用 reviewer-paper-reader 阅读 Zotero 中的“[论文完整题名]”。
```

此方式需要当前 Agent 已连接可用的 Zotero 工具。没有连接时，直接上传 PDF 或提供论文链接即可。

## 阅读结果

回复中会先给出论文的主要内容和判断，详细笔记保存为 Markdown，方便后续整理和回看。笔记通常包括核心思想、论文增加的认识与适用边界、相关工作比较、实验分析、研究建议，以及关键内容的原文位置或链接。保存到本地目录需要当前 Agent 有文件写入能力；网页端可要求提供可下载的 Markdown 文件。

需要指定保存位置时，加一句：

```text
请把阅读笔记保存到当前项目的 notes 目录。
```

只想在对话中阅读，也可以说明“不保存文件”。

读完后可以接着追问，无需重新开始。例如：

```text
刚才对方法的解释还不够直观，请换一个例子。
```

```text
我想继续研究你提到的问题，请先帮我判断实验是否做得起来。
```

## 其他使用问题

### 可以检查阅读结论有没有错吗？

可以在请求中加上“请做独立核查”。会根据环境中可用的核查能力，另附核查结果，说明发现的问题和未能确认的内容。无法完成独立核查时，会如实说明。

### 只有摘要也能读吗？

可以先了解问题和大致思路。方法细节、实验可靠性和创新判断通常还需要全文；缺少材料的部分会标明。

### 能保证找到新选题吗？

研究建议需要进一步查新和实验验证。这个 skill 可以帮助你明确下一步该问什么、该验证什么，但不能保证建议具有新颖性，也不能承诺论文的投稿结果。

### 输出太长，或者还是没看懂怎么办？

直接说“先用几段话讲清楚”，或指出具体卡在哪里。也可以要求一次讲一个问题，等你回答后再继续。

---

[下载技能包](downloads/reviewer-paper-reader-v1.1.zip) · [下载完整仓库](https://github.com/caikw0602/reviewer-paper-reader/archive/refs/heads/main.zip)
