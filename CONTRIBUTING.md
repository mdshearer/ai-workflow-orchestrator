# Contributing to AI Workflow Orchestrator

Thank you for your interest in contributing! This framework grows through community contributions, especially new domains.

---

## Table of Contents

1. [Ways to Contribute](#ways-to-contribute)
2. [Contributing New Domains](#contributing-new-domains)
3. [Quality Standards](#quality-standards)
4. [Persona Template Requirements](#persona-template-requirements)
5. [Prompt Structure Requirements](#prompt-structure-requirements)
6. [Constitution Template Requirements](#constitution-template-requirements)
7. [Example Project Requirements](#example-project-requirements)
8. [Submission Process](#submission-process)
9. [Review Criteria](#review-criteria)
10. [Code of Conduct](#code-of-conduct)

---

## Ways to Contribute

### 1. Propose a New Domain

**Best for:** Adding coverage for new fields (grant writing, video production, product design, etc.)

**Process:**
1. Open an issue using the [New Domain Proposal template](.github/ISSUE_TEMPLATE/new-domain-proposal.md)
2. Fill in all required sections
3. Wait for maintainer review and feedback
4. If approved, implement the domain following quality standards

**Time commitment:** 10-15 hours for a complete domain (5 personas, 10+ prompts, 3 templates, 2 examples)

---

### 2. Improve Existing Domains

**Best for:** Enhancing personas, prompts, or examples in software-development or content-writing

**What to improve:**
- Add more detailed examples
- Clarify persona responsibilities
- Improve prompt templates
- Add edge case handling
- Fix typos or broken links

**Process:**
1. Open an issue describing the improvement
2. Wait for feedback
3. Submit a pull request

---

### 3. Add More Examples

**Best for:** Showing the framework applied to different project types

**Examples we'd love:**
- **Software:** API service, Chrome extension, mobile app
- **Content:** Technical tutorial, case study, white paper
- **New domains:** Real-world projects from your domain

**Process:**
1. Create example project following [Example Project Requirements](#example-project-requirements)
2. Submit pull request with the example in `domains/{domain}/examples/{project-name}/`

---

### 4. Improve Documentation

**Best for:** Making the framework easier to understand and use

**What to improve:**
- Clarify confusing sections
- Add diagrams or visuals
- Fix broken links
- Improve cross-domain guides
- Add FAQ sections

**Process:**
1. Submit pull request with documentation improvements
2. Explain what you improved and why

---

### 5. Report Issues

**Best for:** Identifying problems, bugs, or gaps

**What to report:**
- Broken links or missing files
- Confusing documentation
- Persona or prompt errors
- Missing domain coverage

**Process:**
1. Open a GitHub issue with clear description
2. Tag appropriately (`bug`, `documentation`, `enhancement`)

---

## Contributing New Domains

### Before You Start

Ask yourself:

1. **Is there demand?** Will others use this domain?
2. **Is it distinct?** Can't be solved by adapting existing domains?
3. **Can you commit time?** 10-15 hours to build a quality domain?
4. **Do you have expertise?** Familiar with the domain professionally?

If yes to all → Proceed with domain proposal!

---

### Domain Structure

Every domain must include:

```
domains/{domain-name}/
├── README.md                    # Domain overview
├── personas/                    # 4-6 persona files
│   ├── 01-{persona-name}.md
│   ├── 02-{persona-name}.md
│   ├── 03-{persona-name}.md
│   ├── 04-{persona-name}.md
│   └── 05-{persona-name}.md
├── prompts/                     # Phase-based prompts
│   ├── phase-1-{phase-name}/
│   │   ├── 1.1-{prompt-name}.md
│   │   └── 1.2-{prompt-name}.md
│   ├── phase-2-{phase-name}/
│   ├── phase-3-{phase-name}/
│   └── phase-4-{phase-name}/
├── templates/                   # Constitution templates (2-3)
│   ├── {template-1}.md
│   ├── {template-2}.md
│   └── {template-3}.md
├── examples/                    # Example projects (2+)
│   ├── {example-1}/
│   └── {example-2}/
└── workflow/
    └── workflow-overview.md     # Visual workflow diagram
```

---

### Persona Count Guidelines

**4 personas:**
- Strategist → Creator → Reviewer → Finalizer
- Best for: Simple, linear workflows

**5 personas:**
- Strategist → Creator → Specialist → Reviewer → Finalizer
- Best for: Most domains (software, content, grants)

**6 personas:**
- Strategist → Creator → Specialist 1 → Specialist 2 → Reviewer → Finalizer
- Best for: Domains requiring multiple specialized reviews

**More than 6:**
- Rarely needed. Consider if personas can be combined.

---

### Workflow Type Guidelines

**Linear Workflow:**
- Phase 1 → Phase 2 → Phase 3 → Phase 4
- Minimal backtracking
- Example: Content writing (plan → write → edit → publish)

**Iterative Workflow:**
- Phase 1 → Phase 2 ⇄ Phase 3 → Phase 4
- Heavy iteration between implementation and review
- Example: Software development (build → test → refine → repeat)

**Hybrid Workflow:**
- Combination of both
- Clearly document when to iterate vs advance

---

## Quality Standards

### Minimum Requirements

All domains must meet these standards:

- [ ] **Complete persona set** (4-6 personas following template)
- [ ] **Sufficient prompts** (8+ prompts across 4 phases)
- [ ] **Constitution templates** (2-3 templates by project type)
- [ ] **Example projects** (2+ complete examples with artifacts)
- [ ] **Workflow documentation** (workflow-overview.md with diagram)
- [ ] **Domain README** (clear overview, persona table, quick start)
- [ ] **All links work** (no broken internal links)
- [ ] **Consistent formatting** (Markdown, follows existing patterns)
- [ ] **Real-world tested** (you've used it on 2+ real projects)

### Excellence Criteria

Domains that exceed minimum standards:

- ✨ **Detailed examples** showing messy iteration (v1 → v2 → v3)
- ✨ **Comprehensive personas** (8-12KB each with examples)
- ✨ **Edge case coverage** (common pitfalls documented)
- ✨ **Visual diagrams** (workflow visualizations, persona flow)
- ✨ **Template variables** (easy to customize for different projects)
- ✨ **Quality checklists** (clear success criteria for each persona)

---

## Persona Template Requirements

Every persona must include these sections:

### Required Sections

```markdown
# Persona: {Persona Name}

## Role Definition
[2-3 sentences: What this persona does]

## Core Responsibilities
1. [Primary responsibility]
2. [Secondary responsibility]
3. [Tertiary responsibility]
4-7. [Additional responsibilities]

## Expertise Areas
- [Domain knowledge 1]
- [Domain knowledge 2]
- [Domain knowledge 3]

## When to Invoke This Persona
✅ **Use when:**
- [Trigger condition 1]
- [Trigger condition 2]

❌ **Don't use when:**
- [Wrong scenario 1]
- [Wrong scenario 2]

## Input Artifacts (What This Persona Reads)
- `CONSTITUTION.md` - Project principles
- [Previous phase artifacts]

## Output Artifacts (What This Persona Creates)
- **Primary:** `artifacts/{filename}.md`
- **Format:** [Markdown / Report / Checklist]
- **Contents:** [Description]

## Success Criteria
✅ [Quality indicator 1]
✅ [Quality indicator 2]
✅ [Quality indicator 3]
✅ Aligns with CONSTITUTION.md

## Quality Checklist
- [ ] [Criterion 1]
- [ ] [Criterion 2]
- [ ] [Criterion 3]
- [ ] Constitutional alignment verified

## Common Pitfalls
❌ **Pitfall:** [What to avoid]
✅ **Instead:** [What to do]

## Related Personas
- **Previous:** [{Previous Persona}](./0X-previous.md)
- **Next:** [{Next Persona}](./0X-next.md)
```

### Persona Length

- **Minimum:** 6KB (~800 words)
- **Target:** 8-12KB (~1,200-1,600 words)
- **Maximum:** 15KB (~2,000 words)

If longer than 15KB, consider splitting into multiple personas.

---

## Prompt Structure Requirements

Every prompt must include these sections:

### Required Sections

```markdown
# Prompt: {Persona Name} - {Task Name}

**Persona:** {Persona Name}
**Phase:** {Phase Number} - {Phase Name}
**Purpose:** [One sentence description]

---

## When to Use This Prompt

✅ **Use when:**
- [Trigger condition]

❌ **Don't use when:**
- [Wrong scenario]

**Prerequisites:**
- [ ] [Required input 1]
- [ ] [Required input 2]

---

## The Prompt Template

\```markdown
You are a {Persona Name}. Your task is to {Task Description}.

**Rules:**
1. You must adhere to all principles in CONSTITUTION.md
2. [Domain-specific rule 1]
3. [Domain-specific rule 2]
4. Output must be in {Format} format
5. If unclear, ASK questions before proceeding

**Input Artifacts:**
- {File 1}
- {File 2}
- CONSTITUTION.md

**Output Artifact:**
- artifacts/{filename}

**Context:**
{Variables to fill in}

**Quality Checklist:**
- [ ] [Criterion 1]
- [ ] [Criterion 2]
- [ ] Aligns with CONSTITUTION.md
\```

---

## Review Criteria

Your output is ready when:
- [ ] [Quality criterion 1]
- [ ] [Quality criterion 2]
- [ ] All quality checklist items passed

---

## Example Output Structure

[Show what the output artifact should look like]

---

## Related Prompts
- **Previous:** [Previous prompt]
- **Next:** [Next prompt]
```

### Prompt Length

- **Minimum:** 3KB (~400 words)
- **Target:** 4-6KB (~600-800 words)
- **Maximum:** 8KB (~1,000 words)

---

## Constitution Template Requirements

Every constitution template must include:

### Required Sections

```markdown
# {Template Name} Constitution Template

**Domain:** {Domain Name}
**Project Type:** {Type, e.g., "Foundation Grant", "Short-Form Video"}
**Last Updated:** {Date}

---

## How to Use This Template

1. Copy this file to your project root as `CONSTITUTION.md`
2. Fill in all `[BRACKETS]` with your project details
3. Customize principles and standards for your needs
4. Reference in all persona prompts

---

## Project Identity

**Project Name:** [Your project name]

**Target Audience:** [Who is this for?]

**Primary Goal:** [What are you trying to achieve?]

**Timeline:** [When does this need to be done?]

---

## Core Principles (Non-Negotiable)

These principles apply to every decision and artifact:

1. **{Principle 1}** - {Explanation}
2. **{Principle 2}** - {Explanation}
3. **{Principle 3}** - {Explanation}

---

## Standards (Quality Bars)

All work must meet these standards:

### {Category 1}
- {Standard 1}
- {Standard 2}

### {Category 2}
- {Standard 1}
- {Standard 2}

---

## Constraints (Limitations)

What we cannot do or must avoid:

- ❌ {Constraint 1}
- ❌ {Constraint 2}
- ❌ {Constraint 3}

---

## Success Metrics

How we'll know this is successful:

- ✅ {Metric 1}
- ✅ {Metric 2}
- ✅ {Metric 3}

---

## Review Process

**Approval gates:**
1. {Phase 1} approval required from: {Who}
2. {Phase 2} approval required from: {Who}
3. {Phase 3} approval required from: {Who}

**Feedback format:** {How feedback should be given}
```

### Constitution Template Length

- **Minimum:** 2KB (~300 words)
- **Target:** 3-4KB (~400-600 words)
- **Maximum:** 6KB (~800 words)

---

## Example Project Requirements

Every example project must include:

### Required Files

```
examples/{project-name}/
├── README.md                           # Project overview
├── CONSTITUTION.md                     # Customized constitution
├── artifacts/
│   ├── 01-{first-artifact}.md         # Phase 1 output
│   ├── 02-{second-artifact}-v1.md     # Phase 2 output (v1)
│   ├── 02-{second-artifact}-v2.md     # After iteration
│   ├── 03-{third-artifact}.md         # Phase 3 output
│   ├── 04-{review-report}.md          # Review findings
│   ├── 02-{second-artifact}-v3.md     # After review fixes
│   ├── 05-{final-artifact}-FINAL.md   # Publication-ready
│   └── workflow-log.md                # Iteration history
└── [Additional project files]
```

### Example README Requirements

```markdown
# Example: {Project Name}

## Overview
[2-3 sentences: What this example demonstrates]

## What This Demonstrates
- {Learning point 1}
- {Learning point 2}
- {Learning point 3}

## Key Decisions
1. **{Decision 1}:** {Why we made this choice}
2. **{Decision 2}:** {Why we made this choice}

## Iteration History
- **v1:** {What changed}
- **v2:** {What changed}
- **v3-FINAL:** {What changed}

## Artifacts Included
- `01-{artifact}.md` - {Description}
- `02-{artifact}-v1.md` - {Description}
- [List all artifacts]

## Key Takeaways
1. {Lesson 1}
2. {Lesson 2}
3. {Lesson 3}
```

### Example Project Size

- **Minimum:** 2 complete examples per domain
- **Artifacts:** Show 2-3 iterations (v1 → v2 → v3)
- **Workflow log:** Document key decisions and cross-persona dialogue
- **Total size:** 10-20KB per example

---

## Submission Process

### Step 1: Proposal

1. Open issue using [New Domain Proposal template](.github/ISSUE_TEMPLATE/new-domain-proposal.md)
2. Fill in all sections
3. Wait for maintainer feedback (7 days)

### Step 2: Implementation

Once approved:

1. Fork the repository
2. Create branch: `domain/{domain-name}`
3. Build domain following quality standards
4. Test on 2-3 real projects
5. Create all required files

### Step 3: Pull Request

1. Submit PR from your branch
2. PR title: `[NEW DOMAIN] {Domain Name}`
3. PR description must include:
   - Link to approved proposal issue
   - Checklist confirming all requirements met
   - Screenshots of example outputs
   - Summary of testing done

### Step 4: Review

Maintainers will review:

- Completeness (all files present)
- Quality (meets standards)
- Consistency (follows existing patterns)
- Testing (works on real projects)

**Review timeline:** 14 days

### Step 5: Revisions

Address feedback:

1. Make requested changes
2. Update PR
3. Request re-review

### Step 6: Merge

Once approved:

1. Maintainer merges PR
2. Domain goes live
3. You're credited in release notes
4. Celebrate! 🎉

---

## Review Criteria

### Must Have (Required for Approval)

- [ ] All required files present
- [ ] Follows domain structure
- [ ] 4-6 personas (8-12KB each)
- [ ] 8+ prompts across 4 phases
- [ ] 2-3 constitution templates
- [ ] 2+ example projects with artifacts
- [ ] Workflow overview with diagram
- [ ] Domain README with quick start
- [ ] All internal links work
- [ ] Tested on real projects
- [ ] No broken formatting

### Nice to Have (Excellence)

- [ ] 3+ example projects
- [ ] Detailed iteration history in examples
- [ ] Visual workflow diagrams
- [ ] Edge case documentation
- [ ] Video walkthrough
- [ ] Community feedback incorporated

---

## Code of Conduct

### Our Standards

**Positive behaviors:**
- ✅ Respectful and inclusive language
- ✅ Welcoming diverse perspectives
- ✅ Constructive feedback
- ✅ Focusing on what's best for the community
- ✅ Showing empathy

**Unacceptable behaviors:**
- ❌ Harassment or discriminatory language
- ❌ Personal attacks
- ❌ Trolling or inflammatory comments
- ❌ Publishing others' private information
- ❌ Other unethical or unprofessional conduct

### Enforcement

Violations will result in:
1. **Warning:** First offense
2. **Temporary ban:** Second offense
3. **Permanent ban:** Third offense or severe violation

Report violations to: [maintainer email]

---

## Questions?

- **General questions:** Open a [GitHub Discussion](https://github.com/mdshearer/ai-workflow-orchestrator/discussions)
- **Bug reports:** Open a [GitHub Issue](https://github.com/mdshearer/ai-workflow-orchestrator/issues)
- **Domain proposals:** Use [New Domain Proposal template](.github/ISSUE_TEMPLATE/new-domain-proposal.md)

---

## Recognition

Contributors are recognized in:
- Release notes for their contributions
- CONTRIBUTORS.md file (coming soon)
- Domain README files (if applicable)

---

**Thank you for contributing to AI Workflow Orchestrator!**

Together we're building a universal framework for structured AI collaboration across all domains.
