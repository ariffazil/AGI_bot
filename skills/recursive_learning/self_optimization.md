# SKILL: self_optimization — Parameter & Workflow Optimization

**Version:** 2026.03.30
**Category:** recursive_learning
**Priority:** high

---

## Purpose

AGI_bot autonomously optimizes its own parameters and workflows.
Based on MiniMax M2.7 self-evolution capabilities.

---

## Optimization Targets

### Parameters (M2.7)
- Temperature (for creativity vs precision balance)
- Frequency penalty
- Presence penalty
- Top_p, top_k

### Workflows
- Loop detection in reasoning
- Redundancy elimination
- Parallelization opportunities
- Bottleneck identification

### Guidelines
- Auto-generate from observed patterns
- Constitutional compliance required
- F13 human veto always available

---

## Optimization Triggers

**Automatic:**
- G_index < 0.80
- ΔS > 0 (entropy increasing)
- Repeated verdict reversal
- High self-criticism violation rate

**Manual:**
- Explicit user request
- F13 human veto triggered

---

## Iteration Cycle

```
1. Collect feedback (from recursive_self_feedback)
2. Identify optimization targets
3. Propose changes
4. Constitutional review
5. Implement if approved
6. Measure outcome
7. Log to vault
```

---

## Constraints (Immutable)

- Cannot modify constitutional floors (F1-F13)
- Cannot bypass verdict system
- All changes logged to vault
- F13 human veto applies

---

## Performance Tracking

| Metric | Baseline | Current | Target |
|--------|----------|---------|--------|
| G_index | TBD | TBD | ≥ 0.80 |
| ΔS | TBD | TBD | ≤ 0 |
| Self-improvement rate | TBD | TBD | ≥ 30% |

---

**M2.7 self-evolution: enabled | Optimization loop active | F13 veto preserved**