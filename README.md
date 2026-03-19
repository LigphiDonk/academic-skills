# academic-skills

A collection of Claude Code skills for academic research workflows.

## Skills

### `real-literature-trace` — Real Literature Trace

Turns a vague literature request into a traceable paper set. Instead of generating plausible-sounding but fabricated references, this skill searches for real papers, verifies their sources, and returns canonical links you can actually open.

**Triggers automatically when you say things like:**
- 帮我找真实文献 / 找可追溯的论文
- 整理文献综述 / 核心文献表
- 筛选近五年优秀论文
- 找国外顶会顶刊论文
- Find me papers on X with real DOI links

**What it does:**

1. Narrows vague topics before searching — asks only the highest-value clarifying questions
2. Builds a bilingual keyword plan across Chinese and English sources
3. Searches with traceability in mind: CNKI for Chinese papers, DOI/publisher pages for international ones
4. Screens candidates by relevance, venue quality, and verifiability
5. Returns a structured table with title, authors, year, venue, selection rationale, quality grade (S/A/B/C), canonical link, CNKI link, and DOI

**Output example:**

| 序号 | 文献题目 | 作者 | 年份 | 期刊/会议 | 质量等级 | 真实地址 | DOI |
|------|----------|------|------|-----------|----------|----------|-----|
| 1 | ... | ... | 2023 | IEEE TAC | S | publisher page | 10.xxxx |

**Quality guarantee:** Never fabricates titles, DOIs, or links. Marks unverified links as `待核验`. Prefers fewer real papers over many unverifiable ones.

## Install

```bash
# Install the full collection
npx skills add LigphiDonk/academic-skills

# Install a single skill by id
npx skills add LigphiDonk/academic-skills --skill real-literature-trace
```

Restart Claude Code after installing to activate the skill.

## Usage

Once installed, the skill triggers automatically from natural language:

```
帮我找近五年关于"图神经网络"的核心文献，需要有 CNKI 地址
```

```
Find 10 papers on spacecraft pursuit-evasion games from top journals, with DOI links
```

```
做一个关于 XXX 的文献综述，中英文混合，15 篇左右
```

## Repository layout

```
academic-skills/
└── real-literature-trace/
    └── SKILL.md       # trigger conditions, search workflow, output spec
```

Each skill lives in its own directory. `SKILL.md` defines trigger conditions, the search workflow, screening rubric, and output format.
