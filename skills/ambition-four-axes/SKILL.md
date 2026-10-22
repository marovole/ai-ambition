---
name: ambition-four-axes
description: "Use when an AI agent task should aim higher. Rewrites it along Speed / Altitude / Depth / Range into concrete prompts, each with an outside check and the access the agent needs. Triggers: make this more ambitious, upgrade this prompt, 更有野心, 往上一层, 往深一层, 跨领域."
version: 0.1.0
author: marovole (翡冷翠)
license: MIT
metadata:
  hermes:
    tags: [prompting, agents, ambition, task-design, verification]
  source: "Framework adapted from Felix Rieseberg, 'How to be more ambitious: A tutorial for humans with models' (2026-10-13), https://felixrieseberg.com/how-to-be-more-ambitious-a-tutorial-for-humans-with-models/"
---

# Ambition Four Axes（四个方向放大 AI 任务）

Turn a modest request to an AI agent into a more ambitious one along four axes: Speed, Altitude, Depth, Range. Then make the ambitious version runnable and verifiable.

Trigger phrases: "make this more ambitious", "我是不是用错了", "更有野心", "往上一层/往深一层/跨领域", "升级这个提示词", "这个任务还能怎么做大", or any prompt that is clearly one micro-step of a bigger goal.

## Goal

The user leaves with one or more rewritten task briefs that aim higher than what they asked for, each with a concrete way to check the result that does not depend on the model's own judgment, plus a list of the environment pieces (data, tools, access) the agent needs to actually do it.

## The four axes

- Speed: same work, less time. Baseline value; needs little creativity. Mention only if the user's real bottleneck is time.
- Altitude: go up one level of abstraction. Ask "what should happen next? what is the goal behind this goal?" Example: from "fix this crash" to "keep the app crash-free".
- Depth: do the task the way a field-leading expert would. Use their instruments, start from raw material, set unreasonable targets, challenge assumptions, produce new knowledge, use an outside judge.
- Range: pull in fields the task does not obviously need. Rewrite nouns as verbs, then assemble the crew of disciplines that verb calls for.

Details, techniques and worked examples: references/axes.md. Copy-ready prompt templates: references/prompts.md.

## Procedure

1. Restate the user's task in one line, and name the outcome they ultimately care about. If you can't infer the outcome, ask exactly one question.
   Decide the mode:
   - Upgrade mode (user wants a better prompt or plan): return the ladders below.
   - Do mode (user asked for a working artifact, e.g. a script): deliver the as-asked version first, or name it as rung 0, then offer at most 2 higher rungs. Never let the options replace the thing they asked for.
2. Pick the axes that fit (usually 1–2, not all four):
   - Altitude fits when there is a real end outcome or a downstream decision the work feeds (a meeting is a strong tell, not a requirement). It fits creative work poorly.
   - Depth fits when quality of one deliverable matters most.
   - Range fits when the deliverable has to persuade, ship, or survive contact with different audiences.
3. For each chosen axis, write a ladder of 2–3 rungs, each more ambitious than the last. Keep every rung a concrete instruction the agent can start on now.
4. For every rung, attach:
   - Outside check: a test, script, holdout data, benchmark, or human/stakeholder signal. The model grading itself does not count.
   - Prerequisites: data sources, tools, permissions, machines, plus hard real-world limits (login/2FA that can't be automated, platform terms, compliance sign-off, account risk). Missing prerequisites are the usual reason ambitious prompts fail; list them plainly.
   - If a rung only works under a condition you can't confirm, mark it `Blocked if: <condition> → fall back to <rung>` instead of hiding the branch in Needs.
   - For non-technical work (writing, decisions, org process), an outside check can be a human signal, but make it concrete: who (≥1 named role other than the requester), what action counts as a pass, and by when.
5. Recommend one rung to try first: the highest one whose prerequisites are already met.

## Constraints

- Ambition means a different target or method, not a longer prompt. "Deeper, not bigger."
- Expert framing must change methods, not just vocabulary. If the plan still ends in a markdown table where an expert would use a database, a statistical model, or a profiler, push again.
- Range is about techniques, not role-play. Ask the agent to do what a short seller does to research a position, never to write like a short seller.
- Unreasonable targets are allowed (10s → 200ms), but each must come with a measurable check so "keep going" has a finish line.
- Don't invent the user's data, numbers, or org facts. Use placeholders like <last quarter's churn export> when unknown.
- Respect real limits: "go make money" style goals are generally out of reach today; say so instead of pretending.
- Actions with real-world side effects (deploys, sending, spending, deleting) stay behind the user's approval even in the ambitious version.

## Output format

```
Task as given: ...
Outcome behind it: ...

[Axis] Altitude
  Rung 1: <prompt>
    Check: ...
    Needs: ...
  Rung 2: ...
[Axis] Depth
  ...

Start with: <axis + rung>, because <prerequisites met / cheapest check>.
```

If the user just wants their prompt upgraded, return only the rewritten prompt(s) plus the Check and Needs lines.

## Stop rules

- Stop after 1–2 axes, at most 5 rungs in total. More options dilute the push.
- Stop and ask if the outcome is unknowable from context.
- If the user asks you to execute a rung, switch from brainstorming to doing the task, and run the outside check before calling it done.

## Verification (before replying)

- [ ] Each rung changes the target or method, not just the wording.
- [ ] Each rung has an outside check that isn't the model's own opinion.
- [ ] Prerequisites are listed and nothing about the user's environment is assumed.
- [ ] No role-play framing survived in Range rungs.
- [ ] A single recommended starting rung is named.
- [ ] In do mode, the as-asked artifact is delivered (or explicitly rung 0), not replaced by options.
- [ ] Total rungs ≤ 5; conditional rungs use a `Blocked if` line.

## Credit

The four-axis framing, the QBR / crash-free examples, and the "deeper, not bigger" prompt idea come from Felix Rieseberg's essay linked in the frontmatter. This skill is an independent adaptation for agent workflows; read the original for the full argument.
