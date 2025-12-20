# Quick Start: Build Your First Adaptive Workflow

**Get a working workflow with adaptive cycles in 30 minutes**

---

## What You'll Build

By the end of this guide, you'll have:
- ✅ 3-5 defined personas for your domain
- ✅ A working workflow with adaptive cycle phases
- ✅ Memory management setup
- ✅ Your first project ready to run

**Time required:** 30 minutes

---

## Prerequisites

- Basic understanding of your domain's workflow
- A real project you want to tackle
- Text editor (VS Code, Sublime, or any markdown editor)
- AI assistant (Claude, ChatGPT, etc.) for running agents

---

## Step 1: Choose Your Domain (2 minutes)

What kind of work are you orchestrating?

**Common domains:**
- ✏️ Content creation (writing, blogs, marketing)
- 💻 Software development (coding, review, deployment)
- 🎨 Product design (research, prototyping, testing)
- 🔬 Research (literature review, experiments, analysis)
- 📊 Data analysis (collection, processing, visualization)
- Other: _______________

**For this guide, we'll use placeholders. Replace with your domain.**

---

## Step 2: Map Your Process to Adaptive Cycles (5 minutes)

### Quick Mapping Exercise

List 5-7 major activities in your current process:

```
1. ___________________________
2. ___________________________
3. ___________________________
4. ___________________________
5. ___________________________
```

### Assign to Phases

Use this decision tree:

**Q: Does this explore options OR build something?**
- Explore → r-phase
- Build → K-phase

**Q: Does this evaluate quality?**
- Yes → Ω-phase

**Q: Does this improve the system itself?**
- Yes → α-phase

**Example: Content Writing**
```
1. Research topic → r-phase
2. Define strategy → r-phase
3. Create outline → K-phase
4. Write draft → K-phase
5. Edit → K-phase
6. Review for publication → Ω-phase
7. Learn from feedback → α-phase
```

---

## Step 3: Define Your Personas (10 minutes)

### Minimum Viable Personas (3-4 agents)

You need at least:
1. **One r-phase persona** (explorer)
2. **One K-phase persona** (creator)
3. **One Ω-phase persona** (critic)
4. **One α-phase persona** (learner) - optional but recommended

### Fill Out Persona Cards

For each persona, answer:

**Persona 1 (r-phase):**
```
Name: _______________
Role: Define/research/plan [what?]
Inputs: User requirements
Outputs: [artifact-name].md (e.g., strategy-brief.md)
Cannot do: Does NOT build/create the final deliverable
```

**Persona 2 (K-phase):**
```
Name: _______________
Role: Create/build [what?]
Inputs: [output from Persona 1]
Outputs: [artifact-name].md (e.g., draft.md)
Cannot do: Does NOT evaluate quality (that's Ω-phase)
```

**Persona 3 (Ω-phase):**
```
Name: _______________
Role: Evaluate quality and decide: ship or iterate?
Inputs: [output from Persona 2]
Outputs: critique-report.md with score (0-100)
Cannot do: Does NOT fix issues, only identifies them
```

**Persona 4 (α-phase) - Optional:**
```
Name: _______________
Role: Learn from failures, update system rules
Inputs: [critique report showing failure]
Outputs: Updated constitution, learnings
Triggers: Only when quality score < 50
```

### Example: Minimal Content Workflow

```yaml
Persona 1: Strategist (r-phase)
  → Outputs: content-brief.md

Persona 2: Writer (K-phase)
  → Inputs: content-brief.md
  → Outputs: draft.md

Persona 3: Critic (Ω-phase)
  → Inputs: draft.md
  → Outputs: critique-report.md (score 0-100)

Persona 4: Evolutionist (α-phase)
  → Triggers: score < 50
  → Updates: constitution.md
```

---

## Step 4: Create Your Project Structure (5 minutes)

### Directory Setup

```bash
cd ai-workflow-orchestrator

# Create your domain folder (or use existing in domains/)
mkdir -p my-workflow
cd my-workflow

# Copy templates
cp ../templates/workflows/workflow-template.yaml workflow.yaml
cp ../templates/memory/constitution-template.md constitution.md
cp ../templates/memory/project-learnings-template.md project-learnings.md

# Create folders
mkdir -p prompts agents projects
```

### Create First Project

```bash
cd projects
mkdir 01-first-project

# Copy memory templates
cp ../../templates/memory/context-template.md 01-first-project/context.md
cp ../../templates/memory/memory-template.md 01-first-project/memory.md
```

---

## Step 5: Configure Your Workflow (5 minutes)

### Edit workflow.yaml

Open `my-workflow/workflow.yaml` and fill in:

```yaml
---
name: "My [Domain] Workflow"
description: "Adaptive workflow for [what you're building]"
domain: "[your-domain]"

agents:
  - id: "persona-1-id"
    name: "Persona 1 Name"
    number: "01"
    phase: "r"
    role: "[One sentence description]"
    prompt_file: "prompts/01-persona-1.md"
    inputs:
      required: ["user-brief"]
    outputs:
      - artifact: "brief"
        schema: "templates/brief-template.md"
    human_checkpoint: "required"

  - id: "persona-2-id"
    name: "Persona 2 Name"
    number: "02"
    phase: "K"
    role: "[One sentence description]"
    prompt_file: "prompts/02-persona-2.md"
    inputs:
      required: ["brief"]
    outputs:
      - artifact: "draft"
    human_checkpoint: "optional"

  - id: "persona-3-id"
    name: "Persona 3 Name"
    number: "03"
    phase: "omega"
    role: "[One sentence description]"
    prompt_file: "prompts/03-persona-3.md"
    inputs:
      required: ["draft"]
    outputs:
      - artifact: "critique-report"
        extract_fields:
          - name: "score"
            type: "integer"
    is_gate: true
    human_checkpoint: "required"

flow:
  - step: 1
    agent: "persona-1-id"
    next: "persona-2-id"

  - step: 2
    agent: "persona-2-id"
    next: "persona-3-id"

  - step: 3
    agent: "persona-3-id"
    next:
      - condition: "score >= 70"
        action: "complete"
      - condition: "score < 70"
        action: "loop_to"
        target: "persona-2-id"
---
```

---

## Step 6: Write Your First Prompt (3 minutes)

### Create Persona 1 Prompt

Create `prompts/01-persona-1.md`:

```markdown
# [Persona 1 Name] - [Role]

You are the **[Persona Name]**, responsible for [responsibility].

## Your Job
[1-2 sentences describing what this persona does]

## Inputs You Have
- User requirements/brief
- (List what this persona can read)

## Output You Must Create
Create a file called `[PROJECT#]-01-[artifact-name]-v1.md` with:

### Required Sections
1. **[Section 1]:** [What goes here]
2. **[Section 2]:** [What goes here]
3. **[Section 3]:** [What goes here]

## Constraints
- [Rule 1]
- [Rule 2]
- You CANNOT [what they can't do]

## Memory Context
Read these files for context:
- `context.md` - Current phase notes
- `constitution.md` - Governing rules

## When Done
1. Save artifact as: `[PROJECT#]-01-[artifact-name]-v1.md`
2. Append to `memory.md` with timestamp and summary
3. Ask human for approval
```

**Tip:** See `examples/` folders for complete prompt examples.

---

## Step 7: Run Your First Project (5 minutes minimum)

### Execute the Workflow

1. **Navigate to your project:**
   ```bash
   cd projects/01-first-project
   ```

2. **Run Persona 1 (r-phase):**
   - Open AI assistant (Claude, ChatGPT)
   - Copy prompt from `prompts/01-persona-1.md`
   - Provide user requirements
   - Save output as `01-01-brief-v1.md`
   - Update `memory.md`

3. **Human Checkpoint:**
   - Review `01-01-brief-v1.md`
   - Approve or request changes
   - If changes needed, iterate (v2, v3...)

4. **Run Persona 2 (K-phase):**
   - Copy prompt from `prompts/02-persona-2.md`
   - Provide `01-01-brief-v1.md` as input
   - Save output as `01-02-draft-v1.md`
   - Update `memory.md`

5. **Run Persona 3 (Ω-phase):**
   - Copy prompt from `prompts/03-persona-3.md`
   - Provide `01-02-draft-v1.md` as input
   - Review critique score
   - If score < 70, loop back to Persona 2
   - If score >= 70, complete!

---

## What's Next?

### After Your First Project

- ✅ Review what worked and what didn't
- ✅ Update `project-learnings.md` with insights
- ✅ Refine prompts based on experience
- ✅ Add more personas if needed

### Going Deeper

1. **Read the frameworks:**
   - [Core: Adaptive Cycle Framework](./core/adaptive-cycle-framework.md)
   - [Core: Memory System](./core/memory-system.md)

2. **Study examples:**
   - [Content Writing Example](./examples/content-writing/)
   - [Software Development Example](./examples/software-development/)

3. **Customize:**
   - [Guide: Defining Your Personas](./guides/defining-your-personas.md)
   - [Guide: Creating Quality Gates](./guides/creating-quality-gates.md)

4. **Expand:**
   - Add 4th, 5th, 6th personas for complexity
   - Implement full adaptive cycle with α-phase
   - Build scoring rubrics for Ω-phase

---

## Common First-Time Questions

### Q: Do I need to use all 4 phases?
**A:** Minimum is 3 (r, K, Ω). You can skip α-phase initially and add it later when you want system learning.

### Q: How do I know if my personas are right?
**A:** Test with a real project. If you feel confused about who does what, you need clearer separation of concerns.

### Q: What if my workflow doesn't fit the adaptive cycle?
**A:** Almost all creative/knowledge work fits. Try the mapping exercise in [guides/mapping-adaptive-cycles.md](./guides/mapping-adaptive-cycles.md).

### Q: Can I automate this?
**A:** Eventually, yes. For now, manual execution helps you learn the workflow before automating.

### Q: Do I need all the memory files?
**A:** Start with just `memory.md`. Add `context.md`, `project-learnings.md`, and `constitution.md` as you scale.

---

## Troubleshooting

### Personas overlap in responsibility
**Fix:** Each persona should have ONE job. Split or clarify boundaries.

### Not sure when to move to next phase
**Fix:** Define explicit triggers (e.g., "human approves brief" triggers r→K).

### Prompts too vague
**Fix:** Study example prompts in `examples/`. Be specific about inputs, outputs, and constraints.

### Workflow feels slow
**Fix:** That's normal for first project. Speed comes with template reuse and clearer prompts.

---

## Next Steps

1. ✅ Complete your first project
2. 📝 Document what worked in `project-learnings.md`
3. 🔄 Run 2-3 more projects to refine your workflow
4. 📊 Add quality scoring (Ω-phase) for objective gates
5. 🧬 Implement α-phase for system learning

**Ready to dive deeper?** → Start with [Core: Adaptive Cycle Framework](./core/adaptive-cycle-framework.md)

---

*Questions? Open an issue or discussion on GitHub.*
