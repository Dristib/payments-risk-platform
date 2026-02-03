# Risk Decision Flow

1. Transaction initiated
2. Risk signals ingested
3. Risk score computed
4. Decision band applied:
   - Low → approve
   - Medium → step-up auth
   - High → block

5. Decision logged with reason codes
6. Metrics updated