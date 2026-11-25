# 🏛️ LLM Council

A [Claude Code](https://claude.com/claude-code) skill that pressure-tests a high-stakes decision from **five independent angles** before you commit to it.

Ask one AI a question and you get one answer from one perspective — you can't tell if it's great or mid. The council runs your question through 5 independent advisors with fundamentally different thinking lenses, has them **peer-review each other anonymously**, then a chairman synthesizes a final verdict.

Adapted from [Andrej Karpathy's LLM Council](https://github.com/karpathy/llm-council) (multiple models → anonymous peer review → chairman), rebuilt to run inside a single Claude Code session using sub-agents instead of different models.

> **Core principle:** independence first, then cross-examination. Advisors never see each other until the peer-review round, and reviews are anonymized — so verdicts come from merit, not deference.

## When to use it

For questions where **being wrong is expensive** and there's genuine uncertainty:

- "Should I launch a \$97 workshop or a \$497 course?"
- "Which of these 3 positioning angles is strongest?"
- "I'm pivoting from X to Y — am I crazy?"
- "Here's my landing page copy / pricing / hire-vs-automate call — pressure-test it."

**Not** for one-right-answer lookups, creation tasks, or trivial "should I" calls with no real stakes.

## The five advisors

Thinking styles, not job titles — chosen to create three natural tensions.

| Advisor | Lens | Hunts for |
|---|---|---|
| **The Contrarian** | downside | the fatal flaw, what's missing, what will fail |
| **The First Principles Thinker** | reframe | "are we even solving the right problem?" — strips assumptions |
| **The Expansionist** | upside | overlooked opportunity, what if this works *bigger* |
| **The Outsider** | fresh eyes | zero context; catches curse-of-knowledge blind spots |
| **The Executor** | feasibility | "OK but what do you do Monday morning?" |

**The tensions:** Contrarian vs Expansionist (downside/upside), First Principles vs Executor (rethink/just-do-it), the Outsider in the middle keeping everyone honest.

## How it works

1. **Frame the question** — reframe your raw question into one neutral prompt every advisor receives, grounded in relevant workspace context.
2. **Convene** — 5 advisor sub-agents run **in parallel**, each leaning fully into its lens (parallelism keeps them independent).
3. **Peer review** — responses are anonymized A–E; each advisor names the strongest answer, the biggest blind spot, and what *all five* missed.
4. **Chairman synthesis** — one agent weighs every response + review into a single, un-hedged verdict.
5. **Verdict in chat** — where the council agrees, where it clashes, blind spots it caught, the recommendation, and the one thing to do first.

The exact sub-agent prompt templates live in [`references/prompts.md`](references/prompts.md).

## Install

Clone into your Claude Code skills directory:

```bash
git clone https://github.com/gouveaero/llm-council.git ~/.claude/skills/llm-council
```

Then trigger it in any Claude Code session with phrases like **"council this"**, **"run the council"**, **"pressure-test this"**, or **"leva pro conselho"**.

## Credits

- Concept: [Andrej Karpathy — LLM Council](https://github.com/karpathy/llm-council)
- Five-advisor council skill (Contrarian, First Principles Thinker, Expansionist, Outsider, Executor + chairman): [Ole Lehmann](https://x.com/itsolelehmann), [aiwithremy/claude-skills-llm-council](https://github.com/aiwithremy/claude-skills-llm-council)
- Claude Code sub-agent adaptation: this skill.

## License

[MIT](LICENSE)
