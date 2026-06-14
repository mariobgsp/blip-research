# Superpowers: Comparison & Analysis

**Date:** Sun Jun 14 2026
**Basis:** Two parallel sessions on identical projects — one with Superpowers, one without

---

## What is Superpowers?

Superpowers is a complete software development methodology for coding agents, built on composable skills and instructions that make your agent follow structured workflows automatically. It's not a tool — it's a set of mandatory process skills that trigger before tasks.

**Core idea:** Instead of an agent jumping straight into code, Superpowers enforces a disciplined workflow:

1. **Brainstorming** — Refine ideas through questions, explore alternatives, present design in sections
2. **Writing Plans** — Break work into bite-sized tasks (2-5 min each) with exact file paths, code, and verification steps
3. **Subagent-Driven Development** — Dispatch fresh subagents per task with two-stage review (spec compliance, then code quality)
4. **Test-Driven Development** — RED-GREEN-REFACTOR cycle
5. **Verification Before Completion** — Verify before declaring success

---

## How Superpowers Works

### The Basic Workflow

```
Brainstorming → Writing Plans → Subagent Execution → Code Review → Completion
```

1. **brainstorming** — Activates before writing code. Refines rough ideas through questions, explores alternatives, presents design in chunks for validation. Saves design document.

2. **writing-plans** — Activates with approved design. Breaks work into 2-5 minute tasks. Every task has exact file paths, complete code, verification steps.

3. **subagent-driven-development** — Dispatches fresh subagent per task with two-stage review (spec compliance, then code quality).

4. **test-driven-development** — RED-GREEN-REFACTOR: write failing test → watch it fail → write minimal code → watch it pass → commit.

5. **verification-before-completion** — Ensure it's actually fixed before claiming success.

### Key Principle

The agent checks for relevant skills before any task. These are mandatory workflows, not suggestions.

---

## Comparison: With vs Without Superpowers

### Session Setup

| Metric | Without Superpowers | With Superpowers |
|--------|-------------------|-----------------|
| Session ID | `ses_13a1c9ef3ffeWEd3aruK2iQpLC` | `ses_ui_ux_enhancement` |
| Project | `say-no-to-mbg-copy` | `say-no-to-mbg` |
| Model | opencode/mimo-v2.5-free | opencode/mimo-v2.5-free |
| Starting point | Same React 19 + TypeScript + Vite project | Same project |

### Process Comparison

| Phase | Without Superpowers | With Superpowers |
|-------|-------------------|-----------------|
| **1. Repo Analysis** | Read files, summarize | Read files, summarize |
| **2. Design** | ❌ None — jumped straight to implementation | ✅ Brainstorming skill: visual companion, 3 approaches presented, 5 design sections validated |
| **3. Planning** | ❌ None — ad-hoc todo list of 8 items | ✅ Writing-plans skill: design spec (266 lines) + implementation plan (9 tasks) |
| **4. Implementation** | Single-threaded: 7 enhancements sequentially | Parallel: 9 subagents dispatched simultaneously |
| **5. Code Review** | ❌ None — manually checked build/lint | ✅ Verification-before-completion: 2 review subagents (spec compliance + code quality) |
| **6. Verification** | Build passes, lint clean | Build passes, lint clean, code review passed (0 blockers, 0 critical) |

### Results Comparison

| Metric | Without Superpowers | With Superpowers | Difference |
|--------|-------------------|-----------------|------------|
| **Enhancements** | 7 | 9 | +2 more |
| **Files modified** | 9 | 9 | Same |
| **CSS lines added** | ~150 | ~200 | +50 more |
| **TSX lines modified** | ~80 | ~150 | +70 more |
| **Total time** | ~24 min | ~35 min | +11 min slower |
| **Tool calls** | ~45+ | ~60+ | +15 more |
| **Subagents dispatched** | 0 | 11 (9 impl + 2 review) | +11 |
| **Context usage** | 57% (120K/200K) | 131% (289K/200K) | +74% (overflow) |
| **Code review** | ❌ Manual | ✅ Automated (2 reviewers) | Quality gate |
| **Design spec** | ❌ None | ✅ 266 lines | Documentation |
| **Implementation plan** | ❌ None | ✅ 9 tasks documented | Documentation |

### What Each Approach Produced

#### Without Superpowers (say-no-to-mbg-copy)
1. Mobile hamburger menu
2. Back-to-top button
3. Enhanced card hover effects
4. News scroller navigation
5. Improved mobile timeline
6. Accessibility improvements
7. Visual polish (animations, gradients)

#### With Superpowers (say-no-to-mbg)
1. Design system updates (CSS variables, animations, utility classes)
2. Navbar active section indicator
3. Hero gradient background, entrance animations
4. Vote section click animations, particle effects
5. Analytics section interactive chart tooltips
6. News scroller scroll-snap, pagination dots
7. Timeline gradient spine, hover effects, expandable cards
8. Harmful projects hover effects
9. Footer social links hover effects

---

## Pros and Cons

### Pros of Using Superpowers

| Benefit | Evidence |
|---------|----------|
| **More structured process** | Brainstorming → Plan → Execute → Review flow ensures design is validated before coding |
| **Parallel execution** | 9 subagents ran simultaneously, each handling one task independently |
| **Built-in code review** | Two-stage review caught issues before user saw them |
| **More enhancements** | 9 vs 7 — more work completed per session |
| **Better documentation** | Design spec (266 lines) + implementation plan created as artifacts |
| **Consistent quality** | Code review passed with 0 blockers, 0 critical issues |
| **Reusable plans** | Implementation plan can be re-run or adapted for future work |

### Cons of Using Superpowers

| Drawback | Evidence |
|----------|----------|
| **Higher context usage** | 131% vs 57% — caused context overflow requiring resets |
| **Longer session time** | ~35 min vs ~24 min — 46% slower due to process overhead |
| **More tool calls** | ~60+ vs ~45+ — skill loading and subagent dispatch add overhead |
| **Context overflow risk** | Subagent dispatches with full file contents consume massive context |
| **Overhead for simple tasks** | Brainstorming + planning phases may be overkill for straightforward enhancements |
| **Learning curve** | User needs to understand when skills trigger and how to work with them |

---

## Optimization Opportunities

### Reducing Context Usage

| Optimization | Impact |
|-------------|--------|
| **Reduce subagent file content** | Instead of sending full file contents to subagents, send only the relevant sections |
| **Skip visual companion for simple tasks** | Visual companion is token-intensive; skip it for non-visual questions |
| **Use executing-plans instead of subagent-driven-development** | executing-plans runs in batches with human checkpoints, lower context overhead |
| **Batch similar tasks** | Group related enhancements into single subagent tasks |

### Reducing Time Overhead

| Optimization | Impact |
|-------------|--------|
| **Skip brainstorming for well-defined tasks** | If requirements are clear, go straight to planning |
| **Use parallel task dispatch earlier** | Don't wait for full design approval on independent tasks |
| **Combine planning and execution** | For small projects, merge writing-plans into a single step |

### When to Use Superpowers vs Not

| Scenario | Recommendation |
|----------|---------------|
| **Complex feature with unclear requirements** | ✅ Use Superpowers — brainstorming clarifies intent |
| **Multiple independent tasks** | ✅ Use Superpowers — parallel subagents speed things up |
| **Simple, well-defined enhancement** | ❌ Skip Superpowers — direct implementation is faster |
| **Prototyping/quick iteration** | ❌ Skip Superpowers — process overhead slows experimentation |
| **Production code with quality requirements** | ✅ Use Superpowers — code review catches issues |
| **Learning/understanding a codebase** | ❌ Skip Superpowers — just read files directly |

---

## What Can Be Optimized

### With Superpowers

1. **Subagent context minimization** — Send only relevant code sections, not full files
2. **Smart skill selection** — Don't activate brainstorming for trivial tasks
3. **Context window management** — Use git worktrees to isolate sessions and reduce context bleed
4. **Task batching** — Group related tasks to reduce subagent count
5. **Incremental planning** — Create plans in phases instead of all at once

### Without Superpowers

1. **Manual design review** — Ask clarifying questions before coding (mimic brainstorming)
2. **Write implementation plan** — Create a simple plan before starting (mimic writing-plans)
3. **Code review** — Review your own work before declaring done (mimic verification)
4. **Parallel file edits** — Use multiple tool calls in parallel (mimic subagent parallelism)
5. **Build verification** — Always run build + lint before finishing (already done in both sessions)

---

## Conclusion

Superpowers adds structure and quality gates at the cost of time and context. For this specific UI/UX enhancement task:

- **Without Superpowers**: Faster (24 min), less context (57%), fewer enhancements (7), no documentation
- **With Superpowers**: Slower (35 min), more context (131% overflow), more enhancements (9), full documentation + code review

The optimal approach depends on task complexity:
- **Simple tasks**: Direct implementation wins on speed
- **Complex tasks**: Superpowers wins on quality and completeness
- **Context-limited sessions**: Without Superpowers is safer
- **Quality-critical code**: Superpowers' review process is valuable

**Recommendation**: Use Superpowers for production features and complex multi-step tasks. Skip it for quick prototypes, simple fixes, and context-constrained sessions.
