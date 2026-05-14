# LMI — Platform Engineer Interview Prep · Round 2

**When:** Mon 2026-05-18 at 10:30 AM CST (11:30 AM EST)
**Format:** Microsoft Teams — **panel (2 interviewers)**
**With:** **Timothy Amico** (Cloud Principal Technical Architect) + **Aakash Patel** (Platform Engineer, IronSled team)
**R1 outcome:** Cleared — see [main prep doc](./lmi-platform-engineer.md) for full background, comp anchor, story bank, what-not-to-do
**Score on file:** [#363 report](../reports/363-lmi-platform-engineer-ironsled-2026-05-12.md) · 4.1/5

**Time to R2:** Today is Thursday 2026-05-14. R2 is Monday 2026-05-18 — **1 prep day (Friday) + a weekend** before the call.
- **Friday 5/15:** Focused study on ETL + CMMC + GitLab CI + **networking refresh** (Timothy's specialty — see new section below)
- **Weekend:** Light review + story-bank refresh
- **Monday morning:** Re-read this doc once, refresh the three core stories, light pre-call routine

---

## ⚠ Read This First — Panel Composition

This is a **balanced technical panel**: senior architect + peer engineer. Each interviewer has a different evaluation lens. Address both. Don't favor one.

### Timothy Amico — Cloud Principal Technical Architect
- Senior. Designs IL2/4/5 cloud environments meeting FedRAMP and NIST requirements
- Works with **both AWS and Azure** at LMI
- Holds **AWS Certified Advanced Networking — Specialty**
- Career path: Senior Infrastructure Engineer → Cloud Principal Technical Architect

**What he'll probe:**
- Cloud architecture depth (multi-account, networking, IAM, security boundaries)
- Networking — his specialty cert, expect a real question here
- IL/FedRAMP/NIST architecture — your wheelhouse, be sharp
- Multi-cloud — Azure question is likely. Have honest framing ready (you're AWS-only)
- How you reason about trade-offs at architecture level

**Bridge to him:** "Your background in IL2/4/5 design is exactly the work I've been operating against on Cloud One — STIG hardening, RMF documentation, FedRAMP-equivalent boundary management."

### Aakash Patel — Platform Engineer, IronSled team
- Peer-level. Recent Rutgers Computer Engineering grad (March 2026)
- NYC-based
- **Was actively recruiting for this same role** — he's hiring his own teammate
- Likely an Aakash-as-future-collaborator screen, not Aakash-as-deep-evaluator

**What he'll probe:**
- Day-to-day work compatibility — what's it like to pair with you?
- Hands-on technical fluency (vs architecture)
- Team-fit, communication style, how you handle being unblocked / blocked
- Practical IronSled-flavored work scenarios

**Bridge to him:** Match his energy. He's a working engineer, not a senior architect. Be conversational, share concrete experience, ask about how the team actually operates day-to-day.

### Panel dynamics — tactical

- **Eye contact:** Look at whoever asked the question while answering. Glance to the other person briefly mid-answer to include them. Don't stare at one for the whole answer.
- **Name them when natural:** "Tim, to your earlier point about networking..." or "Aakash, you mentioned the IronSled pipeline — does that mean..."
- **Don't favor the senior one** — this is a common candidate mistake. Aakash gets equal time and attention.
- **If they trade off questions clearly:** they've coordinated. Each has a lane. Honor that — give substantive answers to both lanes.
- **If one dominates:** that's a signal too. Don't try to redirect; let the dynamics play out.
- **Final question slot:** ask one question for each of them, not just one for the room. "Tim, I'd love your read on... Aakash, from your perspective..." Show you see them as two distinct contributors.

---

---

## What R2 Likely Looks Like

You don't know yet. But based on the role and the way HM rounds usually escalate at federal contractors, R2 is most likely one of:

| Interviewer type | What to expect |
|---|---|
| Senior engineer / tech lead on the IronSled team | Whiteboard-style design discussion, walk through a project end-to-end, "how would you handle X" scenarios |
| Director or VP-level | Bigger-picture: strategy, mission alignment, "why platform engineering matters," team leadership posture |
| Cross-functional panel | Mix of the above, multiple perspectives, longer (60-90 min) |

**Default assumption:** Senior engineer technical screen, 45-60 min, Teams. Camera on. Same no-AI-tools / no-notes policy as R1.

---

## Primary Prep — Your Self-Identified Gaps

### ETL (you flagged this)

**Why it matters here:** IronGate = commercial-to-IL data bridge. Moving data from commercial sources into IL environments is a constrained ETL problem (with security, classification, and compliance constraints layered on top).

**The 80/20 you need:**

| Concept | What to know |
|---|---|
| **ETL vs ELT** | ETL = transform before loading (legacy pattern, schema-on-write, good for highly regulated targets). ELT = load raw then transform in target (modern pattern, schema-on-read, good for analytics warehouses). For commercial→IL movement, ETL is more likely — you want to transform/sanitize/redact BEFORE crossing the boundary. |
| **Batch vs stream** | Batch = process in chunks on a schedule (nightly, hourly). Stream = process events as they arrive (Kafka, Kinesis). Most federal data movement is batch; some real-time intel/sensor pipelines are stream. |
| **Common patterns** | Source connector → staging → transform → load → validation → audit log. Idempotency matters. Replay safety matters. Data lineage tracking is a federal compliance requirement in many cases. |
| **Common AWS tools** | Glue (managed ETL service, supports Spark), Lambda (lightweight transforms), Step Functions (orchestration), DataSync (bulk transfer), DMS (DB migration). For IL environments, GovCloud equivalents. |
| **Open-source tools** | Airflow (workflow orchestration), dbt (transformation in-warehouse), Apache NiFi (visual data flow — popular in DoD for data ingestion). NiFi specifically is worth knowing — it's used heavily in IC/DoD for cross-domain data movement. |

**What to say if asked about your ETL background:**

> "My data-engineering work has been more on the supporting infrastructure side than building data pipelines themselves — I've built the AWS infra that ETL workloads run on, handled IAM and networking for cross-account data flows, and operated Lambda/Step Functions for lightweight automation. I haven't owned end-to-end ETL pipelines in production — that's an honest ramp area for me. The IronGate use case is interesting because it's not pure ETL, it's also a security/compliance crossing problem."

**Connect to a real story:** EFS Backup Automation at Smartronix — Terraform modules, SSM automation for multi-OS application installs. That's not ETL, but it's data movement automation in a constrained environment.

---

### CMMC (you flagged this)

**Why it matters here:** LMI holds CMMC 2.0 Level 2 certification — perfect-score per public news. As a federal contractor handling CUI, CMMC is part of their compliance posture. You should be conversant enough to discuss how CMMC fits alongside FedRAMP, DISA SRG, and ATO.

**CMMC 2.0 levels (what changed from 1.0):**

| Level | Old name (1.0) | What it covers | Source standard |
|---|---|---|---|
| **Level 1** | Foundational | 17 basic controls. Federal Contract Information (FCI) only. Self-assessed annually. | FAR 52.204-21 |
| **Level 2** | Advanced | 110 controls. Controlled Unclassified Information (CUI). C3PAO assessment every 3 years. | NIST SP 800-171 |
| **Level 3** | Expert | 110 + ~24 enhanced controls. CUI in critical programs (top-tier defense). DIBCAC assessment every 3 years. | NIST SP 800-171 + NIST SP 800-172 |

**Note:** CMMC 2.0 dropped Levels 2 and 4 from the original 5-level model. Don't reference Levels 4 or 5 — they don't exist in 2.0.

**How CMMC relates to other compliance frameworks:**

| Framework | What it is | Where it fits |
|---|---|---|
| **CMMC** | Cybersecurity Maturity Model Certification | DIB contractor cybersecurity baseline. Required to bid on contracts handling FCI/CUI. |
| **NIST SP 800-171** | The control catalog CMMC L2 implements | DFARS 252.204-7012 has required this since 2017; CMMC adds the audit/certification layer |
| **NIST SP 800-53** | Federal information system controls | Used for FedRAMP and federal agency systems (not contractor systems) |
| **FedRAMP** | Authorization for cloud services to federal agencies | Cloud provider compliance — Low / Moderate / High baselines |
| **DISA SRG / IL** | DoD-specific cloud impact levels | IL2 (public), IL4 (CUI), IL5 (CUI + national security), IL6 (Secret) — IronSled targets IL4 + IL6 |
| **STIG** | Security Technical Implementation Guide | Hardening checklists for OS / app configurations. Used inside ATO process. |
| **RMF** | Risk Management Framework | The process for getting an ATO — Categorize → Select → Implement → Assess → Authorize → Monitor |

**What to say if asked:**

> "CMMC L2 is essentially NIST 800-171 with an audit layer — 110 controls, CUI handling, C3PAO assessment. It's a contractor-facing standard, where FedRAMP / DISA SRG sit on the cloud-provider side and STIG / RMF cover the system-implementation side. They're complementary — a fully accredited federal app deployment touches all of them. IronSled's positioning makes sense in that context: a platform that bakes the controls into the pipeline so the audit evidence is generated as a side effect of normal operations."

**Don't claim:** that you've personally led a CMMC assessment, or that you've worked with the C3PAO process directly. Honest framing: "I've worked inside ATO environments where the contractor's CMMC posture mattered, but the assessment itself was handled by the compliance team."

---

## Secondary Prep — Likely R2 Surface Area

### GitLab CI/CD (Required per JD — your real gap)

**The 80/20:**

| Concept | What to know |
|---|---|
| **`.gitlab-ci.yml`** | Pipeline-as-code, lives at repo root. Top-level keys: `stages`, `variables`, `before_script`, `after_script`, plus job definitions. |
| **Stages** | Sequential phases (build → test → scan → deploy). Jobs in the same stage run in parallel. |
| **Jobs** | Individual units of work. Each has a `script:` (commands to run), optionally `image:` (container), `rules:` or `only:`/`except:` (when to run), `artifacts:` (what to pass to next stage). |
| **Runners** | Compute that executes jobs. Shared (GitLab's), group-level, or project-specific. Self-hosted runners common in regulated envs. |
| **Caches and artifacts** | Cache = optional speedup, can be missing. Artifact = required handoff between jobs/stages. |
| **`include:`** | Pull in pipeline templates from other repos. Common for shared pipeline patterns across many projects. |
| **CI/CD variables** | Project-, group-, or instance-level. Can be masked, protected (only on protected branches), or environment-scoped. |
| **Environments + deployments** | First-class concept. Lets you map jobs to env (`staging`, `production`), do reviews, manual approvals, rollbacks. |

**Mental model:** GitLab CI is conceptually similar to Jenkins (which you know). Differences:
- Pipeline definition lives WITH the code (`.gitlab-ci.yml` in repo) vs Jenkins where Jenkinsfile is in repo but pipeline config is often in Jenkins itself
- Runner model is more declarative (tags route jobs to runner pools)
- Native concepts for environments and deployments — Jenkins requires plugins for this

**What to say:**

> "Jenkins is my production CI/CD platform — built and operated pipelines with Artifactory integration, security scan gates, environment promotion. GitLab CI uses a similar mental model: stages, jobs, runners, environments, with pipeline-as-code in `.gitlab-ci.yml`. The `include:` mechanism for shared pipeline templates is something I'd want to lean on heavily for a platform team supporting many app deployments. Productive in a GitLab shop after a short ramp."

**Don't bluff:** if asked about a specific GitLab feature you don't know (auto DevOps, GitLab Pages, specific runner executor types), say "haven't used that one personally — what's the context?" Honest deflection > making things up.

---

### Python Automation (Required 5+ years)

You have this. Just be sharp on framing. The JD calls out: "debug, optimize code, and automate routine tasks."

**Have ready:**

- One example of a Python script you wrote that automated a real production task. SSM automation for multi-OS app installation at Smartronix is a candidate. Or any AWS Lambda / CloudWatch / boto3 work.
- One example of debugging Python in production. Doesn't need to be glamorous — just real.
- One example of optimization. Could be cutting Lambda cold starts, batching API calls, parallel processing.

**Don't claim:** ML/data-science Python depth (pandas/numpy/scikit). You're a systems-Python engineer, not a data engineer.

---

### Networking (NEW — Timothy's specialty cert is AWS Advanced Networking)

This is your **documented weak area** per memory. Timothy will probe it. Get the honest framing rock-solid before Monday.

**The 80/20 you need to be conversant on:**

| Concept | What to know |
|---|---|
| **VPC** | Virtual Private Cloud — isolated network in AWS. CIDR block (e.g., `10.0.0.0/16`). One VPC per account is common; multi-VPC is for separation. |
| **Subnets** | Slice of VPC. Public (route to IGW) vs private (no IGW). Across multiple AZs for HA. |
| **Internet Gateway / NAT Gateway** | IGW = public ingress/egress. NAT GW = private subnets reaching the internet outbound only (no inbound). |
| **Security Groups vs NACLs** | SG = stateful, instance-level, allow-only rules. NACL = stateless, subnet-level, allow + deny rules. SGs are the primary tool; NACLs are fallback. |
| **Route Tables** | Per-subnet (or default). Determines where traffic goes — VPC-local, IGW, NAT, VPN, peering, transit gateway. |
| **VPC Peering** | Direct routing between two VPCs. Doesn't transit (no chains). Cross-account/cross-region supported. |
| **Transit Gateway** | Hub for many VPCs and on-prem. Replaces complex peering meshes. Common in federal multi-account architectures. |
| **VPN / Direct Connect** | VPN = encrypted tunnel over internet. Direct Connect = dedicated line. Both terminate at Virtual Private Gateway or Transit Gateway. |
| **PrivateLink / VPC Endpoints** | Private access to AWS services or third-party services without traversing the internet. Critical in IL4+/GovCloud where egress is restricted. |
| **DNS — Route53 + Route53 Resolver** | DNS service. Resolver handles VPC ↔ on-prem DNS resolution. Important for hybrid setups. |

**What to say if Timothy probes deep:**

> "Networking is honestly the area I've operated within rather than designed end-to-end. On Cloud One I've worked inside well-bounded VPC environments — security groups, private subnets, VPC endpoints for AWS service access without internet egress. I can reason about routing, security groups vs NACLs, and the basic ingress/egress patterns. Where I'd lean on someone with deeper expertise like yourself is on transit gateway architecture, multi-region failover design, and complex DNS. That's an area I'd want to grow into."

**Why this works:**
- States the gap honestly without apologizing
- Names what you DO know (VPCs, SGs, endpoints, classified-egress patterns — all real)
- Compliments his expertise without being sycophantic ("someone with deeper expertise like yourself" — said once, naturally)
- Frames it as growth area, not blocker

**Don't bluff:** if asked about a specific advanced topic (BGP routing, AWS Network Firewall, Gateway Load Balancer, transit gateway route propagation), say "I haven't worked with that one in production — what's the IronSled use case?" Honest deflection > making things up. Timothy will see through bluffing immediately.

---

### Multi-cloud / Azure (NEW — Timothy works AWS + Azure at LMI)

Thomas is AWS-only. Azure question is likely. Honest framing:

> "AWS is my production background — 9 years total, 5 specifically in GovCloud. I haven't worked with Azure in production. The concepts transfer (VNet ≈ VPC, NSG ≈ Security Group, Azure AD ≈ IAM with different model), and I'm a fast learner — but I'd be honest day one that Azure is a ramp area, not a strength."

**Don't claim:** Azure cert progress, Azure conceptual depth beyond mapping. Timothy will know.

---

### K8s Vocabulary (JD says "familiarity")

You've already got the honest framing in the R1 doc. Refresh the vocab so you don't go blank in conversation:

| Term | One-line |
|---|---|
| **Pod** | Smallest deployable unit. Usually one container per pod, sometimes sidecars. |
| **Deployment** | Manages pod replicas + rolling updates. Most common workload type. |
| **Service** | Stable network endpoint for a set of pods. ClusterIP / NodePort / LoadBalancer. |
| **Ingress** | HTTP routing into the cluster from outside. NGINX, Traefik, etc. |
| **Namespace** | Logical isolation within a cluster. RBAC and resource quotas often per-namespace. |
| **ConfigMap / Secret** | Inject non-secret config / secret config into pods at runtime. Secrets are base64, not encrypted by default — use KMS / sealed-secrets / vault for real protection. |
| **RBAC** | Roles and RoleBindings (namespace) or ClusterRoles/ClusterRoleBindings (cluster-wide). |
| **StatefulSet** | Like Deployment but for stateful workloads (databases). Stable pod identity, ordered rollout. |
| **DaemonSet** | One pod per node. Used for log collectors, monitoring agents. |
| **Helm** | Package manager for K8s. Charts = templated YAML manifests. |

**What to say:**

> "Docker is my container production background. K8s I'm conceptually solid on — pods, deployments, services, RBAC, namespaces, ingress — but I haven't operated it in production depth. Ramp on EKS or OpenShift is Week 1-2 work for me. I can read manifests and reason about behavior; I can't yet debug a misbehaving cluster fluently."

---

### DevSecOps Philosophy (JD: "embrace the DevSecOps culture")

The hiring panel will want to hear how you think about DevSecOps as a discipline, not just tools.

**Talking points (memorize the gist, don't recite verbatim):**

- **Shift-left security** — security gates in dev/build pipeline, not bolted on at deploy. Catches issues when they're cheap to fix.
- **Pipeline as the policy enforcement point** — if a scan fails, promotion blocks. The pipeline is the gate, not a human reviewer.
- **Automation first** — anything done twice should be automated. Anything fragile should be hardened. Manual remediation is technical debt.
- **Observability + remediation loop** — detection → action → observation → tuning. The Self-Healing Auto-Scaling story (CloudWatch + Lambda + SSM) is exactly this loop.
- **SBOM + supply chain security** — know what's in your artifacts. SLSA framework, signed artifacts, dependency scanning (Dependabot, Snyk, etc.). Federal supply chain security is increasingly load-bearing post-SolarWinds.
- **The audit trail is a side effect** — if you have to assemble compliance evidence at audit time, your pipeline isn't doing its job. The artifacts (build logs, scan results, deployment records) ARE the evidence.

**Tie back to your work:**

> "On Wickr Cloud One, the pipeline was the policy enforcement point — STIG scan failures blocked promotion automatically. The artifacts produced by the pipeline (scan results, signed builds, deployment logs) doubled as ATO evidence. That's the same pattern IronSled is selling — bake the controls in, not bolt them on."

---

### DoD Compliance Landscape (Your Strong Area — Be Sharp)

You know this. Don't over-prep. But have the relationships clean in your head:

```
ATO process     RMF (NIST 800-37)
Controls        NIST 800-53 (federal systems) | NIST 800-171 (contractor CUI)
Hardening       DISA STIG (system configs)
Cloud           FedRAMP (Low/Mod/High) | DISA SRG IL2/4/5/6
Contractor      CMMC 2.0 (L1/L2/L3)
Apps            Application-specific STIGs, CIS benchmarks
```

**Quick relationships to verbalize:**
- FedRAMP is for cloud providers selling to federal agencies; DISA IL is the DoD-specific overlay
- IL4 ≈ FedRAMP Moderate baseline + CUI handling; IL5 = High baseline + national security; IL6 = Secret classification (different network entirely)
- CMMC L2 = NIST 800-171 with C3PAO certification; required to handle CUI as a contractor
- RMF is the *process*, NIST 800-53/171 are the *controls*, STIG is the *implementation*
- An ATO is the output of running RMF successfully

---

## Tertiary Prep — Only If Time

### LIGER / AI Infra Adjacency

LIGER is in LMI's product portfolio. R2 may or may not touch it, but the AI-in-your-work conversation probably will.

**Quick LIGER context:**
- GenAI platform, RAG architecture, IL5
- Active Army contract (DASA-DES — Deputy Assistant Secretary for Data, Engineering, Software)
- Use cases: market research automation, contract writing, decision support
- Sectors: defense, health, civilian, intel

**If asked about AI infra:** lean on the AI-in-your-work section from the R1 doc. Honest framing: you've built the foundation (automated remediation, observability) that AIOps builds on, but you haven't operated production ML systems.

### Army Software Factory Ecosystem

The JD lists "knowledge of the Army software development process" as Desired. If your R2 interviewer is Army-focused, this comes up.

**The big three to know by name:**

| Thing | What it is |
|---|---|
| **Platform One** | Air Force-led DevSecOps platform initiative. Provides Iron Bank (hardened containers), Big Bang (K8s reference architecture), Party Bus (managed environment). Used across DoD. |
| **Iron Bank** | Hardened, scanned, signed container image registry. Mandatory source for many DoD container deployments. |
| **Big Bang** | Reference K8s configuration with security baked in (Istio, Kyverno, etc.). |

**Connection to LMI:** IronSled is conceptually adjacent to Platform One — both are "DevSecOps factories" for federal use. LMI built theirs; Platform One is government-built. Knowing Platform One exists and how IronSled is positioned relative to it is a small but real signal.

---

## Likely R2 Questions (Inferred from Pattern + Role + Panel Composition)

### From Timothy (Architect lens)

- "Walk me through how you'd architect a CI/CD pipeline for an application going through ATO."
- "Describe the network topology of an environment you've worked in — VPC layout, security boundaries, service-to-service traffic."
- "How would you handle secrets management in a regulated environment?"
- "How do you think about observability in a system where you can't ship logs to the public internet?"
- "How does FedRAMP Moderate differ from DISA IL4 in practice?"
- "If you were architecting IronSled from scratch today, what would you prioritize?"
- "What's your experience with multi-account / multi-VPC AWS architectures?"
- **"What's your Azure experience?"** → honest framing
- **"How comfortable are you with networking deep-dive — transit gateways, VPC endpoints, hybrid DNS?"** → honest framing

### From Aakash (Peer / day-to-day lens)

- "What's your day-to-day workflow look like? IDE, terminal, AI assistants, anything you wouldn't give up?"
- "Walk me through a recent script or pipeline you wrote — what did it do, what was hard about it?"
- "Tell me about a time you had to pick up a new technology fast in a real project."
- "How do you handle being blocked? What's your default move?"
- "What's your code review philosophy — what do you look for, what do you push back on?"
- "How would you approach onboarding a new application onto IronSled?"
- "What's something you've automated recently that saved your team time?"
- "What's your relationship with on-call been like?"

### Cultural / Mindset (either could ask)

- "What does 'platform engineering' mean to you?"
- "How do you balance velocity vs safety in a regulated environment?"
- "Tell me about a disagreement with a security or compliance person — how did you handle it?"
- "What's the difference between operating someone else's product vs building one?" (← honest answer: you're moving from the first to the second; speak to the bridge, not the gap)
- "Why LMI specifically — why not stay at a big prime?"

### Probing for Gaps (either may ask)

- "How comfortable are you with Kubernetes in production?" → honest framing
- "Have you done much GitLab CI?" → bridge framing from Jenkins
- "What's your experience with ETL workloads?" → "infrastructure side, not pipeline side" framing
- "Do you have hands-on experience with CMMC assessments?" → "Worked inside CMMC-required environments; the assessment itself was the compliance team's lane."
- **"What's your networking depth?"** → honest framing (see networking section)
- **"How fluent are you with Azure?"** → honest framing (AWS-only, ramp area)

---

## Stories to Refresh Before R2

Same story bank as R1 (`interview-prep/story-bank.md`), but R2 may want more depth. Re-read these tonight so the details are sharp:

| Story | Why it matters more in R2 |
|---|---|
| **Wickr Enterprise on Cloud One** | The single closest match to IronSled's customer pattern. Be ready to go DEEP — how the pipeline was structured, what scan gates fired, how STIG hardening was applied, how the team coordinated across security/compliance/application teams. |
| **Self-Healing Auto-Scaling** | The strongest "tell me about an impactful automation" story. Be ready to talk about the failure mode (transient signals → premature termination), the fix (tighter eval periods + circuit-breaker), and what that taught you about safe automation. |
| **EFS Backup with Terraform at Smartronix** | Useful if asked about learning a new tool quickly. Same shape works for the GitLab CI ramp story. |
| **RMF/ATO cycle at GDIT** | Have a clean version ready — what the cycle looked like, where you owned vs supported, how you handled deadline pressure. |

---

## Before R2 — Action Items

**Friday 5/15 (your real prep day):**
- [ ] Read this entire doc once carefully
- [ ] **Networking refresh** — go through the networking table above; make sure you can speak fluently about VPCs/SGs/NACLs/endpoints/peering vs transit
- [ ] **ETL primer** — read through the ETL section; have one example of "data movement infra you've built" ready
- [ ] **CMMC primer** — memorize the L1/L2/L3 distinction and the relationships table
- [ ] **GitLab CI** — skim a sample `.gitlab-ci.yml` (any open-source repo); be able to follow what a stage/job does
- [ ] Refresh the three story-bank stories (Wickr, Auto-Scaling, EFS)

**Weekend (light):**
- [ ] Skim Platform One's Iron Bank product page (10 min — `https://p1.dso.mil/products/iron-bank`)
- [ ] Glance at Apache NiFi's project page (5 min — context for IronGate)
- [ ] Look up Timothy Amico and Aakash Patel on LinkedIn for additional context (10 min total)
- [ ] Brain rest — don't keep grinding

**Monday morning (T-2 hours):**
- [ ] Re-read this doc once
- [ ] Quick mental rehearsal of the 5-cold-answers (clearance / TMAY / why-leaving / comp / AI-in-your-work) plus the **3 honest-framing scripts** (networking gap, Azure gap, K8s gap)
- [ ] Pre-call routine from main prep doc

**Don't over-prep.** R2 is a conversation, not an exam. The goal is to sound like someone who's done this work and is honest about gaps — not to perform encyclopedic recall.

---

## Reminders from R1

- Camera on full duration
- No prep doc visible during call
- No AI assistants running
- Comp anchor stays $155–170K within posted band ($101,145–$173,000)
- Honest framing on K8s production gap and GitLab CI experience
- Lead questions: success criteria for R2 interviewer + portfolio fit clarification (e.g., "How does IronGate connect to IronSled's pipeline architecture?")
