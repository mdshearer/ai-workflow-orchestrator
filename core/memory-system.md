# Memory System

**A four-tier memory architecture for AI workflow orchestration**

---

## The Problem: Context Saturation

Traditional AI workflows suffer from **context window saturation**:

```
Iteration 1: [Strategy] ✅ (500 tokens)
Iteration 2: [Strategy + Research] ✅ (1,500 tokens)
Iteration 3: [Strategy + Research + Outline] ✅ (3,000 tokens)
Iteration 4: [Strategy + Research + Outline + Draft] ⚠️ (8,000 tokens)
Iteration 5: [All of the above + Edits] ❌ (15,000 tokens - context overflow)
```

**Result:** Important early decisions get truncated or forgotten.

---

## The Solution: Four-Tier Memory

Instead of dumping everything into the AI's context window, we use a **structured memory hierarchy**:

```
┌─────────────────────────────────────────┐
│  TIER 1: CONTEXT (Volatile)             │
│  Current phase working notes            │
│  Cleared at phase transitions           │
│  ~200-500 tokens                        │
└─────────────────────────────────────────┘
                  ↓ (summarize on phase transition)
┌─────────────────────────────────────────┐
│  TIER 2: MEMORY (Persistent)            │
│  Project history and decisions          │
│  Append-only, never deleted             │
│  ~2,000-5,000 tokens                    │
└─────────────────────────────────────────┘
                  ↓ (extract patterns)
┌─────────────────────────────────────────┐
│  TIER 3: PROJECT LEARNINGS (Wisdom)     │
│  Cross-project patterns and insights    │
│  Updated by α-phase only                │
│  ~1,000-3,000 tokens                    │
└─────────────────────────────────────────┘
                  ↓ (codify into rules)
┌─────────────────────────────────────────┐
│  TIER 4: CONSTITUTION (Governance)      │
│  Non-negotiable principles and rules    │
│  Rarely updated, high authority         │
│  ~3,000-10,000 tokens                   │
└─────────────────────────────────────────┘
```

---

## Tier 1: Context (Volatile Memory)

### Purpose
**Short-term working memory** for the current phase.

### Characteristics
- **Volatile** - Cleared at phase transitions
- **Fast-changing** - Updated frequently within a phase
- **Small** - ~200-500 tokens
- **Phase-specific** - Only relevant to current work

### What Goes Here
- Current phase's working notes
- Active decisions being made
- Open questions for this phase
- Temporary reminders
- Draft ideas not yet finalized

### Example: context.md
```markdown
---
project: "01-saas-blog-post"
phase: "K"
last_updated: "2025-12-20T10:30:00Z"
clear_on_transition: true
---

# Working Context

## Current Phase: K (Conservation)

## Active Decisions
- Using 3-section structure (Problem → Solution → Action)
- Target word count: 1,200 words
- Skipping Investigator (opinion piece, no research needed)

## Open Questions
- Should we include code examples? (Ask user)
- Tone: conversational (4/10) or professional (6/10)?

## Working Notes
- User prefers bullet points over long paragraphs
- Emphasize practical takeaways
- Avoid jargon (target: non-technical founders)

## Reminders
- Check constitution for Kill List before finalizing
- Validate hook strength in intro

---
*This context will be cleared at K→Ω transition*
```

### When to Clear
- **r→K transition:** Summarize strategy decisions → memory, clear context
- **K→Ω transition:** Preserve for Critic (DO NOT clear yet)
- **Ω→α transition:** Preserve everything (α needs full context)
- **α→r transition:** Clear everything, fresh start

### Management Rules
- **Read by:** All agents in current phase
- **Written by:** All agents in current phase
- **Cleared by:** System at phase transitions (except K→Ω)
- **Summarized to:** Memory (tier 2) before clearing

---

## Tier 2: Memory (Persistent Project Memory)

### Purpose
**Long-term project memory** capturing the full history.

### Characteristics
- **Persistent** - Never deleted, append-only
- **Chronological** - Time-ordered log of events
- **Complete** - All major decisions and artifacts
- **Project-scoped** - Specific to one project

### What Goes Here
- Persona executions (which agent ran when)
- Artifacts created (with version numbers)
- Key decisions made
- Human feedback and approvals
- Iteration history
- Phase transitions

### Example: memory.md
```markdown
---
project: "01-saas-blog-post"
type: "memory"
created: "2025-12-20T09:00:00Z"
last_updated: "2025-12-20T14:30:00Z"
---

# Project Memory Log

## 2025-12-20 09:00 - Strategist (Step 1, r-phase)
- Defined UVP: "First practitioner comparison of no-code tools from solo founder POV"
- Target audience: Non-technical founders building first SaaS
- Key insight: Most comparisons are from agency/dev perspective
- **Created:** 01-01-content-brief-v1.md
- **Human feedback:** "Love the angle, approved"

## 2025-12-20 09:30 - Investigator SKIPPED
- **Reason:** Opinion piece based on personal experience
- **Decision:** Drafter will work from existing knowledge

## 2025-12-20 10:00 - Architect (Step 3, K-phase)
- **Phase transition:** r→K (cleared context, summarized strategy)
- Created 3-section structure: Problem → Solution → Action
- Mapped personal stories to each section
- **Created:** 01-03-article-skeleton-v1.md
- **Human checkpoint:** APPROVED

## 2025-12-20 11:00 - Drafter (Step 4, K-phase)
- Generated 1,250 words
- Used conversational tone (4/10 intensity)
- Included 2 personal anecdotes
- **Created:** 01-04-draft-manuscript-v1.md

## 2025-12-20 11:30 - Editor (Step 5, K-phase)
- **Found issues:**
  - 3 MEDIUM: Kill List violations ("leverage", "delve")
  - 1 LOW: Inconsistent heading capitalization
- **Verdict:** PASS with revisions
- **Created:** 01-05-validation-report-v1.md

## 2025-12-20 12:00 - Drafter (Step 4, revision)
- Fixed kill list violations
- Corrected heading capitalization
- **Created:** 01-04-draft-manuscript-v2.md

## 2025-12-20 12:15 - Editor (Step 5, re-validation)
- **Verdict:** PASS, ready for Critic
- **Created:** 01-05-validation-report-v2.md

## 2025-12-20 12:30 - Critic (Step 6, Ω-phase)
- **Phase transition:** K→Ω
- **Stability score:** 87/100
  - Voice Integrity: 90/100
  - Research Validity: N/A (opinion piece)
  - Structural Coherence: 85/100
  - Engagement Potential: 88/100
  - Strategic Alignment: 92/100
- **Verdict:** APPROVE
- **Created:** 01-06-critique-report-v1.md
- **Human decision:** Published ✅

## Project Outcome
- **Status:** COMPLETED
- **Total iterations:** 2 (draft v1 → v2)
- **Time:** 3.5 hours
- **Quality:** 87/100
- **Published:** 2025-12-20

---
*Append-only log. Never delete entries.*
```

### When to Update
- After each agent execution
- At phase transitions
- When human feedback is received
- At project completion

### Management Rules
- **Read by:** All agents (for context)
- **Written by:** All agents (append-only)
- **Format:** Chronological, timestamped entries
- **Length:** Unlimited (but summarize key patterns to Tier 3)

---

## Tier 3: Project Learnings (Cross-Project Wisdom)

### Purpose
**Pattern library** capturing what works across multiple projects.

### Characteristics
- **Cross-project** - Not specific to one project
- **Pattern-focused** - Recurring themes and insights
- **Curated** - Only important patterns, not everything
- **Updated rarely** - By α-phase agents or manual curation

### What Goes Here
- Recurring success patterns
- Recurring failure patterns
- Workflow optimizations discovered
- Best practices by content type
- Constitution evolution history
- Aggregate metrics (average scores, common issues)

### Example: project-learnings.md
```markdown
---
type: "project_learnings"
created: "2025-11-01"
last_updated: "2025-12-20"
total_projects: 23
---

# Cross-Project Pattern Library

## Recurring Success Patterns

### Pattern: Skipping Investigator for Opinion Pieces
**Occurrences:** 8 projects (Projects: 01, 05, 07, 11, 14, 16, 19, 22)
**Context:** Opinion/analysis pieces based on personal experience
**Outcome:** Average quality score 85/100, faster workflow (2-3 hours saved)
**Recommendation:** Skip Investigator when content is opinion-based or experiential

### Pattern: Architect Checkpoint Critical for 2000+ Word Posts
**Occurrences:** 12 projects (Projects: 02, 03, 06, 08, 09, 12, 15, 17, 18, 20, 21, 23)
**Context:** Long-form content (2000+ words)
**Outcome:** Projects with approved skeleton score 12 points higher on average
**Recommendation:** Never skip Architect human checkpoint for long-form content

---

## Recurring Failure Patterns

### Pattern: Audience Mismatch (HIGH PRIORITY)
**Occurrences:** 7 projects (Projects: 03, 04, 09, 13, 15, 19, 21)
**Symptoms:** Content targets wrong expertise level (too technical or too basic)
**Root Cause:** Strategist doesn't validate audience assumptions
**Solution:** Added audience validation checklist to Strategist prompt (v1.3)
**Impact:** Zero occurrences in last 5 projects

### Pattern: Kill List Violations Despite Constitution
**Occurrences:** 11 projects (Projects: 01, 04, 05, 06, 10, 13, 14, 15, 17, 19, 21)
**Symptoms:** Drafter uses forbidden words ("leverage", "delve", "unlock") despite constitution
**Root Cause:** Constitution not explicitly loaded at start of Drafter prompt
**Solution:** Updated Drafter prompt to reference constitution in opening paragraph
**Impact:** 80% reduction in violations (last 5 projects: only 2 violations total)

### Pattern: Weak Introductions
**Occurrences:** 9 projects (Projects: 02, 05, 07, 08, 11, 14, 16, 18, 22)
**Symptoms:** Generic openings, weak hooks, low Engagement Potential scores
**Root Cause:** Drafter follows skeleton too literally, doesn't add compelling hook
**Solution:** Added "Hook strength" validation to Editor prompt
**Impact:** Ongoing, too early to measure

---

## Workflow Insights

### Average Stability Scores by Workflow Type
- **Full workflow** (7 agents): 87/100 (n=12)
- **Quick workflow** (6 agents, skip Investigator): 84/100 (n=8)
- **Simple workflow** (5 agents, skip Investigator + Architect): 79/100 (n=3)

### Time by Workflow Type
- **Full workflow:** 4-6 hours
- **Quick workflow:** 2-4 hours
- **Simple workflow:** 1-2 hours

### Best Workflow by Content Type
| Content Type | Recommended Workflow | Avg Score | Projects |
|--------------|---------------------|-----------|----------|
| Long-form blog (2000+ words) | Full | 88/100 | 8 |
| Medium blog (1000-2000 words) | Quick | 85/100 | 11 |
| Short post (<1000 words) | Simple | 79/100 | 4 |

---

## Constitution Evolution

### Version 1.0 → 1.1 (2025-11-15)
**Trigger:** Project 03 (catastrophic audience mismatch)
**Changes:**
- Added audience validation checklist to Strategist guidelines
- New rule: "Always define technical level explicitly"

### Version 1.1 → 1.2 (2025-12-01)
**Trigger:** Project 13 (repeated kill list violations)
**Changes:**
- Added "unlock", "empower", "game-changer" to Kill List
- Strengthened tone guidance: prefer direct over enthusiastic

### Version 1.2 → 1.3 (2025-12-10)
**Trigger:** Project 19 (weak introduction despite good content)
**Changes:**
- Added "Hook strength" validation to Editor responsibilities
- New requirement: Every article must open with specific example or data point

---

## Metrics Dashboard

### Overall Performance
- **Total projects:** 23
- **Average stability score:** 84/100
- **Approval rate (first attempt):** 65% (15/23)
- **Evolution triggers (score <50):** 2 (Projects 03, 13)

### Dimension Breakdown (Average Scores)
- **Voice Integrity:** 86/100
- **Research Validity:** 81/100 (when applicable)
- **Structural Coherence:** 83/100
- **Engagement Potential:** 82/100
- **Strategic Alignment:** 88/100

### Most Common Issues (Editor findings)
1. Kill List violations (48% of projects)
2. Weak transitions (35% of projects)
3. Inconsistent tone (22% of projects)
4. Missing citations (17% of projects, when research applied)

---

*Updated by Evolutionist agent (α-phase) or manual curation*
*Last curated: 2025-12-20*
```

### When to Update
- After α-phase execution (Evolutionist extracts patterns)
- Manual curation (quarterly review of patterns)
- When recurring patterns reach threshold (3+ occurrences)

### Management Rules
- **Read by:** All agents (for pattern awareness)
- **Written by:** Evolutionist (α-phase) or humans (manual curation)
- **Format:** Categorized patterns with evidence
- **Length:** Curated, only significant patterns

---

## Tier 4: Constitution (System Governance)

### Purpose
**Non-negotiable principles and rules** that govern all work.

### Characteristics
- **Authoritative** - Highest priority, overrides everything
- **Stable** - Rarely updated (only after serious failures)
- **Domain-specific** - Customized for your field
- **Comprehensive** - Covers voice, quality, ethics, process

### What Goes Here
- Brand voice and tone guidelines
- Kill lists (forbidden words/patterns)
- Quality standards
- Ethical boundaries
- Technical requirements
- Process rules
- Scoring criteria

### Example: constitution.md (Content Writing)
```markdown
---
domain: "content-writing"
version: "1.3"
last_updated: "2025-12-10"
changelog: "CONSTITUTION-CHANGELOG.md"
---

# Editorial Constitution

## Section 1: Voice and Tone

### Voice Characteristics
- **Direct** - Say things plainly without hedging
- **Conversational** - Write like you're explaining to a smart friend
- **Evidence-based** - Claims backed by data or experience
- **Respectful** - No condescension or assumed knowledge

### Tone Intensity Scale
- **1-3/10:** Casual, friendly (social posts, newsletters)
- **4-6/10:** Professional, balanced (blog posts, guides)
- **7-10/10:** Formal, authoritative (whitepapers, academic)

**Default for blog posts:** 4-5/10

### The Kill List (Forbidden Words/Phrases)
**Absolutely forbidden:**
- leverage, unlock, empower
- delve, dive deep
- game-changer, revolutionary
- synergy, paradigm shift
- thought leader, guru

**Reason:** Overused corporate jargon, signals lazy thinking

---

## Section 2: Research Standards

### Source Quality Requirements
- **Primary sources preferred** - Original research, official docs
- **No Wikipedia** as sole source (can be starting point)
- **Recent sources** - Published within 3 years (unless historical context)
- **Verifiable URLs** - All facts must have active source links

### Citation Format
Inline citations with markdown links:
```
According to [study from XYZ Institute](https://example.com), 73% of users...
```

### Unverified Claims
If fact cannot be verified, use placeholder:
```
[NEEDS_VERIFICATION: Claim about X]
```

---

## Section 3: Structural Standards

### Article Length by Type
- **Short post:** 500-800 words
- **Medium post:** 1,000-1,500 words
- **Long-form:** 2,000-3,000 words

### Required Elements
Every article must have:
1. **Hook** - Compelling opening (specific example or surprising data)
2. **Clear thesis** - What's the unique angle?
3. **Evidence** - Data, examples, or reasoning
4. **Practical takeaway** - What should reader do?

### Heading Hierarchy
- **H1:** Title only (one per article)
- **H2:** Main sections (3-5 per article)
- **H3:** Sub-sections (as needed)

---

## Section 4: Quality Gates

### Stability Scoring Dimensions
1. **Voice Integrity (20%)** - Kill List compliance, tone consistency
2. **Research Validity (20%)** - Source quality, fact accuracy
3. **Structural Coherence (20%)** - Logical flow, clear hierarchy
4. **Engagement Potential (20%)** - Hook strength, practical value
5. **Strategic Alignment (20%)** - Delivers on unique angle

### Thresholds
- **85-100:** APPROVE - Ready to publish
- **70-84:** REVISE - Minor fixes needed
- **50-69:** RESTRUCTURE - Major structural issues
- **<50:** RELEASE - Trigger evolution, fundamental problems

---

## Section 5: Audience Validation

**Before drafting, explicitly define:**
- **Expertise level** (beginner, intermediate, expert)
- **Role/context** (founder, developer, marketer, etc.)
- **Primary goal** (learn, decide, implement, etc.)

**Validation checkpoint:**
Every content brief must answer: "Who is this for and why do they care?"

---

## Section 6: Evolution Rules

### When Constitution Updates Trigger
- **Score <50 on any project** (automatic evolution)
- **Recurring pattern (3+ projects)** (flag for review)
- **Quarterly review** (manual curation)

### What Can Change
- Add to Kill List (based on observed violations)
- Refine quality criteria (based on scoring patterns)
- Update structural guidelines (based on what works)
- Strengthen audience validation (based on mismatches)

### What Cannot Change
- Core voice principles (direct, conversational, evidence-based)
- Fundamental ethics (no plagiarism, no fabrication)
- Respect for audience (no condescension)

---

*Last updated: 2025-12-10*
*Version: 1.3*
```

### When to Update
- After α-phase execution (Evolutionist proposes changes)
- Manual review (quarterly or after major failures)
- Human approval required for all changes

### Management Rules
- **Read by:** All agents (highest priority input)
- **Written by:** Evolutionist (α-phase) or humans (manual updates)
- **Approval:** Human must approve all constitution changes
- **Version control:** Track changes in changelog

---

## Memory Flow Across Phases

### r-phase (Growth)
**Context (Tier 1):**
- Strategy questions and options
- Research notes
- Decision points

**Memory (Tier 2):**
- Log strategy decisions
- Document chosen angle

**Learnings (Tier 3):**
- Reference patterns from past strategies

**Constitution (Tier 4):**
- Audience validation requirements
- Strategic alignment criteria

---

### K-phase (Conservation)
**Context (Tier 1):**
- Current section being worked on
- Temporary draft notes
- Open questions

**Memory (Tier 2):**
- Log artifact creation
- Document iterations

**Learnings (Tier 3):**
- Reference best practices for structure

**Constitution (Tier 4):**
- Voice and tone guidelines
- Kill List enforcement
- Quality standards

---

### Ω-phase (Release)
**Context (Tier 1):**
- Preserved from K-phase (don't clear!)
- Critique notes

**Memory (Tier 2):**
- Log stability score and verdict
- Document issues found

**Learnings (Tier 3):**
- Compare score to historical averages

**Constitution (Tier 4):**
- Scoring rubrics
- Quality thresholds

---

### α-phase (Reorganization)
**Context (Tier 1):**
- Full context preserved
- Root cause analysis notes

**Memory (Tier 2):**
- Read full project history
- Identify failure points

**Learnings (Tier 3):**
- WRITE patterns to learnings
- Update metrics

**Constitution (Tier 4):**
- PROPOSE updates (human approves)
- Version increment

---

## Phase Transition Memory Management

### r→K Transition
```
Action: Summarize context → memory, then clear context

Why: K-phase needs focus on production, not strategy
What to preserve: Approved strategy, key decisions
What to clear: Open questions, rejected options
```

### K→Ω Transition
```
Action: Preserve context, do NOT clear

Why: Critic needs full context to evaluate
What to preserve: Everything (working notes, drafts, decisions)
What to clear: Nothing
```

### Ω→α Transition (Conditional)
```
Action: Preserve everything, enable full access

Why: Evolutionist needs complete picture for root cause analysis
What to preserve: All tiers (context, memory, learnings, constitution)
What to clear: Nothing
```

### α→r Transition
```
Action: Clear all context, update constitution, start fresh

Why: New cycle with evolved system
What to preserve: Memory (log evolution), learnings (patterns), constitution (updates)
What to clear: Context (complete reset)
```

---

## Implementation Guidelines

### For Each Agent Prompt
Include this memory injection pattern:

```markdown
# Memory Context

## From Context (Current Phase)
{read: context.md}

## From Memory (This Project)
{read: memory.md - last 10 entries}

## From Learnings (Cross-Project)
{read: project-learnings.md - relevant patterns only}

## From Constitution (Governance)
{read: constitution.md - relevant sections}
```

### Memory Size Limits
- **Context:** Target ~500 tokens, max 1,000
- **Memory:** No limit (but latest 10-20 entries most relevant)
- **Learnings:** Target ~3,000 tokens (curate regularly)
- **Constitution:** Target ~10,000 tokens (comprehensive but focused)

### Anti-Patterns to Avoid

❌ **Dumping everything into context**
- Problem: Context window saturation
- Fix: Use tiered system

❌ **Never clearing context**
- Problem: Irrelevant info pollutes decisions
- Fix: Clear at phase transitions (except K→Ω)

❌ **Not logging to memory**
- Problem: Lost institutional knowledge
- Fix: Every agent appends to memory

❌ **Ignoring cross-project patterns**
- Problem: Repeating same mistakes
- Fix: Evolutionist updates learnings

❌ **Constitution never evolves**
- Problem: System doesn't improve
- Fix: α-phase updates after failures

---

## Benefits of This Architecture

### 1. Prevents Context Saturation
By clearing volatile context, keep AI focused on current phase without overload.

### 2. Preserves Institutional Knowledge
Memory and learnings capture what works across projects.

### 3. Enables System Evolution
Constitution evolves based on actual failures, not guesswork.

### 4. Multi-Scale Learning
- Project-level: Memory captures this project's history
- Cross-project: Learnings capture patterns across projects
- System-level: Constitution codifies best practices

### 5. Transparent Decision-Making
All decisions logged in memory, auditable and reviewable.

### 6. Human in the Loop
Constitution changes require human approval, maintaining control.

---

## Next Steps

1. **Create your templates** using [templates/memory/](../templates/memory/)
2. **Define constitution** for your domain
3. **Start first project** and observe memory usage
4. **Review learnings** after 5-10 projects
5. **Evolve constitution** based on patterns

---

## Related Resources

- **[Core: Adaptive Cycle Framework](./adaptive-cycle-framework.md)** - Understanding phase transitions
- **[Templates: Memory Templates](../templates/memory/)** - Blank templates for all tiers
- **[Examples](../examples/)** - See memory system in action

---

*This memory architecture is inspired by cognitive science (working vs. long-term memory) and organizational learning theory.*
