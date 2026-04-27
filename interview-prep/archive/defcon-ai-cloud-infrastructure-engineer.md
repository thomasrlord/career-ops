# Interview Intel: DEFCON AI — Cloud Infrastructure Engineer

**Evaluation Report:** [#077](../reports/077-defcon-ai-cloud-infrastructure-engineer-2026-04-21.md) · Score: 4.1/5
**Researched:** 2026-04-22
**Sources:** 0 Glassdoor reviews (too small/new), 0 Blind posts, 6 press/funding sources, JD analysis

---

## Process Overview

- **Current round:** Recruiter screen — 30 min Teams call with Lindsay Vervynckt
- **Expected process (inferred — ~35-person startup):** Recruiter screen → Hiring manager / technical phone → Possibly a take-home or live technical → Offer
- **Rounds total:** Unknown — likely 2-3 total
- **Difficulty:** Unknown — no data. Small defense startup; expect practical and mission-focused over LeetCode.
- **Known:** They're actively growing (recent hires Feb 2026), VP of Engineering role also open — they're building the team now.

---

## Round 1: Recruiter Screen (TODAY'S CALL)

- **Duration:** 30 min
- **Conducted by:** Lindsay Vervynckt (recruiter)
- **What she evaluates:** Culture fit, clearance status, location/availability, comp alignment, background coherence, interest in mission
- **This is NOT a technical round.** She is deciding whether to advance you to the hiring manager.

### What to nail in 30 minutes

1. **Open with your clearance:** "I hold an active TS/SCI — I understand you're looking for Secret or above, so I exceed that requirement and can start immediately without adjudication wait."
2. **Connect your background to their mission:** "I spent five years deploying and sustaining software on Cloud One — AWS GovCloud, classified environment, ATO compliance, CI/CD pipelines. That maps directly to what you're doing with ARTIV on Game Warden."
3. **Show you've done homework:** Mention ARTIV by name. Mention IL5/IL6. Mention Paul Selva if it feels natural ("The leadership here is impressive — having the former Vice Chairman of the Joint Chiefs as CSO signals this is a serious program").
4. **Comp:** They listed $140K–$180K. Your target is $155K–$175K. If she asks: *"I'm targeting $160K–$175K based on market data for senior cleared cloud roles — the upper range reflects the TS/SCI clearance premium. I'm flexible on structure."*

---

## Likely Technical Questions (Rounds 2+)

### Technical — AWS GovCloud & Infrastructure

| Question | Source | Your best answer angle |
|----------|--------|----------------------|
| Walk me through how you'd architect a compliant CI/CD pipeline in a classified AWS environment | [inferred from JD] | Wickr on Cloud One: Jenkins → Artifactory → CloudFormation → GovCloud deploy. STIG-hardened AMIs. IAM least-privilege. |
| How have you handled STIG compliance at scale? | [inferred from JD] | DISA STIG hardening for RHEL/CentOS at GDIT, automated compliance checks in pipeline, RMF/ATO documentation |
| How do you manage secrets in AWS GovCloud? | [inferred from JD] | AWS Systems Manager Parameter Store + IAM roles. No hardcoded credentials in pipelines. |
| Describe your CloudFormation/IaC experience | [inferred from JD] | CloudFormation primary, CDK secondary. Used both at GDIT for automated provisioning across dev/test/prod |
| What's your Terraform experience? | [inferred from JD — flagged gap] | "CloudFormation is my primary IaC tool — I've worked with Terraform and am actively deepening it. I can be productive in a Terraform shop from day one." |
| What's your container experience? | [inferred from JD] | Docker is my primary container tool — image builds, deployment pipelines. ECS and EKS are not in my production background; be direct about this. |
| How would you approach moving a COTS product into an IL5/IL6 environment? | [inferred from JD + ARTIV context] | Wickr Enterprise: Docker containers, harden AMIs, STIG scan, CloudFormation deploy, ATO documentation, iterate with security team |
| How do you handle EC2/VPC network segmentation in a classified environment? | [inferred from JD] | **Gap — networking is not a strong suit.** Be honest: "I've worked within VPC environments and understand the concepts — security groups, private subnets — but deep network architecture design isn't my primary expertise." Don't bluff on routing, NACLs, or complex VPC peering. |

### Behavioral

| Question | What they're really asking | Your story |
|----------|---------------------------|------------|
| Tell me about yourself | Can you tell a coherent story in 90 seconds? | "20 years in DoD — started in the Air Force as a sysadmin, moved into cloud engineering around 2017. The last 9 years have been cloud, the last 5 specifically in AWS GovCloud on Cloud One at GDIT — classified CI/CD, CloudFormation IaC, DISA STIG, ATO. That work is exactly what DEFCON AI is doing with ARTIV." |
| Tell me about a time you had to meet a tight compliance deadline | Are you calm under ATO pressure? | RMF/ATO cycle at GDIT — coordinating STIG hardening, scanning, POA&M remediation, documentation for an authorization deadline |
| Tell me about a time you had to debug a production issue in a classified environment | Can you troubleshoot with limited tooling? | Pick any GovCloud incident — limited egress, no public internet, had to use CloudWatch + Systems Manager for RCA |
| Tell me about working with government stakeholders | Can you navigate bureaucracy? | GDIT → government COR coordination on deliverables, change control boards, documentation requirements |
| Tell me about a gap in your skills you're actively closing | Self-awareness + growth mindset | "Terraform — CloudFormation is my primary IaC tool. I'm actively working through Terraform in personal projects and can be productive immediately." |

### Background Red Flags — Questions to Expect

| Likely question | Why it comes up | Recommended framing |
|-----------------|-----------------|---------------------|
| Why are you leaving GDIT after 5 years? | Gap between departure (March 2026) and now | "My contract was winding down and I'm intentionally targeting my next role — I'm looking for a company with a clear mission and room to build, not just maintain. DEFCON AI fits that." |
| How deep is your container/Kubernetes experience? | JD mentions ECS/EKS/K8s | "Docker is my primary container tool. ECS and EKS I haven't run in production. Kubernetes — I'm solid on the concepts (pods, deployments, services, namespaces) but haven't operated it in depth in production. I'd be upfront about that." |
| Azure is listed — do you have Azure experience? | JD mentions Azure alongside AWS | "AWS is my primary platform — GovCloud specifically. I have limited Azure hands-on but I'm a fast learner and the concepts transfer directly." |
| This is a startup vs. large contractor — different pace | Culture fit check | "That's actually the draw. I've spent my career in large contractor environments and I'm ready to build from the ground up rather than maintain inherited systems." |

---

## Story Bank Mapping

| # | Likely question | Best story | Fit |
|---|-----------------|-----------|-----|
| 1 | Hardest infrastructure challenge | Wickr Enterprise on Cloud One deployment | **Strong** — COTS + CloudFormation + GovCloud + STIG |
| 2 | ATO / compliance under pressure | RMF/ATO cycle at GDIT | **Strong** |
| 3 | CI/CD pipeline ownership | Jenkins + Artifactory pipelines at GDIT | **Strong** |
| 4 | Debugging production in classified env | GovCloud incident response | **Strong** |
| 5 | Working with gov stakeholders | GDIT COR/change control board | **Partial** — needs specifics |
| 6 | Learning a new tool quickly | [GAP — build this story] | **None** |
| 7 | Terraform / IaC depth | [GAP — Terraform answer needed] | **None** |

**Gaps to fill before Round 2:**
- **"Learning a new tool quickly"** — think of a specific time you adopted a new AWS service or tool fast in a production environment. Smartronix Terraform modules for EFS backup is a candidate.
- **Terraform story** — even small: "At Smartronix I wrote Terraform modules for Amazon EFS backup automation — that was my first Terraform production work."

---

## Technical Prep Checklist

- [ ] **Game Warden / Second Front** — read https://www.secondfront.com/products/game-warden/ — understand IL2/IL4/IL5/IL6 levels and how ATO inheritance works. You'll likely be asked about this.
- [ ] **ARTIV product** — read defconai.com/mission/ — know what the product does so you can connect your infra work to the mission impact
- [ ] **IL5 vs IL6 difference** — IL5 = CUI/controlled unclassified (FedRAMP High equivalent), IL6 = Secret classified. Know the boundary.
- [ ] **Terraform basics** — review module structure, state management, `terraform plan/apply`. You don't need to be an expert — you need to not look blank when they ask.
- [ ] **ECS / EKS** — these are listed in the JD but are not in your background. Be direct: "I've worked with Docker extensively; ECS and EKS are adjacent but not something I've operated in production." Don't bluff.
- [ ] **AWS KMS + encryption at rest** — JD mentions KMS/encryption. Know the pattern: CMK vs AWS-managed keys, envelope encryption.
- [ ] **CMMC 2.0 Level 2 vs Level 3** — DEFCON AI is likely targeting Level 2 minimum, possibly Level 3. Know the difference and where your GDIT experience sits.

---

## Company Signals

**Vocabulary to use:**
- "contested mobility" — their product framing
- "ARTIV" — name their product
- "Game Warden" / "Second Front" — shows you understand the deployment model
- "IL5/IL6" — shows you understand classification levels
- "ATO" — Authority to Operate, central to everything they do
- "mission-focused" — their self-description

**Values they screen for** (inferred from careers page + leadership background):
- Mission alignment — Paul Selva came from USTRANSCOM. They care about the DoD mission, not just the tech.
- Ownership mindset — 35 people, no hand-holding
- Honesty about gaps — small team, no room for inflated CVs

**Things to avoid:**
- Don't oversell Terraform or Kubernetes depth — they'll find out in Round 2
- Don't refer to the role as "just infrastructure" — frame it as mission-critical delivery
- Don't ask about work-life balance in Round 1 (recruiter screen)

**Sharp questions to ask Lindsay:**
1. *"ARTIV is now deployed at both IL5 and IL6 — is the Cloud Infrastructure role primarily supporting one of those environments, or both?"*
2. *"I noticed DEFCON AI has several product lines beyond ARTIV — is this role supporting infrastructure across all of them, or is it focused on the defense/DoD side?"*
3. *"How many products is the Cloud Infrastructure Engineer expected to support, and what does the team structure look like around that? I want to make sure I understand the scope."*
4. *"You also have a VP of Engineering role open — how does the Cloud Infrastructure Engineer fit into that org as it takes shape?"*
5. *"What does success look like in the first 90 days for this role?"*

**Recruiter screen debrief (2026-04-22):**
- Scope confirmed: all general cloud responsibilities across products — not DoD-focused only
- Team: this role + one DevSecOps engineer under a general IT umbrella
- Comp: aligned
- No surprises
- Concern: two engineers supporting 4+ product lines at 35 people — significant load, no redundancy

---

## Round 2: Technical Call with Current Engineer

**Goal:** Understand the real day-to-day scope before committing further. This is a fact-finding conversation as much as an interview.

**Questions to ask the engineer:**

### Scope & Workload
1. *"What does a typical week look like for you — what percentage is reactive (incidents, tickets) vs. proactive (building, improving)?"*
2. *"How many distinct environments or products are you actively maintaining right now?"*
3. *"What does on-call look like? Is there a rotation, or does it fall to whoever owns the infrastructure?"*
4. *"What's the biggest infrastructure fire you've dealt with in the last 6 months?"*

### Team & Coverage
5. *"With two people on the infrastructure side, how do you handle coverage when someone is out?"*
6. *"Is there a plan to grow the team, or is two the expected steady-state?"*
7. *"How much do the product engineering teams handle themselves vs. coming to you?"*

### Tech Stack
8. *"What does the current IaC setup look like — Terraform, CloudFormation, something else?"*
9. *"How mature is the CI/CD pipeline today, and what are the biggest gaps you're trying to close?"*
10. *"What's the biggest technical challenge you're hoping this hire helps solve?"*

### Reality Check
11. *"What do you wish you'd known about this role before joining?"*
12. *"What would make someone unsuccessful in this role?"*

**Note on scope:** At 35 people with 4+ product lines and only 2 infrastructure engineers, assess whether the workload is sustainable. If the engineer describes constant firefighting with no time to build, that's a signal. If they describe a maturing platform with clear ownership boundaries, that's different.

---

## Comp Script

If Lindsay asks about compensation:

> "Based on market data for senior cleared cloud roles, I'm targeting $160K–$175K. I understand the DEFCON AI range is $140K–$180K, so we're aligned. I'm open to discussing the full package — equity and the mission matter to me as much as base."

If she pushes for a single number:
> "I'd say $165K as a target — open to conversation once I understand the full structure."

---

## One-Page Cheat Sheet (for the call)

**Their product:** ARTIV Air — routing optimization for military logistics (cargo/personnel movement, disruption modeling, adversarial threat scenarios). Plus R-ALIGN (multimodal global theater logistics), R-IMS (infrastructure planning), SimSource/Synapse (manufacturing/healthcare). Broader than just military — but defense is the anchor. Deployed on AWS via Second Front Game Warden at IL5/IL6.
**Their stage:** $44M seed, 35 people, Bessemer-backed, Air Force + USTRANSCOM customers.
**Their need:** Someone who can build and own cloud infrastructure for classified DoD workloads from scratch.
**Your hook:** "20 years in DoD, 9 in cloud — the last 5 specifically in AWS GovCloud on Cloud One. DISA STIG, ATO, CI/CD, CloudFormation. That's exactly what ARTIV on Game Warden needs."
**Your clearance:** TS/SCI — exceeds their Secret requirement. Lead with it.
**Your gaps:** Terraform (not primary — CloudFormation is), ECS/EKS (not in production background — Docker yes), Kubernetes concepts known but not operated in depth, deep AWS networking. Own all honestly — don't bluff on any of them.
