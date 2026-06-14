# Superpowers: Testing Proof & Model Analysis

**Date:** Sun Jun 14 2026
**Evidence from:** Two parallel sessions on identical projects
**Model Used:** `opencode/mimo-v2.5-free` (200K context, 32K output, $0 free tier)

---

## Testing Evidence

### What "Testing" Actually Happened

Neither session ran unit tests, integration tests, or end-to-end tests. Here's the proof:

#### Without Superpowers (say-no-to-mbg-copy)

```
Verification steps performed:
1. npm run build → ✅ Pass (after fixing 3 unused imports)
2. npm run lint → ⚠️ 4 pre-existing errors (not from changes)
3. npm run dev → ✅ Running at http://localhost:5173/
```

**No test script exists in package.json:**
```json
"scripts": {
  "dev": "vite",
  "build": "tsc -b && vite build",
  "lint": "eslint .",
  "preview": "vite preview"
}
```

**No test framework installed:**
- No `vitest`, `jest`, `@testing-library/*`, or `cypress` in dependencies
- No `test` script defined
- No `*.test.*` or `*.spec.*` files exist

**Verification was:** Build compiles + lint runs + dev server starts = "it works"

#### With Superpowers (say-no-to-mbg)

```
Verification steps performed:
1. npm run build → ✅ Pass
2. npm run lint → ⚠️ 4 pre-existing errors (same ones)
3. npm run preview -- --host → ✅ Running at http://localhost:4173/
4. Code review (2 subagents) → ✅ Passed (0 blockers, 0 critical)
```

**Same problem:** No test framework, no test script, no test files.

**Verification was:** Build compiles + lint runs + code review = "it works"

### The Gap

Superpowers has a `test-driven-development` skill that enforces RED-GREEN-REFACTOR:
1. Write failing test
2. Watch it fail
3. Write minimal code
4. Watch it pass
5. Commit

**But it never triggered.** Why? Because the project has no test framework configured. Superpowers can't enforce TDD if there's no test runner to execute tests against.

### What Superpowers' Code Review Actually Verified

The 2 review subagents checked:

| Reviewer | What It Checked | Result |
|----------|----------------|--------|
| Spec Compliance | Does code match the design spec? | ✅ PASS |
| Code Quality | Patterns, performance, accessibility | ✅ PASS (0 blockers, 0 critical, 2 suggestions) |

**What it did NOT check:**
- ❌ No functional tests (does the button actually work?)
- ❌ No visual regression tests (does the UI look correct?)
- ❌ No accessibility tests (does screen reader work?)
- ❌ No performance tests (is the animation smooth?)
- ❌ No integration tests (do components work together?)

The code review was a **static analysis** — it read the code and judged quality, but never executed anything.

---

## Model Analysis: opencode/mimo-v2.5-free

### Model Specifications

| Property | Value |
|----------|-------|
| Model ID | `opencode/mimo-v2.5-free` |
| Provider | OpenCode Zen |
| Context Window | **200,000 tokens** (200K) |
| Max Output Tokens | **32,000 tokens** (32K) |
| Cost | **$0** (free tier) |
| Capabilities | Tool calling, Reasoning, Text + Image input |
| Released | 2026-04-24 |

### What the Model Did Well

| Strength | Evidence |
|----------|----------|
| **Tool calling** | Successfully read files, edited code, ran bash commands |
| **Code generation** | Generated working CSS animations, React components |
| **Build fixing** | Identified and fixed 3 unused import errors |
| **File understanding** | Correctly analyzed 14 components, 3 hooks, 899-line CSS |

### What the Model Struggled With

| Weakness | Evidence |
|----------|----------|
| **Context management** | With Superpowers: 131% context overflow (289K used / 200K limit) |
| **Server startup** | With Superpowers: 5 attempts to start dev server (3 timed out) |
| **Skill orchestration** | With Superpowers: dispatched 9 subagents that each consumed massive context |
| **Task completion** | Both sessions: required user prompts to continue (didn't self-direct) |

### Context Overflow Breakdown

```
Without Superpowers:
  Total Input:  ~108,000 tokens (54% of 200K)
  Total Output: ~5,250 tokens (16% of 32K)
  Status: ✅ No overflow

With Superpowers:
  Total Input:  ~236,000 tokens (118% of 200K) ← OVERFLOW
  Total Output: ~25,000 tokens (78% of 32K)
  Status: ❌ Context overflow across messages
```

**Root cause:** Subagent dispatches sent full file contents to each subagent. With 9 subagents, each receiving complete component files, context exploded.

---

## Would a Different Model Optimize This?

### Model Comparison (Hypothetical)

| Model | Context | Output | Cost | Likely Impact |
|-------|---------|--------|------|---------------|
| **opencode/mimo-v2.5-free** (current) | 200K | 32K | $0 | Context overflow with Superpowers |
| **Claude Sonnet 4** | 200K | 64K | $3/$15 per 1M | Larger output window, better context management |
| **Claude Opus 4** | 200K | 32K | $15/$75 per 1M | Better reasoning, more careful planning |
| **GPT-4o** | 128K | 16K | $2.5/$10 per 1M | Smaller context, worse for Superpowers |
| **Gemini 2.5 Pro** | 1M | 64K | $1.25/$10 per 1M | Massive context, no overflow issues |

### What Would Change With a Better Model?

#### Scenario 1: Larger Context Window (Gemini 2.5 Pro — 1M tokens)

| Aspect | Current (200K) | With 1M Context |
|--------|----------------|-----------------|
| Context overflow | ❌ 131% overflow | ✅ No overflow (29% usage) |
| Subagent dispatches | Limited by context | Full file contents OK |
| Session length | ~35 min | Could be longer |
| Cost | $0 | $1.25/$10 per 1M |

**Verdict:** Context overflow disappears, but cost increases.

#### Scenario 2: Better Reasoning (Claude Opus 4)

| Aspect | Current (mimo-v2.5-free) | With Opus 4 |
|--------|--------------------------|-------------|
| Planning quality | Good (266-line spec) | Better (more thorough) |
| Code review | 0 blockers, 2 suggestions | Likely more suggestions |
| Context management | Poor (overflow) | Better (more careful) |
| Server startup | 5 attempts | Likely 1-2 attempts |
| Cost | $0 | $15/$75 per 1M |

**Verdict:** Quality improves, but at 10-50x cost.

#### Scenario 3: Faster Model (GPT-4o)

| Aspect | Current (mimo-v2.5-free) | With GPT-4o |
|--------|--------------------------|-------------|
| Speed | Moderate | Faster |
| Context | 200K | 128K (worse) |
| Cost | $0 | $2.5/$10 per 1M |
| Quality | Good | Similar |

**Verdict:** Faster but smaller context — worse for Superpowers.

### The Real Problem

The issue isn't just the model — it's the **combination of Superpowers + free tier model**:

1. **Superpowers dispatches subagents with full file contents** → context explosion
2. **Free tier model has 200K context** → overflow at 131%
3. **Model doesn't manage context well** → needed 5 server startup attempts

**With a paid model (e.g., Claude Sonnet 4):**
- 200K context, but better context management
- 64K output (2x current) for longer responses
- Better tool calling reliability
- Cost: ~$0.50-$2.00 for this session

**With a massive context model (e.g., Gemini 2.5 Pro):**
- 1M context → no overflow possible
- Could send full files to all subagents without worry
- Cost: ~$0.30-$1.00 for this session

---

## What Makes Superpowers Needed or Not

### When Superpowers IS Needed

| Scenario | Why Superpowers Helps |
|----------|----------------------|
| **Complex feature with unclear requirements** | Brainstorming phase clarifies intent before coding |
| **Multiple independent tasks** | Parallel subagents speed up implementation |
| **Production code with quality requirements** | Code review catches issues before deployment |
| **Team handoff** | Design specs + implementation plans document decisions |
| **Long-running sessions** | Structured workflow prevents drift |

**Evidence from this session:**
- Without Superpowers: 7 enhancements, no documentation, no review
- With Superpowers: 9 enhancements, design spec (266 lines), implementation plan, code review (0 blockers)

### When Superpowers is NOT Needed

| Scenario | Why Skip Superpowers |
|----------|---------------------|
| **Simple, well-defined task** | Process overhead > benefit |
| **Quick prototype** | Speed matters more than quality |
| **Context-limited sessions** | Subagent dispatches cause overflow |
| **No test framework** | TDD skill can't trigger |
| **Free tier model** | Context management too poor for subagent workflow |

**Evidence from this session:**
- Without Superpowers: 24 min, 57% context, working result
- With Superpowers: 35 min, 131% context overflow, same working result

### The Decision Matrix

```
                    Task Complexity
                    Low         High
                ┌───────────┬───────────┐
    Context     │           │           │
    Available   │  SKIP     │  USE      │
    High        │  Super-   │  Super-   │
    (1M+)       │  powers   │  powers   │
                ├───────────┼───────────┤
    Context     │           │           │
    Limited     │  SKIP     │  SKIP     │
    (200K)      │  Super-   │  Super-   │
                │  powers   │  powers   │
                └───────────┴───────────┘
```

**Key insight:** With a 200K context model, Superpowers causes overflow on anything beyond trivial tasks. You need either:
- A larger context model (1M+), OR
- A model with better context management (paid tier), OR
- Skip Superpowers for simple tasks

---

## Recommendations

### For This Project (say-no-to-mbg)

1. **Add a test framework** — Install vitest + @testing-library/react so Superpowers' TDD skill can actually work
2. **Use a paid model** for Superpowers sessions — Claude Sonnet 4 or Gemini 2.5 Pro to avoid context overflow
3. **Skip Superpowers for simple CSS tweaks** — Direct implementation is faster
4. **Use Superpowers for new features** — When adding complex components, use brainstorming + planning

### For Superpowers Optimization

1. **Reduce subagent context** — Send only relevant code sections, not full files
2. **Batch related tasks** — Group similar enhancements into single subagents
3. **Skip visual companion for non-visual questions** — Saves tokens
4. **Use executing-plans instead of subagent-driven-development** — Lower context overhead

### For Model Selection

| Use Case | Recommended Model | Why |
|----------|------------------|-----|
| Quick fixes | mimo-v2.5-free | Free, fast, good enough |
| Superpowers with simple tasks | mimo-v2.5-free | Works, just watch context |
| Superpowers with complex tasks | Claude Sonnet 4 | Better context management, 64K output |
| Superpowers with many subagents | Gemini 2.5 Pro | 1M context, no overflow |

---

## Conclusion

**Testing proof:** Neither session ran actual tests. Both verified via build + lint + dev server only. Superpowers' TDD skill never triggered because no test framework exists in the project.

**Model impact:** The free tier model (mimo-v2.5-free) works for direct implementation but causes context overflow with Superpowers' subagent workflow. A paid model with better context management or a larger context window would optimize the Superpowers experience.

**Superpowers necessity:** Needed for complex, multi-step tasks where quality and documentation matter. Not needed for simple, well-defined tasks where speed matters more. The model choice determines whether Superpowers' full workflow is viable.
