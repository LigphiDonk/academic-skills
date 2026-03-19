# Academic Skills

**GitHub:** [LigphiDonk/academic-skills](https://github.com/LigphiDonk/academic-skills)

`academic-skills` 是一个用于 AI Agent 的 Skill 集合仓库。这里的每个 skill 都是一套面向特定任务的可复用工作流，Agent 在识别到对应场景后，可以按 `SKILL.md` 里的说明执行，减少重复提示和手工整理成本。

## 这个仓库里有什么

- `real-literature-trace/` - 用于真实学术文献检索、核验、筛选和整理

这个 skill 适合这些场景：

- 做文献综述
- 整理核心文献表
- 找 CNKI、DOI、出版社等可追溯链接
- 筛选近五年高质量论文
- 整理中英文混合文献

## Skill 是什么

你可以把 `skill` 理解成给 AI Agent 用的“任务手册”。

- 把一类重复任务封装成固定流程
- 让 Agent 在特定任务上更稳定、更可控
- 方便通过 GitHub 仓库安装、更新和分发

## 安装方式

如果你的环境支持 `npx skills`，可以直接从这个仓库安装。

安装整个仓库：

```bash
npx skills add LigphiDonk/academic-skills
```

只安装某个 skill：

```bash
npx skills add LigphiDonk/academic-skills --skill real-literature-trace
```

先查看仓库里可安装的 skill：

```bash
npx skills add LigphiDonk/academic-skills --list
```

## 使用示例

安装后，你可以直接让 Agent 按这个 skill 的方式工作，例如：

- `帮我找近五年的真实文献`
- `整理一个关于 XXX 的核心文献表`
- `把这些论文按 CNKI / DOI / 期刊来源分类`

安装完成后，重启 Codex 或重新加载 Agent 环境，让新 skill 生效。
