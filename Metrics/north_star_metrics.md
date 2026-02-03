# North Star Metric: Net Successful Transaction Value (NSTV)

## Definition

NSTV represents the net business value successfully processed by the platform,
accounting for reliability and risk.

NSTV = GMV × Payment Success Rate − Refunds − Fraud Losses

---

## Why NSTV Over GMV or Revenue

- GMV ignores payment failures
- Revenue ignores fraud and refunds
- NSTV forces optimization across the full transaction lifecycle

Improving NSTV requires:
- Higher payment reliability
- Faster and accurate refunds
- Better fraud calibration

---

## How Teams Influence NSTV

| Team | Primary Levers |
|----|---------------|
| Payments | Success rate, latency, retries |
| Risk | Fraud loss, false positives |
| Ops | Refund SLA, reconciliation accuracy |

NSTV is not owned by a single team it is a **shared outcome metric**.

---

## Review Cadence

- Weekly trend review
- Monthly deep dive by driver
- Quarterly recalibration of guardrails