# Entire CLI Test Results - physics-phenomena

**Date**: 2026-06-15
**Repo**: `/home/mariobgsp/Projects/physics-phenomena`
**Branch**: `feat/interactive-controls-and-slider-fix`
**Agent**: OpenCode (deepseek-v4-flash-free)

---

## Doctor Results

```
✓ Metadata branches: OK

Found 3 stuck session(s):

  Session: ses_1390895d4ffeESf2Pq2lYvPC4A
  Phase:   active
  Reason:  active, last interaction 13h21m0s ago
  Agent:   OpenCode
  Last interaction: 2026-06-14T23:30:29+07:00
  Shadow branch: not found
  Checkpoints: 0, Files touched: 0

  Session: ses_13917e57dffeyFgUsgRuzA2VcC
  Phase:   active
  Reason:  active, last interaction 13h ago

  Session: ses_1391e0a45ffezLE4wSIX06LhpU
  Phase:   active
  Reason:  active, last interaction 13h ago
```

**Note**: `entire doctor` found stuck sessions but the interactive TTY fix failed in non-interactive mode. Sessions marked "stale" need manual cleanup or running `entire doctor` in a TTY environment.

---

## Status

```
● Enabled · manual-commit · branch feat/interactive-controls-and-slider-fix
  Agents · OpenCode

── Active Sessions ─────────────────────────────────────────

OpenCode (deepseek-v4-flash-free) · ses_1390895d4ffeESf2Pq2lYvPC4A
> "For each of these 13 simulation files, read the `setParam..."
started 13h ago · active 13h ago · tokens 151k · stale

OpenCode (deepseek-v4-flash-free) · ses_13917e57dffeyFgUsgRuzA2VcC
> "For each file below, I need to understand:
1. What initia..."
started 13h ago · active 13h ago · tokens 55.3k · stale

OpenCode (deepseek-v4-flash-free) · ses_1391e0a45ffezLE4wSIX06LhpU
> "I need to find control key mismatches between phenomena.t..."
started 13h ago · tokens 177.3k · stale

OpenCode (deepseek-v4-flash-free) · ses_1394fb9c0ffeeZihiv5l6LpVOR
> "understand this project"
started 14h ago · active 12h ago · tokens 24268.3k
```

---

## Session List

| Session | Agent | Model | Tokens | Status | Checkpoint |
|---------|-------|-------|--------|--------|------------|
| `ses_1390895d4ffeESf2Pq2lYvPC4A` | OpenCode | deepseek-v4-flash-free | 151k | active/stale | `8720e48539b7` |
| `ses_13917e57dffeyFgUsgRuzA2VcC` | OpenCode | deepseek-v4-flash-free | 55.3k | active/stale | `8720e48539b7` |
| `ses_1391e0a45ffezLE4wSIX06LhpU` | OpenCode | deepseek-v4-flash-free | 177.3k | active/stale | `8720e48539b7` |
| `ses_1394fb9c0ffeeZihiv5l6LpVOR` | OpenCode | deepseek-v4-flash-free | 24,268.3k | idle | `960fb1eef357` |

**Total tokens used**: ~24,652k (~24.6M tokens across 4 sessions)

---

## Checkpoints

```
  branch       feat/interactive-controls-and-slider-fix
  checkpoints  3

● 960fb1eef357  "understand this project"
  06-15 00:02 (56d79ba) fix: slider and interactive input fixing

● ses_1394fb9c  [temporary]  carry forward: uncommitted session files
  06-14 23:59 (b0e678d) carry forward: uncommitted session files

● 8720e48539b7  "understand this project"
  06-14 23:58 (d15f394) feat: add interactive controls, rich explanations, and canvas annotations for...
```

---

## Checkpoint 8720e48539b7 - Detailed Breakdown

**Sessions**: 3 sessions merged into this checkpoint
**Total tokens**: ~383.6k (151k + 55.3k + 177.3k)
**Commit**: `d15f394` - "feat: add interactive controls, rich explanations, and canvas annotations for 13 physics sims"

### What Happened

This checkpoint captured a massive feature implementation across 3 parallel agent sessions:

#### Session 1 (ses_1390895d) - 151k tokens
**Task**: "For each of these 13 simulation files, read the `setParams` implementation..."
- Analyzed all 13 simulation files
- Mapped control keys vs setParams implementations
- Identified control mismatches between phenomena.ts and sim files

#### Session 2 (ses_13917e57) - 55.3k tokens
**Task**: "For each file below, I need to understand: 1. What initial state..."
- Deep-dived into simulation initialization patterns
- Documented each sim's initial state and reset behavior
- Identified which sims needed restart functionality

#### Session 3 (ses_1391e0a4) - 177.3k tokens
**Task**: "I need to find control key mismatches between phenomena.t..."
- Found and fixed control key mismatches
- Implemented `setParams` for all 13 sims
- Added `restart()` method to all sims
- Fixed the critical React StrictMode bug (useMemo side-effect)

### Files Modified
- `src/App.tsx` - Control handling, restart button, simKey state
- `src/data/phenomena.ts` - Extended Phenomenon interface, controls for 13 sims
- `src/components/SimulationCanvas.tsx` - RAF loop, annotation overlay
- `src/components/ExplanationAccordion.tsx` - New component
- `src/components/AnnotationOverlay.tsx` - New component
- `src/simulations/gravity.ts` - Controls, restart, particle effects
- `src/simulations/pendulum.ts` - Mass control, dynamic ball radius
- `src/simulations/projectile.ts` - Controls, restart
- `src/simulations/waves.ts` - Controls, restart, TDZ fix
- `src/simulations/doppler.ts` - Frequency control, restart
- `src/simulations/electric_field.ts` - Controls, restart
- `src/simulations/brownian.ts` - Controls, restart
- `src/simulations/spring.ts` - Controls, restart
- `src/simulations/bernoulli.ts` - Controls, restart
- `src/simulations/lorentz.ts` - Controls, restart
- `src/simulations/pascal.ts` - Controls, restart
- `src/simulations/buoyancy.ts` - Controls, restart
- `src/simulations/ideal_gas.ts` - Controls, restart
- `src/simulations/utils/easing.ts` - New utility
- `src/simulations/utils/effects.ts` - New utility
- `src/simulations/utils/particles.ts` - New utility
- `src/simulations/utils/annotations.ts` - New utility
- `src/simulations/utils/controls.ts` - ParamManager class
- `src/simulations/utils/index.ts` - Barrel exports

### Key Bug Fixed
**Root Cause**: React 19 StrictMode calls `useMemo` factories twice. The side-effect `simRef.current = sim` inside `useMemo` caused `simRef.current` to point to a discarded instance while `currentSim` held the used one. Slider changes modified the wrong object.

**Fix**: Removed side-effect from `useMemo`, added `useEffect` to sync `simRef.current = currentSim`.

---

## Checkpoint 960fb1eef357 - Detailed Breakdown

**Session**: ses_1394fb9c0ffeeZihiv5l6LpVOR
**Tokens**: 24,268.3k
**Commit**: `56d79ba` - "fix: slider and interactive input fixing"

### What Happened

This was the initial "understand this project" session that kicked off the entire feature:

1. **Project exploration** - Read all source files, understood architecture
2. **Brainstorming** - Used visual companion to design approaches
3. **Design approval** - User selected Approach B (Infrastructure-First)
4. **Spec creation** - Wrote design spec to `docs/superpowers/specs/`
5. **Implementation** - Built shared utils, data model, UI components
6. **Debugging** - Found and fixed the React StrictMode bug

### Brainstorming Artifacts Created
- `.superpowers/brainstorm/42278-1781450116/content/approaches.html`
- `.superpowers/brainstorm/42278-1781450116/content/control-animation-infra.html`
- `.superpowers/brainstorm/42278-1781450116/content/data-arch.html`
- `.superpowers/brainstorm/42278-1781450116/content/explanation-ui.html`
- `.superpowers/brainstorm/42278-1781450116/content/waiting.html`
- `.superpowers/brainstorm/42278-1781450116/state/server-info`
- `docs/superpowers/specs/2026-06-14-physicslab-enhancement-design.md`

---

## Entire CLI Observations

### What Worked Well
1. **Automatic session tracking** - All 4 sessions were captured without manual intervention
2. **Checkpoint creation** - Checkpoints tied to git commits with full transcripts
3. **Token tracking** - Accurate per-session token counts
4. **Branch isolation** - Checkpoint data stored on separate branch (`entire/checkpoints/v1`)
5. **Metadata preservation** - Session prompts, timestamps, and file changes tracked

### Issues Encountered
1. **Stale sessions** - Sessions marked "stale" after 13h with no cleanup
2. **Doctor TTY issue** - `entire doctor` failed to fix sessions in non-interactive mode
3. **Recap auth required** - `entire recap` required login (cloud feature)
4. **Dispatch CLI missing** - `entire dispatch --local` requires Claude CLI (not installed)
5. **No summary generation** - `entire checkpoint explain` shows "Not generated yet" for summaries

### Recommendations
1. Run `entire doctor` in a TTY to fix stale sessions
2. Configure `--summarize-provider` for local summary generation
3. Consider running `entire login` for cloud features (recap, dispatch)
4. Use `entire checkpoint search` for semantic search across sessions
