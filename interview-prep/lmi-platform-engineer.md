# LMI — Platform Engineer Interview Prep

**When:** Wed 2026-05-13, 3:30 PM EST (2:30 PM CT)
**Format:** Microsoft Teams — **camera on for the full duration**
**With:** **George — Hiring Manager, Product Development** (this is the HM, not HR)
**Role link:** [#363 report](../reports/363-lmi-platform-engineer-ironsled-2026-05-12.md) · Score 4.1/5

---

## ⚠ LMI's Interview Policy (READ THIS)

From the confirmation email:

> "We ask that you remain on camera for the duration of the interview and refrain from using AI tools or interview guides. We're most interested in hearing your authentic thoughts and experiences in your own words. While AI should not be used to answer questions in real time, you're welcome to share examples of how you use AI to make your work more effective."

**What this means for you:**
- **Internalize this prep doc tonight.** Do not have it open or visible during the call.
- **No second monitor, no notes, no AI assistants running.** They will be reading body language and eye movement.
- **Camera on the entire time.**
- **They DO want to hear about how you use AI in your work** — see the "AI in your work" section below. Have a real example ready.

---

## The 30-Second Context

**LMI** — Logistics Management Institute. Not-for-profit federal contractor, decades of DoD work, Tysons VA HQ. Serves defense, space, healthcare, energy. Different culture from for-profit primes like GDIT/Leidos/BAH — "mission first" is real, not just a tagline.

**The team — Product Development.** George runs it. LMI builds and operates products (not just delivers services). That's the key shift from your prior federal-IT background.

**Product portfolio you should know:**

| Product | What it is | What you'd be on |
|---|---|---|
| **IronSled™** | DevSecOps PaaS for DoD. IL4 and IL6. Cloud or on-prem. TRL-7. "Built-in pipeline" — accelerates ATO for apps deployed inside. | **YES — this is the role's main surface area** |
| **LIGER®** | LMI's flagship GenAI platform for government. RAG architecture, IL5. Awarded an Army contract (DASA-DES) for the Deputy Assistant Secretary for Data, Engineering, Software. Used for market research, contract writing, decision support across defense / health / civilian / intel. | Adjacent — they may want IronSled-style infra for LIGER deployment |
| **IronGate** | **Unknown — not surfaced in public search.** Could be internal, newer, or unannounced. **Ask George about it.** Don't bluff. |

**Comp posted:** $101,145 – $173,000. Your anchor: $155–170K.

---

## What Round 1 Actually Is

This is the **hiring manager's screen**, not HR. ~30-45 minutes. George is deciding whether you'd be a good fit on his Product Development team.

What he's likely evaluating:
- Your actual technical work history — what you've built, not just where you've worked
- How you think about DevSecOps and pipeline design
- Whether your background maps to product development (you have ops/sustainment experience; products are a different muscle — be honest about the bridge)
- Communication style and how you handle gaps in your skill set
- Genuine interest in LMI's products and the kind of work they do

What it's probably **not** (yet):
- Deep coding or live systems design (those come in later rounds if HM advances you)
- Hard salary negotiation (that's the offer stage)
- Compliance/clearance verification (HR handled most of that)

**Key reframe:** This is more substantive than a recruiter screen. He'll probably ask about specific projects in detail and probe how you'd approach problems. Lead with what you've *built*, not your tenure or org chart.

---

## What to Nail in 30 Minutes (HM Edition)

### 1. Lead with what you've built, not your tenure

> "The last 5 years I've been on AWS Cloud One at GDIT — running classified GovCloud workloads. The hands-on work that's most relevant here: I built the CloudFormation IaC and Jenkins-plus-Artifactory pipelines for deploying Wickr Enterprise inside an ATO-authorized environment, with DISA STIG hardening and RMF documentation baked in. That's the same pattern IronSled is productizing — built-in pipelines, security scanning gates, accreditation acceleration."

### 2. Acknowledge the platform-vs-product shift honestly

If George asks why this role / why now:

> "I've been on the operations side — deploying and sustaining other people's products inside classified envs. What's drawn me here is moving toward platform engineering for products specifically built for that environment. The work is the same shape but the lever is bigger — instead of building a one-off pipeline for one application, I'd be helping build a platform that accelerates ATO for many applications."

### 3. Clearance (work it in naturally, not a cold open with an HM)

Somewhere in the conversation:

> "Active TS/SCI — exceeds the Secret requirement, no adjudication needed."

(Don't lead with this for the HM. HR cares; he probably already knows. Slot it in when it's natural.)

### 4. Comp framing (only if he asks — HM usually doesn't)

> "I'd target the upper half of the posted band, $155–170K. Flexible on structure."

**Don't go above $173K.** Federal contractor ATS auto-rejects (lesson from GDIT #360, 2026-05-04).

---

## Likely Questions from George (HM-flavored)

### "Tell me about yourself"

Compress to 60-90 seconds. Lead technical, not chronological.

> "20 years in DoD IT, last 9 in cloud engineering. The work I'd point to most for this role: 5 years on AWS GovCloud at GDIT, on the Cloud One program — classified CI/CD pipelines with Jenkins and Artifactory, CloudFormation IaC, DISA STIG hardening, RMF/ATO documentation. The most fun work has been the automation layer underneath that — for example, building CloudWatch + Lambda + SSM auto-remediation so the team stopped getting paged for routine failures. The work IronSled is doing reads like a productized version of what I've been doing bespoke."

### "Walk me through a project you're proud of"

Use the **Wickr Enterprise on Cloud One** story — it's the closest match to IronSled's customer pattern. Have the **Self-Healing Auto-Scaling** story ready as a follow-up if he wants to see range.

### "How do you approach building a CI/CD pipeline with security scan gates?"

Don't recite a textbook answer. Walk through what you actually did:

> "On Wickr Cloud One: source goes through Jenkins, artifact lands in Artifactory tagged with a version. Before promotion to higher environments, the pipeline gates on STIG scan and RMF documentation status. If either fails, promotion blocks and the team gets notified. CloudFormation handles the actual deploy with stack policies for safe updates. Rollback is a previous tagged artifact + a stack update."

### "Tell me about a hard problem you solved"

Pick **Self-Healing Auto-Scaling.** It shows:
- You see and own a real toil problem (paging for routine failures)
- You build durable automation, not duct tape
- You think about safety (the circuit-breaker lesson — automation acted on transient signals, you tightened evaluation periods)

### "Why are you leaving GDIT?"

> "Contract was winding down and I'm intentionally targeting my next role. I'm looking for a place where the work compounds — building platform tooling that helps multiple teams, rather than one-off pipelines for one program."

### "What's a skill you're actively working on?"

> "Two things. Kubernetes — I'm conceptually solid but haven't operated it in production depth. Working through it now. And recertifying my AWS Solutions Architect Associate — I held it through 2023 and let it lapse; planning to reschedule the exam soon."

### "Are you considering other opportunities?"

> "Yes — in late-stage conversations with another federal employer. Not in a rush. Wanted to be straight about the timeline so we're on the same page."

(You can mention you're at offer stage without naming BAH. Sets soft urgency, signals you're a real candidate elsewhere — not a pressure tactic.)

### "Where are you located? Can you work the hours?"

> "Florida Panhandle, fully remote. Standard business hours fine."

---

## Honest Framing for the Two Soft Gaps

If she lobs technical questions (she might pre-screen on these), here's the honest framing — don't bluff.

### GitLab CI/CD

> "Jenkins is my production CI/CD platform. GitLab CI is conceptually transferable — pipeline-as-code, runners, stages — and I'd be productive in a GitLab shop after a short ramp."

### Kubernetes / EKS / OpenShift

> "Docker is my container production background. K8s I'm conceptually solid on — pods, deployments, services, RBAC, namespaces — but I haven't operated it in production depth. Ramp on EKS or OpenShift would be Week 1-2 work."

**Rule for both:** State the gap plainly, then bridge with what you do have. Don't apologize.

---

## AI in Your Work (They Invited This — Use It)

LMI explicitly said they want to hear how you use AI to make your work more effective. This is your opportunity to differentiate. Most candidates won't have a thoughtful answer — you can.

**Don't say:** "I use ChatGPT sometimes" (weak, generic)

**Do say something like:**

> "AI tools are a thinking partner for me — most useful for accelerating the ramp on something new and for pressure-testing my own reasoning before I commit code. When I picked up Terraform after years of CloudFormation, I used Claude as a sparring partner to test my mental model against the state-management differences — that cut my time to productive output significantly. I also use it for code review — having an extra set of eyes on a script before it goes anywhere near production is cheap insurance."

**Then bridge to where AI fits in DevSecOps specifically:**

> "On the DevSecOps side, I'm watching the AIOps direction closely — automating remediation for known failure modes so on-call attention is reserved for novel problems. I've built that pattern manually with CloudWatch, Lambda, and SSM. The next step is using ML to sharpen the detection signal so the automation triggers on the right things. The discipline has to come first though — the value isn't AI deciding what to do, it's the detection → action → observation loop being safe and observable end-to-end."

**Why this works:**
- Specific and credible (not hand-wavy)
- Shows you use AI thoughtfully, not as a crutch
- Bridges to a real production pattern you've built (the AIOps STAR story)
- Signals you understand where AI in DevSecOps is going

**Keep your honest framing:** You haven't built ML-driven AIOps in production. Don't claim you have. The pitch is that you've built the *foundation* (automated remediation) and you understand the trajectory.

**Bonus context — LIGER is in their portfolio.** LIGER is LMI's GenAI platform for government (RAG architecture, IL5, Army contract). George leads Product Development which includes both IronSled and LIGER. That makes the AI-in-your-work question doubly relevant — and it gives you a natural opening to ask about IronSled-style infra for LIGER deployment.

---

## Story Bank — Quick Pick

| If they ask about... | Lead with... |
|---|---|
| Most impactful project | **Wickr Enterprise on Cloud One** — CloudFormation IaC, Jenkins + Artifactory pipelines, DISA STIG hardening, ATO. Direct match for what LMI does with IronSled. |
| Automation you're proud of | **Self-Healing Auto-Scaling** — CloudWatch + Lambda + SSM auto-remediation. Reduced on-call load and MTTR. |
| Learning a new tool | **EFS Backup with Terraform at Smartronix** — first production Terraform work coming from CloudFormation. Use this same shape if asked about GitLab CI ramp. |
| Compliance under pressure | **RMF/ATO cycle at GDIT** — STIG hardening, scanning, POA&M remediation, ATO documentation under deadline. |
| Cross-functional work | **GDIT government stakeholder coordination** — application team, security team, government COR, change control boards. |

Full stories are in `interview-prep/story-bank.md` if you want to refresh memory.

---

## Your Questions for George

Have 3-4 ready. HM screens always end with "any questions for me?" — and the quality of your questions tells him a lot.

**Best ones for a hiring manager:**

1. **"I noticed three products mentioned — IronSled, LIGER, and IronGate. I'm familiar with IronSled and LIGER from public information, but I haven't been able to find anything on IronGate. Can you tell me what it is and how the three fit together as a portfolio?"**
   - Honest about your knowledge limits, signals you did homework on the other two
2. **"What does the IronSled team look like today — team size, how engineers split between platform work and customer deployments?"**
   - Reveals role shape; lets you check that this is engineer-on-team, not lead/solo-owner
3. **"What's the biggest engineering challenge IronSled is working on right now? Where would my work hit the ground in the first 90 days?"**
   - Shows you're thinking about contribution, not just collecting a title
4. **"How does the team work with the LIGER side? Is there shared platform infrastructure, or are they distinct stacks?"**
   - Demonstrates portfolio thinking; opens up the AI-adjacency conversation
5. **"From your perspective as the hiring manager, what would make someone a great fit on this team versus just a competent one?"**
   - Lets George tell you exactly what success looks like — and signals you're evaluating fit, not just selling yourself

**Optional if conversation goes deep on tech:**

6. **"GitLab CI is in the JD — is the migration from other CI/CD systems still in progress, or is everything already on GitLab?"**
   - Lets him talk about the actual stack maturity; calibrates the GitLab CI ramp expectation

**Avoid:** comp-trajectory questions (save for offer stage), "what's the company culture like" (vague), anything that sounds like you're testing him, asking about benefits or PTO.

---

## Pre-Call Checklist (15 min before)

- [ ] Teams app open and logged in
- [ ] **Camera on. Stays on the full call.**
- [ ] **This prep doc CLOSED. No notes visible. No AI assistants running.** (They'll notice eye drift to a second screen.)
- [ ] Water nearby
- [ ] Phone on silent and face down
- [ ] Bathroom break before the call starts
- [ ] Anything visible behind you on camera is clean and uncluttered
- [ ] Test mic and audio in Teams 5 minutes early

**Earlier today (before the 15-min checklist):**

- [ ] Read this whole prep doc once carefully — internalize, don't memorize verbatim
- [ ] Skim `lmi.org/who-we-are` and `lmi.org/what-we-do` — 5 min
- [ ] Quick news scan: "LMI federal contractor 2026" — anything recent worth mentioning
- [ ] Glance at George on LinkedIn if you can find him (LMI / Product Development / DevSecOps) — even 30 seconds of context on his background helps you calibrate technical depth

---

## After the Call

Send a short thank-you within 2-3 hours. Two sentences max. Confirm continued interest, mention one thing you took away from the conversation.

Then update the tracker — status, interviewer name, what they said about next steps, anything notable.

---

## Notes / Updates Log

- 2026-05-12: Initial invite from Anna Keyes received; replied with availability after 1pm CST; prep brief drafted
- 2026-05-12: Anna confirmed slot — Wed 2026-05-13 at 3:30 PM EST via Teams
- 2026-05-13: Confirmation email arrived. Two updates: (1) LMI's no-AI-during-interview / camera-on policy; (2) explicit invitation to discuss how you use AI in your work
- 2026-05-13: Interviewer named — **George, Hiring Manager, Product Development**. Three products in portfolio: **IronSled** (DevSecOps PaaS for IL4/IL6 DoD), **LIGER®** (GenAI platform for government, RAG, IL5, Army DASA-DES contract), **IronGate** (not publicly documented — flagged as a question to ask George). Prep refocused from HR-screen to HM-screen.
