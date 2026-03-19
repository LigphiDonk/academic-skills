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

---

### `academic-figure-prompt` — Academic Figure Prompt

Generates highly detailed English prompts for AI image tools (NanoBanana / Gemini / DALL-E / Midjourney) to produce top-conference-quality academic figures — framework diagrams, network architecture diagrams, pipeline flowcharts, module detail diagrams, comparison/ablation figures, and data pattern grids.

**Triggers automatically when you say things like:**
- 论文配图提示词 / 生成论文配图 / 架构图提示词
- 顶会风格配图 / CVPR 风格图 / NeurIPS 风格图
- 给我的论文写生图 prompt
- paper figure prompt / academic diagram prompt
- Provide a `.tex` / `.pdf` / `.docx` file and ask for figure prompts

**What it does:**

1. Reads the paper source (LaTeX, PDF, Word) and extracts concepts, architectures, and data flows for each section
2. Presents **8 preset color schemes** to choose from before generating anything — plus links to 6 color picker tools for custom palettes
3. Generates an information-dense, multi-layer English prompt per figure, covering: global description, section-by-section module breakdown with embedded monochrome thumbnails, math formula annotations, dimension labels, and a complete STYLE SPECIFICATIONS block
4. Enforces academic figure standards: white-dominant layout, max 3 accent colors, no colored fills, no banner bars, no gradients — passes the grayscale print test

**Color scheme presets:**

| # | Name | Style |
|---|------|-------|
| A | Okabe-Ito | Nature / Science / CVPR, colorblind-safe |
| B | Blue mono | Minimal, module detail diagrams |
| C | Teal + Amber | Modern, ICLR / NeurIPS feel |
| D | Navy + Coral | Authoritative, IEEE journal feel |
| E | Slate + Violet | Elegant, medical / bioinformatics |
| F | Forest + Gold | Classic, natural science journals |
| G | Minimal Grey | Extreme minimal, arXiv report style |
| H | Custom | User-supplied hex values |

**Color tools included:** Coolors, ColorHunt, Adobe Color, ColorBrewer (academic data viz), Viz Palette (colorblind simulation), Paletton

**Supported figure types:** Overall framework · Network architecture · Module detail · Comparison / Ablation · Data / Behavior pattern grid

## Install

```bash
# Install the full collection
npx skills add LigphiDonk/academic-skills

# Install a single skill by id
npx skills add LigphiDonk/academic-skills --skill real-literature-trace
npx skills add LigphiDonk/academic-skills --skill academic-figure-prompt
```

Restart Claude Code after installing to activate the skills.

## Usage

Once installed, skills trigger automatically from natural language.

**Real Literature Trace:**

```
帮我找近五年关于"图神经网络"的核心文献，需要有 CNKI 地址
```

```
Find 10 papers on spacecraft pursuit-evasion games from top journals, with DOI links
```

**Academic Figure Prompt:**

```
给我的论文生成整体框架图的提示词，论文在 /path/to/thesis.tex
```

```
为第四章的网络架构图生成 prompt，用 Teal + Amber 配色
```

```
paper figure prompt for my CVPR submission, chapter 3 pipeline diagram
```

## Repository layout

```
academic-skills/
├── real-literature-trace/
│   └── SKILL.md       # trigger conditions, search workflow, output spec
└── academic-figure-prompt/
    └── SKILL.md       # color selection, prompt templates, style specs
```

Each skill lives in its own directory. `SKILL.md` defines trigger conditions, the workflow, and output format.
