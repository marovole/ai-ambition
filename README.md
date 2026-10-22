# AI 的野望 / AI Ambition

Agent skills for aiming higher with AI agents.

给 AI agent 用的 skill 合集，帮你把交给 AI 的事做得更有野心。

## Skills

### ambition-four-axes

Turns a small request into a more ambitious one along four axes (Speed, Altitude, Depth, Range). Each ambitious version comes out runnable: a concrete prompt, an outside check that doesn't rely on the model grading itself, and the data, tools, and access the agent needs.

把交给 AI agent 的小任务，沿速度、高度、深度、广度四个方向放大，并且每个放大版本都能直接用：给出可用的提示词、不靠模型自评的外部检验方法，以及 agent 需要的数据、工具和权限清单。

- 高度（Altitude）：往上一层，盯最终结果而不是单个步骤。例如从"修这个崩溃"到"让 App 保持不崩溃"。
- 深度（Depth）：按行业顶尖专家的方法做，用原始数据，目标定得离谱，结果交给外部裁判。
- 广度（Range）：拉进别的领域的方法，把名词换成动词，再组一支跨学科的队。
- 速度（Speed）：更快完成，基本盘，只在时间是真瓶颈时提。

Files:

- `skills/ambition-four-axes/SKILL.md`: procedure, constraints, output format, self-check
- `skills/ambition-four-axes/references/axes.md`: each axis explained with a worked example
- `skills/ambition-four-axes/references/prompts.md`: copy-ready prompt templates (English + 中文)

The framework comes from Felix Rieseberg's essay [How to be more ambitious: A tutorial for humans with models](https://felixrieseberg.com/how-to-be-more-ambitious-a-tutorial-for-humans-with-models/). This repo is an independent adaptation for agent workflows and is not affiliated with him or his employer.

框架出自 Felix Rieseberg 的文章（链接见上）。本仓库是面向 agent 工作流的独立改编，与作者本人及其雇主无关。

## Install

Works with any agent that reads `SKILL.md` folders (Claude Code, Codex, Hermes, etc.):

```bash
git clone https://github.com/marovole/ai-ambition.git
# Claude Code
cp -r ai-ambition/skills/ambition-four-axes ~/.claude/skills/
# Hermes
cp -r ai-ambition/skills/ambition-four-axes ~/.hermes/skills/
```

## Example

> Me: Summarize last week's customer support tickets for me.
>
> Skill: writes the summary as asked (rung 0), then offers at most two higher rungs. Depth: tag every raw ticket against a clear taxonomy instead of skimming (check: compare with a human-labeled sample of 50 tickets). Altitude: find the root causes behind the most frequent tickets and propose fixes (check: whether those ticket categories shrink next month). Every rung lists what it needs, such as export access to the helpdesk.

> 我：帮我总结一下上周的客服工单。
>
> Skill：先按要求把总结交了（第 0 级），再给最多两级升级。深度：不靠略读，按一套清晰的分类给每张原始工单打标签（检验：和人工标注的 50 张样本对比）。高度：找出最常见工单背后的根因并提出修复方案（检验：下个月这几类工单有没有变少）。每一级都写明需要什么，比如客服系统的导出权限。

## License

MIT for the skill text in this repo. Ideas and examples credited to the original essay remain its author's.
