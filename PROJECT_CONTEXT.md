# NgobrolQA Project Context

Use this document to onboard quickly into the NgobrolQA project. It covers the website, infrastructure, conference materials, and key decisions made so far.

---

## Owner

**Aditya Mirza Bahari**
- President, IDSTB (Indonesia Software Testing Board)
- Lead QA, Shopee (Sea Group)
- Creator, NgobrolQA (QA Community & Podcast)
- Member, ISQA (Indonesia Software Quality Assurance)
- ISTQB Certified Practitioner
- Host, NgobrolQA Podcast
- Email: ngobrolqa@gmail.com
- LinkedIn: https://id.linkedin.com/in/adityamirzabahari

---

## Repository & Hosting

- **Repo:** https://github.com/ngobrolqa/ngobrolqa.git
- **Branch:** `main` (production)
- **Hosting:** GitHub Pages with custom domain
- **Domain:** `ngobrolqa.com` (configured via `CNAME` file)
- **Tech stack:** Pure HTML/CSS/JS (no framework, no build step). Each page is a standalone `.html` file.

---

## Website Structure

### Live Pages (root directory)

| File | URL | Purpose |
|------|-----|---------|
| `index.html` | ngobrolqa.com | Homepage with feature cards, NgobrolQA Insights section, About |
| `qa-skill-framework.html` | ngobrolqa.com/qa-skill-framework | The core framework: 5 Stages of QA Growth + 4 Skill Dimensions with full stage progression |
| `qa-self-assessment.html` | ngobrolqa.com/qa-self-assessment | 20-question self-assessment across 4 dimensions, generates radar chart + personalized results |
| `qa-learning-plan.html` | ngobrolqa.com/qa-learning-plan | Curated learning paths by persona and stage |
| `consult.html` | ngobrolqa.com/consult (old `/QA_Consult` still redirects) | Consultation page for individual/company QA challenges |
| `qa-career-compounding.html` | ngobrolqa.com/qa-career-compounding | NgobrolQA Career Compounding Theory (article-style page) |
| `ctfl-mock-exam.html` | ngobrolqa.com/ctfl-mock-exam (old `/CTFL_Mock_Exam` still redirects) | ISTQB CTFL v4.0 mock exam: register, pick a sample set (A-D) or a random mix, timed 40-question exam, instant scoring + review, team leaderboard |

### User Journey (intended flow)

```
Home → Framework → Assessment → Learning → Consult
                                              ↑
Career Compounding Theory (accessible via Insights section on homepage
                           and "See the Bigger Picture" CTA on Framework page)
```

### Other files

| File/Folder | Purpose |
|-------------|---------|
| `ngobrolqa-logo.png` | Logo used across all pages |
| `CNAME` | GitHub Pages custom domain config (contains: `ngobrolqa.com`) |
| `docs/` | Early framework drafts (Markdown): `Framework_Complete.md`, `Framework_Draft.md`, `Self_Assessment_Detailed.md` |
| `_archive/` | Old v1 framework files |
| `ctfl-exam/data/questions.json` | Static question bank for `ctfl-mock-exam.html` (question text/options only, no answers — answer key lives only in a private tab of the spreadsheet, read by the Apps Script backend) |
| `ctfl-exam/apps-script/` | `Code.gs` (backend: register/grade/leaderboard via a Google Sheet) + deployment `README.md` |

---

## Key Concepts & Terminology

### NgobrolQA Skill Acquisition Model

Adapted from the Dreyfus Model (1980), rebranded with NgobrolQA's own terminology:

| Stage | Dreyfus Equivalent | Description |
|-------|--------------------|-------------|
| **Starter** | Novice | Just beginning, follows rules |
| **Practitioner** | Advanced Beginner | Building experience, recognizes patterns |
| **Professional** | Competent | Plans, prioritizes, seeking direction |
| **Leader** | Proficient | Sees the whole system, leads and mentors |
| **Industry** | Expert | Shapes the profession, intuition and innovation |

**Important:** All pages and slides use NgobrolQA names (Starter/Practitioner/Professional/Leader/Industry), NOT Dreyfus names. The Dreyfus Model is only credited as the academic source, never used as the primary terminology.

### 4 Skill Dimensions

Every QA professional is assessed across these 4 areas:

1. **Testing Fundamentals** (Test Design, Execution, Defect Management, Test Analysis)
2. **Technical Depth** (Automation, API, Performance, AI-Assisted Testing, AI System Testing, Security)
3. **Quality Thinking** (Risk-Based Thinking, Root Cause Analysis, Prevention, Strategy, Metrics)
4. **Influence & Impact** (Collaboration, Communication, Ownership, Leadership, Domain Expertise)

### Career Compounding Theory (NgobrolQA Original)

A theory about QA career growth over 20+ years, compounding across 4 domains:

1. **Fundamentals** (core testing knowledge, slowest but most enduring)
2. **Market** (what the industry wants now, fast but can expire)
3. **Future** (not mainstream yet, your edge when timing is right)
4. **Others** (wildcard: soft skills, resilience, unique experiences)

The page features 6 interactive personas: Rina (Balanced), Budi (Single Domain), Junior QA, Stuck Manager, Career Switcher, AI Early Adopter.

---

## Backend / Integrations

### Google Sheets (Form Data)

Both forms submit to the same Google Sheet but different tabs:
- **Sheet ID:** `1_2w2iLlNv_Mv6cP2eMfUzO6OBpKFJheSiNHkO0enj_8`
- **Assessment tab:** "Result"
- **Consult tab:** "Consult"

### Google Apps Script (Two separate projects)

1. **NgobrolQA-Assessment** (for `qa-self-assessment.html`)
   - Deployed URL: `https://script.google.com/macros/s/AKfycbwxJ9cH9b2H_j6CIn8QdP75XiYHUq9-DqcLP6zoFy_6Y7bo00UIPkP5Su1p5lIFBcjD9g/exec`
   - Targets "Result" tab
   - Includes reCAPTCHA server-side verification

2. **NgobrolQA-Consult** (for `consult.html`)
   - Deployed URL: `https://script.google.com/macros/s/AKfycbzzq3z8Pfe4sbP2vv4byxRP5tIrWBweE9EKaJewiNcaJVL6xrZsn--Ddo9pve1DNDsgug/exec`
   - Targets "Consult" tab
   - Includes reCAPTCHA server-side verification

3. **NgobrolQA-CTFL-Exam** (for `ctfl-mock-exam.html`) — source kept in-repo at `ctfl-exam/apps-script/Code.gs`
   - Deployed URL: _not yet deployed — see `ctfl-exam/apps-script/README.md`_
   - Targets "CTFL_Registrations" and "CTFL_Results" tabs (auto-created)
   - Reads the private answer key (sheet tab `CTFL_AnswerKey`) and the passwords (Script Properties) server-side; grades submissions and serves the leaderboard
   - No reCAPTCHA (low-stakes internal practice tool, not a public lead-gen form)

### reCAPTCHA v2 (Checkbox)

- **Site Key:** `6LcseZssAAAAALzkD8Pyb9qZuOygRE5Gb-zspkf5`
- **Secret Key:** `6LcseZssAAAAAAo4sabzYUbm5QrbfEKVPjVujTU5`
- Used on both Assessment and Consult forms (client-side + server-side in Apps Script)

---

## Conference: ISQA 2026

### Event Details

- **Conference:** ISQA Conference 2026 (10 Years Anniversary)
- **Date:** April 26, 2026
- **Talk Title:** "Rethinking QA Growth in the AI Era"
- **Speaker:** Aditya Mirza Bahari
- **Website:** https://conference.isqa.or.id/
- **Format:** Online (Zoom/Webinar)

### Conference Files (`ISQA_2026_Conference/`)

| File | Purpose |
|------|---------|
| `ISQA_2026_Slides_v4.html` | **Latest** presentation slides (HTML-based, keynote style) |
| `ISQA_2026_Slides_v3.html` | Previous version (before Career Compounding + rebranding) |
| `ISQA_2026_Slides_v2.html` | Earlier version |
| `ISQA_2026_Slides.html` | Original version |
| `ISQA_2026_Speaker_Notes.md` | Detailed speaker script (English) |
| `ISQA_2026_Speaker_Notes.html` | Print-friendly HTML of speaker notes (English) |
| `ISQA_2026_Speaker_Notes_ID.html` | Print-friendly HTML of speaker notes (Bahasa Indonesia, casual tone) |
| `ISQA Conference 2026 - Speaker Notes (Bahasa Indonesia).pdf` | Exported PDF of Indonesian speaker notes |
| `ISQA_2026_Talk_Outline.md` | Talk outline/structure |
| `ISQA_2026_Talk_Brief.md` | Brief/abstract for the talk |
| `isqa-logo.png` | ISQA logo |
| `idstb-logo.png` | IDSTB logo |
| `ngobrolqa-logo.png` | NgobrolQA logo (copy) |

### Slides v4 Structure (39 slides)

The presentation follows a keynote style (big text, one idea per slide, killer statements):

| Section | Slides | Content |
|---------|--------|---------|
| **Opening** | 1-6 | Title, Speaker bio, QA context, "Sound familiar?" personas, insight, clarity |
| **01: Where Are You?** | 7-14 | Skill Acquisition intro, 5 Stages, 4 Dimensions (with QR to Framework page), QA Problems by Level tables |
| **02: The Bigger Picture** | 15-19 | Career Compounding section: hook, 4 domains, personas, takeaway |
| **03: AI as Accelerator** | 20-24 | AI amplifies your level, Fear vs Reality, AI by stage, copilot warning |
| **04: Prove Your Skills** | 25-26 | ISTQB certification path (CTFL, CT-AI, CT-GenAI) |
| **05: Your Next Move** | 27-35 | Growth journey steps (Framework, Assess, Plan, Learn/Certify, Consult), Free resources + QR |
| **Closing** | 36-39 | 4 takeaways, closing statement, Q&A, Thank You |

### Speaker Notes Style

- Structured as: Hook → Problem → Insight → Framework → Application → Closing
- Includes pauses, emphasis markers, tone indicators, killer lines
- Casual/confident tone, non-native English friendly
- Indonesian version uses santai (casual) tone

---

## Design Conventions

### Colors

```
Primary:    #0f62f0 (blue)
Primary Dark: #0a47b8
Navy:       #071c44 (nav, footer, mobile menu; also --secondary)
Accent:     #f59e0b (amber)
Pink:       #ec4899 (used for "Others" domain in Career Compounding)

The four skill-dimension colors in QA_Skill_Framework.html (teal, indigo, amber, pink) are categorical data colors, not brand colors, and were deliberately left unchanged in the 2026-10 navy/blue rebrand.
Mark: plain N (ngobrolqa-mark.svg; ngobrolqa-mark-reversed.svg for navy bars); favicon: favicon.svg.
```

### Fonts

- **Website:** Inter (body), used across all pages
- **Career Compounding article:** Lora (serif, for body text) + Inter (headings)
- **Slides:** Space Grotesk (headings/statements) + Inter (body)

### Navigation

All pages share the same nav structure: Home | Framework | Assessment | Learning | Consult | [Free Assessment CTA button]. Mobile has hamburger menu.

### UI Patterns

- Feature cards on homepage (no numbering)
- NgobrolQA Insights section on homepage (article snippets, tag: "Original Theory")
- Interactive elements: persona switcher (Career Compounding), radar chart (Assessment), collapsible stage progressions (Framework)
- Share section on Career Compounding page (LinkedIn, X, WhatsApp, Copy Link)

---

## Pending / Future Considerations

- Speaker notes may need updating to reflect v4 slide changes (Career Compounding section added, terminology rebranded)
- Career Compounding Theory page and Framework page still reference "Dreyfus Model" in some places (the Career Compounding page has a vs Dreyfus comparison section). Consider whether to rebrand those too for consistency with slides.
- The Insights section on the homepage is designed to scale. New articles/theories can be added as snippet cards without needing a blog system.
- v4 slides are not yet pushed to production (they live in the Conference folder, not served on ngobrolqa.com).

---

## Quick Commands

```bash
# Navigate to project
cd ~/Desktop/"Competency QA"

# Push to production
git add . && git commit -m "message" && git push origin main

# Open a page locally
open index.html
open QA_Career_Compounding.html
open ISQA_2026_Conference/ISQA_2026_Slides_v4.html
```

## URLs (2026-10)

Internal links and canonical tags use extensionless, lowercase, hyphenated URLs (`/consult`, `/ctfl-mock-exam`,
`/qa-skill-framework`, `/qa-self-assessment`, `/qa-learning-plan`, `/qa-career-compounding`, `/`); GitHub Pages
serves `/x` from `x.html`, so both forms work. Old names (`QA_Consult`, `CTFL_Mock_Exam`, `QA_Skill_Framework`,
`QA_Self_Assessment`, `QA_Learning_Plan`, `QA_Career_Compounding`) remain as tiny redirect stubs (they keep query
strings and hashes); do not delete them if old links may still be out there (e.g. LinkedIn shares of the Career
Compounding article). `ctfl-mock-exam` is not `ctfl-exam` because that name is the data/apps-script folder.
`python3 -m http.server` cannot serve extensionless URLs, so test locally with a server that tries `path.html`.

## Insight pages (2026-10)

Long-form, hand-built pieces that share the Career Compounding page's look (dark hero, serif body, one interactive
element each, share block): `qa-career-compounding`, `qa-green-tests-not-proof`, `qa-api-function-calling-mcp`,
`qa-start-with-ai-agents`, `qa-ai-agent-least-privilege`. All are listed under "NgobrolQA Insights" on the home page.
The four newer pages were generated from a small script kept outside the repo (`ngobrolqa-insights-builder/` next to this
repo), which copies the shared CSS, nav, share block and footer from `qa-career-compounding.html`. The output is plain
static HTML; edit the files directly or re-run the generator. Pieces written in the Quill admin editor are different
(`Article?slug=...`, plain template) and are not listed on the home page.
