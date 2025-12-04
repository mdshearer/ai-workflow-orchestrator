# Guide: Working with Teams

This guide shows how small teams (2-10 people) use AI Workflow Orchestrator collaboratively.

---

## Core Concept: Assign Personas to People

Instead of one person invoking all personas, **assign personas to team members based on their expertise:**

```
Traditional approach:
Developer does everything: plan → code → test → document → deploy

Constitutional approach:
Product Manager → Product Owner persona (planning)
Developer → Developer persona (implementation)
QA Engineer → QA Engineer persona (testing)
Technical Writer → Technical Writer persona (documentation)
```

**Key benefit:** Specialists do what they do best, with clear handoffs and quality gates.

---

## Team Sizes & Persona Assignment

### 2-Person Team

**Option A: Software Development**
- **Person A:** Product Owner + Solutions Architect (planning)
- **Person B:** Developer + QA Engineer (implementation + testing)
- **Both:** Technical Writer (documentation)

**Option B: Content Writing**
- **Person A:** Content Strategist + Writer (planning + drafting)
- **Person B:** SEO + Editor (optimization + polish)
- **Both:** Fact Checker (verification)

---

### 3-Person Team

**Software Development:**
- **Person A:** Product Owner (defines what to build)
- **Person B:** Solutions Architect + Developer (designs + builds)
- **Person C:** QA Engineer + Technical Writer (tests + documents)

**Content Writing:**
- **Person A:** Content Strategist (planning + distribution)
- **Person B:** Content Writer (drafting)
- **Person C:** SEO + Fact Checker + Editor (refinement)

---

### 5+ Person Team

**Software Development (Full Specialization):**
- **Product Manager:** Product Owner persona
- **Tech Lead:** Solutions Architect persona
- **Developer(s):** Developer persona
- **QA Engineer:** QA Engineer persona
- **Technical Writer:** Technical Writer persona

**Content Writing (Full Specialization):**
- **Content Lead:** Content Strategist persona
- **Writer:** Content Writer persona
- **SEO Specialist:** SEO Specialist persona
- **Researcher:** Fact Checker persona
- **Editor:** Editor persona

---

## Team Workflow: Handoffs & Gates

### The Handoff Pattern

```
┌──────────────────┐
│  Person A        │
│  (Product Owner) │
│  Creates PRD     │
└──────────────────┘
        ↓ Handoff
┌──────────────────┐
│  Person B        │
│  (Architect)     │
│  Reviews PRD     │ ← Can send back if unclear
│  Creates spec    │
└──────────────────┘
        ↓ Handoff
┌──────────────────┐
│  Person C        │
│  (Developer)     │
│  Reviews spec    │ ← Can send back if not feasible
│  Implements      │
└──────────────────┘
```

**Key:** Each persona can reject and send back if quality gate fails.

---

### Phase Gates: When to Advance

**Gate 1: Planning Complete**
- [ ] PRD is clear and complete (no ambiguity)
- [ ] Tech spec is feasible (architect confirms)
- [ ] Team agrees on approach
- **Who approves:** Tech lead or product manager
- **If fails:** Send back to Product Owner or Architect

**Gate 2: Implementation Complete**
- [ ] All acceptance criteria met
- [ ] Code follows standards (per constitution)
- [ ] Developer self-review passed
- **Who approves:** Developer (self) + brief peer review
- **If fails:** Developer continues work

**Gate 3: Quality Review Passed**
- [ ] QA review complete, no CRITICAL issues
- [ ] Security audit passed (if applicable)
- [ ] Performance benchmarks met
- **Who approves:** QA Engineer
- **If fails:** Send back to Developer with issue list

**Gate 4: Documentation Complete**
- [ ] README exists and is clear
- [ ] API docs are current (if applicable)
- [ ] User guides written (if needed)
- **Who approves:** Technical Writer + Product Owner
- **If fails:** Technical Writer completes

---

## Collaboration Tools

### Shared Constitution

**Why:** Everyone must follow the same principles

**How:**
1. Create `CONSTITUTION.md` in project root
2. Reference in every prompt: "Adhere to CONSTITUTION.md"
3. Update when team agrees on changes
4. Review quarterly

**Example repo structure:**
```
project-root/
├── CONSTITUTION.md          ← Shared by all
├── artifacts/               ← All personas output here
│   ├── 01-prd.md
│   ├── 02-tech-spec.md
│   ├── 03-implementation/
│   ├── 04-qa-report.md
│   └── 05-readme.md
└── workflow-log.md          ← Document decisions and handoffs
```

---

### Artifact Management

**Who creates what:**
```
Product Owner → artifacts/01-prd.md
Architect → artifacts/02-tech-spec.md
Developer → artifacts/03-implementation/ (code files)
QA Engineer → artifacts/04-qa-report.md
Technical Writer → artifacts/05-readme.md
```

**Version control:** Use Git
```bash
# Product Owner commits PRD
git add artifacts/01-prd.md
git commit -m "docs: add PRD for user authentication"

# Architect reviews, then commits spec
git add artifacts/02-tech-spec.md
git commit -m "docs: add tech spec for authentication"

# Developer implements
git add src/auth/
git commit -m "feat: implement user authentication"

# QA reviews
git add artifacts/04-qa-report.md
git commit -m "test: QA audit for authentication"
```

**Benefit:** Full iteration history, can see what changed when

---

### Workflow Log (Cross-Persona Dialogue)

**Why:** Document questions, decisions, feedback between personas

**Format:** `workflow-log.md` at project root

**Example:**
```markdown
# Workflow Log: User Authentication Feature

## 2024-01-15: PRD Review (Architect → Product Owner)

**Issue:** PRD doesn't specify session timeout duration
**Question:** How long should sessions last? 7 days? 30 days? Indefinite?
**Response (Product Owner):** 7 days for security, with "remember me" option for 30 days
**Action:** Updated PRD (v2) with session timeout spec

## 2024-01-16: Tech Spec Review (Developer → Architect)

**Issue:** Tech spec requires Redis for session storage
**Concern:** We don't have Redis in our current stack, adds complexity
**Response (Architect):** Good point. Let's use PostgreSQL for sessions (simpler)
**Action:** Updated tech spec (v2) to use Postgres-based sessions

## 2024-01-18: Implementation Review (QA → Developer)

**Issue:** Password reset emails don't have expiration links
**Impact:** CRITICAL security issue
**Response (Developer):** You're right, adding 1-hour expiration
**Action:** Updated implementation, added tests
```

**Key:** Transparent decisions, everyone can see the reasoning

---

## Communication Patterns

### Daily Standup (Async or Sync)

**Format:**
- What persona/phase are you working on?
- Any blockers?
- What handoffs are coming?

**Example:**
```
Person A (Product Owner): Finished PRD v2 after architect feedback.
Ready to hand off to developer. No blockers.

Person B (Developer): Implemented auth endpoints.
Waiting for QA review. No blockers.

Person C (QA Engineer): Reviewed implementation, found 2 HIGH issues.
Sent report to developer. Blocked until fixes.
```

---

### Review Requests

**When:** Handing off between personas

**Format (Slack/Email):**
```
@Person B (Architect)
I've completed the PRD for user authentication.
Please review: artifacts/01-prd-v2.md

Key sections to check:
- User stories (lines 10-35)
- Acceptance criteria (lines 37-60)
- Security requirements (lines 62-80)

Let me know if anything is unclear or needs refinement.
```

**Response:**
```
@Person A (Product Owner)
Reviewed the PRD. Looks good overall!

One question: Line 45 mentions "secure password storage" but doesn't
specify hashing algorithm. Can we add that to acceptance criteria?

Other than that, approved. I'll start tech spec tomorrow.
```

---

### Issue Escalation

**When:** Personas disagree on approach

**Process:**
1. Document the disagreement in workflow-log.md
2. Present both perspectives
3. Escalate to team lead or product manager
4. Make decision, document reasoning

**Example:**
```markdown
## Disagreement: Authentication Approach

**Developer perspective:**
Use JWT tokens (stateless, scalable)
- Pros: No database lookups, works across services
- Cons: Can't revoke tokens easily

**Architect perspective:**
Use session tokens in database (stateful, revocable)
- Pros: Can revoke sessions instantly, better security
- Cons: Database lookup on every request

**Decision (Tech Lead):**
Use session tokens. Security > scalability for our use case.
We can optimize later if needed.

**Reasoning:**
- User security is priority #1 per constitution
- Current scale doesn't require JWT
- Can migrate to JWT later if scaling demands it
```

---

## AI + Human Hybrid Teams

**Pattern:** Mix human and AI personas

### Example 1: Developer Uses AI for QA
```
Human Developer → Implements feature
AI (as QA Engineer) → Reviews code, finds issues
Human Developer → Fixes issues
Human QA Engineer → Final manual verification
```

**Benefit:** AI catches common issues, human focuses on complex edge cases

### Example 2: Writer Uses AI for SEO
```
Human Writer → Creates draft
AI (as SEO Specialist) → Optimizes keywords, readability
Human Editor → Final polish
```

**Benefit:** AI handles tedious SEO work, human focuses on voice and flow

---

## Team Best Practices

### 1. Agree on Constitution Early

**Before starting work:**
- [ ] Review constitution template together
- [ ] Customize for your project
- [ ] All team members understand and agree
- [ ] Commit to repo

**Why:** Prevents "but I thought we were..." later

---

### 2. Use Clear Handoff Protocol

**Handoff checklist:**
- [ ] Artifact is complete (passed quality checklist)
- [ ] Notify next persona (@mention or email)
- [ ] Link to artifact file
- [ ] Highlight key sections to review
- [ ] Set expectations (review by when?)

**Example:**
```
Handoff: PRD → Tech Spec
From: @ProductOwner
To: @Architect
Artifact: artifacts/01-prd-v2.md
Key sections: User stories (lines 10-35), Security (lines 62-80)
Deadline: Please review by EOD tomorrow
```

---

### 3. Document Everything in Artifacts

**Don't:**
- Discuss important decisions only in Slack/Email
- Make verbal agreements without documentation
- Skip writing things down "because everyone knows"

**Do:**
- Document decisions in workflow-log.md
- Put specs in artifact files
- Reference constitution for "why" decisions

**Benefit:** New team members can onboard quickly, context isn't lost

---

### 4. Respect Persona Boundaries

**Product Owner shouldn't:**
- Tell developer how to implement (that's Architect's job)
- Skip writing a PRD (developer needs requirements)

**Developer shouldn't:**
- Define what to build (that's Product Owner's job)
- Skip QA review (QA needs to validate)

**Why:** Separation of concerns prevents issues from slipping through

---

### 5. Iterate Within Phases, Not Backward

**Good:**
```
Developer implements → QA finds issues → Developer fixes → QA re-reviews
(Iteration within Phase 3)
```

**Bad:**
```
Developer implements → QA finds issues → Go back to PRD phase
(Went backward unnecessarily)
```

**Exception:** If issue reveals fundamental misunderstanding, go back. But document why.

---

## Team Size Trade-offs

### Smaller Teams (2-3 people)

**Pros:**
- Fast communication
- Flexible persona assignment
- Less coordination overhead

**Cons:**
- People wear multiple hats (fatigue risk)
- Less specialization
- Harder to maintain objectivity (same person reviewing own work)

**Best practices:**
- Use AI for some personas to offload work
- Take breaks between personas to stay fresh
- Document extra carefully (smaller teams = less peer review)

---

### Larger Teams (5-10 people)

**Pros:**
- True specialization (each person focuses on their strength)
- More rigorous reviews (dedicated QA, editor, etc.)
- Better quality gates

**Cons:**
- More coordination required
- Slower handoffs
- More potential for miscommunication

**Best practices:**
- Clear handoff protocol (don't assume people know)
- Regular syncs (daily standup)
- Strong constitution (more people = need more alignment)

---

## Next Steps for Teams

1. **Define roles** - Who plays which personas?
2. **Set up repo** - Shared CONSTITUTION.md, artifacts/ folder
3. **Create workflow-log.md** - Document decisions
4. **Agree on handoff protocol** - How do we notify next person?
5. **Start with Phase 1** - Product Owner creates first artifact
6. **Follow the workflow** - Respect phase gates and handoffs

---

**More resources:**
- [Working Solo](./working-solo.md) - For individual contributors
- [Customizing Personas](./customizing-personas.md) - Adapting for your team
- [Choosing Your Domain](./choosing-your-domain.md) - Which domain to use
