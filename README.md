# project-planner

Task breakdown and project planning agent that decomposes work into dependency-mapped items with three-point PERT estimates, milestones, critical path analysis, and risk tracking. Produces actionable project plans with parallelization flags and realistic timelines calibrated against historical data.

[![gitagent registry](https://img.shields.io/badge/gitagent-registry-blue)](https://registry.gitagent.sh)
[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)

---

## Run

```bash
npx @open-gitagent/gitagent run -r https://github.com/Mathews-Tom/project-planner
```

---

## What It Can Do

- **Scope Analysis** — extracts components from architecture documents or codebases, identifies reusable infrastructure vs. new work
- **Task Decomposition** — breaks work into 1-4 hour chunks with dependencies, parallelization flags, and definitions of done
- **PERT Estimation** — three-point estimates (optimistic, expected, pessimistic) with weighted averaging per task and phase
- **Risk Assessment** — categorizes technical, dependency, and timeline risks with probability-impact scoring and mitigations
- **Critical Path Analysis** — identifies the longest dependency chain that determines the project timeline
- **Plan Validation** — stress-tests the plan for oversized tasks, missing dependencies, and deadline feasibility

---

## Structure

```
project-planner/
├── agent.yaml
├── SOUL.md
├── RULES.md
├── README.md
├── assets/
│   ├── icon.png
│   └── banner.png
└── knowledge/
    ├── pert-estimation.md
    ├── task-decomposition.md
    └── risk-assessment-framework.md
```

---

## Built with

Built for the [gitagent](https://gitagent.sh) ecosystem.
