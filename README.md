# EDA-Writing-Skills

**English** | [中文](README.zh-CN.md)

A Claude Code Skill for **paper writing targeting top EDA conferences and journals** (DAC, ICCAD, DATE, ASP-DAC, TCAD, etc.). It helps you rewrite paper drafts into reviewer-friendly, high-clarity versions: paragraph logic, section structure, figure/table quality, claim–evidence alignment, and pre-submission adversarial self-review.

## Features

- **Section-level guidance**: dedicated writing guidelines for Abstract / Introduction / Related Work / Method / Experiments / Conclusion, loaded on demand.
- **Paragraph-level polishing**: one message per paragraph, topic-first sentences, sentence-to-sentence flow checks (cause / contrast / consequence / refinement), plus reverse outlining to verify the logical chain.
- **Claim–evidence alignment**: every major claim in the Abstract and Introduction must map to experimental evidence; unsupported claims are weakened or removed.
- **Pre-submission self-review**: adversarial checks from a reviewer's perspective across five dimensions — contribution, writing clarity, experimental strength, evaluation completeness, and method design soundness.
- **Figure/table standards**: quality requirements for teaser / pipeline figures and minimal-ink tables, treating visual quality as core content rather than decoration.

## Installation

This skill is provided as a [Claude Code Skill](https://docs.anthropic.com/en/docs/claude-code).

**Project-level install** (available only in the current paper repository):

```bash
mkdir -p .claude/skills/research-paper-writing
cp /path/to/EDA-Writing-Skills/skills.md .claude/skills/research-paper-writing/SKILL.md
```

**Global install** (available in all projects):

```bash
mkdir -p ~/.claude/skills/research-paper-writing
cp /path/to/EDA-Writing-Skills/skills.md ~/.claude/skills/research-paper-writing/SKILL.md
```

> The skill references section guides under `references/` (e.g., `references/introduction.md`). If the repository provides these files, copy the whole directory into the skill directory as well.

## Usage

After installation, trigger the skill with natural language in Claude Code, or invoke it explicitly via `/research-paper-writing`. Typical usage:

```text
# Rewrite a section
Rewrite my Introduction to top-EDA-conference standards; the target venue is DAC.

# Check whether a paragraph flows
Does the second paragraph of my Method section read smoothly? Run a paragraph clarity check.

# Check whether claims are backed by experiments
Check whether every claim in the Abstract is supported by evidence in the Experiments section, and give me a claim-evidence map.

# Full pre-submission self-review
The paper is almost done. Run a five-dimension adversarial review and list the high-risk rejection points.
```

### Output format

When asked to rewrite or draft sections, the skill returns:

1. A compact section outline (3–7 bullets);
2. Revised paragraphs annotated with paragraph roles (opening / challenge / method / advantage / evidence / limitation);
3. A self-review checklist covering clarity, flow, terminology consistency, unsupported claims, and missing evidence;
4. An alignment map for each major claim: `Claim: ... | Evidence: ... | Status: supported/needs evidence`.

## Recommended workflow

1. Align on the paper's core story with Claude before making sentence-level edits;
2. Rewrite paragraph by paragraph, with each paragraph carrying exactly one message;
3. Run reverse outlining after finishing each section;
4. Verify all major claims in the Abstract / Introduction with a claim–evidence map;
5. Before finalizing, run an adversarial self-review with the paper review checklist and resolve every high-risk issue.

## Acknowledgments

This repository is based on [Master-cai/Research-Paper-Writing-Skills](https://github.com/Master-cai/Research-Paper-Writing-Skills). Building on its paper-writing skill framework, it has been adapted and extended with my own experience from submitting to top EDA conferences. Many thanks to the original author for open-sourcing their work.

If this repository helps you, please also star and credit the original repository.

## License

See [LICENSE](LICENSE).
