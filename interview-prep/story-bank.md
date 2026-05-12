# Story Bank — Master STAR+R Stories

This file accumulates your best interview stories over time. Each evaluation (Block F) adds new stories here. Instead of memorizing 100 answers, maintain 5-10 deep stories that you can bend to answer almost any behavioral question.

## How it works

1. Every time `/career-ops oferta` generates Block F (Interview Plan), new STAR+R stories get appended here
2. Before your next interview, review this file — your stories are already organized by theme
3. The "Big Three" questions can be answered with stories from this bank:
   - "Tell me about yourself" → combine 2-3 stories into a narrative
   - "Tell me about your most impactful project" → pick your highest-impact story
   - "Tell me about a conflict you resolved" → find a story with a Reflection

## Stories

<!-- Stories will be added here as you evaluate offers -->

### [IaC + Compliance] Wickr Enterprise Deployment on Cloud One
**Source:** Report #077 — DEFCON AI — Cloud Infrastructure Engineer
**S (Situation):** GDIT needed to deploy and sustain Wickr Enterprise — a large COTS secure messaging platform — on AWS Cloud One GovCloud for DoD users in a classified environment under ATO.
**T (Task):** Own the infrastructure deployment: CloudFormation templates, Jenkins CI/CD pipelines, DISA STIG hardening, and ongoing sustainment across dev/test/production.
**A (Action):** Designed CloudFormation IaC for all infrastructure components. Built Jenkins pipelines integrating Artifactory for artifact management. Implemented DISA STIG hardening for RHEL/CentOS. Automated compliance checks and maintained RMF documentation for ATO. Managed IAM and Secrets via Systems Manager Parameter Store.
**R (Result):** Wickr Enterprise deployed and sustained on Cloud One with ATO. Zero production outages attributed to infrastructure during tenure. Compliance automation reduced manual remediation cycles.
**Reflection:** The hardest part wasn't the technology — it was coordinating across government stakeholders with different priorities and timelines. I learned to front-load documentation and get written alignment early, which shortened every subsequent ATO cycle.
**Best for questions about:** IaC at scale, STIG/compliance, CI/CD in classified environments, COTS deployment, ATO process, government stakeholder management

### [Automation] EFS Backup Automation at Smartronix
**Source:** Report #077 — DEFCON AI — Cloud Infrastructure Engineer
**S (Situation):** At Smartronix, backup processes for Amazon EFS volumes were manual and inconsistent across environments.
**T (Task):** Automate EFS backup using Infrastructure as Code to ensure consistency and reduce operational risk.
**A (Action):** Developed Terraform modules to automate EFS backup processes. Created AWS Systems Manager automation scripts for multi-OS application installations.
**R (Result):** Backup processes standardized and automated across environments. Reduced manual intervention and risk of missed backups.
**Reflection:** This was my first production Terraform work — coming from CloudFormation, the state management model was the sharpest learning curve. Knowing that now, I'd invest earlier in remote state and locking patterns.
**Best for questions about:** Terraform experience, automation, learning new tools, reducing toil

### [AIOps-adjacent / Automation] Self-Healing Auto-Scaling Infrastructure
**Source:** Report #140 — Booz Allen Hamilton — AI DevOps Engineer (interview prep 2026-04-28)
**S (Situation):** Across multiple roles (Smartronix and earlier GDIT 2017–2019), production AWS workloads supporting government and DoD customers were running on EC2 fleets where common, well-understood failure modes (unhealthy hosts, hung services, disk-full conditions, ASG instance failures) were being handled manually. On-call engineers were paged for the same routine failures repeatedly; mean time to recovery on common failures was tens of minutes to hours depending on time of day.
**T (Task):** Eliminate the manual step for the common, well-understood failure modes — get the infrastructure to remediate itself for cases the team already knew how to fix, and reserve human attention for genuinely novel failures.
**A (Action):** Built CloudWatch alarms on the known failure signatures (ASG health checks, EC2 system status, disk thresholds, custom application metrics via CloudWatch agent). Wired alarms to AWS Lambda functions and SSM automation documents that took remediation actions — terminate-and-replace via Auto Scaling group, restart-via-SSM-Run-Command, or scale-out events. Tuned ASG policies (health check grace periods, cooldowns, target-tracking and step scaling) so the group could replace instances and absorb load spikes without thrashing. Built AMI bake and SSM bootstrap automation so replacement instances came up clean and configured. Every automated action logged to CloudWatch and was visible on the operational dashboard.
**R (Result):** Common failure modes resolved without human intervention. On-call load on routine failures dropped from regular to rare. MTTR on common failures collapsed from manual-response timeframes to ASG replacement time. Team attention shifted from triaging known failures to investigating novel ones.
**Reflection:** Automated remediation is only safe when you trust the detection signal AND the replacement state. Early on, a couple of cases hit on transient signals and the automation took action prematurely — terminating instances that would have recovered on their own. The fix was tightening alarm evaluation periods and adding circuit-breaker logic to prevent looping. That experience shaped how I think about AIOps: the value isn't AI deciding what to do, it's the detection → decision → action → observation loop being safe and observable end-to-end. AI sharpens the detection signal; the remediation discipline has to come first.
**Best for questions about:** AIOps adjacency, self-healing infrastructure, observability-driven automation, reducing on-call load, automated remediation, CloudWatch + Lambda + SSM patterns, "most impactful automation"
<!-- Format:
### [Theme] Story Title
**Source:** Report #NNN — Company — Role
**S (Situation):** ...
**T (Task):** ...
**A (Action):** ...
**R (Result):** ...
**Reflection:** What I learned / what I'd do differently
**Best for questions about:** [list of question types this story answers]
-->
