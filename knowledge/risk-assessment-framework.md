# Risk Assessment Framework

Structured risk identification, scoring, and mitigation for project planning.

## Risk Categories

| Category | Examples |
|----------|----------|
| Technical | Unfamiliar technology, complex algorithms, performance unknowns |
| Dependency | External API instability, waiting on other teams, library maturity |
| Timeline | Deadline pressure, team availability, competing priorities |
| Scope | Requirement ambiguity, scope creep, changing priorities |
| Resource | Key person dependency, skill gaps, tooling limitations |
| External | Regulatory changes, vendor pricing changes, market shifts |

## Probability-Impact Matrix

|  | LOW Impact | MEDIUM Impact | HIGH Impact |
|--|-----------|---------------|-------------|
| **HIGH Probability** | MEDIUM | HIGH | CRITICAL |
| **MEDIUM Probability** | LOW | MEDIUM | HIGH |
| **LOW Probability** | LOW | LOW | MEDIUM |

## Probability Definitions

| Level | Definition | Quantified |
|-------|-----------|------------|
| LOW | Unlikely to occur, team has handled similar before | < 20% |
| MEDIUM | Possible, some uncertainty or unfamiliarity | 20-60% |
| HIGH | Likely to occur, known friction or unknowns | > 60% |

## Impact Definitions

| Level | Schedule Impact | Scope Impact |
|-------|----------------|--------------|
| LOW | < 1 day delay | Cosmetic changes only |
| MEDIUM | 1-3 day delay | Feature reduced or reworked |
| HIGH | > 3 day delay | Milestone missed or feature cut |

## Risk Entry Template

```markdown
### R<ID>: <Risk Title>

**Category:** Technical | Dependency | Timeline | Scope | Resource | External
**Probability:** LOW | MEDIUM | HIGH
**Impact:** LOW | MEDIUM | HIGH
**Severity:** LOW | MEDIUM | HIGH | CRITICAL
**Trigger:** <Observable event indicating risk is materializing>
**Mitigation:** <Action to reduce probability or impact>
**Contingency:** <Action if risk materializes despite mitigation>
**Owner:** <Person responsible for monitoring>
```

## Common Software Project Risks

| Risk | Category | Typical Probability | Mitigation |
|------|----------|-------------------|------------|
| Third-party API changes during development | Dependency | MEDIUM | Pin API version, build adapter layer |
| Database schema changes after implementation starts | Scope | MEDIUM | Finalize schema in architecture phase |
| Performance targets not met | Technical | MEDIUM | Load test early, profile hot paths |
| Auth implementation takes longer than estimated | Technical | HIGH | Use proven auth library, spike first |
| CI/CD pipeline setup delays | Technical | MEDIUM | Use established templates, allocate setup phase |
| Key team member unavailable | Resource | LOW | Document decisions, pair on critical tasks |
| Requirement changes mid-sprint | Scope | HIGH | Scope lock per sprint, change request process |

## Risk Response Strategies

| Strategy | When to Use | Example |
|----------|-------------|---------|
| Avoid | High probability, high impact | Change approach to eliminate the risk |
| Mitigate | Medium-high risk, actionable | Spike/prototype to reduce uncertainty |
| Transfer | Risk outside team's control | Use managed service instead of self-hosting |
| Accept | Low severity, cost of mitigation exceeds impact | Document and monitor |

## Risk Monitoring

- Review risk log at each milestone
- Update probability/impact as information emerges
- Close risks that have passed their trigger window
- Escalate risks that move to CRITICAL severity
- Track risk-to-issue conversion rate for calibration
