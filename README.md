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

## Current Focus: Entire CLI

[Entire CLI](https://docs.entire.io) is a session tracking and checkpoint system for AI coding agents. It records every interaction and creates persistent checkpoints tied to git commits.

### Analysis Documents

| Document | Description |
|----------|-------------|
| [`ENTIRE-CLI-GUIDE.md`](ENTIRE-CLI-GUIDE.md) | How entire-cli works, setup, commands, real test results, review |
| [`physics-phenomena-test-results.md`](physics-phenomena-test-results.md) | Raw output from doctor, status, sessions, checkpoints |

### Key Findings

- **Session tracking**: All 4 sessions captured automatically (~24.6M tokens total)
- **Checkpoint creation**: 3 checkpoints tied to git commits with full transcripts
- **Local features work**: doctor, status, session list, checkpoint list, checkpoint explain - no auth needed
- **Cloud features need auth**: recap, search, dispatch, review require `entire login`
- **Critical bug found**: React 19 StrictMode `useMemo` double-call caused slider changes to modify wrong sim instance

### Test Results

Tested on `physics-phenomena` repo with `feat/interactive-controls-and-slider-fix` branch:
- 4 commits, 34 files changed, +2397/-312 lines
- ~24.6M tokens across 4 sessions
- 98% of tokens spent debugging React StrictMode bug

## Model Used

All analysis performed with `opencode/mimo-v2.5-free` (200K context, 32K output, $0 free tier).