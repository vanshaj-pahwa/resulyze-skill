# resulyze

A Claude skill for writing and rewriting job search content: resumes, cover letters, and LinkedIn bios, without the AI slop.

---

**What it covers**

- **Resume / CV:** ATS formatting rules, bullet rewrites, summary cleanup, JD tailoring
- **Cover letters:** structure, opening hooks, cutting generic filler, matching to a role
- **LinkedIn:** headline options, About section drafts, killing mission-statement inflation

One skill, one install, the whole application package.

---

**Install**

**Claude.ai (no setup required)**

1. Download this repo as a ZIP (click **Code > Download ZIP** on GitHub)
2. Go to [claude.ai](https://claude.ai)
3. Open **Settings > Customize > Skills**
4. Upload the ZIP

That's it. Claude picks it up immediately.

**Claude Code / CLI**

Drop the `resulyze/` folder into your Claude skills directory:

```
~/.claude/skills/resulyze/
└── SKILL.md
```

Claude picks it up on next load.

---

**Usage**

**Claude.ai**

Paste whatever you're working on and ask Claude to improve it. The skill triggers automatically for requests like:

- "Rewrite my resume"
- "Fix my bullets"
- "Write me a cover letter for this role"
- "Clean up my LinkedIn About section"
- "Make this sound less ChatGPT"
- "Optimize for ATS"
- "Tailor this to [job description]"

If you have a job description, paste it alongside your content. All three formats improve significantly with one.

**Claude Code / CLI**

Use the `/resulyze` slash command to trigger the skill, then describe what you need:

```bash
claude
> /resulyze rewrite my resume and optimize for ATS
> /resulyze fix these bullets: [paste bullets]
> /resulyze write a cover letter for this role: [paste JD]
> /resulyze clean up my LinkedIn About section: [paste text]
```

---

**What gets fixed**

**Resume**
- Duty lists → achievement bullets with outcomes and numbers
- Power verb openers ("Spearheaded", "Catalyzed") → plain language with results
- Passive constructions ("Responsible for") → ownership statements
- Personality adjectives ("passionate", "detail-oriented") → deleted
- Buzzword summaries → 2-4 sentences with actual experience signals
- ATS issues: section names, date format inconsistencies, keyword gaps, structural problems

**Cover letter**
- Generic enthusiasm openers → specific connection to the role
- Resume rehash in prose → 1-2 relevant achievements, written as a person explaining their work
- Formal closing theatre → one direct sentence
- Company flattery with no specifics → either cut or made concrete

**LinkedIn**
- "I am passionate about" openers → what you actually do, in plain language
- Mission statement inflation → specific positioning
- Listicle skills dumps → removed
- Third-person bios → first-person rewrites
- Vague value propositions → grounded in what you've actually built

---

**Example (resume bullet)**

**Before:**
> Spearheaded the development of scalable microservices, leveraging cutting-edge technologies to drive business value in a fast-paced, agile environment.

**After:**
> Migrated a monolith to 6 microservices; deploy time dropped from 40 minutes to 7.

---

**Example (LinkedIn About opener)**

**Before:**
> I am a passionate software engineer deeply committed to leveraging innovative technologies to deliver seamless, impactful solutions that drive business growth.

**After:**
> I build the backend systems that sit between raw data and the dashboards people make decisions from.

---

**Contributing**

PRs welcome. Useful additions: before/after examples for non-engineering roles (PM, design, marketing), additional ATS edge cases, or LinkedIn headline formulas for specific industries.
