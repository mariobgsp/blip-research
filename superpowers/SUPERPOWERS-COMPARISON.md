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

## Session Code: With Superpowers (say-no-to-mbg)

All code from the Superpowers session. Git history: 18 commits, 10 files changed, 415 insertions, 104 deletions.

### 1. Design System — CSS Variables & Animations (`src/index.css`)

```css
/* Click particle */
.particle {
  position: fixed;
  width: 4px;
  height: 4px;
  background: var(--red);
  border-radius: 50%;
  pointer-events: none;
  z-index: 1000;
}

/* Vote progress bar */
.vote-progress {
  height: 4px;
  background: var(--surface-3);
  border-radius: 2px;
  margin-top: 1rem;
  overflow: hidden;
  max-width: 700px;
  margin-left: auto;
  margin-right: auto;
}

.vote-progress__fill {
  height: 100%;
  background: var(--red);
  transition: width 0.5s var(--ease-out);
  border-radius: 2px;
}

/* Vote count animation */
.vote__count-number.animating {
  animation: count-up 0.5s var(--ease-out);
}

/* Navbar active section indicator */
.navbar__links a.active {
  color: var(--text-1);
  position: relative;
}
.navbar__links a::after {
  content: '';
  position: absolute;
  bottom: -4px;
  left: 0;
  right: 0;
  height: 2px;
  background: var(--red);
  border-radius: 1px;
  opacity: 0;
  transition: opacity 0.2s ease;
}
.navbar__links a.active::after {
  opacity: 1;
}

/* Hero gradient background */
.hero__bg {
  background: var(--gradient-bg);
}

/* News pagination dots */
.news__pagination {
  display: flex;
  justify-content: center;
  gap: 0.5rem;
  margin-top: 1.5rem;
}

.pagination-dot {
  width: 8px;
  height: 8px;
  border-radius: 50%;
  background: var(--surface-3);
  border: none;
  cursor: pointer;
  transition: background 0.2s ease, transform 0.2s ease;
}

.pagination-dot:hover {
  background: var(--text-3);
}

.pagination-dot.active {
  background: var(--red);
  transform: scale(1.2);
}

/* Chart tooltip */
.chart-tooltip {
  position: fixed;
  background: var(--surface-2);
  color: var(--text-1);
  padding: 0.5rem 1rem;
  border-radius: var(--radius-sm);
  font-size: 0.875rem;
  font-weight: 600;
  pointer-events: none;
  z-index: 100;
  border: 1px solid var(--border);
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.3);
}

/* Timeline expand button */
.timeline__body-header { display: flex; align-items: center; justify-content: space-between; }
.timeline__expand {
  width: 24px;
  height: 24px;
  border: 1px solid var(--border);
  border-radius: 50%;
  background: var(--surface-2);
  color: var(--text-2);
  font-size: 1rem;
  font-weight: 700;
  cursor: pointer;
  display: flex;
  align-items: center;
  justify-content: center;
  transition: background 0.2s, border-color 0.2s;
}
.timeline__expand:hover { background: var(--surface-3); border-color: var(--border-strong); }
.timeline__item.hovered { transform: scale(1.02); box-shadow: var(--shadow-glow); }
.timeline__details {
  margin-top: 1rem;
  padding-top: 1rem;
  border-top: 1px solid var(--border);
  animation: slide-down 0.3s ease;
}
@keyframes slide-down {
  from { opacity: 0; max-height: 0; }
  to { opacity: 1; max-height: 200px; }
}
```

### 2. Navbar — Active Section Indicator (`src/components/Navbar.tsx`)

```tsx
const Navbar: React.FC = () => {
  const [scrolled, setScrolled] = useState(false);
  const [progress, setProgress] = useState(0);
  const [activeSection, setActiveSection] = useState('hero');

  useEffect(() => {
    const sectionIds = ['hero', 'stats', 'vote', 'news', 'analytics', 'timeline', 'projects'];
    const sectionElements: Record<string, HTMLElement> = {};

    const cacheElements = () => {
      sectionIds.forEach((id) => {
        const el = document.getElementById(id);
        if (el) sectionElements[id] = el;
      });
    };

    cacheElements();

    const onScroll = () => {
      const scrollY = window.scrollY;
      const docH = document.documentElement.scrollHeight - window.innerHeight;
      setScrolled(scrollY > 50);
      setProgress(docH > 0 ? (scrollY / docH) * 100 : 0);

      const scrollPosition = scrollY + 100;
      for (const sectionId of sectionIds) {
        const element = sectionElements[sectionId];
        if (element) {
          const offsetTop = element.offsetTop;
          const offsetHeight = element.offsetHeight;
          if (scrollPosition >= offsetTop && scrollPosition < offsetTop + offsetHeight) {
            setActiveSection(sectionId);
            break;
          }
        }
      }
    };

    window.addEventListener('scroll', onScroll, { passive: true });
    const handleResize = () => cacheElements();
    window.addEventListener('resize', handleResize);

    return () => {
      window.removeEventListener('scroll', onScroll);
      window.removeEventListener('resize', handleResize);
    };
  }, []);

  return (
    <nav className={`navbar ${scrolled ? 'scrolled' : ''}`} aria-label="Main navigation">
      <a className="navbar__logo" href="#">
        Say No to <span>MBG.</span>
      </a>
      <ul className="navbar__links">
        <li><a href="#vote" className={activeSection === 'vote' ? 'active' : ''}>Voting</a></li>
        <li><a href="#news" className={activeSection === 'news' ? 'active' : ''}>Berita</a></li>
        <li><a href="#analytics" className={activeSection === 'analytics' ? 'active' : ''}>Data</a></li>
        <li><a href="#timeline" className={activeSection === 'timeline' ? 'active' : ''}>Timeline</a></li>
        <li><a href="#projects" className={activeSection === 'projects' ? 'active' : ''}>Proyek</a></li>
      </ul>
      <div className="navbar__progress" style={{ width: `${progress}%` }} />
    </nav>
  );
};
```

### 3. VoteSection — Click Animations & Progress Bar (`src/components/VoteSection.tsx`)

```tsx
const TARGET_VOTES = 10000;

const VoteSection: React.FC<{ baseVotes: number }> = ({ baseVotes }) => {
  // ... existing state ...
  const [clickParticles, setClickParticles] = useState<Array<{ id: number; x: number; y: number }>>([]);
  const [animating, setAnimating] = useState(false);
  const previousVotesRef = useRef(storedVotes);
  const previousAttemptsRef = useRef(attempts);
  const timersRef = useRef<Array<ReturnType<typeof setTimeout>>>([]);

  const particleValues = useMemo(() =>
    Array.from({ length: 20 }, (_, i) => ({
      yOffset: (i * 3.7) % 60,
      delay: (i * 0.013) % 0.2,
    })),
  []);

  useEffect(() => {
    return () => {
      timersRef.current.forEach(t => clearTimeout(t));
      timersRef.current = [];
    };
  }, []);

  const createParticles = (e: React.MouseEvent) => {
    const newParticles = Array.from({ length: 8 }, (_, i) => ({
      id: Date.now() + i,
      x: e.clientX,
      y: e.clientY,
    }));
    setClickParticles(prev => [...prev, ...newParticles]);
    timersRef.current.push(setTimeout(() => {
      setClickParticles(prev => prev.filter(p => !newParticles.find(np => np.id === p.id)));
    }, 500));
  };

  useEffect(() => {
    if (storedVotes > previousVotesRef.current) {
      setAnimating(true);
      const timer = setTimeout(() => setAnimating(false), 500);
      previousVotesRef.current = storedVotes;
      return () => clearTimeout(timer);
    }
  }, [storedVotes]);

  // Deterministic particles (replaced Math.random)
  {Array.from({ length: 20 }).map((_, i) => {
    const values = particleValues[i];
    return (
      <div key={i} style={{
        transform: `rotate(${i * 18}deg) translateY(-${40 + values.yOffset}px)`,
        animationDelay: `${values.delay}s`,
      }} />
    );
  })}

  {/* Progress bar */}
  <div className="vote-progress">
    <div className="vote-progress__fill"
      style={{ width: `${Math.min((storedVotes / TARGET_VOTES) * 100, 100)}%` }} />
  </div>
};
```

### 4. AnalyticsSection — Tooltips & Animated Counters (`src/components/AnalyticsSection.tsx`)

```tsx
const AnimatedNumber: React.FC<{ value: number; duration?: number }> = ({ value, duration = 500 }) => {
  const [displayValue, setDisplayValue] = useState(0);

  useEffect(() => {
    const start = 0;
    const end = value;
    const startTime = Date.now();
    let animationFrameId: number;

    const animate = () => {
      const elapsed = Date.now() - startTime;
      const progress = Math.min(elapsed / duration, 1);
      const easeOutQuart = 1 - Math.pow(1 - progress, 4);
      setDisplayValue(Math.floor(start + (end - start) * easeOutQuart));

      if (progress < 1) {
        animationFrameId = requestAnimationFrame(animate);
      }
    };

    animate();
    return () => {
      if (animationFrameId) cancelAnimationFrame(animationFrameId);
    };
  }, [value, duration]);

  return <span>{displayValue.toLocaleString()}</span>;
};

// Tooltip on chart dots
<circle cx={p.x} cy={p.y} r="4" ...
  onMouseMove={(e) => {
    setTooltip({ x: e.clientX, y: e.clientY - 30, value: `${p.deficit}%` });
  }}
  onMouseLeave={() => setTooltip(null)}
/>
{tooltip && (
  <div className="chart-tooltip" style={{ left: tooltip.x, top: tooltip.y }}>
    {tooltip.value}
  </div>
)}
```

### 5. NewsScroller — Scroll-snap & Pagination (`src/components/NewsScroller.tsx`)

```tsx
const [activeIndex, setActiveIndex] = useState(0);

const scrollToIndex = (index: number) => {
  if (!trackRef.current) return;
  const children = trackRef.current.children;
  if (children[index]) {
    (children[index] as HTMLElement).scrollIntoView({
      behavior: 'smooth', block: 'nearest', inline: 'start',
    });
  }
};

useEffect(() => {
  const container = trackRef.current;
  if (!container) return;
  const handleScroll = () => {
    const scrollPosition = container.scrollLeft;
    const firstChild = container.children[0] as HTMLElement | undefined;
    if (firstChild) {
      const itemWidth = firstChild.clientWidth;
      const gap = parseFloat(getComputedStyle(container).gap) || 0;
      const stride = itemWidth + gap;
      const newIndex = Math.round(scrollPosition / stride);
      setActiveIndex(Math.min(newIndex, news.length - 1));
    }
  };
  container.addEventListener('scroll', handleScroll);
  return () => container.removeEventListener('scroll', handleScroll);
}, [news.length]);

{/* Pagination dots */}
<div className="news__pagination">
  {news.map((_, index) => (
    <button key={index}
      className={`pagination-dot ${index === activeIndex ? 'active' : ''}`}
      onClick={() => scrollToIndex(index)}
      aria-label={`Go to news item ${index + 1}`}
    />
  ))}
</div>
```

### 6. TimelineSection — Gradient Spine & Expandable Cards (`src/components/TimelineSection.tsx`)

```tsx
const [hoveredEvent, setHoveredEvent] = useState<number | null>(null);
const [expandedEvent, setExpandedEvent] = useState<number | null>(null);

{/* Gradient spine */}
<div className="timeline__spine" style={{
  background: 'linear-gradient(to bottom, var(--red), rgba(255, 59, 48, 0.3))'
}}>
  <div className="timeline__spine-fill" style={{ height: `${fillHeight}%` }} />
</div>

{/* Hover effect */}
<div className={`timeline__item ... ${hoveredEvent === i ? 'hovered' : ''}`}
  onMouseEnter={() => setHoveredEvent(i)}
  onMouseLeave={() => setHoveredEvent(null)}
>

{/* Expandable content */}
<div className="timeline__body-header">
  <span className={`timeline__badge ...`}>{item.status}</span>
  <button className="timeline__expand"
    onClick={() => setExpandedEvent(expandedEvent === i ? null : i)}>
    {expandedEvent === i ? '−' : '+'}
  </button>
</div>

{expandedEvent === i && (
  <div className="timeline__details">
    {item.news_links?.map((link, li) => (
      <a key={li} href={link.url} target="_blank" rel="noopener noreferrer"
        className="timeline__news-link">
        📰 {link.label}
      </a>
    ))}
  </div>
)}
```

### 7. HarmfulProjects — Hover Effects (`src/components/HarmfulProjects.tsx`)

```diff
- <div className={`project-card reveal delay-${delay} ${visible ? 'visible' : ''}`}>
+ <div className={`project-card hover-lift reveal delay-${delay} ${visible ? 'visible' : ''}`}>
```

### 8. Icons/StatsBanner/Timeline — Unused Import Cleanup

```diff
// Icons.tsx
-import React from 'react';
+

// StatsBanner.tsx
-import React, { useRef } from 'react';
+import React from 'react';

// TimelineSection.tsx
-import React, { useEffect, useRef, useState } from 'react';
+import React, { useEffect, useState } from 'react';
```

---

## Session Code: Without Superpowers (say-no-to-mbg-copy)

No git history available. Code changes reconstructed from session documentation.

### 1. Mobile Hamburger Menu (`src/components/Navbar.tsx`)

```tsx
// Added navItems array for DRY link rendering
const navItems = [
  { href: '#vote', label: 'Voting' },
  { href: '#news', label: 'Berita' },
  { href: '#analytics', label: 'Data' },
  { href: '#timeline', label: 'Timeline' },
  { href: '#projects', label: 'Proyek' },
];

const [menuOpen, setMenuOpen] = useState(false);

// Body scroll lock when menu is open
useEffect(() => {
  document.body.style.overflow = menuOpen ? 'hidden' : '';
  return () => { document.body.style.overflow = ''; };
}, [menuOpen]);

const closeMenu = () => setMenuOpen(false);

// Animated hamburger button (3 lines → X)
<button className="navbar__burger" onClick={() => setMenuOpen(o => !o)}
  aria-label="Toggle menu" aria-expanded={menuOpen}>
  <span className={`burger-line ${menuOpen ? 'open' : ''}`} />
  <span className={`burger-line ${menuOpen ? 'open' : ''}`} />
  <span className={`burger-line ${menuOpen ? 'open' : ''}`} />
</button>

// Slide-in mobile menu panel
{menuOpen && (
  <div className="mobile-menu" role="dialog" aria-modal="true">
    <div className="mobile-menu__panel">
      <div className="mobile-menu__links">
        {navItems.map((item, i) => (
          <a key={item.href} href={item.href} onClick={closeMenu}
            style={{ animationDelay: `${i * 0.05}s` }}>
            {item.label}
          </a>
        ))}
      </div>
    </div>
  </div>
)}
```

### 2. Back-to-Top Button (`src/App.tsx`)

```tsx
const BackToTop = () => {
  const [visible, setVisible] = useState(false);

  useEffect(() => {
    const onScroll = () => setVisible(window.scrollY > 600);
    window.addEventListener('scroll', onScroll, { passive: true });
    return () => window.removeEventListener('scroll', onScroll);
  }, []);

  return (
    <button className={`back-to-top ${visible ? 'visible' : ''}`}
      onClick={() => window.scrollTo({ top: 0, behavior: 'smooth' })}
      aria-label="Back to top">
      ↑
    </button>
  );
};
```

### 3. Enhanced Card Hover Effects (`src/index.css`)

```css
/* News cards: deeper lift + red glow */
.news__card:hover {
  transform: translateY(-6px);
  box-shadow: 0 8px 30px rgba(255, 59, 48, 0.15);
}

/* Bento cards: subtle lift */
.bento-card:hover {
  transform: translateY(-2px);
  box-shadow: 0 4px 20px rgba(0, 0, 0, 0.3);
}

/* Project cards: lift */
.project-card:hover {
  transform: translateY(-2px);
  box-shadow: 0 4px 20px rgba(0, 0, 0, 0.3);
}

/* Stats items: inset glow */
.stats-bar__item:hover {
  box-shadow: inset 0 0 20px rgba(255, 59, 48, 0.1);
}
```

### 4. News Scroller Navigation (`src/components/NewsScroller.tsx`)

```tsx
const [activeIndex, setActiveIndex] = useState(0);

const scrollTo = (index: number) => {
  if (!trackRef.current) return;
  const children = trackRef.current.children;
  if (children[index]) {
    (children[index] as HTMLElement).scrollIntoView({
      behavior: 'smooth', block: 'nearest', inline: 'start',
    });
  }
};

{/* Prev/next arrows */}
<div className="news__nav">
  <button className="news__nav-btn" onClick={() => scrollTo(Math.max(0, activeIndex - 1))}>←</button>
  <div className="news__nav-dots">
    {news.map((_, i) => (
      <button key={i} className={`news__nav-dot ${i === activeIndex ? 'active' : ''}`}
        onClick={() => scrollTo(i)} />
    ))}
  </div>
  <button className="news__nav-btn" onClick={() => scrollTo(Math.min(news.length - 1, activeIndex + 1))}>→</button>
</div>
```

### 5. Visual Polish (`src/index.css`)

```css
/* Hero title pulsing glow */
.hero__title .accent {
  animation: glowPulse 3s infinite alternate;
}
@keyframes glowPulse {
  from { text-shadow: 0 0 20px rgba(255, 59, 48, 0.5); }
  to { text-shadow: 0 0 40px rgba(255, 59, 48, 0.8); }
}

/* Hero CTA shimmer */
.hero__cta::before {
  content: '';
  position: absolute;
  inset: 0;
  background: linear-gradient(90deg, transparent, rgba(255,255,255,0.2), transparent);
  transform: translateX(-100%);
  transition: transform 0.6s;
}
.hero__cta:hover::before {
  transform: translateX(100%);
}

/* Vote button pulse */
.btn-tidak {
  animation: pulse 2.5s infinite;
}
@keyframes pulse {
  0%, 100% { box-shadow: 0 0 0 0 rgba(255, 59, 48, 0.4); }
  50% { box-shadow: 0 0 0 10px rgba(255, 59, 48, 0); }
}

/* Footer gradient */
.footer {
  background: linear-gradient(to top, rgba(255, 59, 48, 0.05), transparent);
}
```

### 6. Accessibility Improvements (Multiple Files)

```tsx
// Navbar.tsx
<nav aria-label="Main navigation">
<a aria-label="Home">
<button aria-label="Toggle menu" aria-expanded={menuOpen}>
<div role="dialog" aria-modal="true">

// HarmfulProjects.tsx
<button aria-expanded={open} onKeyDown={e => (e.key === 'Enter' || e.key === ' ') && setOpen(o => !o)}>

// TimelineSection.tsx
<a aria-label={`Read more about ${link.label}`}>

// VoteSection.tsx
<button aria-label="Vote TIDAK">
<button aria-label="Vote YA" aria-disabled={voted}>

/* index.css */
:focus-visible {
  outline: 2px solid var(--red);
  outline-offset: 2px;
}
```

---

## Code Quality Comparison

| Aspect | Without Superpowers | With Superpowers |
|--------|-------------------|-----------------|
| **Deterministic randomness** | ❌ Used `Math.random()` in render | ✅ Replaced with `useMemo` + precomputed values |
| **Cleanup on unmount** | ❌ `setTimeout` not cleaned up | ✅ `timersRef` tracks all timers, cleans up on unmount |
| **requestAnimationFrame cleanup** | ❌ Not handled | ✅ `cancelAnimationFrame` in cleanup |
| **ARIA attributes** | ✅ Added | ✅ Added |
| **Keyboard support** | ✅ Added (Enter/Space) | ✅ Added |
| **CSS design tokens** | ❌ Hardcoded colors | ✅ CSS custom properties (`--color-primary`, etc.) |
| **Reusable utilities** | ❌ New CSS for each component | ✅ Reused existing `.hover-lift` class |
| **TypeScript errors** | ⚠️ 3 unused imports (fixed after build) | ✅ No new errors |

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

opencode -s ses_13a1f4e0bffe24lbLT1u7WmOXB
opencode -s ses_13a1c9ef3ffeWEd3aruK2iQpLC
