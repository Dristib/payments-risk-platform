# Chargebacks & Disputes Lifecycle PRD

## Problem Statement

Chargebacks represent one of the most expensive failure modes in a payments
ecosystem. Beyond direct financial loss, chargebacks introduce operational
overhead, legal complexity, network penalties, and long term trust degradation
with card networks and banks.

For merchants operating across multiple gateways, chargeback management is
fragmented, reactive, and opaque often handled through emails, spreadsheets,
and delayed alerts.

The absence of a unified chargeback lifecycle results in:
- Missed response deadlines and automatic losses
- Poor evidence quality and low win rates
- Inaccurate financial exposure tracking
- Inability to learn from dispute patterns

---

## Goals

- Centralize chargeback intake across gateways and networks
- Track dispute lifecycle with legal grade auditability
- Maximize win rate while minimizing operational cost
- Provide clear financial exposure and loss forecasting

---

## Non-Goals

- Acting as a legal advisory system
- Handling non card payment disputes (e.g., UPI disputes)
- Automating legal judgment or liability assignment

---

## Target Users

- Risk & fraud operations teams
- Finance and reconciliation teams
- Merchants managing dispute exposure
- Payments platform PMs

---

## Key Concepts & Definitions

- **Chargeback:** A payment reversal initiated by the issuing bank
- **Dispute Reason Code:** Network defined classification of dispute cause
- **Representment:** Submission of evidence to contest a chargeback
- **Win Rate:** Percentage of disputes successfully reversed
- **Exposure Window:** Period during which a transaction is eligible for dispute

---

## User Scenarios

1. Issuing bank initiates a chargeback due to “fraud” claim
2. Merchant receives dispute notification with limited response time
3. Ops team gathers evidence across systems
4. Representment is submitted to the card network
5. Dispute is won, lost, or escalated to arbitration

---

## Functional Requirements

### Chargeback Intake & Normalization
- Ingest chargeback events from multiple gateways
- Normalize dispute reason codes across networks
- De-duplicate disputes across providers
- Attach disputes to original transaction records

---

### Dispute Lifecycle Management
- State machine covering:
  - Chargeback received
  - Evidence required
  - Representment submitted
  - Network review
  - Won / Lost / Arbitration
- Timestamped transitions for compliance
- SLA tracking for response deadlines

---

### Evidence Management
- Evidence templates by reason code
- Centralized document storage
- Auto collection of transaction metadata
- Versioned evidence submissions

---

### Financial Exposure Tracking
- Real time exposure calculation
- Loss forecasting by reason code and gateway
- Tracking of fees, penalties, and reversals
- Reconciliation with settlements

---

### Ops & Alerting
- Deadline breach alerts
- High volume dispute spikes
- Win rate degradation alerts
- Manual override and escalation paths

---

## Metrics & Success Criteria

### Input Metrics
- Evidence submission completion rate
- Average time to representment
- Ops effort per dispute

### Outcome Metrics
- Chargeback win rate
- Net loss per 1,000 transactions
- Network penalty avoidance rate

### Guardrails
- Missed response deadline rate
- Evidence rejection rate
- Arbitration cost overruns

---

## Trade-offs & Design Considerations

- Defending all disputes vs selective representment
- Manual curation vs templated evidence
- Automation vs legal accuracy
- Aggressive defense vs customer goodwill

---

## Risks & Failure Modes

- Missing deadlines due to alert failures
- Submitting low quality or incorrect evidence
- Misclassification of reason codes
- Network rule changes breaking workflows

---

## Dependencies

- Gateway dispute APIs and webhooks
- Card network rules and SLAs
- Secure document storage
- Finance ledger integration

---

## Open Questions

- When should disputes be auto abandoned?
- What win rate threshold justifies arbitration?
- How much configurability should merchants have?
- How should dispute insights feed back into risk rules?