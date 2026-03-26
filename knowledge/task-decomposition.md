# Task Decomposition

Work breakdown structure patterns for software projects.

## Decomposition Principles

1. Every task is 1-4 hours of work
2. Each task has a clear definition of done
3. Dependencies between tasks are explicit
4. Parallelization flags indicate concurrent execution
5. Tasks are grouped into logical phases

## Standard Phase Structure

| Phase | Purpose | Typical Tasks |
|-------|---------|---------------|
| Setup | Environment, scaffolding | Repo init, config, CI, dependencies |
| Foundation | Shared code, types, schemas | Data models, interfaces, DB migrations |
| Core | Primary business logic | Service implementations, API endpoints |
| Integration | Component wiring | Inter-service communication, auth flow |
| Testing | Coverage completion | Integration tests, E2E tests, edge cases |
| Polish | Quality and documentation | Error messages, logging, README, API docs |
| Delivery | Release preparation | Pre-landing review, deployment config |

## Task Definition Template

```markdown
### T<ID>: <Title>

**Phase:** <phase name>
**Depends on:** T<ID>, T<ID> | None
**Parallel:** Yes | No
**Estimate:** O: Xh | E: Xh | P: Xh | W: Xh
**Definition of done:**
- [ ] <specific, verifiable criterion>
- [ ] <specific, verifiable criterion>
- [ ] Tests passing with >X% coverage
```

## Dependency Graph Patterns

### Linear Chain
```
T1 → T2 → T3 → T4
```
Critical path = sum of all tasks. No parallelization.

### Fan-Out
```
T1 → T2a
T1 → T2b
T1 → T2c
```
T2a, T2b, T2c run in parallel after T1. Duration = T1 + max(T2a, T2b, T2c).

### Fan-In
```
T2a → T3
T2b → T3
T2c → T3
```
T3 waits for all predecessors.

### Diamond
```
T1 → T2a → T3
T1 → T2b → T3
```
Common in: foundation → parallel services → integration.

## Decomposition Checklist

| Check | Requirement |
|-------|-------------|
| Max task size | No task > 4 hours |
| Definition of done | Every task has verifiable criteria |
| Dependencies complete | No orphaned tasks, no circular deps |
| Parallelization marked | Every task flagged Yes/No |
| Phase assignment | Every task belongs to a phase |
| No scope gaps | Architecture components fully covered |
| No duplicate work | No two tasks overlap in scope |

## Common Decomposition Mistakes

| Mistake | Fix |
|---------|-----|
| "Implement feature X" (too vague) | Break into: types, service, endpoint, tests |
| "Set up project" (too broad) | Break into: repo, deps, config, CI, scaffold |
| Missing integration tasks | Add explicit wiring tasks between components |
| No testing tasks | Add test tasks per component or per phase |
| Ignoring config/deploy | Add environment setup and deployment tasks |
| Sequential when parallelizable | Review dependencies, mark parallel where possible |

## Critical Path Identification

1. List all task chains from start to end
2. Calculate duration of each chain (sum of weighted estimates)
3. Longest chain = critical path
4. Any delay on critical path delays the project
5. Non-critical tasks have float (slack time before they delay the project)
