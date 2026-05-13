# LMI — Platform Engineer Interview Prep

**When:** Wed 2026-05-13, 3:30 PM EST (2:30 PM CT)
**Format:** Microsoft Teams — **camera on for the full duration**
**With:** TBD — confirmation came through without naming the interviewer
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

**The role** — Platform Engineer on LMI's DevSecOps practice. They support a product called IronSled (DevSecOps tooling for software deployed in ATO-authorized federal environments — cloud + on-prem). It's the productized version of what you've been building bespoke at GDIT for 5 years on Cloud One.

**Comp posted:** $101,145 – $173,000. Your anchor: $155–170K.

---

## What Round 1 Actually Is

This is an **HR / recruiter screen**, not a technical round. ~30 minutes. Anna or a partner is deciding whether to advance you to the hiring manager.

What they're evaluating:
- Clearance status
- Remote eligibility / location
- Comp alignment with the posted band
- Coherent background story
- Genuine interest in the role + LMI

What it's **not**:
- Technical deep-dive
- Coding or systems design
- Product (IronSled) interrogation

---

## What to Nail in 30 Minutes

### 1. Open with clearance

> "I hold an active TS/SCI — exceeds the Secret requirement, no adjudication wait."

### 2. Connect your background to the role (15-20 seconds)

> "Last 5 years I've been on AWS Cloud One — classified GovCloud, DISA STIG hardening, RMF and ATO documentation, CI/CD pipelines that gate promotion on security scans. That's exactly the DevSecOps work in this JD."

### 3. Why LMI / Why now

> "LMI's not-for-profit, mission-first posture appeals to me. The role description maps directly to where I've been operating — and where I want to keep going. Building DevSecOps tooling that actually streamlines ATO is high-leverage work."

### 4. Comp framing (if she asks)

> "Based on my background — TS/SCI, 9 years cloud, 5 in GovCloud, deep federal compliance — I'd target the upper half of the posted band, $155–170K. I'm flexible on structure."

**Don't go above $173K.** Federal contractor ATS auto-rejects (lesson from GDIT #360, 2026-05-04).

---

## Likely Questions + Your Answers

### "Tell me about yourself" (the opener)

> "20 years in DoD — started in the Air Force as a sysadmin, moved into cloud engineering around 2017. Last 9 in cloud, last 5 specifically on AWS GovCloud — Cloud One at GDIT. Classified CI/CD pipelines, DISA STIG, RMF, ATO. The work in this JD reads like a description of my last 5 years."

### "Why are you leaving / why now?"

> "My GDIT contract was winding down and I'm intentionally targeting my next role. I'm looking for a place where I can keep doing federal DevSecOps work — and ideally where my experience compounds rather than just gets maintained."

### "What's your salary expectation?"

See comp framing above. **Stay inside the posted band.**

### "Are you considering other opportunities?"

> "Yes — I'm in late-stage conversations with a few other federal employers. Not in a rush, but moving."

(If pressed for specifics, you don't need to name BAH — "another federal contractor at offer stage" is enough. Sets a soft urgency without making it a pressure tactic.)

### "Can you work the hours / location?"

> "Yes — I'm based in the Florida Panhandle, fully remote-capable, and the JD says remote-eligible. Occasional on-site at government-authorized environments is fine."

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

## Your Questions for Them

Have 2-3 ready. Recruiter screens almost always end with "any questions for us?" — silence here is a small but real negative signal.

Good ones for an HR/recruiter screen:

1. **"What does the interview process look like from here? Who would I be meeting with in the next round?"**
2. **"What's the team I'd be joining — size, where they sit, who reports where?"**
3. **"How does LMI think about career growth for platform engineers? Is there a defined trajectory — Senior, Principal, Lead?"**
4. **"What's the makeup of the IronSled team today, and where does this role fit?"**

Avoid: comp-trajectory questions (save for HM/offer stage), product-internal questions you can't follow up on, anything that sounds like you're testing them.

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
- [ ] Glance at Anna Keyes on LinkedIn for background context

---

## After the Call

Send a short thank-you within 2-3 hours. Two sentences max. Confirm continued interest, mention one thing you took away from the conversation.

Then update the tracker — status, interviewer name, what they said about next steps, anything notable.
