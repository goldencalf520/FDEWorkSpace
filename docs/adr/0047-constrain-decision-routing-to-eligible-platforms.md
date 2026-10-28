# Constrain decision routing to eligible platforms

The Decision API will exclude unavailable, unauthorized, regionally inaccessible, data-policy-incompatible, over-budget, unhealthy, or unverified model and agent platforms before optimizing for task capability, cost, or speed. Routing records the evaluated candidates, reasons, estimates, selected fallback, and actual result, because a low-cost platform that cannot lawfully or reliably execute the task is not a valid decision candidate.
