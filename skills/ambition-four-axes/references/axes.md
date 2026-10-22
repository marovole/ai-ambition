# The four axes in detail

Adapted from Felix Rieseberg, "How to be more ambitious: A tutorial for humans with models" (2026-10-13). Paraphrased; see the original for his wording.

Running example used throughout: a company needs a quarterly business review (QBR) deck, and is worried about customer churn.

## Speed

Same work in less time. It is the established, economically obvious use of AI and needs little creativity in how you approach the model. Only bring it up when time is the user's real constraint.

## Altitude: go up a level

Question to ask: what do you want to happen next? What is the goal beyond the goal?

Ladder for the QBR:
1. Don't just refresh the numbers in the template. Give the model as much business data as you can and ask what changed this quarter, why, and what to do about it.
2. Good meetings end in decisions. Ask it to work out the three most urgent decisions given everything it learned, and start drafting directions with for/against arguments.
3. Question the format itself. The review exists so leadership catches problems early and moves money and people to the right places. Ask it to design a better mechanism than a quarterly deck, show from the company's own history that it would have caught problems sooner, and run it beside the current process for a quarter.

When it fits: there is a real ultimate outcome; a good tell is that the work would otherwise lead to meetings. Fits creative work less well.

Limits: open-ended goals like "go make money" don't work for most businesses yet; capable models handle higher abstraction over time.

Agent implication: altitude usually requires changing the workflow so the human can leave the loop. Rieseberg's example: before Claude could keep apps crash-free, it needed easy access to crash reports, a mapping from app versions to git commits, and Windows/macOS/Linux machines to reproduce and verify fixes on its own. Treat these as the prerequisites list.

## Depth: go down a level

Aim: push the model to use the tools, techniques, media, and knowledge of the best professionals in the field, until even those people might learn something.

Techniques:
- Insist on expert instruments. Models asked to "act like a professional" often switch vocabulary but not methods. Replace markdown tables with databases and statistical models. The user doesn't need to know the expert toolset; the model usually does.
- Unreasonable goals, framed as reasonable. Want the page to load in 5s instead of 10s? Ask for 200ms. If the model calls it impossible, restate that it is solvable and it should keep going.
- Challenge what you know. Business beliefs are often rough approximations. Give raw data and ask it to adversarially test assumptions: "We believe churn is an onboarding problem. Try to reproduce that from the raw data."
- Produce new knowledge. Once deep in the data, ask for blind spots: build a simulation of customers that reproduces last year from logs, find the earliest churn signal nobody knows about, and show it predicts on data it hasn't seen.
- Outside judge. Do not ask the model to judge itself. Prefer a tool the model can run for immediate feedback.

## Range: go wide

Aim: look at the work from more fields than used to be economical. Think of the heist-movie opening where the crew of specialists is assembled. Multi-agent setups (threads, orchestrators, subagents) make this cheap.

Techniques:
- Replace nouns with verbs (from Tom Kelley & Jonathan Littman, The Art of Innovation). A QBR is not "a deck"; it is getting busy people to believe a cause-and-effect story and decide under uncertainty in 30 minutes. The verbs suggest which fields matter.
- Assemble the crew. If the deck had to be extraordinary, who would you hire? Analyst, journalist, editor for quality; motion and audio designer if it's presented; an adversarial red team such as a short seller and a forensic accountant.
- Avoid role-play. It makes transcripts weirder without improving outcomes. Use the crew to find fields and techniques, then ask the agent to do what that specialist actually does.

This is the axis that needs the most creativity, and per Rieseberg, where the most surprising results show up.

## Common prerequisite

All of the above assume the model has a computer where it can install software, plus access to the relevant data (via MCP connectors or other means). If the agent lacks these, the first rung is usually "set up access", not a better prompt.

## Why people under-reach (optional context for the user)

Rieseberg frames it as self-efficacy: people are held back by what they believe possible and tend to trust themselves only in narrow disciplines. Specific hard goals beat "do your best" (Locke & Latham's goal-setting research); seeing someone else do it, and giving yourself permission to fail, also help.
