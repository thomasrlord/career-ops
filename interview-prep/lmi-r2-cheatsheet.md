# LMI R2 Cheat Sheet

**Mon 2026-05-18, 10:30 AM CDT (11:30 AM EDT) · Teams · Panel: Timothy Amico (Cloud Principal Tech Architect) + Aakash Patel (Platform Engineer, peer)**

Camera on full duration. No notes visible. No AI assistants running.

---

## 🎤 60-90 Second Pitch (the "Tell Me About Yourself" Answer)

Practice until it sounds natural, not memorized. Target ~75 seconds spoken. Don't recite your résumé — they have it. **Stay product-neutral** — this round is fit discovery; let the conversation surface where you'd land.

**The message you want to land:** seasoned IT veteran. Adapts to what the team needs. Catches on quick. Contributes early. Not a one-stack specialist; not stuck in their ways.

> "I'm an IT veteran — 20 years across DoD environments, the last 9 in AWS, the last 5 in GovCloud at GDIT on the Cloud One program. The technical work I'd point to: CloudFormation IaC, Jenkins/Artifactory pipelines, DISA STIG hardening, RMF/ATO documentation, and automated remediation with Lambda and SSM.
>
> What I'd want to convey beyond the résumé is how I've worked across that span. I've come up through systems administration, virtualization, cloud engineering, and now DevOps platform work — every step has been a new stack and a new mission context. I learn fast, contribute early, and adapt to what the team actually needs rather than insisting on a particular tool or approach.
>
> Honest about ramp areas — GitLab CI, Kubernetes in production depth, Azure — but the patterns transfer, and I'd rather get productive on what your team is doing than hold out for a perfect tool match."

**Coaching notes:**
- ~175 words. At a natural pace this is 70-80 seconds. If you're rushing, you're nervous — slow down, you have the time.
- **The heart of the pitch is paragraph 2** — "adapt to what the team actually needs" is the line that should land. If you under-pace anywhere, slow there.
- Pause after the first sentence. Don't blur "20 years across DoD environments" into the next clause.
- "Cloud One" name-drops — they'll likely know it.
- "IT veteran" can read as either deeply experienced or set-in-their-ways — paragraph 2 disproves the second read. Don't rush past it.
- If Tim or Aakash interrupts mid-pitch with a follow-up, **stop and answer it.** Don't fight to finish. The pitch is a vehicle; the conversation is the goal.

---

## 🎯 Honest-Framing Scripts (Memorize These — They're the Whole Game)

The panel will probe gaps and motivation. These scripts are your safety net. Read them out loud until they feel natural, not rehearsed.

### 1. Networking depth (Timothy will probe — his cert specialty)

> "Networking is honestly the area I've operated within rather than designed end-to-end. On Cloud One I've worked inside well-bounded VPC environments — security groups, private subnets, VPC endpoints for AWS service access without internet egress. I can reason about routing, SGs vs NACLs, basic ingress/egress patterns. Where I'd lean on deeper specialty expertise is on transit gateway architecture, multi-region failover design, complex DNS. That's an area I'd want to grow into."

### 2. Azure / multi-cloud (Timothy works both at LMI)

> "AWS is my production background — 9 years total, 5 in GovCloud. I haven't worked with Azure in production. The concepts transfer (VNet ≈ VPC, NSG ≈ Security Group, Azure AD ≈ IAM with a different model), and I'm a fast learner — but day one I'd be honest that Azure is a ramp area, not a strength."

### 3. Kubernetes in production (JD soft bar)

> "Docker is my container production background. K8s I'm conceptually solid on — pods, deployments, services, RBAC, namespaces, ingress — but I haven't operated it in production depth. Ramp on EKS or OpenShift is Week 1-2 work for me."

### 4. GitLab CI (JD required, you have Jenkins)

> "Jenkins is my production CI/CD platform — pipelines with Artifactory, security scan gates, environment promotion. GitLab CI uses a similar mental model: stages, jobs, runners, environments, with pipeline-as-code in `.gitlab-ci.yml`. The `include:` mechanism for shared pipeline templates is something I'd lean on heavily for a platform team supporting many app deployments. Productive in a GitLab shop after a short ramp."

### 5. ETL background

> "My data-engineering work has been more on the supporting infrastructure side than building data pipelines themselves — I've built the AWS infra ETL workloads run on, handled IAM and networking for cross-account flows, operated Lambda/Step Functions for lightweight automation. I haven't owned end-to-end ETL pipelines in production — that's an honest ramp area."

### 6. Why IronSled specifically (if asked about product interest)

The panel is IronSled-anchored — Aakash is on the team. Expect a probe on what specifically interests you about the product. Answer honestly without over-committing.

> "From what George described in R1, IronSled is the closest match to what I've actually built — productizing the DevSecOps pattern I ran bespoke on Cloud One. That's a real draw. I came in open though — I'd rather use this conversation to figure out where I fit best across your work than assume I know after one chat."

**Why this works:** Names a real, specific reason for genuine interest (not generic enthusiasm). Doesn't lock in IronSled at the expense of other LMI work. Frames the round as discovery, which is what you actually want.

### 7. Timeline / competing offer (likely to surface — BAH offer letter is in writing, deadline 2026-05-22)

> "I'm in late-stage conversation with another federal employer where I have a written offer in hand. I haven't shared specifics out of respect for both processes. I'm continuing with LMI because the IronSled work and team are a better strategic fit for where I want to grow — but the other side does have a near-term decision window. If LMI extends an offer, I'd want the timelines to align so I can make the right decision rather than a rushed one."

**Why this works:** Honest (BAH offer is real), preserves dignity (no company/dollar disclosure), signals you need LMI to move with some pace without manufacturing pressure. **Use this only if asked** — don't volunteer it.

**Universal fallback for anything specific you don't know:**
> "I haven't worked with that in production — what's the use case at LMI?" (Honest deflection beats bluffing every time.)

---

## Networking Reference (Timothy's Lane)

### Core concepts (one-liners)

- **VPC** = isolated virtual network, CIDR block (e.g. `10.0.0.0/16`)
- **Subnet** = AZ-scoped slice of VPC. Public = route to IGW. Private = no IGW.
- **IGW** = bidirectional public traffic. **NAT GW** = outbound-only from private subnets.
- **Route Table** = decides destinations: VPC-local, IGW, NAT, peering, TGW, VPN
- **VPC Peering** = 1:1, no transit. **TGW** = hub for many VPCs + on-prem.
- **VPN** = IPsec tunnel over internet. **Direct Connect** = dedicated line.
- **VPC Endpoints / PrivateLink** = private AWS service access without internet egress (critical in IL4+/GovCloud — you've operated this on Cloud One)
- **Route53 Resolver** = DNS for VPC ↔ on-prem hybrid

### SG vs NACL (the question you might get)

|  | Security Group | NACL |
|---|---|---|
| Scope | Instance / ENI | Subnet |
| State | Stateful | Stateless |
| Rules | Allow only | Allow + deny |
| Use as | Primary tool | Defense-in-depth |

### What you DO know — don't undersell

VPC + subnet design within regulated env · SG/NACL practical use · VPC endpoints for AWS access without egress · Cloud One networking operations · public/private subnet patterns · NAT/IGW basics

---

## CMMC + Compliance Landscape

### CMMC 2.0 levels (L4/L5 don't exist anymore — don't reference them)

| Level | Covers | Standard | Assessment |
|---|---|---|---|
| **L1** | FCI (basic federal info) | FAR 52.204-21 | Self-assessed annually |
| **L2** | CUI | NIST 800-171 | C3PAO every 3 years |
| **L3** | CUI in critical programs | 800-171 + 800-172 | DIBCAC every 3 years |

**LMI holds CMMC 2.0 Level 2 — perfect-score certification.**

### Framework relationships (one-liners)

- **CMMC vs NIST 800-171?** CMMC L2 implements 800-171; CMMC adds the audit/cert layer
- **NIST 800-53 vs 800-171?** 800-53 = federal systems (used by FedRAMP). 800-171 = contractor systems holding CUI.
- **FedRAMP vs DISA IL?** FedRAMP = federal cloud baselines (Low/Mod/High). DISA IL = DoD-specific overlay (IL2/4/5/6).
- **IL4** ≈ FedRAMP Mod + CUI. **IL5** = High + national security CUI. **IL6** = Secret (separate network).
- **RMF** = the *process* (Categorize→Select→Implement→Assess→Authorize→Monitor). 800-53/171 = the *controls*. STIG = the *implementation*.
- **ATO** = output of running RMF successfully. **POA&M** = list of known control gaps + remediation timelines.

### Why this work matters (use if asked "why is this kind of work meaningful")

> "The hardest part of ATO work isn't the technology — it's the timeline. Months of paperwork to get an app deployed when the technical change might be weeks of engineering. Anything that collapses that timeline — inheriting from a pre-accredited platform, standardized pipelines, reusable hardening — is a real lever for federal teams. That's the kind of work I want to be doing next."

---

## GitLab CI (Jenkins Bridge)

### Mental model translation

| Jenkins | GitLab CI |
|---|---|
| `Jenkinsfile` (in repo) | `.gitlab-ci.yml` (in repo) |
| Jenkins agents | GitLab Runners |
| Pipeline stages | `stages:` block |
| Plugins for env/deploy | First-class `environment:` + `deployments:` |
| Shared libraries | `include:` directive |
| Credentials plugin | CI/CD variables (masked / protected) |

### Annotated mini-sample

```yaml
stages: [build, test, scan, deploy]   # sequential phases

build_app:
  stage: build
  script: [pip install -r requirements.txt, python -m build]
  artifacts:
    paths: [dist/]                    # handoff to next stage

security_scan:
  stage: scan                         # YOUR ATO GATE
  image: aquasec/trivy:latest
  script: [trivy fs --exit-code 1 --severity HIGH,CRITICAL .]
  # Pipeline blocks promotion if scan fails (exit 1)

deploy_staging:
  stage: deploy
  script: [./deploy.sh staging]
  environment: { name: staging }
  only: [main]
  when: manual                        # human approval gate
```

### Key concepts to be fluent on

- **`stages:`** sequential, jobs in same stage parallel
- **`artifacts:`** required handoff between stages
- **`environment:`** first-class env tracking (rollback, history, manual approval)
- **`include:`** pull pipeline templates from other repos — **your platform-team lever**
- **Runner tags** route jobs to specific pools (e.g., `tags: [govcloud-runner]`)

### Don't bluff on

GitLab Auto DevOps · GitLab Pages · specific runner executor types · Container Registry · GitLab DAST/SAST features

---

## ETL + Data Movement (Federal Context)

### Key one-liners

- **ETL** = transform before load (regulated targets, boundary crossings)
- **ELT** = load raw, transform in target (modern warehouses, schema-on-read)
- **Batch** = scheduled chunks (most federal). **Stream** = real-time events (Kafka/Kinesis).
- **For commercial-to-IL boundary crossing:** ETL pattern; you can't land arbitrary data inside IL and clean later

### AWS tools (compressed)

Glue (Spark ETL) · Lambda (lightweight) · Step Functions (orchestration) · DataSync (bulk transfer) · DMS (DB migration/CDC) · Kinesis Firehose (stream→S3) · EventBridge (event routing). GovCloud equivalents for all in IL.

### Apache NiFi — Worth Knowing By Name

Built by NSA (originally "Niagarafiles"), open-sourced 2014. **Heavy in DoD/IC for cross-domain data movement.** Visual flow design, built-in data provenance/lineage tracking (compliance gold), supports cross-domain solutions for IL boundary crossing.

If asked about NiFi:
> "I'm aware of NiFi as a common DoD/IC tool for cross-domain data movement, especially with the provenance tracking it provides for compliance. Haven't operated it in production — would be a ramp area if it's part of the stack here."

---

## Story Bank Quick Pick (See `interview-prep/story-bank.md` for Full)

| If asked about... | Lead with |
|---|---|
| Most impactful project | **Wickr Enterprise on Cloud One** (CFN + Jenkins + Artifactory + STIG + ATO — DevSecOps platform pattern) |
| Automation you're proud of | **Self-Healing Auto-Scaling** (CloudWatch + Lambda + SSM auto-remediation) |
| Learning a new tool | **EFS Backup with Terraform at Smartronix** (CloudFormation → Terraform jump) |
| Compliance under pressure | **RMF/ATO cycle at GDIT** |
| Cross-functional work | **GDIT government stakeholder coordination** |

---

## Panel Tactics (Don't Forget)

- **Eye contact:** look at whoever asked, glance to the other mid-answer to include them
- **Name them when natural:** "Tim, to your earlier point..." or "Aakash, you mentioned..."
- **Aakash is your peer, not a junior.** He's the team's voice on what the work *actually* looks like day-to-day. Ask him things you genuinely want his answer on. Don't lecture; don't soften technical content for him.
- **If Tim throws a design prompt** ("how would you design X"), clarify scope first — "what's the IL level, scale, failure mode I'm designing for?" — before sketching. Architects respect requirements-first thinking over jumping to a diagram.
- **Final question slot:** ask one for each, not just one for the room

---

## Your Questions to Ask (Pick 3-4)

**Don't ask:**
- ❌ Comp, benefits, PTO, equity → Anna's lane. Asking here signals you're not engaged in the technical conversation.
- ❌ Remote/hybrid policy → already known.
- ❌ "Why is the role open?" → R1 territory.
- ❌ Anything George already covered in R1 — Tim and Aakash were briefed; repeats signal you weren't listening.

1. **(Open with — fit discovery)** *Tim and Aakash* — "Help me understand the landscape — what does the platform and DevSecOps work look like across LMI's products today? Where is it concentrated, and where are the active needs?"
2. *To Tim (cross-product view)* — "From your seat across products, what's the engineering profile that tends to thrive at LMI versus struggle? What separates the two?"
3. *To Aakash (day-to-day reality)* — "What does your week actually look like — how much is platform building versus customer-facing deployment versus operations?"
4. *To either (mobility / portability)* — "How does LMI think about engineers moving between products over time? Is platform expertise portable across teams, or do engineers tend to specialize once they're placed?"
5. **(Close with)** *Tim and Aakash* — "From your perspectives, what separates someone who thrives at LMI from someone who's just doing the job?"

---

## Pre-Call (T-15 min)

- [ ] Teams open + logged in — **click the meeting link to confirm auth works**, don't discover at T-0 that Teams needs a refresh
- [ ] **Camera on, this doc CLOSED, no AI assistants running**
- [ ] Water nearby
- [ ] Phone on silent, face down
- [ ] CV in another window
- [ ] Background tidy
- [ ] Mic + audio test 5 min early
- [ ] **Restroom at T-5** (90-minute call possible — don't get caught)
