# Prompt templates

Fill the <placeholders>. Each template ends with a check line; keep it.

## Ladder skeleton (any axis)

```
Rung 0 (as asked): <the task exactly as requested>
Rung 1: <same outcome, one step more ambitious>
  Check: <outside signal>
  Needs: <data / tools / access / hard limits>
  Blocked if: <condition> → fall back to <rung>
Rung 2: <goal behind the goal, or expert-grade method>
  Check: ...
  Needs: ...
```

## Altitude

```
I asked you to <task>. The reason I want it is <outcome>.
Before doing the task as stated, propose the version of this work that would
directly secure <outcome> instead of just this step. Tell me what you'd need
access to (data, tools, permissions) to own that outcome without me feeding you
tasks one by one. Then start on the highest version you can do with what you have.
Check: <signal that the outcome happened, e.g. crash-free rate, decision made, metric moved>.
```

Ladder shortcut: task → what decision does this feed → what process produces that decision → design a better process and backtest it on our history.

## Depth: "deeper, not bigger"

Adapted from the prompt in Rieseberg's essay:

```
I want a deeper version of this task, not a bigger one. Before rewriting it:
1. Say what a top professional in this field would do here that I'm not asking for.
2. Name the rawest material they'd start from, instead of what's already been digested for me.
3. Name the specific methods and tools they'd use.
4. Say what, other than you or me, would show the result is right.
Then rewrite my prompt to ask for exactly that.

My task: <task>
```

中文版：

```
我要的是这个任务更深的版本，不是更大的版本。改写之前先回答：
1. 这个领域的顶尖专家会做什么我没要求的事；
2. 他们会从哪种最原始的材料起手，而不是用已经替我消化过的东西；
3. 他们会用哪些具体方法和工具；
4. 除了你和我，还有什么能证明结果是对的。
然后把我的提示词改写成正好要这些东西。

我的任务：<任务>
```

Unreasonable target add-on:

```
Target: <10x better number>. This is solvable. If you think it isn't, list what
blocks it and keep going on the parts that aren't blocked.
Check: <benchmark / measurement command>.
```

Assumption test add-on:

```
We believe <belief>. Using only <raw data>, try to reproduce that belief.
If you can't, tell me what the data supports instead.
```

## Range

```
Rewrite "<deliverable noun>" as what it must accomplish, in verbs.
List the 4–6 fields whose methods best serve those verbs, including at least one
adversarial field (someone who would try to break or short this).
For each field, name one concrete technique it would apply here, then apply it.
Don't write in anyone's voice; do the work each field would do.
Check: <who/what will receive the deliverable and how you'll know it landed>.
```

With subagents: one subagent per field, each returns findings plus evidence; the orchestrator merges and flags conflicts.
