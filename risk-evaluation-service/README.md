# Risk Evaluation Service

Backend service for real-time payment transaction risk evaluation.

## What This Does

Evaluates every payment transaction and returns a decision:
- **ALLOW** - Low risk, approve payment
- **REVIEW** - Medium risk, needs manual check
- **BLOCK** - High risk, decline payment

## How It Works

1. Receives transaction details (amount, user, payment method)
2. Runs 3 risk rules:
   - High amount check
   - Velocity check (too many transactions)
   - Geographic mismatch check
3. Calculates risk score (0-100)
4. Returns decision + reason codes

## Based on PRDs

Implements the risk logic from:
- [Fraud & Risk Scoring PRD](../PRDs/03_fraud_risk_scoring_PRD.md)
- [Risk Decision Flow](../Flows/risk_decision_flow.md)

## Tech Stack

- Node.js + Express
- PostgreSQL
- REST API

## Status

🚧 **In Progress** - Architecture complete, code coming soon

## Next Steps

1. Build database schema
2. Implement risk rules
3. Create API endpoints
4. Add tests

---

**Full documentation:** [Architecture](./docs/ARCHITECTURE.md) | [API Docs](./docs/API.md)
