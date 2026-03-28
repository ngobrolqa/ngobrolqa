# QA Skill Framework V2 - Draft

> **Status:** Work in Progress  
> **Author:** Aditya Mirza Bahari  
> **Core Concept:** Know your level, understand your problem, learn what matters next

---

## The 4 Skill Dimensions

### 1. 🎯 TESTING CRAFT
**What it is:** The core practice of testing — how you design, execute, and analyze tests.

| Sub-Area | What It Covers | ISTQB Alignment |
|----------|---------------|-----------------|
| **Test Design** | Creating test cases, applying techniques (BVA, EP, decision tables, state transition) | CTFL Ch.4 |
| **Test Execution** | Running tests, documenting results, managing test data | CTFL Ch.4-5 |
| **Defect Management** | Finding, reporting, tracking, analyzing bugs | CTFL Ch.5 |
| **Test Analysis** | Understanding requirements, identifying test conditions | CTFL Ch.4 |

**AI Integration:**
- AI can generate test cases → but YOU validate relevance
- AI can suggest edge cases → but YOU understand context
- AI can draft bug reports → but YOU verify accuracy

**Key Question:** *How well do you practice the craft of testing?*

---

### 2. ⚙️ TECHNICAL DEPTH
**What it is:** The technical skills that expand what you can test and how you test it.

| Sub-Area | What It Covers | ISTQB Alignment |
|----------|---------------|-----------------|
| **Automation** | Test automation design, frameworks, maintenance | CT-TAE |
| **API & Integration** | API testing, service testing, integration points | CT-TAE |
| **Performance** | Load testing, performance analysis, optimization | CT-PT |
| **AI/ML Testing** | Testing AI systems, LLM testing, prompt testing | CT-AI, CT-GenAI |
| **Security Basics** | Security testing fundamentals, OWASP awareness | CT-SEC |

**AI Integration:**
- AI can write automation scripts → but YOU design the architecture
- AI can analyze performance data → but YOU interpret business impact
- AI can test AI systems → but YOU understand the risks

**Key Question:** *How deep is your technical toolkit?*

---

### 3. 🧠 QUALITY THINKING
**What it is:** The mindset and strategic thinking that separates good testers from great ones.

| Sub-Area | What It Covers | ISTQB Alignment |
|----------|---------------|-----------------|
| **Risk-Based Thinking** | Identifying, assessing, prioritizing risks | CTFL Ch.5, CTAL-TM |
| **Root Cause Analysis** | Finding why defects happen, not just what | CTAL-TM |
| **Prevention Mindset** | Shifting left, quality gates, early feedback | CTFL Ch.2 |
| **Test Strategy** | Planning approach based on context, not templates | CTAL-TM |
| **Metrics & Analysis** | Using data to drive decisions | CTAL-TM |

**AI Integration:**
- AI can identify patterns → but YOU connect to business context
- AI can suggest risks → but YOU prioritize based on domain knowledge
- AI can generate metrics → but YOU tell the story

**Key Question:** *How strategically do you think about quality?*

---

### 4. 💬 INFLUENCE & IMPACT
**What it is:** Your ability to drive quality outcomes through people, not just through testing.

| Sub-Area | What It Covers | ISTQB Alignment |
|----------|---------------|-----------------|
| **Collaboration** | Working with dev, PM, stakeholders | Soft skills |
| **Communication** | Reporting, presenting, explaining | Soft skills |
| **Ownership** | Taking responsibility for outcomes, not just tasks | Professional |
| **Leadership** | Mentoring, leading initiatives, building teams | Professional |
| **Domain Expertise** | Deep knowledge of your industry/product | Domain-specific |

**AI Integration:**
- AI can draft communications → but YOU build relationships
- AI can summarize status → but YOU earn trust through judgment
- AI can provide information → but YOU influence decisions

**Key Question:** *How much quality impact do you create through others?*

---

## Dimension Balance by Stage

```
                Testing   Technical   Quality    Influence
                Craft     Depth       Thinking   & Impact
                ─────────────────────────────────────────────
Starter         ████░░    ██░░░░      █░░░░░     █░░░░░
Practitioner    █████░    ███░░░      ███░░░     ██░░░░
Professional    █████░    ████░░      ████░░     ████░░
Leader          ████░░    ████░░      █████░     ██████
Industry        ███░░░    █████░      ██████     ██████
```

**Key Insight:** 
- Early stages: Focus on **Testing Craft** and **Technical Depth**
- Later stages: **Quality Thinking** and **Influence** become differentiators
- **Technical Depth** remains important but shifts from "doing" to "architecting"

---

## Mapping V1 → V2

| V1 Bucket | V2 Dimension |
|-----------|--------------|
| Functional Excellence (Test Design, System Understanding, Bug Analysis) | **Testing Craft** |
| Problem Solving (Root Cause, Risk, Prevention) | **Quality Thinking** |
| Impact & Ownership (PIC, E2E) | **Influence & Impact** |
| Communication (Dev/PM, Stakeholder) | **Influence & Impact** |
| Process & Strategy (Improvement, Standards) | **Quality Thinking** |
| Culture & Values (Professionalism, Reliability, Humility) | **Influence & Impact** |
| *(missing in V1)* Automation, API, Performance, AI Testing | **Technical Depth** |

---

## ISTQB Certification Path by Dimension

```
Testing Craft     →  CTFL → CTAL-TA
Technical Depth   →  CT-TAE → CT-PT → CT-AI → CT-GenAI → CT-SEC
Quality Thinking  →  CTAL-TM → CT-AI (strategy aspects)
Influence         →  (No cert, but domain certs help)
```

---

## Open Questions

1. **Is "Testing Craft" the right name?** Alternatives: "Test Fundamentals", "Core Testing", "Testing Practice"

2. **Should Security be in Technical Depth or separate?** Currently grouped with technical skills.

3. **Is Domain Expertise part of Influence, or separate?** Currently under Influence as it drives credibility.

4. **How many "I can..." statements per dimension?** Proposal: 5 per dimension × 5 stages = 100 total (vs 300+ in V1)

---

## Next Steps

- [ ] Validate dimension names and coverage
- [ ] Define 5 "I can..." statements per dimension per stage
- [ ] Create the full Stage Grid (Problem + Next Move + AI Role)
- [ ] Update website framework page
- [ ] Update self-assessment questions

---

**Feedback needed before proceeding!**
