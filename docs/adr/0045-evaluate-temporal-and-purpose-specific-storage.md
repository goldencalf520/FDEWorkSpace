---
status: proposed
---

# Evaluate Temporal and purpose-specific storage

The Durable Orchestration module will initially evaluate a self-hosted Temporal adapter plus a lightweight local adapter without exposing either implementation through its interface. The data design will evaluate PostgreSQL for relationships, current views, and key events; S3-compatible or controlled local content storage for large artifacts; rebuildable full-text and vector projections; secret stores for credentials; and Redis only for disposable cache, leases, and short-lived coordination. Acceptance requires recovery and twenty-agent scheduling evidence rather than product-name preference.
