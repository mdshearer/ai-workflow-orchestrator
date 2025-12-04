# AI Workflow Orchestrator

**Build high-quality work in any domain using AI with constitutional governance and specialized personas.**

```
┌─────────────────────────────────────────┐
│         YOUR CONSTITUTION               │
│    (Non-negotiable principles)          │
└─────────────────────────────────────────┘
                  ↓
┌─────────────────────────────────────────┐
│     4-6 SPECIALIZED PERSONAS            │
│  (Each checks the others' work)         │
└─────────────────────────────────────────┘
                  ↓
┌─────────────────────────────────────────┐
│       4-PHASE WORKFLOW                  │
│  Plan → Create → Review → Finalize      │
└─────────────────────────────────────────┘
                  ↓
┌─────────────────────────────────────────┐
│      VERSIONED ARTIFACTS                │
│   (Reviewable, trackable outputs)       │
└─────────────────────────────────────────┘
```

**Current Domains:** [Software Development](./domains/software-development/) | [Content Writing](./domains/content-writing/)
**Coming Soon:** Grant Writing

---

## The Problem

**Traditional AI workflow:**
```
You: "Build me a landing page"
AI: [Generates 500 lines of code]
You: [Overwhelmed, can't iterate methodically]
Team member: Uses their own AI to modify further, everyone quickly gets frustrated and throws in the towel!
```

**Constitutional workflow:**
```
You: "Build me a landing page. Start with product requirements."
Product Owner Persona → artifacts/01-prd.md (REVIEWABLE)

You: "Good, but emphasize conversion more."
Product Owner → artifacts/01-prd-v2.md (IMPROVED)

You: "Approved. Now create the technical design."
Architect Persona → artifacts/02-tech-spec.md (STRUCTURED)

[Continue through phases...]

Result: Transparent, methodical, version-controlled work
```

---

## Who Is This For?

✅ **Solo practitioners** who want quality checks without a team
✅ **Small teams (2-10 people)** who need specialized expertise without hiring
✅ **Anyone frustrated** with inconsistent AI outputs

---

## Why This Works

| Approach | Traditional AI Prompting | Constitutional Workflow |
|----------|-------------------------|------------------------|
| **Process** | Ad-hoc, one-shot prompts | Structured 4-phase workflow |
| **Quality Control** | You catch all issues | Multiple personas review each other |
| **Iteration** | Re-prompt from scratch | Version-controlled artifacts (v1, v2, v3) |
| **Governance** | Implicit rules in prompts | Explicit CONSTITUTION.md file |
| **Transparency** | Chat history only | Reviewable artifact files |
| **Specialization** | Generic AI | Specialized personas (strategist, creator, reviewer) |
| **Accountability** | Hard to track decisions | Documented iteration history |
| **Team Collaboration** | Copy-paste chaos | Shared constitution + artifacts |

**Result:** Consistent quality, methodical iteration, transparent process

---

## What's Included

- **2 Complete Domains** (software dev + content writing)
- **10+ Specialized Personas** (ready to use or customize)
- **25+ Phase-Based Prompts** (strategic, creation, review, finalization)
- **6+ Constitution Templates** (by project type)
- **5+ Example Projects** (with iteration history)

---

## Quick Start

### 1. [Choose Your Domain](./domains/)
- **Software Development** - Apps, APIs, tools
- **Content Writing** - Blogs, marketing, docs

### 2. [5-Minute Quick Start](./QUICKSTART.md)
Get up and running in 5 minutes

### 3. See Examples
- [Software: SaaS Dashboard](./domains/software-development/examples/client-app/)
- [Content: SaaS Blog Post](./domains/content-writing/examples/saas-blog-post/)

---

## How It Works

### 1. Constitution (Your Project's Principles)
Define non-negotiable rules that govern all work:
- **Software:** Tech stack, security standards, coding conventions
- **Content:** Brand voice, SEO requirements, style guide
- **Grant:** Funder requirements, compliance rules, writing tone

### 2. Specialized Personas (Expert Perspectives)
Each domain has 4-6 personas that check and balance each other:
- **Software:** Product Owner → Architect → Developer → QA → Technical Writer
- **Content:** Strategist → Writer → SEO Specialist → Fact Checker → Editor

### 3. 4-Phase Workflow (Quality Gates)
Every project flows through structured phases:
- **Phase 1:** Strategy/Planning
- **Phase 2:** Creation/Implementation
- **Phase 3:** Review/Refinement
- **Phase 4:** Finalization/Documentation

### 4. Versioned Artifacts (Transparent Iteration)
Every phase produces reviewable files:
- `artifacts/01-strategy-v1.md` → `v2` → `v3` (iteration history)
- `artifacts/02-draft-v1.md` → cross-persona feedback → `v2`
- `artifacts/workflow-log.md` (documents all decisions)

---

## Documentation

- **[Quick Start Guide](./QUICKSTART.md)** - Get started in 5 minutes
- **[Domain Selection](./domains/)** - Choose software, content, or (soon) grant writing
- **[Guides](./docs/guides/)** - Working solo, teams, customization
- **[Architecture](./docs/architecture/)** - Design decisions and patterns

---

## Examples

### Software Development
- [Internal Tool: Expense Tracker](./domains/software-development/examples/internal-tool/)
- [Client App: SaaS Dashboard](./domains/software-development/examples/client-app/)
- [AI Agent: Slack Support Bot](./domains/software-development/examples/ai-agent/)

### Content Writing
- [SaaS Blog Post](./domains/content-writing/examples/saas-blog-post/) - SEO-focused, B2B audience
- [Product Launch Post](./domains/content-writing/examples/product-launch-post/) - Marketing, conversion-focused

---

## Contributing

We welcome contributions! See [CONTRIBUTING.md](./CONTRIBUTING.md) for:
- How to propose new domains
- Quality standards for submissions
- Persona and prompt templates

---

## License

MIT License - see [LICENSE](./LICENSE) for details

---

## Why "Constitutional"?

Traditional AI prompting is like asking one person to do everything with vague instructions. Constitutional workflows:
- **Encode principles** in a CONSTITUTION.md file (non-negotiable rules)
- **Separate concerns** with specialized personas (like separation of powers)
- **Enforce checks and balances** through cross-persona reviews
- **Document decisions** in versioned artifacts (transparent governance)

The result: AI collaboration that's methodical, transparent, and consistently high-quality.

---

**Ready to get started?** → [Choose your domain](./domains/) or [5-minute quick start](./QUICKSTART.md)
