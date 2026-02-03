# Build vs Buy: Payment Orchestration

## Build Pros
- Full control over routing logic
- Custom retry strategies
- Deep observability

## Build Cons
- Higher maintenance cost
- Slower initial time-to-market
- Requires strong infra maturity

---

## Buy Pros
- Faster launch
- SLA-backed reliability
- Reduced engineering overhead

## Buy Cons
- Limited customization
- Vendor lock-in
- Black-box decisioning

---

## Decision

Initial phase favors **partial build**:
- Core routing and retry logic in-house
- Gateways used as execution rails

This balances speed with long-term control.