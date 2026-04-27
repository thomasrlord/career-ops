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
