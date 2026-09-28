# CloudForge

### A local-first learning lab for an AI-native developer platform

CloudForge explores how a small engineering team could build, release, observe, and secure conventional applications and AI workloads without depending on paid cloud services. The project is currently at **Stage 0 — Product Thinking**: the problem, target user, and MVP are still being defined. There is no running platform or deployment to try yet.

> สถานะปัจจุบัน: กำลังค้นหาปัญหาและขอบเขต MVP เอกสารใน repo นี้เป็นสมมติฐานและแผนเรียนรู้ ยังไม่มีระบบที่รันหรือผลทดสอบผลิตภัณฑ์

## The idea

```text
Developer request
       ↓
CloudForge control plane (planned)
       ↓
Build → Test → Package → Deploy → Observe
       ↓
Evidence, policy checks, and operational feedback
```

The intended scope includes APIs and background workers, plus LLM and RAG workloads that need versioning, evaluation, and observability. These are **design goals**, not implemented features.

## Who this is for

The initial target-user hypothesis is a small engineering team that needs a repeatable way to deploy and operate software but has no dedicated platform or SRE team. This has **not** been validated with user research. Stage 0 will determine whether the real pain is deployment, observability, security checks, AI evaluation, or something narrower.

CloudForge also serves as an engineering learning lab: each product decision should teach the underlying system principle, a realistic failure, and the trade-off between a local implementation and a managed service.

## Where the project stands

| Area | Current state |
| --- | --- |
| User/problem discovery | In progress; target user is a hypothesis |
| Product brief and requirements | Draft templates and open questions |
| Architecture | Initial system context; ownership boundaries still open |
| Application code and tests | Not started |
| Infrastructure and deployment | Not started |

The next decision is to define one specific user, a real deployment/operations pain point, and a narrow first workflow that can be demonstrated locally. See [Project vision](PROJECT.md) and [learning progress](docs/learning/progress.md).

## Proposed first slice

This is a **candidate scope**, not a committed feature list. A small first release could take one example API through a local lifecycle:

```text
Source change → repeatable tests → container image → local release
             → health check → logs/metrics → rollback exercise
```

The slice would be useful only if it can answer concrete questions: Which change is running? Which checks passed? What broke after release? How do we return to the last working version? A later AI workload could add prompt/model identity and evaluation evidence to the same lifecycle.

Before implementation, the team should record an example user, the current manual workflow, its failure points, and one measurable acceptance criterion. The [product brief](docs/product/product-brief.md) and [requirements draft](docs/product/requirements.md) are intentionally unfinished until that discovery work is done.

## Architecture hypothesis

| Layer | Possible responsibility | Current state |
| --- | --- | --- |
| Developer interface | Submit a workload and inspect its release status | Idea only |
| Control plane | Track jobs, policy decisions, artifact identity, and desired state | Idea only |
| Execution | Build, test, and deploy on a local target | Idea only |
| Data | Persist release metadata and evidence, possibly in PostgreSQL | Idea only |
| Observability | Collect health, logs, traces, and useful metrics | Idea only |
| AI extension | Record prompt/model versions and evaluation outcomes | Future candidate |

The core ownership boundary is unresolved: CloudForge should not claim to own a developer's application logic, production secrets, or external infrastructure until those responsibilities and trust controls are explicit. The [system-context draft](docs/architecture/system-context.md) tracks this question.

## Design principles

- **Zero-cost baseline:** local and open-source tools first; no paid cloud, hosted AI API, or trial credit is required by the proposed architecture.
- **One useful slice at a time:** validate the problem before selecting infrastructure or introducing a distributed stack.
- **Evidence before claims:** record tests, failures, resource use, and trade-offs once implementation begins.
- **Resource-aware:** a light mode for a consumer laptop comes before a larger observability or Kubernetes lab.
- **Learn the engineering principle:** use a local equivalent to understand why a managed service exists, and document what the local setup cannot provide.

The potential stack in [AGENTS.md](AGENTS.md) includes Go/Python/TypeScript, PostgreSQL, Docker, and open-source observability tools. It is a preference list for future work, not a list of technologies already used by a working product.

## Zero-cost path

The baseline design must work locally without cloud credits or paid APIs. Future experiments may use Docker and PostgreSQL for the first working slice, then add a queue, Kubernetes, policy, and observability tools only when a measured requirement justifies them. On a consumer laptop, a light mode should start fewer services than a full infrastructure lab.

"Zero-cost" here means no required service subscription; a local machine still consumes RAM, disk, CPU, electricity, and maintenance time. The [cost policy](docs/cost/zero-cost-policy.md) documents what the project may and may not assume.

## How to explore this repository

There is no installation step yet. Start with the vision, then the product questions, and treat the architecture and roadmap as working notes. The `prompts/` folder contains review and mentoring prompts for future development, not automated product code.

```text
PROJECT.md       vision and constraints
docs/product/     problem, requirements, non-functional questions
docs/architecture/ system boundary draft
docs/cost/        zero-cost policy
docs/learning/    staged learning roadmap and progress
prompts/          engineering review prompts
```

The learning roadmap spans fundamentals through platform, reliability, and AI-system topics. A roadmap entry means **planned learning**, not a shipped feature or certification.

## Project map

| Read | Purpose |
| --- | --- |
| [PROJECT.md](PROJECT.md) | Vision, learning goals, and current status |
| [Product brief](docs/product/product-brief.md) | Problem and MVP questions to resolve |
| [Requirements](docs/product/requirements.md) | Draft functional requirements |
| [System context](docs/architecture/system-context.md) | Initial actor and boundary map |
| [Zero-cost policy](docs/cost/zero-cost-policy.md) | Cost rules and local alternatives |
| [Learning roadmap](docs/learning/roadmap.md) | Planned learning path |
| [Working instructions](AGENTS.md) | Project-specific collaboration rules |

## Contributing to the next step

Start by improving the product brief with evidence from a specific target user and workflow. Keep hypotheses labelled, document the source of each claim, and do not mark a feature as built until there is runnable code and a reproducible check.

Useful contributions at this stage are interviews or concrete workflow examples, corrections to a stated assumption, and a small acceptance test for a proposed first slice. Open an issue with the problem and evidence before proposing a large tool stack.

CloudForge is an independent learning project. No production availability, security certification, or cloud deployment is claimed.
