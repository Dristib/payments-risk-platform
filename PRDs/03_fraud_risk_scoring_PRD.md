# Fraud & Risk Scoring PRD

## Problem Statement

As transaction volume scales, payment platforms become increasingly exposed to
fraud vectors including account takeovers, synthetic identities, refund abuse,
and card testing attacks.

A naïve risk system either:
- Blocks too aggressively, killing conversion and merchant revenue, or
- Lets fraud through, resulting in direct financial loss and trust erosion

The challenge is not fraud prevention alone, but **risk calibration**
optimizing for loss prevention without materially degrading legitimate user
experience.

---

## Goals

- Accurately assess transaction level fraud risk in real time
- Minimize fraud losses while preserving checkout conversion
- Provide explainability for risk decisions to ops and merchants
- Enable dynamic tuning based on merchant risk appetite

---

## Non-Goals

- Acting as a chargeback management platform
- Building proprietary ML models from scratch (initial phase)
- Making irreversible customer level judgments (e.g., permanent bans)

---

## Target Users

- Risk & fraud operations teams
- Payments platform PMs
- Merchants with configurable risk tolerance
- End customers affected by risk decisions

---

## Core Concepts & Definitions

- **Risk Score:** Numerical representation of fraud likelihood (0–100)
- **Decision Bands:** Thresholds mapping risk scores to actions
- **False Positive:** Legitimate transaction incorrectly blocked
- **False Negative:** Fraudulent transaction incorrectly allowed
- **Step-Up Authentication:** Additional verification triggered for medium risk

---

## User Scenarios

1. Legitimate customer flagged due to IP mismatch
2. Fraudulent transaction bypasses basic checks
3. Merchant wants stricter fraud rules during high risk sales
4. Ops team investigates spike in blocked transactions
5. Risk rules degrade conversion unintentionally

---

## Functional Requirements

### Risk Signal Ingestion
- Device fingerprinting
- IP reputation and geolocation mismatch
- Velocity checks (transactions per device/account)
- Payment instrument history
- Behavioral anomalies (time-to-checkout, retries)

---

### Risk Scoring Engine
- Real time risk score computation (<150ms budget)
- Weighted aggregation of signals
- Configurable signal weights
- Deterministic scoring for auditability

---

### Decision Engine
- Configurable decision bands:
  - Low risk → auto-approve
  - Medium risk → step-up authentication
  - High risk → block
- Merchant specific overrides
- Fallback behavior on signal failure

---

### Explainability & Observability
- Reason codes attached to every decision
- Signal level contribution breakdown
- Audit logs for blocked transactions
- Ops dashboard with trend analysis

---

### Ops & Controls
- Manual allow/deny overrides
- Emergency kill switch for risk rules
- Real time alerting on anomaly detection
- Shadow mode testing for new rules

---

## Metrics & Success Criteria

### Input Metrics
- Signal availability rate
- Risk score computation latency
- Step up authentication success rate

### Outcome Metrics
- Fraud loss rate (% of GMV)
- Checkout conversion rate
- False positive rate
- False negative rate

### Guardrails
- Revenue impact due to blocks
- Ops review volume per 1,000 transactions
- Customer complaints tied to risk decisions

---

## Trade-offs & Design Decisions

- Rules vs ML models:
  - Rules offer explainability and control
  - ML offers adaptability but increases opacity
- Aggressive blocking vs step up friction
- Global thresholds vs merchant specific tuning
- Real time scoring vs async enrichment

---

## Risks & Failure Modes

- Overfitting rules to short term fraud patterns
- Bias amplification in risk signals
- Signal degradation during outages
- Silent conversion drops due to tuning errors

---

## Dependencies

- Device fingerprinting providers
- IP intelligence vendors
- Gateway support for step up auth
- Real time analytics pipeline

---

## Open Questions

- When should merchants self configure risk thresholds?
- What explainability level should be exposed externally?
- How should conflicting signals be resolved?
- What is the acceptable false positive ceiling?