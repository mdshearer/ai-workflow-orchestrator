# AI Workflow Orchestrator

**A generic framework for building adaptive AI workflows with specialized personas, quality gates, and system learning**

```
┌─────────────────────────────────────────┐
│      ADAPTIVE CYCLE FRAMEWORK           │
│   r (Explore) → K (Build) →             │
│   Ω (Critique) → α (Learn)              │
└─────────────────────────────────────────┘
                  ↓
┌─────────────────────────────────────────┐
│    SPECIALIZED PERSONAS (3-7)           │
│  Each with clear role and expertise    │
└─────────────────────────────────────────┘
                  ↓
┌─────────────────────────────────────────┐
│     4-TIER MEMORY SYSTEM                │
│  Context → Memory → Learnings →         │
│  Constitution                           │
└─────────────────────────────────────────┘
                  ↓
┌─────────────────────────────────────────┐
│    HUMAN-IN-LOOP ORCHESTRATION          │
│  You control, AI executes               │
└─────────────────────────────────────────┘
```

**Works for any domain:** Content writing • Software development • Product design • Research • Data analysis • [Your domain]

---

## 🚀 Quick Start: AI-Guided Setup

**New to this framework?** Copy the [**Workflow Architect prompt**](./WORKFLOW-ARCHITECT.md) into your AI assistant. It will guide you through 10-15 minutes of conversation to build your complete workflow.

**[→ Try the Workflow Architect](./WORKFLOW-ARCHITECT.md)** *(Recommended for first-time users)*

---

## What Is This?

The AI Workflow Orchestrator is a **domain-agnostic framework** for building high-quality work using AI agents organized into **adaptive workflows** inspired by resilience theory and panarchy.

Instead of asking one AI to do everything, you:
1. **Define specialized personas** (agents) for your domain
2. **Map them to adaptive cycle phases** (explore → build → critique → learn)
3. **Orchestrate them sequentially** with human checkpoints
4. **Capture learnings** that make your system smarter over time

---

## The Problem

**Traditional AI workflows:**
```
You: "Build me a complete solution"
AI: [Generates 5000 words/500 lines of code]
You: [Overwhelmed, hard to iterate methodically]
Result: Generic output, no quality control, no learning
```

**Adaptive workflows:**
```
Explorer Persona → Defines strategy (REVIEWABLE)
Builder Persona → Creates solution (REVIEWABLE)
Critic Persona → Scores quality 0-100 (OBJECTIVE GATE)
  ↓ (if score < 70)
Learner Persona → Updates system rules → Try again
  ↓ (smarter next time)
Result: Specialized output, objective quality, continuous improvement
```

---

## Core Concepts

### 1. Adaptive Cycle (r→K→Ω→α)

Inspired by ecological resilience theory, workflows move through four phases:

| Phase | Name | Mindset | Activities | Example Personas |
|-------|------|---------|------------|-----------------|
| **r** | Growth | Exploratory | Strategy, research, planning | Strategist, Researcher, Analyst |
| **K** | Conservation | Productive | Building, refining, validating | Architect, Developer, Writer, Editor |
| **Ω** | Release | Critical | Quality scoring, gatekeeping | Critic, Reviewer, Tester |
| **α** | Reorganization | Evolutionary | Learning from failures, system updates | Evolutionist, Retrospective Lead |

**Key insight:** Separating these phases prevents context-switching and enables specialized expertise.

[Read more: Core Adaptive Cycle Framework](./core/adaptive-cycle-framework.md)

---

### 2. Specialized Personas

Each persona is an AI agent with:
- **One clear job** (separation of concerns)
- **Specific inputs** (artifacts from previous personas)
- **Concrete outputs** (artifacts for next personas)
- **Domain expertise** (deep knowledge in one area)
- **Phase assignment** (r, K, Ω, or α)

**Example: Content Writing Domain**
```
Strategist (r) → Researcher (r) → Architect (K) →
Writer (K) → Editor (K) → Critic (Ω) → Evolutionist (α)
```

**Example: Software Development Domain**
```
Product Owner (r) → Architect (K) → Developer (K) →
Tester (K) → Reviewer (Ω) → Retrospective Lead (α)
```

[Read more: Guide to Defining Your Personas](./guides/defining-your-personas.md)

**Want to see how this translates across domains?** Check out the [Universal Pattern Visual](./core/universal-pattern-visual.md) for a comprehensive guide showing how the same framework applies to software development, grant writing, content creation, and product design with side-by-side comparisons.

---

### 3. Four-Tier Memory System

Prevents context saturation while preserving institutional knowledge:

| Tier | Name | Scope | Lifespan | Size |
|------|------|-------|----------|------|
| **1** | Context | Current phase | Cleared at phase transitions | ~500 tokens |
| **2** | Memory | This project | Permanent (append-only) | Unlimited |
| **3** | Learnings | Cross-project | Curated patterns | ~3,000 tokens |
| **4** | Constitution | System rules | Rarely updated | ~10,000 tokens |

**Key insight:** Clear volatile context at phase transitions to keep AI focused, while preserving what matters.

[Read more: Core Memory System](./core/memory-system.md)

---

### 4. Quality Gates with Objective Scoring

Ω-phase personas score work objectively (0-100) and issue verdicts:

- **85-100:** ✅ APPROVE → Ship it
- **70-84:** 🔄 REVISE → Minor fixes, back to Editor
- **50-69:** ⚠️ RESTRUCTURE → Major issues, back to Architect
- **<50:** 🔥 RELEASE → Trigger system learning (α-phase)

**No more subjective "looks good enough"**

---

### 5. System Learning (α-phase)

When quality scores < 50 or patterns recur 3+ times:
1. **Evolutionist persona analyzes** root causes
2. **Proposes constitution updates** (with human approval)
3. **Seeds next attempt** with learnings
4. **System gets smarter** - recurring mistakes prevented

**Result:** Your workflow improves over time.

---

## Quick Start

### 🎯 New: AI-Guided Setup (10-15 minutes)

**Let an AI assistant set up your workflow through conversation**

Copy the [Workflow Architect prompt](./WORKFLOW-ARCHITECT.md) into your AI assistant to get:
- ✅ Conversational discovery of your personas
- ✅ Complete workflow.yaml generated
- ✅ Custom constitution for your domain
- ✅ Ready-to-use prompts for each persona
- ✅ Project structure and setup commands

**[→ Get the Workflow Architect Prompt](./WORKFLOW-ARCHITECT.md)**

This is the fastest way to get started - the AI asks you questions about your work and builds everything for you.

---

### Option 1: Use an Existing Domain (5 minutes)

```bash
# Clone the repository
git clone https://github.com/[org]/ai-workflow-orchestrator
cd ai-workflow-orchestrator

# Choose a domain
cd domains/content-writing  # or domains/software-development

# Read the domain README
cat README.md

# See QUICKSTART.md in main directory
cat ../../QUICKSTART.md
```

**Available domains:**
- [Content Writing](./domains/content-writing/) - Blogs, marketing, documentation
- [Software Development](./domains/software-development/) - Apps, APIs, tools

---

### Option 2: Build Your Own Workflow (30 minutes)

```bash
# Follow the quick start guide
cat QUICK-START.md

# Or read the full guide
open guides/defining-your-personas.md
```

**Steps:**
1. Map your domain to adaptive cycle phases
2. Define 3-5 personas (explorer, builder, critic, learner)
3. Write prompts for each persona
4. Run your first project
5. Iterate and improve

---

## Why This Works

| Traditional AI | Adaptive Workflows |
|----------------|-------------------|
| Ad-hoc prompting | Structured 4-phase process |
| Generic output | Specialized personas |
| Subjective quality | Objective 0-100 scoring |
| Re-prompt from scratch | Version-controlled artifacts |
| No learning | System evolves from failures |
| Context saturation | 4-tier memory management |
| One-shot generation | Iterative with checkpoints |

---

## What's Included

### Core Framework
- **[Adaptive Cycle Framework](./core/adaptive-cycle-framework.md)** - Understanding r→K→Ω→α
- **[Memory System](./core/memory-system.md)** - 4-tier architecture
- **[Naming Conventions](./docs/naming-conventions.md)** - File organization

### Guides
- **[Defining Your Personas](./guides/defining-your-personas.md)** - Discover agents for your domain
- **[Mapping Adaptive Cycles](./guides/mapping-adaptive-cycles.md)** - Map your work to phases
- **[Creating Quality Gates](./guides/creating-quality-gates.md)** - Design Ω-phase scoring
- **[Memory Strategy](./guides/memory-strategy.md)** - When to use each tier

### Templates
- **[Workflow Template](./templates/workflows/workflow-template.yaml)** - Blank workflow structure
- **[Agent Template](./templates/agents/agent-template.yaml)** - Blank persona definition
- **[Memory Templates](./templates/memory/)** - Context, memory, learnings, constitution

### Domain Examples
- **[Content Writing](./domains/content-writing/)** - Complete 7-persona workflow
- **[Software Development](./domains/software-development/)** - Complete 5-persona workflow

---

## Use Cases

### Content Creation
- Blog posts, articles, whitepapers
- Marketing copy, landing pages
- Technical documentation
- Social media content
- **Personas:** Strategist, Researcher, Writer, Editor, Critic

### Software Development
- Feature development
- Code review workflows
- API design
- Bug fixing processes
- **Personas:** Product Owner, Architect, Developer, Tester, Reviewer

### Product Design
- User research → prototyping → testing
- Design system development
- UX iteration workflows
- **Personas:** Researcher, Designer, Prototyper, Tester

### Research & Analysis
- Literature reviews
- Experiment design
- Data analysis pipelines
- **Personas:** Analyst, Researcher, Statistician, Reviewer

### **Your Domain Here**
The framework is domain-agnostic. Define your personas and get started!

---

## How It Works

### 1. Define Your Workflow
```yaml
# workflow.yaml
agents:
  - id: "strategist"
    phase: "r"
    role: "Define what to build and why"

  - id: "builder"
    phase: "K"
    role: "Create the solution"

  - id: "critic"
    phase: "omega"
    role: "Score quality 0-100, decide ship vs iterate"

flow:
  - strategist → builder → critic
  - if score < 70: loop back to builder
  - if score < 50: trigger learner (α-phase)
```

### 2. Run Personas Sequentially
Each persona:
- Reads previous artifacts
- Creates new artifact
- Logs to memory
- Human reviews at checkpoints

### 3. Quality Gate Decides
Critic persona scores work and issues verdict:
- Ship it ✅
- Revise it 🔄
- Restructure it ⚠️
- Learn from it 🔥 (trigger α-phase)

### 4. System Learns
When failures occur (score < 50):
- Evolutionist analyzes root cause
- Proposes constitution updates
- Next cycle uses evolved system

---

## Documentation

### Getting Started
- **[QUICK-START.md](./QUICK-START.md)** - Build your first workflow in 30 minutes
- **[Choose a domain](./domains/)** - Or browse existing domains

### Core Framework
- **[Adaptive Cycle Framework](./core/adaptive-cycle-framework.md)** - Understanding the four phases
- **[Memory System](./core/memory-system.md)** - Four-tier architecture explained

### Practical Guides
- **[Defining Your Personas](./guides/defining-your-personas.md)** - Discovery process
- **[Mapping Adaptive Cycles](./guides/mapping-adaptive-cycles.md)** - Map your domain to phases
- **[Creating Quality Gates](./guides/creating-quality-gates.md)** - Design scoring rubrics
- **[Memory Strategy](./guides/memory-strategy.md)** - When to use each memory tier

### Domain Examples
- **[Content Writing](./domains/content-writing/README.md)** - 7-persona workflow
- **[Software Development](./domains/software-development/README.md)** - 5-persona workflow

---

## Examples

### Content Writing: Blog Post Workflow
```
Strategist (r-phase)
  → Defines unique angle, audience
  → Output: content-brief.md

Researcher (r-phase)
  → Gathers facts, sources
  → Output: research-dossier.md

Architect (K-phase)
  → Creates structure
  → Output: article-skeleton.md
  → HUMAN CHECKPOINT

Writer (K-phase)
  → Generates prose
  → Output: draft-manuscript.md

Editor (K-phase)
  → Validates voice, facts
  → Output: validation-report.md

Critic (Ω-phase)
  → Scores 0-100
  → Output: critique-report.md
  → Verdict: APPROVE (87/100) ✅
```

[See full example](./domains/content-writing/examples/)

---

### Software Development: Feature Workflow
```
Product Owner (r-phase)
  → Defines requirements
  → Output: prd.md

Architect (K-phase)
  → Designs solution
  → Output: tech-spec.md
  → HUMAN CHECKPOINT

Developer (K-phase)
  → Implements code
  → Output: source files

Tester (K-phase)
  → Validates functionality
  → Output: test-report.md

Reviewer (Ω-phase)
  → Code review, security audit
  → Output: review-report.md
  → Verdict: REVISE (72/100) 🔄
  → Loop back to Developer
```

[See full example](./domains/software-development/examples/)

---

## Philosophy

This framework adapts principles from:

**Software Engineering:**
- Separation of concerns
- Single responsibility principle
- Code review / QA gates
- Continuous improvement (CI/CD)

**Resilience Theory:**
- Adaptive cycles (Holling, 1973)
- Panarchy (multi-scale nested cycles)
- Creative destruction (Ω-phase)
- Reorganization and learning (α-phase)

**Organizational Learning:**
- Institutional knowledge capture
- Pattern recognition across projects
- Constitution as living document
- Human-in-loop governance

**Result:** AI workflows that are transparent, methodical, and continuously improving.

---

## Contributing

We welcome contributions!

**Ways to contribute:**
- 🆕 **Add a new domain** - See [CONTRIBUTING.md](./CONTRIBUTING.md)
- ✨ **Improve existing domains** - Better prompts, refined personas
- 📚 **Share examples** - Real project case studies
- 🐛 **Report issues** - Found a problem? Let us know
- 💡 **Suggest features** - Ideas for framework improvements

[Read contribution guidelines](./CONTRIBUTING.md)

---

## License

MIT License - see [LICENSE](./LICENSE) for details

---

## Why "Adaptive" and "Panarchy"?

**Adaptive Cycle:** A model from ecology describing how systems move through growth (r), consolidation (K), collapse (Ω), and reorganization (α). This mirrors knowledge work:
- **r-phase:** Explore possibilities (research, strategy)
- **K-phase:** Build and refine (production)
- **Ω-phase:** Critically evaluate (quality gates)
- **α-phase:** Learn and evolve (system improvement)

**Panarchy:** Nested adaptive cycles at different scales interact. Example:
- **Micro:** Individual paragraphs/functions
- **Meso:** Sections/modules
- **Macro:** Full documents/systems

When lower scales fail (Ω), they can trigger learning at higher scales (α), which then constrains future lower-scale attempts (remember function).

**Why this matters:** Your workflow learns and evolves, getting smarter with each failure.

---

## Roadmap

### Current (v1.0)
- ✅ Core adaptive cycle framework
- ✅ 4-tier memory system
- ✅ Content writing domain
- ✅ Software development domain
- ✅ Comprehensive guides and templates

### Near-term (v1.1-1.2)
- 🔄 Product design domain
- 🔄 Research & analysis domain
- 🔄 Interactive workflow builder (CLI tool)
- 🔄 Automated artifact tracking

### Future (v2.0+)
- 🔮 Multi-agent automation (reduce manual execution)
- 🔮 Visual workflow editor
- 🔮 Cross-domain pattern library
- 🔮 Community domain marketplace

---

## FAQ

### Q: Do I need to code to use this?
**A:** No. The framework is prompt-based. You copy prompts, run them in AI chat, and save outputs. YAML configs are optional for power users.

### Q: What AI models work with this?
**A:** Any LLM (Claude, ChatGPT, Gemini, local models). Personas are model-agnostic.

### Q: Can I automate the workflow?
**A:** Eventually, yes. Start manually to learn the workflow, then automate specific steps. Full automation coming in v2.0.

### Q: How is this different from prompt libraries?
**A:** Prompt libraries give you individual prompts. This gives you a **system**: personas, phases, memory, quality gates, and learning. Your workflow evolves.

### Q: Do I need all 4 phases?
**A:** Minimum is 3 (r, K, Ω). You can skip α-phase initially. Add it when you want system learning.

### Q: What if my domain doesn't fit?
**A:** Almost all knowledge/creative work fits. Try the [mapping exercise](./guides/mapping-adaptive-cycles.md). If truly stuck, open a discussion.

### Q: How long does this take?
**A:** First project: 30-60 minutes setup + project time. After setup, projects run at normal speed with higher quality.

---

## Get Started Now

**🎯 Fastest path:** [**Workflow Architect**](./WORKFLOW-ARCHITECT.md) - AI-guided setup in 10-15 minutes

**📚 Manual setup:** [QUICK-START.md](./QUICK-START.md) - Build your workflow step-by-step

**📖 Use existing:** [Choose a domain](./domains/) - Content writing or software development

**Questions?** → Open an [issue](https://github.com/[org]/ai-workflow-orchestrator/issues) or [discussion](https://github.com/[org]/ai-workflow-orchestrator/discussions)
