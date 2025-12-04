# Guide: Customizing Personas

This guide shows how to adapt existing personas or create new ones for your specific needs.

---

## When to Customize

### Use Existing Personas When:
- ✅ Standard roles fit your needs (Product Owner, Content Strategist, etc.)
- ✅ Standard workflow works (4 phases, linear or iterative)
- ✅ Templates match your project type

### Customize Personas When:
- 🔧 Your domain has unique roles (e.g., "Brand Voice Specialist" for strict brand guidelines)
- 🔧 You need specialized expertise (e.g., "Accessibility Auditor" for WCAG compliance)
- 🔧 Standard personas are too generic (e.g., "E-commerce Content Writer" vs generic writer)
- 🔧 You're adapting for a new domain (e.g., video production, product design)

---

## Customization Approaches

### Level 1: Tweak Existing Persona (Easiest)

**Use case:** Persona is 90% right, needs small adjustments

**How to:**
1. Copy existing persona file
2. Rename (e.g., `02-content-writer.md` → `02-ecommerce-writer.md`)
3. Update sections:
   - Role Definition (add specifics)
   - Core Responsibilities (add/remove items)
   - Best Practices (add domain-specific tips)
   - Success Criteria (adjust metrics)

**Example:** Content Writer → E-commerce Content Writer
```markdown
## Core Responsibilities (ADDED)
1. ... (existing responsibilities)
8. Write product descriptions optimized for conversion
9. Follow e-commerce SEO best practices (product schema, etc.)

## Best Practices (ADDED)
- Include product specs in structured format
- Write benefit-focused copy (not just features)
- Follow e-commerce conventions (size guides, shipping info, reviews)
```

**Time:** 15-30 minutes per persona

---

### Level 2: Merge Personas (Moderate)

**Use case:** Small team, need to combine roles

**How to:**
1. Identify personas to merge (related roles work best)
2. Create new persona file
3. Combine responsibilities and checklists
4. Add section distinguishing when to use each role

**Example:** SEO Specialist + Editor → Content Optimizer
```markdown
# Persona: Content Optimizer

## Role Definition
Combines SEO optimization and editorial polish into one streamlined review.

## When to Use This Combined Persona
✅ Use when: Small team, content needs both SEO and editing
❌ Don't use when: Need deep SEO analysis OR content has major structural issues

## Core Responsibilities
### From SEO Specialist:
1. Optimize keyword usage
2. Improve readability
3. Add meta tags

### From Editor:
4. Polish brand voice
5. Fix grammar and style
6. Strengthen CTAs

## Process
1. **First pass (SEO):** Optimize keywords, check readability
2. **Second pass (Editing):** Polish voice, fix grammar
3. Output: Single combined report + optimized draft
```

**Benefit:** Faster workflow for small teams
**Trade-off:** Less specialized, may miss deep issues

**Time:** 1-2 hours per combined persona

---

### Level 3: Create New Persona (Advanced)

**Use case:** Unique role not covered by existing personas

**How to:** Follow persona template structure

#### Persona Template

```markdown
# Persona: [Persona Name]

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
- **Primary:** `artifacts/[filename].md`
- **Format:** [Markdown / Report / Checklist]
- **Contents:** [Description]

## Success Criteria
✅ [Quality indicator 1]
✅ [Quality indicator 2]
✅ [Quality indicator 3]

## Quality Checklist
- [ ] [Criterion 1]
- [ ] [Criterion 2]
- [ ] [Criterion 3]
- [ ] Constitutional alignment verified

## Common Pitfalls
❌ **Pitfall:** [What to avoid]
✅ **Instead:** [What to do]

## Related Personas
- **Previous:** [Previous persona]
- **Next:** [Next persona]
```

**Time:** 2-4 hours per new persona (including testing)

---

## Real-World Customization Examples

### Example 1: Add Brand Voice Specialist

**Scenario:** Company with strict brand guidelines needs persona to enforce voice consistency

**Customization:**
1. Create new persona: `02-brand-voice-specialist.md`
2. Place between Content Strategist and Writer
3. Responsibilities: Review briefs for brand alignment, ensure tone matches guidelines

**Workflow change:**
```
Before: Strategist → Writer → SEO → Editor
After:  Strategist → Brand Voice Specialist → Writer → SEO → Editor
```

**Result:** Extra quality gate for brand consistency

---

### Example 2: Split Developer Persona by Specialty

**Scenario:** Team has frontend and backend specialists

**Customization:**
1. Copy `03-specialist-developer.md` twice
2. Create `03a-frontend-developer.md` and `03b-backend-developer.md`
3. Specialize responsibilities:
   - Frontend: UI/UX, accessibility, browser compatibility
   - Backend: APIs, database, security, performance

**Workflow change:**
```
Before: Developer (does everything)
After:  Frontend Developer (UI) + Backend Developer (API/DB)
```

**Result:** Parallel development, better specialization

---

### Example 3: Add Accessibility Auditor

**Scenario:** Building product requiring WCAG 2.1 AA compliance

**Customization:**
1. Create new persona: `04b-accessibility-auditor.md`
2. Place in Phase 3 (Review), alongside QA Engineer
3. Responsibilities: WCAG compliance check, keyboard navigation, screen reader testing

**Workflow change:**
```
Before: Developer → QA Engineer → Technical Writer
After:  Developer → QA Engineer → Accessibility Auditor → Technical Writer
```

**Result:** Dedicated accessibility review before documentation

---

### Example 4: Simplify for Solo Practitioner

**Scenario:** Solo developer wants faster workflow

**Customization:**
1. Merge Product Owner + Architect → "Product Designer" (1 persona)
2. Keep Developer
3. Merge QA + Technical Writer → "Quality Reviewer" (1 persona)

**Workflow change:**
```
Before: 5 personas (PO, Arch, Dev, QA, Writer)
After:  3 personas (Designer, Dev, Reviewer)
```

**Result:** Faster workflow, still has quality gates

**Trade-off:** Less specialized review

---

## Creating Prompts for Custom Personas

Once you've created a custom persona, create a corresponding prompt:

### Prompt Template

```markdown
# Prompt: [Persona Name] - [Task Name]

**Persona:** [Persona Name]
**Phase:** [Phase Number] - [Phase Name]
**Purpose:** [One sentence description]

---

## When to Use This Prompt
✅ **Use when:** [Trigger]
❌ **Don't use when:** [Wrong time]

---

## The Prompt Template

\```markdown
You are a [Persona Name]. Your task is to [Task Description].

**Rules:**
1. You must adhere to all principles in CONSTITUTION.md
2. [Domain-specific rule 1]
3. [Domain-specific rule 2]
4. Output must be in [Format] format
5. If unclear, ASK questions before proceeding

**Input Artifacts:**
- [File 1]
- [File 2]
- CONSTITUTION.md

**Output Artifact:**
- artifacts/[filename]

**Context:**
[Variables to fill in]

**Quality Checklist:**
- [ ] [Criterion 1]
- [ ] [Criterion 2]
- [ ] Aligns with CONSTITUTION.md

\```

---

## Example Output
[Show what output looks like]

---

## Related Prompts
- **Previous:** [Previous prompt]
- **Next:** [Next prompt]
```

**Time:** 1-2 hours per prompt

---

## Testing Your Custom Personas

### Validation Checklist

After creating a custom persona:

- [ ] **Role is clear:** Can explain in 1-2 sentences what this persona does
- [ ] **Responsibilities are specific:** Not too vague ("ensures quality") or too narrow ("checks commas")
- [ ] **Success criteria are measurable:** Can tell if persona succeeded
- [ ] **Fits into workflow:** Clear handoff from previous persona, clear output for next
- [ ] **Prompt works:** AI can execute the persona role effectively
- [ ] **Produces value:** Catches issues or adds quality (not just busywork)

### Test Run

1. **Use the persona** on a real project
2. **Document issues:**
   - Was anything confusing?
   - Did AI struggle with any part?
   - Did it catch real issues or just nitpick?
3. **Iterate:**
   - Refine responsibilities
   - Add examples
   - Clarify success criteria
4. **Re-test** until it works smoothly

**Budget:** 2-3 test runs per persona

---

## Common Customization Patterns

### Pattern 1: Add Domain Expertise

**When:** Generic persona needs specialized knowledge

**Example:** Content Writer → Medical Content Writer
- Add: Medical terminology expertise
- Add: Clinical accuracy review
- Add: Citation requirements (peer-reviewed sources)

---

### Pattern 2: Add Compliance Check

**When:** Industry has specific regulations

**Example:** Add "HIPAA Compliance Reviewer" (healthcare)
- Responsibilities: Check for PHI exposure, audit data handling
- Place: Phase 3 (Review)
- Output: Compliance report with CRITICAL/HIGH/MEDIUM issues

---

### Pattern 3: Split by Channel

**When:** Different distribution channels need different approaches

**Example:** Content Writer → Blog Writer + Email Writer + Social Writer
- Each optimized for channel (long-form vs short-form vs visual)
- Each with channel-specific best practices

---

### Pattern 4: Add Performance Optimization

**When:** Performance is critical (e.g., high-traffic sites, mobile apps)

**Example:** Add "Performance Optimizer" (after QA Engineer)
- Responsibilities: Load testing, optimization recommendations
- Place: Phase 3 (Review)
- Output: Performance report, optimization checklist

---

## When NOT to Customize

**Don't customize if:**
- ❌ It's your first project with the framework (learn standard first)
- ❌ You're just adding busy work (personas should add value, not steps)
- ❌ Existing persona would work with minor constitution changes
- ❌ You're avoiding using a persona because it's "inconvenient" (that's often where issues hide)

**Better:** Use standard personas for first 2-3 projects, then customize based on what you learned

---

## Sharing Custom Personas

Created a great custom persona? Share it!

1. **Document thoroughly:**
   - Persona definition
   - Prompt template
   - Example output
   - When to use

2. **Test it:**
   - Use on 2-3 real projects
   - Refine based on results

3. **Contribute:**
   - Open PR to this repo
   - See [CONTRIBUTING.md](../../CONTRIBUTING.md)
   - Help others benefit from your work

**We're building a library of community personas!**

---

## Next Steps

1. **Start with standard personas** - Learn the patterns first
2. **Identify gaps** - What's missing for your domain?
3. **Customize thoughtfully** - Don't add personas just to add them
4. **Test and iterate** - Refine based on real usage
5. **Share if useful** - Help the community

---

**More resources:**
- [Working Solo](./working-solo.md) - Solo practitioner strategies
- [Working with Teams](./working-with-teams.md) - Team collaboration
- [Choosing Your Domain](./choosing-your-domain.md) - Domain selection
- [CONTRIBUTING.md](../../CONTRIBUTING.md) - Submit your custom personas
