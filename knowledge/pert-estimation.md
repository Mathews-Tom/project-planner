# PERT Estimation

Program Evaluation and Review Technique for software project estimation.

## Three-Point Estimation Formula

```
Weighted Estimate = (O + 4E + P) / 6

O = Optimistic  (best case, no surprises, familiar territory)
E = Expected    (realistic with normal friction)
P = Pessimistic (unfamiliar code, integration issues, requirement ambiguity)
```

## Standard Deviation

```
SD = (P - O) / 6
```

Use SD to calculate confidence intervals:
- 68% confidence: Weighted +/- 1 SD
- 95% confidence: Weighted +/- 2 SD
- 99.7% confidence: Weighted +/- 3 SD

## Estimation Calibration Factors

| Factor | Multiplier | Applies When |
|--------|-----------|--------------|
| Unfamiliar codebase | 1.5x | First time working in the repo |
| New technology | 1.5-2x | Team has not shipped with this stack |
| Third-party integration | 1.3x | Depends on external API/SDK |
| Unclear requirements | 1.5x | Spec has ambiguities or gaps |
| Legacy code modification | 1.3-1.5x | No tests, unclear boundaries |
| Greenfield | 0.9x | No legacy constraints |
| Team has shipped similar | 0.8x | Direct prior experience |

## Task Size Guidelines

| Duration | Classification | Action |
|----------|---------------|--------|
| < 30 min | Too small | Merge with related task |
| 30 min - 4 hours | Correct size | Estimate directly |
| 4 - 8 hours | Borderline | Decompose if possible |
| > 8 hours | Too large | Must decompose further |

## Roll-Up Methodology

### Sequential Tasks
```
Total = Sum of all weighted estimates
```

### Parallel Tasks
```
Total = Max of parallel track durations
```

### Phase Roll-Up
```
Phase Duration = Critical path duration within phase
Project Duration = Sum of phase durations + buffer
```

## Buffer Allocation

| Project Type | Buffer |
|-------------|--------|
| Well-understood, similar to past work | 15% |
| Standard project, some unknowns | 20% |
| High uncertainty, new technology | 25-30% |

Buffer is applied to the total project estimate, not individual tasks.

## Common Estimation Biases

| Bias | Description | Correction |
|------|-------------|------------|
| Anchoring | First estimate dominates | Estimate O, E, P independently |
| Optimism | Underweighting obstacles | Use pessimistic from similar past projects |
| Planning fallacy | Ignoring historical data | Compare against actual durations from past sprints |
| Scope creep | Estimating initial scope only | Add risk buffer for discovered work |

## Velocity Tracking

Track ratio of `actual / estimated` per task category to calibrate future estimates:

| Ratio | Interpretation |
|-------|---------------|
| < 0.8 | Over-estimating (padding) |
| 0.8 - 1.2 | Well-calibrated |
| 1.2 - 1.5 | Slightly under-estimating |
| > 1.5 | Systematic under-estimation, adjust calibration factors |
