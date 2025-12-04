# Guide: Working Solo with AI Workflow Orchestrator

This guide shows how solo practitioners use personas effectively with AI tools.

---

## The Core Idea

When working alone, **you invoke each persona sequentially** to get multiple expert perspectives on your work:

```
You → Content Strategist persona → Creates brief
You → Review brief → Approve or iterate
You → Content Writer persona → Creates draft
You → SEO Specialist persona → Reviews and optimizes
You → Fact Checker persona → Verifies claims
You → Editor persona → Final polish
```

**Key insight:** Each persona gives you a different lens to evaluate your work. You're not just asking AI to "write an article" - you're using specialized perspectives to ensure quality.

---

## How to Invoke Personas

### Method 1: AI Coding Tools (Claude Code, Cursor, Replit)

**Best for:** Software development, integrated workflow

1. Add the persona file and prompt to your project
2. Reference in your AI conversation: "Act as the Product Owner persona from personas/01-product-owner.md"
3. AI reads the persona definition and executes that role
4. Review output, iterate if needed

**Example:**
```
You: "Act as Product Owner (personas/01-product-owner.md) and create a PRD for user authentication."
AI: [Asks clarifying questions, then produces PRD]
You: "Good, now act as Solutions Architect and create the tech spec."
```

### Method 2: Copy-Paste (ChatGPT, Claude web)

**Best for:** Content writing, quick workflows

1. Copy the prompt content from `prompts/phase-X/prompt-name.md`
2. Fill in the template variables ([PROJECT_TYPE], [TOPIC], etc.)
3. Paste into ChatGPT/Claude
4. AI executes persona role and produces artifact

**Example:**
```
1. Open prompts/phase-1-planning/1.1-content-brief.md
2. Copy the entire prompt
3. Replace [TOPIC] with "How to choose project management software"
4. Paste into Claude/ChatGPT
5. Review generated brief
```

### Method 3: Custom AI Agents (if supported)

**Best for:** Repeated workflows, team sharing

1. Create custom GPT/Agent with persona definition
2. Save with persona name ("Content Strategist", "QA Engineer")
3. Invoke when needed
4. Maintains consistent persona behavior

---

## Solo Workflow Example: Blog Post

### Step 1: Planning (You as Content Strategist)
```
Time: 30 minutes
Action: Use prompt 1.1-content-brief.md
Output: artifacts/01-content-brief.md

What you do:
- Copy prompt, fill in topic and audience
- AI (as Content Strategist) asks clarifying questions
- You answer questions
- AI produces brief
- You review and approve (or iterate)
```

### Step 2: Drafting (You as Content Writer)
```
Time: 2 hours
Action: Use prompt 2.1-first-draft.md
Output: artifacts/02-draft-v1.md

What you do:
- Copy prompt, reference the brief
- AI (as Content Writer) creates first draft
- You review for brand voice and structure
- If major issues: iterate. If minor: move to next phase
```

### Step 3: SEO (You as SEO Specialist)
```
Time: 30 minutes
Action: Use prompt 3.1-seo-optimization.md
Output: artifacts/03-seo-report.md, draft-v2

What you do:
- AI (as SEO Specialist) analyzes keyword usage, readability
- AI produces optimization report
- You review CRITICAL and HIGH issues
- AI applies fixes to produce draft-v2
```

### Step 4: Fact-Checking (You as Fact Checker)
```
Time: 45 minutes
Action: Use prompt 3.2-fact-checking.md
Output: artifacts/04-fact-check-report.md, draft-v3

What you do:
- AI (as Fact Checker) identifies all factual claims
- AI verifies claims (or flags as unverifiable)
- You review any flagged claims
- AI adds citations and produces draft-v3
```

### Step 5: Editing (You as Editor)
```
Time: 30 minutes
Action: Use prompt 3.3-editing.md
Output: artifacts/05-editing-report.md, draft-v4-FINAL

What you do:
- AI (as Editor) reviews voice, flow, grammar
- AI produces editing report
- You review recommendations
- AI applies fixes to produce final draft
```

### Step 6: Publishing (You as Content Strategist)
```
Time: 20 minutes
Action: Use prompts 4.1 and 4.2
Output: Meta tags, distribution plan

What you do:
- AI creates meta tags and distribution plan
- You copy meta tags to CMS
- You execute distribution plan
- Publish!
```

**Total time:** ~5 hours for 1,800-word blog post

---

## How to Avoid Bias When Self-Reviewing

When you're both creator and reviewer, bias is a risk. Here's how personas help:

### Problem: Confirmation Bias
**Issue:** You overlook your own mistakes because you "know what you meant"

**Solution:** Each persona has a specific focus
- **SEO Specialist:** Only looks at keywords and readability (doesn't care about your original intent)
- **Fact Checker:** Only verifies claims (doesn't care if it ruins your narrative)
- **Editor:** Only cares about clarity and grammar (will challenge your "clever" phrasing)

### Problem: Attachment to Your Work
**Issue:** You don't want to delete paragraphs you spent time writing

**Solution:** Personas are ruthless
- QA Engineer will flag bad code even if it "mostly works"
- Editor will cut fluff even if it sounds nice
- You judge the feedback objectively: "Is this valid criticism?"

### Problem: Missing Your Own Errors
**Issue:** You read what you meant to write, not what you actually wrote

**Solution:** Fresh persona perspective
- Each persona reads the artifact fresh
- No context about your intentions
- Catches what you can't see because you're too close

---

## Tips for Effective Solo Work

### 1. Don't Skip Personas
**Temptation:** "I'll just write and publish, no need for SEO review"
**Reality:** The persona you skip is usually where the issues are

**Better:** Use all personas but adjust depth
- Quick project: Brief review from each persona
- Important project: Deep review from each persona

### 2. Use Versioned Artifacts
**Temptation:** Keep editing the same file (draft.md)
**Reality:** You lose iteration history and can't compare versions

**Better:** Version your artifacts
```
artifacts/02-draft-v1.md  (after writing)
artifacts/02-draft-v2.md  (after SEO)
artifacts/02-draft-v3.md  (after fact-check)
artifacts/02-draft-v4-FINAL.md  (after editing)
```

Benefit: Can revert if a revision makes things worse

### 3. Take Breaks Between Personas
**Temptation:** Run through all personas in one session
**Reality:** Mental fatigue makes you less critical

**Better:** Spread over 2-3 work sessions
- Session 1: Strategist + Writer (2-3 hours)
- Session 2: SEO + Fact-check (1-2 hours)
- Session 3: Editor + Publishing (1 hour)

Fresh eyes catch more issues.

### 4. Document Your Decisions
**Temptation:** Accept or reject feedback without explanation
**Reality:** Future you won't remember why you made that choice

**Better:** Use workflow-log.md
```markdown
## SEO Specialist Feedback (Line 234)
**Issue:** Keyword density too high (2.8%)
**Decision:** ACCEPTED - Removed 5 instances
**Reasoning:** Makes sense, was feeling stuffed

## Editor Feedback (Line 567)
**Issue:** Suggested removing this paragraph
**Decision:** REJECTED - Paragraph is essential for context
**Reasoning:** Editor focused on brevity but this explains key concept
```

### 5. Trust the Process
**Temptation:** "This is taking too long, I'll just publish"
**Reality:** Quality takes time, but saves time later (fewer rewrites, better results)

**Better:** Embrace the workflow
- First time: Feels slow (learning curve)
- Second time: Smoother (familiar pattern)
- Third+ time: Fast (muscle memory)

Plus: Higher quality = better performance = less need for rewrites

---

## Common Solo Practitioner Questions

### Q: Do I really need all 5 personas for every project?

**A:** Depends on project importance

**Quick blog post (low stakes):**
- Strategist → Writer → Editor (skip SEO and fact-check)
- ~2 hours

**Important article (high stakes):**
- All 5 personas, thorough reviews
- ~5-6 hours

**Rule of thumb:** More visibility/importance = more personas

---

### Q: Can I combine personas to save time?

**A:** Yes, but carefully

**Good combinations:**
- SEO + Editor (for short content)
- Strategist + Writer (for simple content)

**Bad combinations:**
- Writer + Editor (same phase, defeats the purpose)
- QA + Developer (in software - defeats checks and balances)

**Better:** Use all personas but adjust review depth

---

### Q: What if AI disagrees with me?

**A:** You're the orchestrator - you judge

**Process:**
1. AI (as persona) provides feedback
2. You evaluate: "Is this valid criticism?"
3. If valid: Accept and apply fix
4. If invalid: Reject with reasoning (document why)

**Example:**
```
Editor: "Remove this technical section - too complex"
You: "REJECTED - Audience is technical, they need this detail"
[Document in workflow-log.md]
```

You're using AI for expertise, not following blindly.

---

### Q: How do I know if my workflow is working?

**A:** Track these signals

**Good signs:**
- Personas catch issues you missed
- Quality improves from v1 to final
- Fewer post-publication edits needed
- Better engagement/performance metrics

**Bad signs:**
- Personas produce generic feedback
- You reject most suggestions
- Still finding errors after "final" draft
- No measurable improvement

**If bad:** Refine your prompts, be more specific in context

---

## Tools for Solo Work

### Recommended Stack

**AI Tools:**
- **Claude Code / Cursor:** Best for software development
- **ChatGPT Plus / Claude Pro:** Best for content writing
- **Free tier:** Works but slower

**File Organization:**
- **Simple:** Local folder with artifacts/
- **Better:** Git repo (track versions, undo changes)
- **Team-ready:** GitHub (even for solo work - backup + versioning)

**Optional:**
- **Grammarly:** Catches errors AI might miss
- **Hemingway Editor:** Readability scores
- **Markdown editor:** Typora, Obsidian, VS Code

---

## Next Steps

1. **Choose your domain** - [Domain selection guide](./choosing-your-domain.md)
2. **Pick a project** - Start with something small to learn the workflow
3. **Set up your workspace** - Create artifacts/ folder, copy constitution
4. **Invoke first persona** - Use Phase 1 prompt for your domain
5. **Follow the workflow** - Trust the process, don't skip personas

**Remember:** First time is slowest. By the third project, it'll feel natural.

---

**More resources:**
- [Working with Teams](./working-with-teams.md) - When you add collaborators
- [Customizing Personas](./customizing-personas.md) - Adapting for your needs
- [Choosing Your Domain](./choosing-your-domain.md) - Which domain to use
