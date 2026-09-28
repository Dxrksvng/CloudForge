# CloudForge

### A local-first learning lab for an AI-native developer platform

CloudForge explores how a small engineering team could build, release, observe, and secure conventional applications and AI workloads without depending on paid cloud services. The project is currently at **Stage 0 — Product Thinking**: the problem, target user, and MVP are still being defined. There is no running platform or deployment to try yet.

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

## Where the project stands

| Area | Current state |
| --- | --- |
| User/problem discovery | In progress; target user is a hypothesis |
| Product brief and requirements | Draft templates and open questions |
| Architecture | Initial system context; ownership boundaries still open |
| Application code and tests | Not started |
| Infrastructure and deployment | Not started |

The next decision is to define one specific user, a real deployment/operations pain point, and a narrow first workflow that can be demonstrated locally. See [Project vision](PROJECT.md) and [learning progress](docs/learning/progress.md).

## Design principles

- **Zero-cost baseline:** local and open-source tools first; no paid cloud, hosted AI API, or trial credit is required by the proposed architecture.
- **One useful slice at a time:** validate the problem before selecting infrastructure or introducing a distributed stack.
- **Evidence before claims:** record tests, failures, resource use, and trade-offs once implementation begins.
- **Resource-aware:** a light mode for a consumer laptop comes before a larger observability or Kubernetes lab.
- **Learn the engineering principle:** use a local equivalent to understand why a managed service exists, and document what the local setup cannot provide.

The potential stack in [AGENTS.md](AGENTS.md) includes Go/Python/TypeScript, PostgreSQL, Docker, and open-source observability tools. It is a preference list for future work, not a list of technologies already used by a working product.

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

CloudForge is an independent learning project. No production availability, security certification, or cloud deployment is claimed.
