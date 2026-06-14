# blip-research

Research and analysis of AI coding agent tools and methodologies.

## Current Focus: Superpowers

[Superpowers](https://github.com/obra/superpowers) is a complete software development methodology for coding agents, built on composable skills that enforce structured workflows (brainstorming, planning, TDD, code review).

### Analysis Documents

| Document | Description |
|----------|-------------|
| [`superpowers/SUPERPOWERS-COMPARISON.md`](superpowers/SUPERPOWERS-COMPARISON.md) | Side-by-side comparison: with vs without Superpowers on identical projects |
| [`superpowers/SUPERPOWERS-TESTING-PROOF.md`](superpowers/SUPERPOWERS-TESTING-PROOF.md) | Testing evidence, model analysis (opencode/mimo-v2.5-free), and optimization recommendations |

### Key Findings

- **With Superpowers**: 9 enhancements, 35 min, design spec + code review, but 131% context overflow
- **Without Superpowers**: 7 enhancements, 24 min, no documentation, 57% context usage
- **Model constraint**: Free tier model (200K context) causes overflow with Superpowers' subagent workflow
- **Recommendation**: Use paid model (Claude Sonnet 4 or Gemini 2.5 Pro) for Superpowers sessions

## Planned Research

More AI coding tools to evaluate:

- [ ] Aider
- [ ] Cursor
- [ ] Windsurf
- [ ] GitHub Copilot
- [ ] Cline
- [ ] Continue.dev

## Model Used

All analysis performed with `opencode/mimo-v2.5-free` (200K context, 32K output, $0 free tier).