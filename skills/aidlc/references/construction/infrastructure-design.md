# Infrastructure Design - Detailed Steps

## Overview

Map application components to infrastructure services for each unit through two integrated parts:
- **Part 1 - Planning**: Create infrastructure mapping plan
- **Part 2 - Generation**: Execute approved plan to generate infrastructure design artifacts

## Prerequisites

- NFR Design must be complete for the unit (if executed)
- Technology stack must be selected
- Scalability and reliability requirements must be defined

---

# PART 1: PLANNING

## Step 1: Analyze Infrastructure Context

- [ ] Read NFR design artifacts
- [ ] Read technology stack selection
- [ ] Identify compute, storage, and networking needs
- [ ] Review scalability and reliability requirements

## Step 2: Create Infrastructure Design Plan

- [ ] Identify infrastructure components:
  - Compute resources (containers, serverless, VMs)
  - Database services (relational, NoSQL, cache)
  - Storage services (object, file, block)
  - Networking (VPC, load balancers, CDN)
  - Security services (IAM, secrets management, WAF)
  - Observability services (logging, monitoring, tracing)
- [ ] Create explicit steps for design
- [ ] Number each step sequentially
- [ ] Add checkboxes [ ] for each step

## Step 3: Generate Context-Appropriate Questions

Generate questions using [Answer]: tag format:

```markdown
### Compute Infrastructure

**Q1**: What compute model is preferred (containers, serverless, VMs)?
[Answer]: 

**Q2**: What container orchestration platform (if applicable)?
[Answer]: 

### Database Infrastructure

**Q3**: What database service should be used?
[Answer]: 

**Q4**: What caching service is needed?
[Answer]: 

### Cloud Provider

**Q5**: What cloud provider is being used?
[Answer]: 

**Q6**: Are there any specific service preferences or constraints?
[Answer]: 
```

## Step 4: Collect and Analyze Answers

- [ ] Wait for user to provide answers
- [ ] Analyze answers for completeness
- [ ] Generate follow-up questions if needed

## Step 5: Create Plan Document

Save complete plan as `aidlc-docs/construction/plans/{unit-name}-infrastructure-design-plan.md`

## Step 6: Wait for Explicit Approval

- **DO NOT PROCEED until user explicitly approves**


---

# PART 2: GENERATION

## Step 7: Load Infrastructure Design Plan

- [ ] Read the complete plan
- [ ] Identify the next uncompleted step
- [ ] Load the context for that step

## Step 8: Execute Current Step

Generate infrastructure design artifacts based on current step:

### Compute Design
- Container/serverless architecture
- Resource sizing and limits
- Auto-scaling configuration
- Deployment topology

### Database Design
- Database service selection
- Instance sizing
- Replication strategy
- Backup configuration

### Networking Design
- VPC/network architecture
- Load balancer configuration
- DNS and routing
- CDN configuration

### Security Infrastructure
- IAM roles and policies
- Secrets management
- Network security groups
- WAF rules

### Observability Infrastructure
- Logging service configuration
- Monitoring dashboards
- Alerting setup
- Tracing configuration

## Step 9: Update Progress

- [ ] Mark the completed step as [x] in the plan
- [ ] Update `aidlc-docs/aidlc-state.md` current status
- [ ] Save generated artifacts

## Step 10: Continue or Complete

- [ ] If more steps remain, return to Step 7
- [ ] If all steps complete, proceed to completion message

## Step 11: Present Completion Message

```markdown
# 🏗️ Infrastructure Design Complete - [unit-name]

[AI-generated summary]
- Compute architecture defined
- Database services mapped
- Networking configured
- Security infrastructure planned

> **📋 REVIEW REQUIRED:**  
> Please examine: `aidlc-docs/construction/[unit-name]/infrastructure-design/`

> **🚀 WHAT'S NEXT?**
>
> **You may:**
>
> 🔧 **Request Changes** - Ask for modifications
> ✅ **Continue to Next Stage** - Proceed to **Code Generation**
```

## Step 12: Wait for Explicit Approval

- **DO NOT PROCEED until user explicitly approves**

## Step 13: Record Approval and Update Progress

- Log approval in audit.md with timestamp
- Mark Infrastructure Design stage as complete for this unit

---

## Output Artifacts

- `aidlc-docs/construction/{unit-name}/infrastructure-design/compute.md`
- `aidlc-docs/construction/{unit-name}/infrastructure-design/database.md`
- `aidlc-docs/construction/{unit-name}/infrastructure-design/networking.md`
- `aidlc-docs/construction/{unit-name}/infrastructure-design/security.md`
- `aidlc-docs/construction/{unit-name}/infrastructure-design/observability.md`
- `aidlc-docs/construction/{unit-name}/infrastructure-design/architecture-diagram.md`

## Infrastructure as Code

When generating IaC artifacts:
- Use appropriate IaC tool (Terraform, CloudFormation, CDK, Pulumi)
- Follow cloud provider best practices
- Include resource tagging strategy
- Document deployment procedures

## Critical Rules

- **CLOUD-NATIVE**: Leverage managed services where appropriate
- **COST-AWARE**: Consider cost implications of infrastructure choices
- **EXPLICIT APPROVAL**: Never proceed without user approval
