# Refund Lifecycle Flow

1. Refund initiated
2. Idempotency key generated
3. Refund request sent to gateway
4. Gateway response:
   - Accepted → pending settlement
   - Failed → retry or manual review

5. Settlement confirmation received
6. Refund marked completed
7. Liability updated and reconciled