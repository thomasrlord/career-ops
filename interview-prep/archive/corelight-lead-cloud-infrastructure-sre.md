# Interview Intel: Corelight — Lead Cloud Infrastructure Engineer / SRE (Federal)

**Evaluation Report:** [#018](../reports/018-corelight-lead-cloud-infrastructure-sre-2026-04-20.md) · Score: 3.9/5
**Researched:** 2026-04-22
**Interview scheduled:** 2026-04-23 10:00 AM Zoom (recruiter screen)
**Sources:** Glassdoor (61 reviews, 28 interview Q&As), Crunchbase/PitchBook, press releases

---

## Company Snapshot

| Signal | Detail |
|--------|--------|
| **Founded** | 2013 |
| **HQ** | San Francisco (remote-distributed) |
| **Size** | ~150–200 employees |
| **Stage** | Series E |
| **Total raised** | $310M — latest $150M Series E (Apr 2024, led by Accel; Cisco Investments + CrowdStrike participating) |
| **ARR growth** | 40%+ YoY; 300% YoY growth in AI/SaaS NDR solutions |
| **Product** | Open NDR (Network Detection and Response) platform |
| **Federal position** | Authorized for DoD, IC, Federal Civilian, and DIB use. Building a dedicated FedRAMP federal cloud region — this role owns that infrastructure. |
| **Stability** | Strong — $150M Series E from top-tier VCs + strategic investors (Cisco, CrowdStrike). No layoff signals in engineering. Minor employee count dip likely from sales reorg. |
| **Glassdoor** | 4.0/5 overall · 67% recommend · Engineering culture: "incredibly smart, refreshingly humble" |

---

## Process Overview

- **Round 1 (tomorrow):** Recruiter screen — 30 min Zoom
- **Known process (Glassdoor):** Recruiter → Hiring Manager chat → Resume discussion → System Design → Technical background/coding
- **Total timeline:** ~27 days average
- **Difficulty:** 3/5 (moderate)
- **Positive experience rate:** 44% (lower than ideal — prep carefully)
- **Note:** Most negative experiences cited were in sales/escalation roles. Engineering interviews described as structured and fair.

---

## Round 1: Recruiter Screen (TOMORROW 10AM)

This is a culture/background fit check. Not technical.

**Your 3 priorities:**

1. **Lead with clearance + federal compliance depth.**
   > "I hold an active TS/SCI and spent 9 years in cloud — the last 5 in AWS GovCloud under IL4/IL5 controls. FedRAMP High is the commercial analog to what I've been operating in. Building out Corelight's federal region is directly in my wheelhouse."

2. **Name the mission.**
   Corelight is a 2025 Gartner Magic Quadrant Leader for NDR. They're building a FedRAMP federal region specifically for DoD and IC customers. This role owns that infrastructure. Say you understand that:
   > "I saw Corelight was named a Gartner NDR leader in 2025 and is actively building a FedRAMP federal region. That's exactly the kind of compliance-critical infrastructure build I want to be part of."

3. **Comp if asked.**
   > "I'm targeting $175K–$195K for a lead-level role. I understand the Corelight range is $172K–$219K so we're well-aligned."

**Questions to ask — scope the role before committing further:**

> *"The JD covers a lot of ground — FedRAMP infrastructure, Kubernetes, and AI/ML pipelines. I want to make sure I understand where the role actually spends most of its time. In a typical week, what does the balance look like between maintaining the federal cloud platform versus building out ML infrastructure?"*

> *"The posting mentions AI/ML pipeline automation — is that work primarily around the infrastructure layer (compute, storage, networking for model workloads), or does this person also own the pipeline logic and model tooling itself?"*

> *"How is the engineering team structured around this role today? Is there a separate ML or data engineering team that owns the model side, or does this role bridge both?"*

> *"Where is the FedRAMP federal region build in the process right now — is this a greenfield infrastructure build, or is the foundation already in place and this role is focused on hardening and scale?"*

> *"The JD mentions 24x7 on-call — how many engineers are currently sharing that rotation, and is the expectation that this role is on-call from day one or after a ramp period?"*

---

## Likely Technical Questions (Rounds 2+)

### System Design (confirmed from Glassdoor)

| Question | Your angle |
|----------|-----------|
| Design a FedRAMP-compliant cloud infrastructure for a SaaS product | Your bread and butter — GovCloud, ATO, STIG, network segmentation, encryption at rest/transit, audit logging, IAM least-privilege |
| How would you implement observability for a distributed system? | Lead with CloudWatch + SNS auto-remediation experience; acknowledge Prometheus/Grafana as target stack you're moving toward |
| How do you approach on-call and incident response for 24x7 infrastructure? | Wickr Enterprise sustained ops, runbooks, RCA process |
| Walk me through a CI/CD pipeline in a compliance-controlled environment | Jenkins + Artifactory + CloudFormation at GDIT — full audit trail, STIG-compliant images, artifact signing |

### Technical — Role Specific

| Question | Source | Your angle |
|----------|--------|-----------|
| How deep is your Kubernetes experience? | [inferred — JD requires 4+ years] | **Be honest:** "I understand Kubernetes conceptually — pods, deployments, services, namespaces — but I haven't operated it in depth in production. Docker is my primary container tool. ECS and EKS are not in my production background. That's a gap I'm actively closing." |
| Terraform vs CloudFormation — what's your preference? | [inferred from JD] | "CloudFormation is my primary IaC tool — I've used Terraform at Smartronix for EFS automation but CloudFormation is where my depth is. I'd be productive in a Terraform shop quickly." |
| How would you handle AI/ML infrastructure requirements? | [inferred — JD lists ML/LLM pipeline] | "My background is infrastructure, not ML engineering. What I bring is containerized workload infrastructure, IaC, and reliability — the platform that ML pipelines run on. I can scale and harden that infrastructure; I'd be direct that I'm not an ML model developer." |
| What's your Prometheus/Grafana experience? | [inferred — JD requires observability stack] | "My observability experience is CloudWatch — alarms, dashboards, SNS-driven auto-remediation. Prometheus and Grafana I understand conceptually and would ramp on quickly. The mental model is the same." |

### Behavioral (Glassdoor-confirmed process includes resume discussion)

| Question | What they're assessing | Your story |
|----------|----------------------|-----------|
| Tell me about yourself | Coherent narrative | "20 years in DoD, 9 in cloud — started as a sysadmin in the Air Force, moved into cloud engineering in 2017. The last 5 years were AWS GovCloud on Cloud One at GDIT — classified CI/CD, CloudFormation IaC, DISA STIG, ATO. I'm now targeting roles where that compliance depth is the core requirement, not a nice-to-have." |
| Tell me about your most complex infrastructure challenge | Technical depth + ownership | Wickr Enterprise on Cloud One — COTS deployment, CloudFormation, Jenkins, DISA STIG, ATO in classified GovCloud |
| Tell me about a time you improved system reliability | SRE mindset | Self-healing infrastructure at Smartronix — CloudWatch + Auto Scaling + SNS auto-remediation, eliminated unplanned downtime |
| How do you handle on-call and incident response? | 24x7 operational maturity | GovCloud incident response process — CloudWatch alerts, RCA discipline, runbooks |
| Tell me about a time you had to learn a new technology quickly | Growth mindset | Terraform at Smartronix — came from CloudFormation background, built EFS backup modules in production |

### Background Red Flags

| Likely question | Why it comes up | Recommended framing |
|-----------------|-----------------|---------------------|
| Your Kubernetes depth doesn't match 4+ years required | Direct gap in JD | "That's a fair observation — Kubernetes conceptual knowledge, not 4+ years operational depth. Docker is my production container tool. I'd own that gap directly and emphasize the compliance and IaC depth that's harder to find." |
| AI/ML infrastructure — no ML background | JD requires ML pipeline experience | "Infrastructure, not model development — I build and scale the platform ML workloads run on. That framing is what I'd bring." |
| Why are you leaving DoD contracting for a commercial company? | Career narrative | "Corelight is building a FedRAMP federal region — this isn't leaving the federal world, it's a different delivery model for the same mission. The compliance requirements are the same; the pace is faster." |

---

## Story Bank Mapping

| # | Likely question | Best story | Fit |
|---|-----------------|-----------|-----|
| 1 | FedRAMP / IL5 compliance | GDIT AWS GovCloud + ATO | **Strong** |
| 2 | CI/CD in compliant environment | Jenkins + Artifactory + CloudFormation at GDIT | **Strong** |
| 3 | Reliability / self-healing | Smartronix CloudWatch + Auto Scaling | **Strong** |
| 4 | IaC at scale | Smartronix Terraform EFS modules | **Partial** |
| 5 | Kubernetes depth | [GAP — be honest, don't fabricate] | **None** |
| 6 | Prometheus/Grafana | [GAP — acknowledge, pivot to CloudWatch] | **None** |
| 7 | AI/ML infrastructure | Wickr containerized workloads (adjacent) | **Partial** |

---

## Technical Prep Checklist

- [ ] **FedRAMP High vs Moderate** — know the difference cold. Corelight is building a federal region; they'll expect you to speak fluently about FedRAMP controls, ATO inheritance, and how that maps to your GovCloud experience.
- [ ] **Kubernetes basics refresh** — pods, deployments, services, namespaces, Helm charts. You'll be asked — know enough to have a real conversation and be honest about depth.
- [ ] **Prometheus mental model** — metrics scraping, alert rules, Grafana dashboards. Not expected to be an expert but understand the architecture vs. CloudWatch.
- [ ] **SLI/SLO/SLA definitions** — error budget, burn rate. JD mentions these explicitly. Know the definitions and have one example of availability thinking from your work.
- [ ] **Corelight product** — read corelight.com/solutions/industry/federal. Know what Open NDR is in one sentence: "network traffic analysis to detect threats that endpoint tools miss."
- [ ] **Gartner NDR Leader 2025** — mention this. Shows you follow the industry.

---

## Company Signals

**Vocabulary to use:**
- "Open NDR" — their product framing (not just "network security")
- "Federal region" — the specific infrastructure build this role owns
- "FedRAMP High" — their target compliance tier for federal customers
- "Network detection and response" — their market category
- "Zeek" — the open-source network analysis framework Corelight is built on (founded by its creator)

**Values they screen for** (Glassdoor):
- Collaborative, humble — "incredibly smart, refreshingly humble" is the recurring description
- Transparency — leadership described as "very communicative"
- Mission-driven — federal customers rely on this for real threat detection

**Things to avoid:**
- Don't oversell Kubernetes or Prometheus depth
- Don't refer to FedRAMP as something you're learning — frame it as something you've lived in a different form (GovCloud/IL5)
- Don't ask about stability — $150M Series E from Accel + Cisco + CrowdStrike is stable

**Sharp questions to ask:**
1. *"You're building a dedicated FedRAMP federal region — where is that build in the process today, and what does the infrastructure team look like around this role?"*
2. *"Corelight was named a Gartner NDR leader in 2025 — how is the federal team structured differently from the commercial side?"*
3. *"What does on-call look like for this role — is there a rotation, and how many engineers share it?"*

---

## Comp Script

If they ask:
> "I'm targeting $175K–$195K for a lead-level role with my clearance and federal compliance background. The Corelight range is well-aligned with that."

If they push for a single number:
> "$185K as a target — open to discussing the full package including equity."

---

## One-Page Cheat Sheet

**Their product:** Open NDR — network traffic analysis for threat detection. DoD, IC, and DIB customers. Building a FedRAMP federal region.
**Their stage:** Series E, $310M raised, Accel + Cisco + CrowdStrike investors. 40%+ ARR growth. Stable.
**Their need:** Someone who can own and build FedRAMP-compliant cloud infrastructure from the ground up for federal customers.
**Your hook:** "20 years in DoD, 9 in cloud. The last 5 in AWS GovCloud under IL4/IL5 — that's the same compliance posture as FedRAMP High. I've lived this."
**Your clearance:** TS/SCI — exceeds their background investigation requirement.
**Your gaps:** Kubernetes depth (conceptual, not 4+ years operational), ECS/EKS (not in production), Prometheus/Grafana (CloudWatch is your stack), AI/ML pipeline (infrastructure yes, model development no), deep networking.
**Own all gaps honestly — their technical rounds will find them.**
