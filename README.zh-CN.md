# EDA-Writing-Skills

[English](README.md) | **中文**

面向 **EDA 顶会/顶刊论文写作**（DAC、ICCAD、DATE、ASP-DAC、TCAD 等）的 Claude Code Skill。帮助你把论文草稿改写成面向审稿人的高清晰度版本：段落逻辑、章节结构、图表质量、claim–evidence 对齐，以及投稿前的对抗式自审（adversarial self-review）。

## 功能

- **章节级指导**：Abstract / Introduction / Related Work / Method / Experiments / Conclusion 各有专门的写作规范，按需加载。
- **段落级打磨**：一段一个 message、首句点题、句间衔接检查（cause / contrast / consequence / refinement），配合 reverse outlining 检验逻辑链。
- **Claim–Evidence 对齐**：Abstract 和 Introduction 中的每个主要 claim 都要能映射到实验证据，无法支撑的 claim 会被削弱或删除。
- **投稿前自审**：从 contribution、写作清晰度、实验强度、评估完整性、方法设计合理性五个维度做审稿人视角的对抗式检查。
- **图表规范**：teaser / pipeline 图与低墨水量（minimal-ink）表格的质量要求，把视觉质量当作核心内容对待。

## 安装

本技能以 [Claude Code Skill](https://docs.anthropic.com/en/docs/claude-code) 的形式提供。

**项目级安装**（仅当前论文仓库可用）：

```bash
mkdir -p .claude/skills/research-paper-writing
cp /path/to/EDA-Writing-Skills/skills.md .claude/skills/research-paper-writing/SKILL.md
```

**全局安装**（所有项目可用）：

```bash
mkdir -p ~/.claude/skills/research-paper-writing
cp /path/to/EDA-Writing-Skills/skills.md ~/.claude/skills/research-paper-writing/SKILL.md
```

> 技能中引用了 `references/` 下的章节指南（如 `references/introduction.md`）。如果仓库提供了这些文件，请将整个目录一并拷贝到 skill 目录下。

## 用法

安装后在 Claude Code 中直接用自然语言触发，或通过 `/research-paper-writing` 显式调用。典型用法：

```text
# 重写某一章节
帮我按 EDA 顶会标准重写 Introduction，目标会议是 DAC。

# 检查段落是否流畅
这段 Method 的第二段读起来顺吗？帮我做 paragraph clarity check。

# 检查 claim 是否有实验支撑
检查 Abstract 里的每个 claim 是否都有 Experiments 部分的证据支持，给出 claim-evidence map。

# 投稿前整体自审
论文快写完了，帮我做一轮五维度的 adversarial review，列出高风险被拒点。
```

### 输出格式

当要求重写或起草章节时，技能会返回：

1. 精简的章节 outline（3–7 条）；
2. 标注了段落角色（opening / challenge / method / advantage / evidence / limitation）的改写段落；
3. 覆盖清晰度、衔接、术语一致性、无支撑 claim、证据缺失的自查清单；
4. 每个主要 claim 的对齐表：`Claim: ... | Evidence: ... | Status: supported/needs evidence`。

## 建议工作流

1. 先和 Claude 对齐论文的核心 story，再做句子级修改；
2. 逐段改写，每段只承载一个 message；
3. 每写完一节做一次 reverse outlining；
4. 用 claim–evidence map 核对 Abstract / Introduction 的所有主要 claim；
5. 定稿前用 paper review checklist 做对抗式自审，逐条消除高风险问题。

## 致谢与引用

本仓库参考了 [Master-cai/Research-Paper-Writing-Skills](https://github.com/Master-cai/Research-Paper-Writing-Skills)，在其论文写作技能框架的基础上，结合了自己在 EDA 顶会投稿中的写作经验进行调整和扩展。感谢原作者的开源分享。

如果本仓库对你有帮助，也请同时关注并致谢原仓库。

## License

见 [LICENSE](LICENSE)。
