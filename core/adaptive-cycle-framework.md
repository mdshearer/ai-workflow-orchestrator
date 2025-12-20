# Adaptive Cycle Framework

**A resilience-based model for AI workflow orchestration**

---

## What Is the Adaptive Cycle?

The adaptive cycle is a model from **resilience theory** that describes how complex systems (ecosystems, organizations, creative processes) move through four distinct phases. Originally developed by ecologist C.S. Holling to understand forest dynamics, it's a powerful framework for orchestrating AI workflows.

**The four phases form a figure-8 loop:**

```
         ┌─────────────────────────┐
         │    α (Reorganization)   │
         │    Innovation           │
         │    Experimentation      │
         └───────────┬─────────────┘
                     │
         ┌───────────▼─────────────┐
         │    r (Growth)           │
         │    Exploration          │
         │    Resource gathering   │
         └───────────┬─────────────┘
                     │
         ┌───────────▼─────────────┐
         │    K (Conservation)     │
         │    Production           │
         │    Refinement           │
         └───────────┬─────────────┘
                     │
         ┌───────────▼─────────────┐
         │    Ω (Release)          │
         │    Critique             │
         │    Creative destruction │
         └───────────┬─────────────┘
                     │
         Back to α or complete
```

---

## The Four Phases

### r-phase: Growth/Exploitation

**Forest analogy:** Pioneer species colonizing after a fire
**Work analogy:** Brainstorming, research, strategy

**Characteristics:**
- **Fast** - Rapid exploration
- **Divergent** - Many possibilities explored
- **Uncertain** - Outcomes not yet clear
- **Resource gathering** - Collecting raw materials/information
- **Low efficiency** - Trial and error

**Agent behaviors in r-phase:**
- Ask clarifying questions
- Explore multiple angles
- Gather information without judgment
- Define constraints and requirements
- Research and analyze

**Examples by domain:**
- **Content writing:** Strategy, research, audience analysis
- **Software development:** Requirements gathering, market research
- **Design:** User research, problem framing
- **Scientific research:** Literature review, hypothesis generation

**Key question:** "What are we trying to do and why?"

---

### K-phase: Conservation

**Forest analogy:** Mature forest with established trees
**Work analogy:** Production, implementation, refinement

**Characteristics:**
- **Slow** - Methodical and structured
- **Convergent** - Single path chosen
- **Stable** - Predictable process
- **Resource optimization** - Efficient use of gathered materials
- **High efficiency** - Streamlined production

**Agent behaviors in K-phase:**
- Build and create
- Follow established structure
- Refine and optimize
- Validate correctness
- Polish and perfect

**Examples by domain:**
- **Content writing:** Outlining, drafting, editing
- **Software development:** Architecture, coding, testing
- **Design:** Prototyping, iteration, refinement
- **Scientific research:** Experiment design, data collection, analysis

**Key question:** "How do we build this well?"

---

### Ω-phase: Release/Collapse

**Forest analogy:** Forest fire (creative destruction)
**Work analogy:** Critical review, quality gates, red-teaming

**Characteristics:**
- **Fast** - Rapid evaluation
- **Adversarial** - Assumes guilt, seeks flaws
- **Destructive** - Can trigger complete restart
- **Gate-keeping** - Veto power
- **Objective** - Measurement-based

**Agent behaviors in Ω-phase:**
- Critically evaluate quality
- Score against objective criteria
- Ask "Should this exist at all?"
- Issue verdicts (approve/revise/restructure/release)
- Provide no solutions, only critique

**Examples by domain:**
- **Content writing:** Stability scoring, publication decision
- **Software development:** Code review, security audit, acceptance testing
- **Design:** Usability testing, stakeholder critique
- **Scientific research:** Peer review, statistical validation

**Key question:** "Is this good enough to ship?"

---

### α-phase: Reorganization

**Forest analogy:** New growth patterns emerging after fire
**Work analogy:** Retrospectives, system learning, process improvement

**Characteristics:**
- **Fast** - Rapid pattern recognition
- **Innovative** - New approaches emerge
- **Meta-level** - Thinks about the system itself
- **Strategic** - Plans next cycle
- **Evolutionary** - Updates system rules

**Agent behaviors in α-phase:**
- Analyze failure patterns
- Extract learnings
- Update system governance (constitution)
- Prevent recurring mistakes
- Seed strategy for next cycle

**Examples by domain:**
- **Content writing:** Update editorial constitution, style guide evolution
- **Software development:** Update coding standards, architectural patterns
- **Design:** Design system updates, pattern library improvements
- **Scientific research:** Methodology improvements, protocol updates

**Key question:** "What should the system learn from this?"

---

## Phase Transitions

### r→K: From Exploration to Production

**Trigger:** Strategy approved, requirements clear
**What changes:**
- Mindset shifts from divergent to convergent
- Uncertainty resolves to concrete plan
- Exploration becomes execution

**Memory management:**
- Summarize context → memory
- Clear volatile context
- Preserve decisions and constraints

**Example:** In content writing, this happens when the content brief and research are approved and the writer starts creating the article structure.

---

### K→Ω: From Production to Critique

**Trigger:** Work product complete and ready for evaluation
**What changes:**
- Creator mindset becomes evaluator mindset
- Production stops, critique begins
- Friendly becomes adversarial

**Memory management:**
- Preserve working context (Critic needs it)
- Log completion of production phase

**Example:** In software development, this is submitting a PR for code review.

---

### Ω→α: From Critique to Evolution (Conditional)

**Trigger:** Critical failure detected (e.g., score < threshold)
**What changes:**
- Focus shifts from product to process
- "What's wrong with this?" becomes "What's wrong with our system?"
- Tactical becomes strategic

**Memory management:**
- Preserve critique report
- Access cross-project learnings
- Enable constitution updates

**Example:** When a blog post scores <50/100 on stability, it triggers root cause analysis and style guide updates.

**Important:** This transition is **conditional** - it only happens on significant failures, not normal revisions.

---

### α→r: From Evolution to Next Cycle

**Trigger:** System learnings captured and constitution updated
**What changes:**
- New cycle begins with evolved system
- Learnings inform strategy
- Process improvements applied

**Memory management:**
- Clear all volatile context
- Update constitution/governance
- Preserve learnings in cross-project memory

**Example:** After updating coding standards based on recurring bugs, the next feature implementation starts with improved guidelines.

---

## Front Loop vs. Back Loop

### Front Loop: r→K (Slow Growth)
- **Duration:** Longer (hours to days)
- **Predictability:** High
- **Focus:** Building capital (knowledge, structure, assets)
- **Agents:** Most of your personas work here

### Back Loop: Ω→α (Fast Reorganization)
- **Duration:** Shorter (minutes to hours)
- **Predictability:** Low
- **Focus:** Creative destruction and renewal
- **Agents:** Typically 1-2 specialized personas

**Implication for workflows:** Spend 80-90% of time in front loop (r→K), 10-20% in back loop (Ω→α).

---

## Panarchy: Nested Cycles

**Panarchy** describes how adaptive cycles at different scales interact.

### Example: Content Writing

**Macro-cycle (document level):**
- r: Document strategy
- K: Write full document
- Ω: Review entire document
- α: Update style guide

**Meso-cycle (section level):**
- r: Section outline
- K: Write section
- Ω: Review section
- α: Note patterns

**Micro-cycle (paragraph level):**
- r: Paragraph idea
- K: Write paragraph
- Ω: Edit paragraph
- α: Learn phrasing patterns

### Cross-Scale Dynamics

**Revolt (bottom-up):**
Crisis at smaller/faster scale cascades upward.
- Example: Multiple bad paragraphs trigger section restructure

**Remember (top-down):**
Larger/slower scale provides memory and constraints.
- Example: Document-level style guide constrains paragraph writing

---

## Why This Matters for AI Workflows

### 1. Prevents Rigidity Traps
Without Ω-phase critique, workflows get stuck in K-phase optimization, producing polished but fundamentally flawed work.

### 2. Enables System Learning
Without α-phase evolution, the same mistakes repeat across projects. The system never gets smarter.

### 3. Provides Natural Checkpoints
Phase transitions are natural points for human review and decision-making.

### 4. Separates Concerns
Each phase has different characteristics, requiring different agent behaviors. Mixing them (e.g., critique while creating) reduces quality.

### 5. Objective Quality Gates
Ω-phase provides measurement-based decision points, not subjective "looks good enough."

### 6. Continuous Improvement
α-phase captures institutional knowledge, making your workflow better over time.

---

## Mapping Your Work to the Adaptive Cycle

### Quick Exercise

For your domain, identify:

1. **r-phase activities** - When do you explore, research, strategize?
2. **K-phase activities** - When do you build, create, refine?
3. **Ω-phase activities** - When do you critically evaluate, measure quality?
4. **α-phase activities** - When do you learn from failures, update processes?

### Decision Tree

Ask yourself about each activity:

**Q1: Is this exploring possibilities (divergent) or building a thing (convergent)?**
- Divergent → r-phase
- Convergent → K-phase

**Q2: Is this creating/refining OR evaluating/critiquing?**
- Creating/refining → K-phase
- Evaluating/critiquing → Ω-phase

**Q3: Is this doing work OR improving the system itself?**
- Doing work → r/K/Ω-phase
- Improving system → α-phase

---

## Common Patterns Across Domains

### Software Development
```
r: Requirements, research, planning
K: Architecture, coding, testing
Ω: Code review, security audit
α: Update standards, refactor patterns
```

### Content Creation
```
r: Strategy, research
K: Outline, draft, edit
Ω: Quality scoring, publication decision
α: Style guide updates, pattern learning
```

### Product Design
```
r: User research, problem framing
K: Sketching, prototyping, refining
Ω: Usability testing, stakeholder review
α: Design system updates
```

### Scientific Research
```
r: Literature review, hypothesis generation
K: Experiment design, data collection, analysis
Ω: Peer review, statistical validation
α: Methodology improvements
```

---

## Implementing Adaptive Cycles in Your Workflow

### 1. Identify Phase Boundaries
Map your existing workflow to the four phases. Where do you naturally shift from exploration to production? From production to critique?

### 2. Assign Agents to Phases
Each agent should primarily operate in one phase. Some agents might span two adjacent phases, but avoid mixing r-phase and Ω-phase behaviors.

### 3. Define Phase Transition Triggers
What conditions cause phase transitions?
- r→K: Strategy approved
- K→Ω: Work complete
- Ω→α: Critical failure (score < threshold)
- α→r: Learnings captured

### 4. Configure Memory Management
What gets preserved vs. cleared at each transition?
- r→K: Summarize and clear context
- K→Ω: Preserve context for critique
- Ω→α: Preserve all artifacts
- α→r: Clear everything, update constitution

### 5. Set Thresholds for Evolution
When does Ω→α trigger?
- Quality score below threshold (e.g., <50/100)
- Recurring pattern detected (e.g., 3rd occurrence)
- Critical system failure

---

## Anti-Patterns to Avoid

❌ **Skipping Ω-phase** - No quality gate means shipping flawed work
❌ **Never reaching α-phase** - System doesn't learn, mistakes repeat
❌ **Mixing creation and critique** - Same agent both builds and judges
❌ **Staying in r-phase too long** - Analysis paralysis, never shipping
❌ **Jumping straight to K-phase** - Building without strategy leads to rework
❌ **Infinite Ω→K loops** - Revising without learning why failures occur

---

## Further Reading

- **Original theory:** Holling, C.S. (1973). "Resilience and Stability of Ecological Systems"
- **Panarchy framework:** Gunderson & Holling (2002). "Panarchy: Understanding Transformations in Human and Natural Systems"
- **Applied to organizations:** Resilience Alliance - [resalliance.org](https://www.resalliance.org)

---

## Next Steps

1. Read [guides/mapping-adaptive-cycles.md](../guides/mapping-adaptive-cycles.md) to map your domain
2. Use [guides/defining-your-personas.md](../guides/defining-your-personas.md) to assign agents to phases
3. See [examples/](../examples/) for reference implementations

---

*This framework is inspired by ecological resilience theory and adapted for AI workflow orchestration.*
