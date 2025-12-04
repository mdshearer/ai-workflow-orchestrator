# 5-Minute Quick Start

Get up and running with AI Workflow Orchestrator in 5 minutes.

---

## 1. Choose Your Domain (30 seconds)

Pick the domain that matches your work:

- **[Software Development](./domains/software-development/)** - Apps, APIs, tools, bots
- **[Content Writing](./domains/content-writing/)** - Blogs, articles, marketing, docs

**Not sure?** See the [domain selection guide](./domains/README.md)

---

## 2. Copy Your Constitution (1 minute)

Every project starts with a CONSTITUTION.md file that defines your non-negotiable principles.

### For Software Development:
Choose a template from [`domains/software-development/templates/`](./domains/software-development/templates/):
- **internal-tool-constitution.md** - Internal tools (fast iteration, minimal security)
- **client-app-constitution.md** - Customer-facing apps (production-grade)
- **ai-agent-constitution.md** - Bots, APIs, automation

### For Content Writing:
Choose a template from [`domains/content-writing/templates/`](./domains/content-writing/templates/):
- **blog-constitution.md** - Company blogs, thought leadership, SEO content
- **marketing-constitution.md** - Landing pages, campaigns, sales content
- **technical-constitution.md** - Product docs, API guides, tutorials

**Action:** Copy the template to your project folder and customize:
- Project name and purpose
- Target audience
- Key constraints
- Success metrics

---

## 3. Start Phase 1: Planning (3 minutes)

Use the first persona prompt to kick off your workflow.

### For Software Development:

1. **Copy the prompt:** [`prompts/phase-1-planning/1.1-product-owner-prd.md`](./domains/software-development/prompts/phase-1-planning/1.1-product-owner-prd.md)
2. **Fill in context:** What feature/project are you building?
3. **Give to your AI:** Use Claude Code, Cursor, or copy-paste into ChatGPT/Claude
4. **Review output:** Check `artifacts/01-prd.md` (or wherever the AI saved it)

### For Content Writing:

1. **Copy the prompt:** [`prompts/phase-1-planning/1.1-content-brief.md`](./domains/content-writing/prompts/phase-1-planning/1.1-content-brief.md)
2. **Fill in context:** Topic, target audience, keywords, goals
3. **Give to your AI:** Use Claude Code, Cursor, or copy-paste
4. **Review output:** Check `artifacts/01-content-brief.md`

**Tip:** If the output isn't quite right, iterate:
- Give feedback: "Good, but emphasize X more"
- AI produces v2: `artifacts/01-content-brief-v2.md`
- Approve when ready

---

## 4. Continue Through Phases

Once Phase 1 is approved, move to the next persona:

### Software Development Flow:
```
Phase 1: Product Owner (PRD) → Architect (Tech Spec)
Phase 2: Developer (Implementation)
Phase 3: QA Engineer (Testing & Review)
Phase 4: Technical Writer (Documentation)
```

See the [software workflow overview](./domains/software-development/workflow/workflow-overview.md)

### Content Writing Flow:
```
Phase 1: Strategist (Brief) → Strategist (Outline)
Phase 2: Writer (First Draft)
Phase 3: SEO Specialist → Fact Checker → Editor
Phase 4: Meta Tags → Distribution Plan
```

See the [content workflow overview](./domains/content-writing/workflow/workflow-overview.md)

---

## 5. Working Solo vs. Teams

### Solo Practitioners (You + AI)

You invoke each persona sequentially:
1. You act as the **Strategist persona** (via AI prompt)
2. Review the output
3. You act as the **Creator persona** (via AI prompt)
4. Review the output
5. You act as the **Reviewer persona** (via AI prompt)
6. You judge which feedback to accept/reject

**Key insight:** Each persona checks the previous one's work. You're using AI to give yourself multiple expert perspectives.

### Small Teams (2-10 people)

Assign personas to real people:
- Person A: Product Owner + Architect
- Person B: Developer
- Person C: QA Engineer + Technical Writer

Or mix: Some personas are people, some are AI-assisted.

See [Working Solo](./docs/guides/working-solo.md) and [Working with Teams](./docs/guides/working-with-teams.md) for details.

---

## Tips for Success

### 1. Version Your Artifacts
Don't overwrite files. Create versions:
```
artifacts/01-prd-v1.md
artifacts/01-prd-v2.md  (after architect feedback)
artifacts/01-prd-v3.md  (final)
```

This creates a transparent iteration history.

### 2. Use workflow-log.md
Track decisions and cross-persona dialogue:
```markdown
## Decision Log

### 2024-12-04: Tech Stack Choice
- **Issue:** React vs Vue for frontend
- **Architect:** Recommended React (team familiarity, hiring)
- **Developer:** Agreed
- **Decision:** React + TypeScript
```

### 3. Don't Skip Phases
The workflow has gates for a reason:
- ❌ Don't code before you have an approved tech spec
- ❌ Don't publish content before fact-checking
- ✅ Each phase builds on the previous one

### 4. Iterate Within Phases
If a persona finds issues, don't advance phases. Fix them first:
```
Draft v1 → Editor finds 5 issues → Draft v2 → Editor approves → Advance
```

### 5. Customize for Your Needs
The templates are starting points. Adapt:
- Add personas if needed (e.g., a Security Specialist)
- Skip personas if not needed (e.g., no QA for a quick prototype)
- Merge prompts (e.g., combine SEO + Editing for faster workflow)

See [Customizing Personas](./docs/guides/customizing-personas.md)

---

## What's Next?

### See Examples
- [Software: SaaS Dashboard](./domains/software-development/examples/client-app/)
- [Content: SaaS Blog Post](./domains/content-writing/examples/saas-blog-post/)

These show real iteration histories and cross-persona dialogue.

### Explore Your Domain
- [Software Development](./domains/software-development/) - All personas, prompts, templates
- [Content Writing](./domains/content-writing/) - All personas, prompts, templates

### Read the Guides
- [Choosing Your Domain](./docs/guides/choosing-your-domain.md)
- [Working Solo](./docs/guides/working-solo.md)
- [Working with Teams](./docs/guides/working-with-teams.md)
- [Customizing Personas](./docs/guides/customizing-personas.md)

---

## Common Questions

**Q: Do I need to use all personas?**
A: No. Start with the essential ones (Strategist, Creator, Reviewer). Add more as needed.

**Q: Can I use this with ChatGPT, Claude, or other AI tools?**
A: Yes. The prompts work with any AI. Copy-paste or use AI coding tools like Claude Code, Cursor, Replit.

**Q: What if I don't agree with a persona's feedback?**
A: You're the orchestrator. You judge which feedback to accept. AI provides expertise, you make decisions.

**Q: How long does a full workflow take?**
A: Depends on scope. A blog post: 2-4 hours. A small feature: 1-2 days. A full app: weeks (but with quality gates at every step).

**Q: Can I mix domains?**
A: Yes! Use software personas for the code, content personas for the docs, grant personas for funding proposals.

---

**Ready to start?** → [Choose your domain](./domains/) and pick your first prompt!
