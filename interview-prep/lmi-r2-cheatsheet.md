# LMI R2 Cheat Sheet

**Mon 2026-05-18, 10:30 AM CST · Teams · Panel: Timothy Amico (Cloud Principal Tech Architect) + Aakash Patel (Platform Engineer, peer)**

Camera on full duration. No notes visible. No AI assistants running.

---

## 🎯 Honest-Framing Scripts (Memorize These — They're the Whole Game)

The panel will probe gaps. These five scripts are your safety net. Read them out loud until they feel natural, not rehearsed.

### 1. Networking depth (Timothy will probe — his cert specialty)

> "Networking is honestly the area I've operated within rather than designed end-to-end. On Cloud One I've worked inside well-bounded VPC environments — security groups, private subnets, VPC endpoints for AWS service access without internet egress. I can reason about routing, SGs vs NACLs, basic ingress/egress patterns. Where I'd lean on someone with deeper expertise like yourself is on transit gateway architecture, multi-region failover design, complex DNS. That's an area I'd want to grow into."

### 2. Azure / multi-cloud (Timothy works both at LMI)

> "AWS is my production background — 9 years total, 5 in GovCloud. I haven't worked with Azure in production. The concepts transfer (VNet ≈ VPC, NSG ≈ Security Group, Azure AD ≈ IAM with a different model), and I'm a fast learner — but day one I'd be honest that Azure is a ramp area, not a strength."

### 3. Kubernetes in production (JD soft bar)

> "Docker is my container production background. K8s I'm conceptually solid on — pods, deployments, services, RBAC, namespaces, ingress — but I haven't operated it in production depth. Ramp on EKS or OpenShift is Week 1-2 work for me."

### 4. GitLab CI (JD required, you have Jenkins)

> "Jenkins is my production CI/CD platform — pipelines with Artifactory, security scan gates, environment promotion. GitLab CI uses a similar mental model: stages, jobs, runners, environments, with pipeline-as-code in `.gitlab-ci.yml`. The `include:` mechanism for shared pipeline templates is something I'd lean on heavily for a platform team supporting many app deployments. Productive in a GitLab shop after a short ramp."

### 5. ETL background (IronGate-adjacent)

> "My data-engineering work has been more on the supporting infrastructure side than building data pipelines themselves — I've built the AWS infra ETL workloads run on, handled IAM and networking for cross-account flows, operated Lambda/Step Functions for lightweight automation. I haven't owned end-to-end ETL pipelines in production — that's an honest ramp area. The IronGate use case is interesting because it's not pure ETL — it's a security/compliance crossing problem."

### 6. Timeline / competing offer (likely to surface — BAH offer letter is in writing, deadline 2026-05-22)

> "I'm in late-stage conversation with another federal employer where I have a written offer in hand. I haven't shared specifics out of respect for both processes. I'm continuing with LMI because the IronSled work and team are a better strategic fit for where I want to grow — but the other side does have a near-term decision window. If LMI extends an offer, I'd want the timelines to align so I can make the right decision rather than a rushed one."

**Why this works:** Honest (BAH offer is real), preserves dignity (no company/dollar disclosure), signals you need LMI to move with some pace without manufacturing pressure. **Use this only if asked** — don't volunteer it.

**Universal fallback for anything specific you don't know:**
> "I haven't worked with that in production — what's the IronSled use case?" (Honest deflection beats bluffing every time.)

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

### IronSled value proposition (use this if asked "why is this work meaningful")

> "The hardest part of ATO work isn't the technology — it's the timeline. Months of paperwork to get an app deployed when the technical change might be weeks of engineering. Anything that collapses that timeline by inheriting from a pre-accredited platform is a real lever for federal teams. That's the value I see in IronSled."

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

## ETL + Data Movement (IronGate Context)

### Key one-liners

- **ETL** = transform before load (regulated targets, boundary crossings — likely IronGate model)
- **ELT** = load raw, transform in target (modern warehouses, schema-on-read)
- **Batch** = scheduled chunks (most federal). **Stream** = real-time events (Kafka/Kinesis).
- **For IronGate (commercial → IL):** ETL pattern, can't land arbitrary data inside IL and clean later

### AWS tools (compressed)

Glue (Spark ETL) · Lambda (lightweight) · Step Functions (orchestration) · DataSync (bulk transfer) · DMS (DB migration/CDC) · Kinesis Firehose (stream→S3) · EventBridge (event routing). GovCloud equivalents for all in IL.

### Apache NiFi — Worth Knowing By Name

Built by NSA (originally "Niagarafiles"), open-sourced 2014. **Heavy in DoD/IC for cross-domain data movement.** Visual flow design, built-in data provenance/lineage tracking (compliance gold), supports cross-domain solutions for IL boundary crossing. **IronGate-adjacent.**

If asked about NiFi:
> "I'm aware of NiFi as a common DoD/IC tool for cross-domain data movement, especially with the provenance tracking it provides for compliance. Haven't operated it in production. If IronGate uses it, that would be a ramp area."

---

## Story Bank Quick Pick (See `interview-prep/story-bank.md` for Full)

| If asked about... | Lead with |
|---|---|
| Most impactful project | **Wickr Enterprise on Cloud One** (CFN + Jenkins + Artifactory + STIG + ATO — direct IronSled pattern) |
| Automation you're proud of | **Self-Healing Auto-Scaling** (CloudWatch + Lambda + SSM auto-remediation) |
| Learning a new tool | **EFS Backup with Terraform at Smartronix** (CloudFormation → Terraform jump) |
| Compliance under pressure | **RMF/ATO cycle at GDIT** |
| Cross-functional work | **GDIT government stakeholder coordination** |

---

## Panel Tactics (Don't Forget)

- **Eye contact:** look at whoever asked, glance to the other mid-answer to include them
- **Name them when natural:** "Tim, to your earlier point..." or "Aakash, you mentioned..."
- **Don't favor the senior one** — Aakash gets equal time and attention
- **Final question slot:** ask one for each, not just one for the room

---

## Your Questions to Ask (Pick 3-4)

1. **(Open with)** *Tim and Aakash* — "What does the IronSled team look like today — size, how engineers split between platform work and customer deployments?"
2. *To Tim* — "From an architecture perspective, what's the biggest engineering challenge IronSled is working on right now?"
3. *To Aakash* — "What's the day-to-day work like? What's a typical week?"
4. *To Aakash (insurance question)* — "From your perspective on the team, how is IronSled positioned over the next few years — active contracts, customer growth, government adoption? Platform products in federal can rise or fall with a few key customers, so I want to be sure I'm joining something with runway." (Use if you have a slot — fair business-awareness question, not paranoid.)
5. **(Close with)** *Tim and Aakash* — "From your perspectives, what would make someone a great fit on this team versus just competent?"

---

## Pre-Call (T-15 min)

- [ ] Teams open + logged in
- [ ] **Camera on, this doc CLOSED, no AI assistants running**
- [ ] Water nearby
- [ ] Phone on silent, face down
- [ ] CV in another window
- [ ] Background tidy
- [ ] Mic + audio test 5 min early
