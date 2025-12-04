# Design Decisions: AI Workflow Orchestrator

This document captures key architectural decisions, trade-offs, and the reasoning behind the structure of the AI Workflow Orchestrator framework.

---

## Table of Contents

1. [Core Architecture Decisions](#core-architecture-decisions)
2. [Domain Organization](#domain-organization)
3. [Persona Design](#persona-design)
4. [Prompt Structure](#prompt-structure)
5. [Documentation Strategy](#documentation-strategy)
6. [Trade-offs Made](#trade-offs-made)
7. [Future Directions](#future-directions)

---

## Core Architecture Decisions

### Decision 1: Constitutional Governance as Foundation

**Context:** Need a way to maintain consistency across AI interactions and prevent scope creep.

**Decision:** Use CONSTITUTION.md as the single source of truth for project principles, standards, and constraints.

**Rationale:**
- **Explicit over implicit:** Writing down non-negotiables prevents "drift" in AI conversations
- **Governance without micromanagement:** Constitution sets boundaries, personas execute within them
- **Reusability:** Same constitution template can be customized for multiple projects
- **Accountability:** Clear reference point when reviewing persona outputs ("Does this align with the constitution?")

**Alternatives Considered:**
- ❌ **Embedding principles in each prompt:** Too redundant, hard to maintain consistency
- ❌ **Relying on conversation context:** Gets lost in long sessions, no single source of truth
- ❌ **No explicit governance:** Leads to inconsistent outputs and scope creep

**Trade-offs:**
- ✅ **Pro:** Clear governance, prevents scope creep, reusable
- ⚠️ **Con:** Requires upfront investment to create constitution (15-30 minutes)
- ⚠️ **Con:** Must remember to reference constitution in all prompts

---

### Decision 2: Persona-Based Specialization

**Context:** Generic "do everything" AI prompts produce inconsistent quality.

**Decision:** Define 4-6 specialized personas per domain, each with specific expertise and responsibilities.

**Rationale:**
- **Separation of concerns:** Strategist thinks differently than Creator thinks differently than Reviewer
- **Quality gates:** Each persona checks the previous persona's work from a different angle
- **Human-like workflow:** Mirrors how real teams work (PM → Designer → Developer → QA)
- **Bias reduction:** For solo practitioners, switching personas provides different perspectives

**Alternatives Considered:**
- ❌ **Single "expert" persona:** Lacks specialized depth, no quality gates
- ❌ **Many micro-personas (10+ per domain):** Too complex, diminishing returns
- ❌ **No personas, just phase prompts:** Loses expertise focus, harder to customize

**Trade-offs:**
- ✅ **Pro:** Higher quality through specialization, clear handoffs, modular
- ⚠️ **Con:** More personas = more steps (but higher quality justifies it)
- ⚠️ **Con:** Solo practitioners must invoke each persona (can't skip)

---

### Decision 3: 4-Phase Workflow Pattern

**Context:** Need consistent structure across domains while allowing domain-specific variations.

**Decision:** Every domain uses a 4-phase workflow: Planning → Creation → Review → Finalization

**Rationale:**
- **Universal pattern:** Applies to software (plan-code-test-document) and content (brief-write-edit-publish)
- **Phase gates:** Natural checkpoints to prevent rushing ahead
- **Iterative within phases:** Allows iteration without breaking the overall structure
- **Teachable:** Easy to explain and visualize

**Alternatives Considered:**
- ❌ **3-phase workflow:** Not enough separation (Review and Finalization get lumped together)
- ❌ **5+ phase workflow:** Too granular, over-complicates simple projects
- ❌ **Domain-specific phases:** Harder to teach universal pattern

**Trade-offs:**
- ✅ **Pro:** Consistent pattern across domains, easy to learn, prevents skipping quality steps
- ⚠️ **Con:** Some simple projects might not need all 4 phases (but skipping undermines quality)
- ⚠️ **Con:** Domain-specific nuances require extra documentation

---

### Decision 4: Artifact-Driven Iteration

**Context:** Chat-based iteration loses history and makes review difficult.

**Decision:** Every persona produces versioned artifact files (v1, v2, v3) stored in artifacts/ folder.

**Rationale:**
- **Reviewability:** Files can be opened, compared, and reviewed independently
- **Version control:** Git tracks iteration history automatically
- **Transparency:** See what changed and why between versions
- **Team collaboration:** Multiple people can review artifacts asynchronously
- **Rollback capability:** Can revert to previous version if iteration makes things worse

**Alternatives Considered:**
- ❌ **Chat-only, no files:** Loses history, hard to review, no version control
- ❌ **Single file, edited in place:** Loses iteration history
- ❌ **Complex version control system:** Overkill for most users

**Trade-offs:**
- ✅ **Pro:** Full transparency, reviewable, version-controlled, team-friendly
- ⚠️ **Con:** More files to manage (but this is actually a feature)
- ⚠️ **Con:** Requires basic file organization skills

---

## Domain Organization

### Decision 5: Domain-Based Folder Structure

**Context:** Framework needs to support multiple domains (software, content, grants, etc.)

**Decision:** Organize by domain at the top level: `domains/software-development/`, `domains/content-writing/`, etc.

**Rationale:**
- **Encapsulation:** Each domain is self-contained (personas, prompts, templates, examples)
- **Scalability:** Easy to add new domains without restructuring
- **Discoverability:** Users navigate by domain, not by resource type
- **Independence:** Domains can evolve independently

**Alternatives Considered:**
- ❌ **Organize by resource type:** `personas/`, `prompts/`, `templates/` at root with subdirectories by domain
  - Con: Hard to see what's included in each domain
  - Con: Adding new domain requires touching multiple folders
- ❌ **Flat structure:** All domains at root level
  - Con: Gets messy as more domains are added
  - Con: Unclear what's domain-specific vs cross-domain

**Trade-offs:**
- ✅ **Pro:** Clear encapsulation, easy to add domains, self-contained
- ⚠️ **Con:** Some duplication in structure (each domain has personas/, prompts/, etc.)
- ⚠️ **Con:** Cross-domain guides need separate location (solved with docs/guides/)

---

### Decision 6: Cross-Domain Guides in docs/guides/

**Context:** Some guidance applies across all domains (working solo, choosing domain, customizing personas).

**Decision:** Create `docs/guides/` for cross-domain documentation separate from domain-specific content.

**Rationale:**
- **DRY principle:** Don't repeat the same "working solo" guide in every domain
- **Universal concepts:** Choosing domain, customizing personas, team collaboration apply to all
- **Easier to maintain:** Update once, applies everywhere

**Alternatives Considered:**
- ❌ **Duplicate guides in each domain:** Hard to maintain, drift between copies
- ❌ **Put in root README:** Too much content, overwhelms the one-pager
- ❌ **No cross-domain guides:** Each domain documents everything (redundant)

**Trade-offs:**
- ✅ **Pro:** DRY, easier to maintain, clear separation of concerns
- ⚠️ **Con:** Users must navigate to different folder (but guides provide links)

---

## Persona Design

### Decision 7: Persona File Structure (8-12KB)

**Context:** Personas need enough detail to guide AI but not so much they become overwhelming.

**Decision:** Standard persona file structure with 10 sections, ~8-12KB each:
1. Role Definition
2. Core Responsibilities
3. Expertise Areas
4. When to Invoke
5. Input Artifacts
6. Output Artifacts
7. Success Criteria
8. Quality Checklist
9. Common Pitfalls
10. Related Personas

**Rationale:**
- **Comprehensive:** Covers all aspects of the persona's role
- **Consistent:** Same structure across all personas makes them easier to learn
- **Actionable:** Quality checklist and success criteria give clear targets
- **Educational:** Common pitfalls teach users what to avoid

**Alternatives Considered:**
- ❌ **Short personas (1-2KB):** Not enough guidance, AI produces generic outputs
- ❌ **Very long personas (20KB+):** Too much to read, overwhelming
- ❌ **Varying structure per persona:** Harder to learn, inconsistent

**Trade-offs:**
- ✅ **Pro:** Right balance of detail, consistent, teachable
- ⚠️ **Con:** Takes time to write (2-3 hours per persona)
- ⚠️ **Con:** Users must read the persona to use it effectively

---

### Decision 8: Persona Archetypes (Universal Pattern)

**Context:** Different domains need different personas but share patterns.

**Decision:** Use 5 universal persona archetypes that translate across domains:
1. **Strategist** - Defines what and why (Product Owner, Content Strategist)
2. **Creator** - Builds the thing (Developer, Content Writer)
3. **Specialist** - Domain expertise (Solutions Architect, SEO Specialist)
4. **Reviewer** - Quality checks (QA Engineer, Fact Checker)
5. **Finalizer** - Polish and documentation (Technical Writer, Editor)

**Rationale:**
- **Teachable pattern:** Once you understand the pattern, applies to all domains
- **Consistency:** Similar roles across domains makes framework easier to learn
- **Flexibility:** Domains can adapt the pattern (e.g., content-writing has 2 reviewers)

**Alternatives Considered:**
- ❌ **No universal pattern:** Each domain creates unique personas from scratch
- ❌ **Strict 5 personas per domain:** Too rigid, some domains need 6
- ❌ **Generic "AI Assistant" personas:** Loses domain specificity

**Trade-offs:**
- ✅ **Pro:** Easy to learn pattern, consistent across domains, flexible
- ⚠️ **Con:** Some domains may not fit perfectly (requires adaptation)

---

## Prompt Structure

### Decision 9: Universal Prompt Template

**Context:** Prompts need consistency while remaining domain-specific.

**Decision:** Every prompt follows this structure:
1. **When to Use** (triggers and anti-patterns)
2. **The Prompt Template** (with template variables)
3. **Review Criteria** (how to judge quality)
4. **Example Output** (shows what good looks like)

**Rationale:**
- **Consistency:** Users know what to expect
- **Template variables:** Easy to customize ([PROJECT_NAME], [AUDIENCE], etc.)
- **Self-documenting:** "When to Use" prevents misuse
- **Quality focus:** Review criteria sets clear expectations

**Alternatives Considered:**
- ❌ **Just the prompt:** No context on when to use or how to judge quality
- ❌ **Very short prompts:** Produces generic outputs
- ❌ **Embedding everything in the prompt:** Gets too long

**Trade-offs:**
- ✅ **Pro:** Consistent, teachable, produces quality outputs
- ⚠️ **Con:** Longer prompts (but quality justifies it)
- ⚠️ **Con:** Users must fill in template variables

---

### Decision 10: Copy-Paste Friendly Format

**Context:** Users work with different tools (Claude Code, Cursor, ChatGPT, Claude web)

**Decision:** Prompts are Markdown files designed for copy-paste or AI tool integration.

**Rationale:**
- **Tool agnostic:** Works with any AI tool
- **Solo-friendly:** No complex setup required
- **Team-friendly:** Can be shared via Git
- **Future-proof:** Markdown is universal

**Alternatives Considered:**
- ❌ **Custom CLI tool:** Requires installation, maintenance
- ❌ **Web app:** Requires hosting, maintenance, login
- ❌ **Platform-specific format:** Locks users into one tool

**Trade-offs:**
- ✅ **Pro:** Universal, simple, no dependencies
- ⚠️ **Con:** Manual copy-paste required (unless using AI coding tool)
- ⚠️ **Con:** No built-in prompt management (users use Git or file system)

---

## Documentation Strategy

### Decision 11: Start Simple, Add Depth Incrementally

**Context:** Users need to onboard quickly but also have access to comprehensive docs.

**Decision:** Layered documentation strategy:
- **Layer 1:** 5-minute QUICKSTART.md (immediate value)
- **Layer 2:** Domain README (overview of domain)
- **Layer 3:** Personas and prompts (detailed specs)
- **Layer 4:** Guides (deeper concepts: customization, teams, etc.)
- **Layer 5:** Architecture docs (for contributors and deep understanding)

**Rationale:**
- **Progressive disclosure:** Users learn what they need when they need it
- **Low barrier to entry:** Can start in 5 minutes
- **Comprehensive:** Advanced users have full documentation
- **Skimmable:** Each layer is self-contained

**Alternatives Considered:**
- ❌ **Everything in README:** Overwhelming, can't find what you need
- ❌ **Minimal docs only:** Users get stuck, can't advance
- ❌ **Wiki-style with many small pages:** Hard to navigate, fragmented

**Trade-offs:**
- ✅ **Pro:** Progressive disclosure, low barrier to entry, comprehensive
- ⚠️ **Con:** More documentation to maintain
- ⚠️ **Con:** Must guide users through layers (solved with clear links)

---

### Decision 12: Examples Show Real Iteration

**Context:** Users need to see messy, real-world iteration, not just perfect final outputs.

**Decision:** Example projects include:
- Multiple draft versions (v1, v2, v3, FINAL)
- Persona feedback reports (SEO report, fact-check report, etc.)
- workflow-log.md showing cross-persona dialogue
- README explaining key decisions

**Rationale:**
- **Realistic:** Shows how iteration actually works
- **Educational:** Users see how to handle feedback
- **Transparency:** Nothing is hidden
- **Trust-building:** "This is how it really works"

**Alternatives Considered:**
- ❌ **Only show final outputs:** Hides the process, not educational
- ❌ **Show every tiny edit:** Too much detail, overwhelming
- ❌ **Perfect examples with no iteration:** Unrealistic, sets wrong expectations

**Trade-offs:**
- ✅ **Pro:** Realistic, educational, builds trust
- ⚠️ **Con:** More files per example (but this teaches the pattern)
- ⚠️ **Con:** Takes time to create (2-3 hours per example)

---

## Trade-offs Made

### Trade-off 1: Simplicity vs Comprehensiveness

**What we chose:** Comprehensive (detailed personas, prompts, examples)

**Why:** Quality requires detail. Users who want simple can skim; users who want depth have it.

**What we sacrificed:** Quick skim-through (but QUICKSTART.md addresses this)

---

### Trade-off 2: Tool-Agnostic vs Integrated Tool

**What we chose:** Tool-agnostic (Markdown files, copy-paste friendly)

**Why:** Works with any AI tool, no lock-in, no maintenance burden

**What we sacrificed:** Seamless integration (but AI coding tools like Claude Code provide this)

---

### Trade-off 3: Universal Pattern vs Domain Optimization

**What we chose:** Universal 4-phase pattern with domain adaptations

**Why:** Easy to learn, consistent across domains, teachable

**What we sacrificed:** Perfect fit for every domain (but domains can adapt)

---

### Trade-off 4: Launch with 2 Domains vs Wait for More

**What we chose:** Launch with software-development + content-writing

**Why:** Demonstrates the pattern works across domains, solves real problems now

**What we sacrificed:** More domain coverage (but grant-writing coming in v2)

---

### Trade-off 5: Artifact Files vs Inline Chat

**What we chose:** Artifact files (versioned, reviewable)

**Why:** Transparency, version control, team collaboration, reviewability

**What we sacrificed:** Simplicity of chat-only (but quality justifies the structure)

---

## Future Directions

### Phase 1: Community Contributions (v1.1)

**Goal:** Enable community to propose and contribute new domains

**Implementation:**
- ✅ CONTRIBUTING.md with clear guidelines
- ✅ Issue template for domain proposals
- Domain quality checklist for submissions
- Review process for accepting domains

**Priority:** HIGH (enables organic growth)

---

### Phase 2: Grant-Writing Domain (v2.0)

**Goal:** Add third domain to demonstrate pattern works beyond software/content

**Personas:**
1. Grant Strategist (identifies opportunities, crafts strategy)
2. Grant Writer (writes narrative, impact statements)
3. Budget Analyst (creates budget justifications)
4. Compliance Reviewer (ensures funder requirements met)
5. Editor (final polish, submission checklist)

**Priority:** HIGH (many users requested this)

---

### Phase 3: More Examples (v2.1)

**Goal:** Show more real-world iteration across different project types

**Examples to add:**
- Software: API service, Chrome extension
- Content: Technical tutorial, marketing landing page
- Grants: Foundation grant, government RFP response

**Priority:** MEDIUM (existing examples sufficient for launch, but more is better)

---

### Phase 4: Video Walkthrough (v2.2)

**Goal:** Video guide showing framework in action

**Content:**
- 10-minute overview: What is this framework?
- 20-minute walkthrough: Creating a blog post with personas
- 30-minute deep dive: Customizing personas for your domain

**Priority:** MEDIUM (dependent on user demand)

---

### Phase 5: Additional Domains (v3.0+)

**Candidate domains based on demand:**
- **Video Production:** Pre-production → Filming → Editing → Distribution
- **Product Design:** Research → Wireframing → Design → Usability Testing
- **Marketing Campaigns:** Strategy → Asset Creation → Execution → Analysis
- **Event Planning:** Planning → Logistics → Execution → Post-event
- **Academic Writing:** Research → Drafting → Peer Review → Revision

**Priority:** LOW (wait for community demand and contributions)

---

### Phase 6: Workflow Automation (Future)

**Goal:** Optional CLI or web tool to automate prompt sequencing

**Features:**
- Auto-invoke next persona after current one completes
- Track which phase you're in
- Auto-version artifacts
- Generate workflow-log.md automatically

**Priority:** LOW (nice to have, not essential, requires maintenance)

**Trade-off:** Adds complexity, requires tool maintenance, could lock users into tooling

---

## Principles for Future Decisions

As the framework evolves, we commit to these principles:

1. **Simplicity over complexity:** If it doesn't add clear value, don't add it
2. **Tool-agnostic:** Must work with copy-paste, even if tool integration is available
3. **Quality over speed:** Framework prioritizes quality outputs over quick outputs
4. **Transparent iteration:** Always show the messy middle, not just perfect results
5. **Community-driven:** Domains should come from real user needs, not speculation
6. **Low barrier to entry:** 5-minute quick start remains a hard requirement
7. **Constitutional governance:** CONSTITUTION.md remains the single source of truth
8. **Domain independence:** Domains evolve independently, universal pattern stays stable

---

## How to Propose Changes

If you want to propose changes to the framework architecture:

1. **Document the problem:** What limitation are you hitting?
2. **Explain the impact:** Who does this affect and how much?
3. **Propose alternatives:** What are 2-3 ways to solve this?
4. **Identify trade-offs:** What do we gain and lose with each alternative?
5. **Recommend one:** Which alternative do you prefer and why?

Submit via [GitHub Issue](https://github.com/mdshearer/ai-workflow-orchestrator/issues) with label `architecture`.

---

## References

- [HANDOFF-UNIVERSAL-TEMPLATE.md](./HANDOFF-UNIVERSAL-TEMPLATE.md) - Original planning document
- [UNIVERSAL-PATTERN-VISUAL.md](./UNIVERSAL-PATTERN-VISUAL.md) - Visual representation of universal pattern
- [CONTRIBUTING.md](../../CONTRIBUTING.md) - How to contribute new domains

---

**Document History:**
- 2024-01-XX: Initial version documenting v1.0 launch decisions
