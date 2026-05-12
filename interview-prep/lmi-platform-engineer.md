# Interview Intel: LMI — Platform Engineer (IronSled)

**Evaluation Report:** [#363](../reports/363-lmi-platform-engineer-ironsled-2026-05-12.md) · Score: 4.1/5
**Researched:** 2026-05-12 (initial — expand as more info arrives)
**Sources:** JD captured from invite thread; LMI public profile; IronSled product context inferred from JD

---

## Process Overview

- **Current round:** Initial screen — Teams call, scheduling in progress with Anna Keyes (TA/HR)
- **Likely process (inferred — established mid/large federal contractor):** HR/recruiter screen → Hiring manager → Technical panel (possibly with platform team) → Offer
- **Rounds total:** Likely 2-3
- **Known:** Anna initiated the invite; she may conduct Round 1 personally or hand off to a recruiter/HM. Wait for her reply to confirm.

---

## Round 1: Recruiter / HR Screen (when scheduled)

- **Duration:** 30-45 min likely
- **Conducted by:** Anna Keyes (or designate) — confirm in her reply
- **What they evaluate:** Clearance status, remote eligibility / location, comp alignment, background coherence, interest in the IronSled product and federal-DevSecOps space
- **This is NOT a technical deep-dive.** Decision is whether to advance you to hiring manager.

### What to nail in 30 minutes

1. **Open with clearance:** "I hold an active TS/SCI — exceeds the Secret requirement, no adjudication wait."
2. **Connect background to the role:** "Last 5 years I've been on AWS Cloud One — classified GovCloud, DISA STIG hardening, RMF/ATO documentation, CI/CD pipelines that gate promotion on security scans. That's exactly the DevSecOps work in this JD."
3. **Comp framing if asked:** Posted band is $101K-$173K. "Based on my background — TS/SCI, 9 years cloud, 5 in GovCloud, deep federal compliance — I'd target the upper half of the posted band, $155-170K range. I'm flexible on structure."
4. **Why LMI / Why now:** Have a 30-second answer ready. "LMI's not-for-profit, mission-first posture appeals to me. The role description maps directly to where I've been operating — and where I want to keep going."

**Note on the product name (IronSled):** It's in the JD but Anna won't grill you on product specifics in Round 1 — she's HR/recruiter. Don't volunteer claims about IronSled internals you can't back up. If she or a later technical interviewer asks what you understand about it, say what the JD says: "DevSecOps platform that streamlines accreditation for software deployed in authorized federal environments — sounds like the productized version of the pipeline + ATO work I've been doing bespoke."

---

## Likely Technical Questions (Rounds 2+)

### Technical — DevSecOps Pipelines & ATO

| Question | Source | Your best answer angle |
|----------|--------|----------------------|
| Walk me through a CI/CD pipeline you've built that gates promotion on security scans | JD Required: "conditional procedure of build and deploy pipeline based on security scans of source and artifact" | Wickr on Cloud One: Jenkins → Artifactory → STIG scan → CloudFormation → GovCloud deploy. Pipeline stages refused promotion on STIG/scan failure. |
| How have you managed STIG / RMF / ATO at scale? | JD Desired: federal security standards | DISA STIG hardening for RHEL/CentOS at GDIT. Automated compliance checks. RMF documentation lifecycle for ATO. |
| How do you handle release artifact versioning, upgrade rollout, rollback? | JD Required: "In-depth knowledge of version control of release artifacts" | Jenkins + Artifactory. Tagged artifacts. CloudFormation stack policies for safe updates. Blue/green and rollback strategies. |
| What's your GitLab CI experience? | JD Required: "Experience with GitLab CI/CD" | **Gap — be direct.** "Jenkins is my production CI/CD platform. GitLab CI's pipeline-as-code YAML, runners, and stages map directly to Jenkins concepts. Productive day one in a GitLab shop after a short ramp." |
| Walk me through your container experience | JD Required: "Strong understanding of containerization of web applications" | Docker production at GDIT. Image build, hardened base images, registry workflows. Containerizing legacy apps for ATO redeployment. |
| Tell me about your K8s / EKS / OpenShift experience | JD Required: "Understanding and familiarity with K8s (EKS, AKS, GKE, Kops, OpenShift)" | **Honest framing — softer bar.** "Kubernetes — solid on the concepts (pods, deployments, services, namespaces, RBAC, ingress) but my production container work has been Docker rather than orchestrated K8s. I'd be upfront that ramp on EKS or OpenShift in their environment would be Week 1-2 work." Don't bluff. |
| Python automation — give me an example | JD Required: 5+ yrs Python | Pick a real automation: SSM script for multi-OS app install (Smartronix), pipeline automation glue, or CloudWatch alarm/Lambda integration |
| Bash scripting | JD Required | Glue scripts in pipelines, log triage automation, AMI bootstrapping |

### Behavioral

| Question | What they're really asking | Your story |
|----------|---------------------------|------------|
| Tell me about yourself | Coherent 90-second narrative | "20 years in DoD — started Air Force sysadmin, moved into cloud around 2017. Last 9 in cloud, last 5 specifically AWS GovCloud on Cloud One at GDIT — classified CI/CD, IaC, DISA STIG, ATO. IronSled is the productization of work I've been building bespoke." |
| Tell me about an impactful automation project | "What can you show me?" | **Self-Healing Auto-Scaling** story from bank (CloudWatch + Lambda + SSM remediation). Strong for "DevSecOps culture + automate what can be automated." |
| Tell me about a hard ATO / compliance deadline | Calm under regulatory pressure | RMF/ATO cycle at GDIT — coordinating STIG hardening, scanning, POA&M remediation, documentation against a deadline |
| Tell me about a time you worked across teams | JD Required: "work with software development team and platform infrastructure team" | GDIT — coordinating across application teams, security team, government COR, change control board on Wickr Enterprise deployment |
| Tell me about a skill gap you closed | Growth mindset | Pick one: Terraform learning from CloudFormation base; or recertifying AWS SAA after lapse |

### Background Red Flags — Questions to Expect

| Likely question | Why it comes up | Recommended framing |
|-----------------|-----------------|---------------------|
| GitLab CI experience? | Listed as Required, you have Jenkins | "Jenkins is my production CI/CD background. GitLab CI is a step transferable from there — I'd be productive in a GitLab shop after a short ramp." Don't apologize for it, just frame the bridge. |
| K8s production experience? | JD lists familiarity with K8s + multiple orchestrators | "Docker is my container production background. K8s I'm conceptually solid on but haven't operated in production depth. Ramp on EKS or OpenShift is Week 1-2 work." |
| Why didn't I see this application come through our normal pipeline? | Application source unknown | Be honest about how the application originated — LinkedIn / Indeed / referral / direct — once you remember the source. |

---

## Story Bank Mapping

| # | Likely question | Best story | Fit |
|---|-----------------|-----------|-----|
| 1 | CI/CD pipeline with security scan gates | Wickr Enterprise on Cloud One | **Direct match** — your existing DevSecOps + ATO experience |
| 2 | ATO / RMF under pressure | RMF cycle at GDIT | **Strong** |
| 3 | Impactful automation | Self-Healing Auto-Scaling (Lambda + SSM + CloudWatch) | **Strong** |
| 4 | Learning new IaC tool | EFS Backup Automation (Terraform from CloudFormation base) | **Strong** — bridge framing for GitLab CI as well |
| 5 | Cross-functional collaboration | GDIT government stakeholder coordination | **Strong** |
| 6 | GitLab CI specific | [GAP — none] | **None — bridge from Jenkins** |
| 7 | K8s production | [GAP — none] | **None — be honest** |

---

## Technical Prep Checklist

- [ ] **LMI corporate context** — review lmi.org/who-we-are, /what-we-do; understand the not-for-profit / federal-mission posture (different culture from for-profit primes like GDIT/Leidos/BAH)
- [ ] **GitLab CI mental model** — review GitLab CI YAML structure, runners, stages, pipelines vs jobs. Aim for "I can read a `.gitlab-ci.yml` and follow what's happening" before any technical round.
- [ ] **K8s vocabulary refresh** — pods, deployments, services, namespaces, ingress, RBAC, ConfigMaps, Secrets. Goal: don't look blank in conversation. You're not pretending to be a K8s SRE — you're showing competent vocabulary.
- [ ] **DoD IT standards refresh** — STIG, RMF, ATO process, NIST 800-53, FedRAMP High vs IL2/IL4/IL5. You know this; review to be sharp.
- [ ] **DevSecOps philosophy** — shift-left, security scanning gates, SBOM, supply chain security (SLSA, signed artifacts). Be conversant in current best practices.
- [ ] **Army software development process** (JD Desired) — DoD Software Modernization Strategy, Software Factory model (Platform One, Iron Bank, Big Bang). Useful general DoD-DevSecOps landscape knowledge.

---

## Open Items

- [ ] Confirm Round 1 interviewer (Anna direct, or recruiter/HM handoff)
- [ ] Request prep materials / interviewer info in next email exchange
- [ ] If Round 2 confirmed as technical → schedule prep session at least 2 days prior to refresh K8s vocab + GitLab CI mental model

---

## Notes / Updates Log

- 2026-05-12: Initial invite from Anna Keyes received; reply sent with availability "most days after 1:00 PM CST"; prep brief drafted (this file)
