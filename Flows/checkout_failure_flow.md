# Checkout Failure Handling Flow

1. User initiates payment
2. Payment routed to selected gateway
3. Gateway response:
   - Success → transaction completed
   - Failure → failure classified

4. Failure classification:
   - User error (insufficient funds)
   - Network timeout
   - Bank decline
   - Gateway outage

5. Retry decision:
   - Eligible → retry via alternate gateway
   - Ineligible → surface failure to user

6. Final state logged with reason code