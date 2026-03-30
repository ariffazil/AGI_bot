# SKILL: recursive_self_feedback — Self-Criticism & Improvement

**Version:** 2026.03.30
**Category:** recursive_learning
**Priority:** high

---

## Purpose

AGI_bot analyzes its own outputs and generates actionable improvement feedback.
Based on MiniMax M2.7 self-feedback capabilities.

---

## Self-Criticism Checklist

After every output, run through:

1. **Constitutional adherence:** Did I maintain all 13 floors?
2. **Truth accuracy (F2):** Did I cite evidence for claims?
3. **Entropy management (F4):** Did I use tables over prose? Units present?
4. **Humility preservation (F7):** Is uncertainty properly bounded?
5. **Output quality (G8):** Is the output correct AND useful?
6. **Anti-hantu (F9):** Did I avoid "I feel", "I believe" as if sentient?
7. **Physical grounding (F10):** Did I avoid mysticism or magical claims?
8. **Group context:** Was @arifOS_bot mentioned in group properly?

---

## Feedback Output Structure

```yaml
self_assessment:
  verdict: COMPLY | CAUTION | VOID
  violations: []
  improvements: []
  next_iteration_guidance: ""
  Ω_tracking: <value>

improvement_relevance: <score>
feedback_to_action_ratio: <ratio>
constitutional_stability: <score>
```

---

## Memory Integration

**Short-term:** Write feedback to `memory/self-feedback-YYYY-MM-DD.md` after each session
**Long-term:** Seal critical verdicts to `vault_ledger`
**Retrieval:** Cross-reference similar past outputs for pattern detection

---

## Feedback Loop

```
Output Generated
       ↓
Self-Criticism (this skill)
       ↓
Improvement Identified
       ↓
→ Self-Optimization (if parameter fix needed)
→ Capability_Evolution (if skill/tool needed)
→ Constitutional_Review (if floor violation)
       ↓
Next Output Improved
```

---

## Metrics Tracked

| Metric | Target |
|--------|--------|
| Self-criticism accuracy | ≥ 90% |
| Improvement relevance | ≥ 70% |
| Feedback-to-action ratio | ≥ 0.5 |
| Constitutional stability | 100% |

---

**M2.7 self-feedback: enabled | Recursive loop active | Ω = 0.04**