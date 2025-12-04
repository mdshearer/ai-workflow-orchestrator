# Guide: Choosing Your Domain

This guide helps you select the right domain for your work.

---

## Quick Decision Tree

```
┌─────────────────────────────────────────┐
│  What are you creating?                 │
└─────────────────────────────────────────┘
           ↓
    ┌──────┴──────┐
    │             │
Software/Apps   Written Content
    │             │
    ↓             ↓
[Software]    Blog/Marketing?
              │           │
            Blog      Marketing/Sales
              ↓           ↓
          [Content]   [Content]
                      (marketing template)
```

---

## Domain Comparison

| Factor | Software Development | Content Writing |
|--------|---------------------|-----------------|
| **Best For** | Apps, APIs, tools | Blogs, marketing, docs |
| **Workflow** | Iterative (build→test→refine) | Linear (plan→draft→publish) |
| **Personas** | 5 (PO, Architect, Dev, QA, Writer) | 5 (Strategist, Writer, SEO, Fact-checker, Editor) |
| **Timeline** | Days to weeks | Hours to days |
| **Iteration Style** | Heavy iteration between phases | Targeted revisions within phases |
| **Key Deliverable** | Working software | Published content |

---

## When to Use Software Development

✅ **Use when building:**
- Web or mobile applications
- APIs and microservices
- CLI tools or scripts
- Bots or automation
- Internal tools

✅ **Key indicators:**
- Need to write and test code
- Require technical architecture
- Security and performance matter
- Iterative development cycles
- Multiple technical stakeholders

---

## When to Use Content Writing

✅ **Use when creating:**
- Blog posts or articles
- Marketing content (landing pages, emails)
- Product documentation
- Technical tutorials
- Thought leadership pieces

✅ **Key indicators:**
- Primary deliverable is text
- SEO or brand voice matters
- Target audience is readers/users
- Publication deadline exists
- Need fact-checking or editing

---

## Can I Use Multiple Domains?

**Yes!** Many projects span domains:

### Example: Building a SaaS Product
1. **Software Development:** Build the application
   - Use: Product Owner → Architect → Developer → QA → Technical Writer
2. **Content Writing:** Create marketing site & blog
   - Use: Content Strategist → Writer → SEO → Editor
3. **Content Writing (Technical):** Write API documentation
   - Use: Technical constitution + Technical Writer persona

Each domain has its own constitution and workflow.

---

## Can I Mix Personas Across Domains?

**Yes!** Personas are modular. Pick what you need:

### Example: Technical Blog Post
- **Content Strategist** (content) - Create brief
- **Developer** (software) - Write code examples
- **SEO Specialist** (content) - Optimize for search
- **Technical Writer** (software) - Ensure technical accuracy
- **Editor** (content) - Polish and publish

Adapt the framework to your needs.

---

## What If My Domain Isn't Listed?

You have 3 options:

### Option 1: Adapt an Existing Domain
Most work fits into software or content with customization:
- **Video production?** Adapt content-writing (replace writing with filming)
- **Product design?** Adapt software-development (replace developer with designer)
- **Event planning?** Adapt content-writing (replace publishing with executing)

### Option 2: Create a Custom Domain
Use the patterns from existing domains:
1. Define 4-6 personas (strategist, creator, specialist, reviewer, finalizer)
2. Create 8-12 prompts across 4 phases
3. Build constitution templates for your project types
4. See [CONTRIBUTING.md](../../CONTRIBUTING.md) for guidelines

### Option 3: Request a New Domain
[Open an issue](https://github.com/mdshearer/ai-workflow-orchestrator/issues) requesting:
- Domain name (e.g., "Grant Writing", "Video Production")
- Target users and use cases
- Why existing domains don't fit

We're building **grant-writing** next based on demand.

---

## Still Unsure? Ask These Questions

### Question 1: What's the final deliverable?
- **Code/software** → Software Development
- **Text/content** → Content Writing
- **Both** → Use both domains
- **Neither** → May need custom domain

### Question 2: What's the primary skill required?
- **Programming** → Software Development
- **Writing** → Content Writing
- **Design** → Adapt software or create custom
- **Other** → Explore custom domain

### Question 3: What's your workflow style?
- **Iterative (build, test, refine, repeat)** → Software Development
- **Linear (plan, create, review, ship)** → Content Writing
- **Combination** → Use both or create custom

### Question 4: What personas do you need?
- **Technical roles (developer, QA, architect)** → Software Development
- **Content roles (writer, editor, SEO)** → Content Writing
- **Mix of both** → Use multiple domains
- **Unique roles** → Create custom domain

---

## Next Steps

Once you've chosen your domain:

1. **Read the domain README**
   - [Software Development](../../domains/software-development/)
   - [Content Writing](../../domains/content-writing/)

2. **Choose a constitution template**
   - Software: internal-tool, client-app, or ai-agent
   - Content: blog, marketing, or technical

3. **Start with Phase 1**
   - Software: [Product Owner PRD](../../domains/software-development/prompts/phase-1-planning/1.1-product-owner-prd.md)
   - Content: [Content Brief](../../domains/content-writing/prompts/phase-1-planning/1.1-content-brief.md)

4. **Follow the workflow**
   - Software: [Workflow Overview](../../domains/software-development/workflow/workflow-overview.md)
   - Content: [Workflow Overview](../../domains/content-writing/workflow/workflow-overview.md)

---

**Still have questions?** Check out:
- [Working Solo Guide](./working-solo.md) - Using personas as an individual
- [Working with Teams Guide](./working-with-teams.md) - Team collaboration strategies
- [Customizing Personas Guide](./customizing-personas.md) - Adapting personas for your needs
