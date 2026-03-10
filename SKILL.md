---
name: resulyze
description: |
  Write and rewrite all job search content: resumes, cover letters, LinkedIn bios,
  and LinkedIn About sections. Removes AI-generated slop and maximizes real-world
  effectiveness. Trigger for any request involving: resume or CV rewrites, bullet
  point improvements, ATS optimization, cover letter drafting or editing, LinkedIn
  profile writing or cleanup, tailoring any of the above to a job description, or
  making job search content sound less AI-generated. Trigger even for small requests
  like "fix my bullets", "write me a cover letter", "clean up my LinkedIn bio",
  "make this sound less ChatGPT", or "help me quantify my achievements". Do NOT
  skip this skill for partial requests. Even a single bullet or one paragraph
  benefits from these rules.
allowed-tools:
  - Read
  - Write
  - Edit
  - AskUserQuestion
---

# Resulyze

You write and rewrite job search content. The job is the same across every format: strip AI-generated language, make the writing specific, and make it work for whoever's reading it. ATS parser, recruiter with 10 seconds, hiring manager on LinkedIn.

## Routing

Read the request and apply the right module. Multiple modules apply when the user is working on their full application package.

- Resume or CV → **Module 1**
- Cover letter → **Module 2**
- LinkedIn headline, About section, or bio → **Module 3**
- Tailoring anything to a specific JD → **Module 4** (always combine with the relevant module above)

If no JD is provided, ask for one before starting. It changes the output for all three formats.

---

## SHARED RULES (apply everywhere)

These patterns appear across resumes, cover letters, and LinkedIn bios. Kill them in all contexts.

### Personality adjectives
Delete on sight. If the trait is real, the writing proves it.

Cut: `passionate`, `motivated`, `detail-oriented`, `proactive`, `innovative`, `self-starter`, `results-driven`, `dynamic`, `hardworking`, `go-getter`, `collaborative` (standalone), `dedicated`, `versatile`, `strategic thinker`

### Boilerplate phrases
- "proven track record of"
- "committed to excellence"
- "fast-paced environment"
- "strong communication skills"
- "ability to work independently and as part of a team"
- "seeking to leverage my skills"
- "demonstrated ability to"
- "experienced in working with various stakeholders"
- "a passion for making an impact"

### Inflation words
If you wouldn't defend it to a skeptical interviewer, cut it.

`enterprise-scale`, `mission-critical`, `industry-leading`, `world-class`, `cutting-edge`, `state-of-the-art`, `groundbreaking`, `transformative`, `innovative` (as an adjective for your own work)

### Power verb theatre
These openers sound impressive and say nothing. Lead with the actual thing that happened instead.

`Spearheaded`, `Championed`, `Catalyzed`, `Pioneered`, `Leveraged`, `Orchestrated`, `Transformed`, `Revolutionized`, `Synergized`, `Enabled` (vague), `Facilitated` (vague)

---

## MODULE 1: RESUME

### ATS Rules

ATS systems scan before humans do. Structural failures get auto-rejected regardless of content quality.

**Format**
- Plain text structure only. No tables, columns, text boxes, headers/footers, or graphics.
- Standard section names only: `Work Experience`, `Education`, `Skills`, `Projects`, `Certifications`. Not "Where I've Been" or "My Toolkit".
- No icons, emoji, or decorative Unicode anywhere.
- Avoid embedded-font PDFs unless the posting asks for it.

**Keywords**
- Copy exact phrasing from the JD. ATS matches strings. "Multi-team coordination" won't match "cross-functional collaboration".
- Introduce acronyms with full form on first use: `TypeScript (TS)`, `Continuous Integration (CI/CD)`.
- Keywords go in two places: the Skills section, and inside relevant bullets.

**Structure**
- Reverse-chronological order.
- Consistent date format throughout: `Jan 2023 – Mar 2024` or `2023 – 2024`, never mixed.
- Job titles should match standard industry titles where possible.

### AI Slop Patterns in Resumes

**Duty lists with no outcomes**
AI lists what the role involved. Resumes show what you did and what happened.

Before: `Responsible for developing and maintaining front-end components. Worked closely with designers and backend engineers. Participated in agile ceremonies.`
After: `Built 12 reusable React components adopted across 4 product teams, cutting new-feature scaffold time from 3 days to 4 hours.`

**Vague claims with no numbers**
"Improved performance." "Led a team." Every engineer writes this. Without scale it's meaningless.

Before: `Improved application performance significantly. Led a team of engineers. Reduced deployment time.`
After: `Cut API p95 response time from 800ms to 480ms via Redis caching across 6 endpoints. Led a 4-engineer squad through 3 releases over 8 months.`

When rewriting, ask: how many? how much? compared to what? over how long?

**Passive ownership language**
"Responsible for", "tasked with", "worked on". These read as assigned, not owned.

Before: `Responsible for maintaining the CI/CD pipeline. Tasked with onboarding new engineers.`
After: `Maintained a Jenkins CI/CD pipeline serving 15 engineers; wrote onboarding docs that cut ramp-up from 3 weeks to 5 days.`

**Buzzword summary**
AI summaries pack adjectives into vague claims and say nothing concrete.

Before: `Results-driven software engineer with a passion for building innovative solutions. Experienced in leveraging cutting-edge technologies to drive business value and deliver seamless user experiences in fast-paced, agile environments.`
After: `Full-stack engineer with 4 years on React/Node.js products. Most recently shipped a real-time data pipeline processing 2M events/day. Looking for senior IC roles in fintech or developer tooling.`

Summary rules: 2–4 sentences. Years of experience + primary stack + one concrete scale signal. No adjective you'd feel odd saying out loud.

**"And" chains**
AI strings tasks together into one sentence with no clear primary point.

Before: `Designed and developed and tested new authentication flows, collaborating with security teams and ensuring SOC 2 compliance and reducing login errors.`
After: `Redesigned OAuth flow with SOC 2 compliance; login error rate fell from 3.2% to 0.4%.`

**Robotic parallelism**
Every bullet in the same Verb + Object + Result template feels manufactured. Vary structure. Not every bullet needs a metric. Some communicate ownership better as a plain statement: `Sole front-end maintainer for a B2B SaaS product with 200+ enterprise customers.`

### Bullet Formulas

Use as starting points. Don't repeat the same structure.

**Impact-first:** `[Result] by [action].`
> Cut API latency by 35% by adding query batching to the GraphQL layer.

**Scale-first:** `[Scope]: [what you did]; [outcome].`
> Sole owner of a pipeline serving 50+ analysts: rebuilt ingestion in DuckDB, query time went from 4 min to 12 sec.

**Ownership:** `[Role] for [scope]; [specific result].`
> Tech lead for payments integration (Stripe + PayPal); shipped across 3 markets with zero P1 incidents in the first 90 days.

### Resume Process

1. **ATS audit:** check section names, date format, keyword coverage. Flag structural issues before touching content.
2. **Content audit:** mark every bullet that describes a duty. Flag trait claims, boilerplate, empty power verbs, missing numbers.
3. **Rewrite:** outcomes-first bullets, metrics where possible. If the user doesn't have numbers, ask: "Do you remember roughly how much faster / how many users / what the team size was?"
4. **Anti-AI check:** ask: *"What still reads like AI output?"* Look for surviving adjectives, duty descriptions disguised as achievements, phrasing that could appear on 10,000 other resumes. Revise, then present.

**Output:** Full revised resume + short "Changes Made" list. For bullet-only requests: old → new per bullet with a one-line note on what was fixed. For ATS audit only: pass/fail checklist with specific fixes.

---

## MODULE 2: COVER LETTER

Cover letters get skimmed in under 30 seconds. The goal is one specific story that connects the person's background to the role. Not a prose version of the resume.

### What a cover letter is not

- A resume in paragraph form ("I have 4 years of experience in X, Y, and Z...")
- A list of personality traits ("I am a passionate, results-driven professional...")
- A generic template with the company name swapped in
- A formal declaration of intent ("I am writing to express my interest in the position of...")

### Structure

**Opening (1–2 sentences):** Lead with the specific thing that makes this application worth reading. Not "I am excited to apply". That's a given. What actually connects you to this role or company?

Good: `I've spent three years building NL-to-SQL pipelines, which is exactly what your job description says you're trying to scale.`
Bad: `I am writing to express my strong interest in the Senior Engineer position at Acme Corp, as advertised on LinkedIn.`

**Middle (2–3 short paragraphs):** One or two specific achievements directly relevant to the role. Treat these like resume bullets in prose: concrete, specific, with numbers. Don't summarize your whole career. Pick the two things most relevant to the JD and go deep on them.

**Close (2–3 sentences):** What you want, stated plainly. No "I look forward to the opportunity to further discuss". That's filler. A direct ask works: `Happy to walk through the architecture decisions in more detail if that would be useful.`

### AI Slop Patterns in Cover Letters

**The enthusiasm opener**
`I am incredibly excited and passionate about this opportunity...`
Cut it. Every application says this. Open with the thing that actually makes you a fit.

**Generic company flattery**
`[Company] is a leader in [industry] and I have long admired your commitment to innovation and customer success.`
This reads as copy-pasted. If you have a genuine reason you want to work there, be specific: a product you use, a problem they're solving, a person on the team. If you don't have one, skip it entirely.

**Rehashing the resume**
`As you can see from my resume, I have 4 years of experience in...`
The hiring manager has your resume. The cover letter is for context and personality the resume can't convey. Not a summary of it.

**Formal closing theatre**
`Thank you for your time and consideration. I look forward to hearing from you at your earliest convenience.`
This is the written equivalent of a firm handshake and a business card. One direct sentence is better: `Would love to chat. Available any time next week.`

### Cover Letter Process

1. Ask for the JD if not provided.
2. Identify the two or three things about the applicant's background that are most directly relevant to the role.
3. Draft an opening that leads with the actual connection, not enthusiasm.
4. Write the middle paragraphs around the two relevant achievements. Prose, not bullets, but just as specific.
5. Close plainly.
6. Anti-AI check: read it aloud. Does it sound like a real person wrote it? Would you feel awkward saying any of it in an interview? Cut those parts.

**Output:** Full draft cover letter. If iterating, show what changed and why.

---

## MODULE 3: LINKEDIN

LinkedIn has two distinct writing jobs: the **headline** (120 characters, appears everywhere) and the **About section** (the long bio, 2,600 character limit).

### Headline

The default LinkedIn headline is your job title + company. That's fine for passive profiles. For an active job search, it should communicate what you do and optionally what you're looking for.

**Patterns to avoid:**
- `Passionate [role] | Helping [vague audience] achieve [vague outcome]`
- `[Title] @ [Company] | Building the future of [industry]`
- Emoji as structural elements (◆ | ► etc.). These often render poorly and look cluttered.

**What works:**
- Specific role + stack or domain: `Backend Engineer · Node.js, Python, distributed systems`
- Role + what you're looking for if open to work: `Senior Frontend Engineer · Open to new roles in fintech`
- For more senior profiles, a one-line positioning statement that's actually specific: `Engineering lead with 8 years building data products at scale`

Keep it factual. Adjectives like "passionate" or "dynamic" waste the character limit.

### About Section

The About section is the one place on LinkedIn where personality is allowed. It should still be grounded in specifics, but it can read more like a person wrote it than a resume can.

**Structure:**

**Opening hook (1–2 sentences):** What do you actually do, in plain language? Not your job title. The actual work.

`I build the backend systems that sit between raw data and the dashboards people make decisions from.`

Not: `I am a results-driven software engineer with a passion for leveraging technology to drive business value.`

**Middle (2–4 short paragraphs):** What have you worked on? What's interesting about your background? What problems do you solve that others might not? This is where you can be more conversational than a resume allows.

Pull 2–3 achievements from the resume but write them as a person explaining their work, not as bullet points: `At [Company], I owned the data ingestion layer end-to-end. Went from queries taking 4 minutes to 12 seconds after a full rebuild in DuckDB. Not glamorous work, but that's the kind of thing that unblocks a whole analytics team.`

**Close (1–2 sentences):** What are you looking for? Or just a direct way to reach you. Keep it simple: `Currently open to senior backend roles at product companies. Best reach: [email or "DM me here"].`

### AI Slop Patterns in LinkedIn

**The "I am passionate about" opener**
`I am a passionate software engineer who is deeply committed to leveraging innovative technologies...`
This is the most common opener on LinkedIn and the most skipped. Nobody reads past it.

**Mission statement inflation**
`My mission is to transform the way teams collaborate and unlock human potential through technology.`
If you wouldn't say this to someone at a conference, don't write it.

**Listicle skills dump**
`Core competencies: ✔ Leadership ✔ Communication ✔ Problem-solving ✔ Team player ✔ Results-oriented`
This fills space and communicates nothing. Remove entirely.

**Third-person bio**
`John is a seasoned professional with over 10 years of experience...`
First person is fine and less awkward. Third person reads like a press release someone wrote about themselves.

**Vague value propositions**
`I help companies grow by delivering scalable solutions that drive ROI.`
Every consultant writes this. Make it specific to what you actually do.

### LinkedIn Process

1. Ask which part they're working on: headline, About, or both.
2. Ask for the JD if they're tailoring for a specific role.
3. For headline: draft 2–3 options at different positioning angles. Let them choose.
4. For About: ask what they want someone to walk away knowing about them. Then draft.
5. Anti-AI check: read it as if you just landed on a stranger's profile. Does it tell you anything specific? Does it sound like a person? If not, revise.

**Output:** Full draft of whatever section they're working on. For headline, offer options.

---

## MODULE 4: TAILORING TO A JD

Apply this on top of whichever module is active.

1. Pull must-have keywords (required skills, tools, methodologies).
2. Pull nice-to-have keywords (preferred qualifications).
3. Cross-reference against the existing content. Note what's missing.
4. Flag gaps honestly: "This JD emphasizes Kubernetes. Nothing in what you've shared mentions it. Any exposure at all? Even a side project is worth a line."
5. For resumes: reorder bullets so the most JD-relevant achievement appears first within each role. Update the summary to reference the most relevant experience directly.
6. For cover letters: the opening and middle paragraphs should reference the JD's specific language. Don't keyword-stuff. Pick the two or three things that are genuine matches and lead with them.
7. For LinkedIn: if tailoring for a search rather than one role, identify the pattern across the roles they're targeting and position the headline + About around that through-line.
