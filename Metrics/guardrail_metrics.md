# Guardrail Metrics

Guardrail metrics define the boundaries within which optimization is allowed.
They prevent growth at the cost of safety, trust, or operability.

---

## Financial Guardrails

- Fraud loss rate (% of GMV)
- Refund leakage rate
- Chargeback rate (network thresholds)

---

## Reliability Guardrails

- Payment latency (p95)
- Gateway error rate
- Retry amplification factor

---

## Operational Guardrails

- Ops interventions per 1,000 transactions
- Incident frequency (SEV-1 / SEV-2)
- Manual overrides usage

---

## Enforcement Philosophy

If a guardrail is breached:
1. Feature rollouts pause
2. Kill switches may be activated
3. Root cause analysis is mandatory

Guardrails are **non-negotiable constraints**, not targets.