# Metric Framework Philosophy

## Context
Payments and risk platforms operate in a high stakes environment where
optimizing for growth alone can introduce systemic fragility, financial loss,
and trust erosion. Metrics in such systems must balance **business outcomes,
system reliability, and risk containment**.

This document outlines the metric philosophy used for the Payments & Risk Platform,
including why a North Star Metric is used, its limitations, and how it is augmented
with complementary metric frameworks.

---

## Why a North Star Metric Exists

The platform uses a **North Star Metric (NSM)** as an alignment mechanism across
product, engineering, operations, and business stakeholders.

**North Star Metric: Net Successful Transaction Value (NSTV)**  
NSTV = GMV × Payment Success Rate − Refunds − Fraud Losses

### Why NSTV
- Captures *net* value, not surface level growth
- Forces trade-offs between conversion, reliability, and fraud risk
- Aligns platform success directly with merchant business outcomes
- Prevents optimization for volume at the cost of trust or loss exposure

NSTV answers the executive level question:
> “If this number improves sustainably, is the platform genuinely healthier?”

---

## Limitations of a North Star Metric

A North Star Metric alone is **insufficient and potentially dangerous**, especially
in financial systems:

- It is **lagging**, not actionable on a daily basis
- It can mask localized failures (e.g., gateway outages, fraud spikes)
- It is vulnerable to gaming if not constrained by guardrails

For this reason, NSTV is treated as an **outcome anchor**, not an execution metric.

---

## Augmented Metric Stack

To address these limitations, the platform uses a layered metric framework.

---

### 1. North Star Metric (Outcome Alignment)
**Purpose:** Strategic alignment and long-term health  
**Used for:** Executive reviews, roadmap prioritization

Example:
- Net Successful Transaction Value (NSTV)

---

### 2. Input / Leading Metrics (Execution Control)
These metrics represent **levers the product team can actively influence** and
are causally linked to the NSM.

Examples:
- Payment success rate by method (UPI, cards, wallets)
- Retry recovery rate by failure type
- Gateway specific latency and error rates

These metrics answer:
> “What exactly changed that moved (or failed to move) the NSM?”

---

### 3. Guardrail Metrics (Risk Containment)
Guardrails ensure that short-term gains do not compromise long-term platform
integrity or merchant trust.

Examples:
- Fraud loss rate
- Refund SLA breach rate
- Latency overhead introduced by orchestration

These metrics define **non-negotiable boundaries**:
> “This number must not cross this threshold, even if growth slows.”

---

### 4. Counter-Metrics (Anti-Gaming & Truth Signals)
Counter metrics exist to detect false positives, metric gaming, and unintended
consequences.

Examples:
- Percentage of retries that reduce conversion
- False positive fraud blocks
- Manual ops intervention rate

These metrics answer:
> “Are we accidentally hurting users or merchants while appearing to grow?”

---

## Why Other Frameworks Were Not Used in Isolation

- **OKRs:** Useful for planning, but weak at representing system health and risk
- **AARRR:** User-centric, but insufficient for platform and infra products
- **HEART:** Optimizes UX quality, not financial or operational integrity

While elements of these frameworks inform feature level decisions, none alone
provide the rigor required for a payments and risk platform.

---

## Summary

The metric strategy intentionally combines:
- A **North Star Metric** for alignment
- **Input metrics** for execution
- **Guardrails** for safety
- **Counter-metrics** for truth

This layered approach ensures the platform optimizes not for activity or optics,
but for **sustainable, trustworthy value creation** in a financial system.