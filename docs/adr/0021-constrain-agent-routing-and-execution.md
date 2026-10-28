# Constrain agent routing and execution

The Decision API may route work across models and platforms according to task capability, language, context size, enterprise data policy, availability, price, and speed, but data policy filters candidates before cost optimization. Every run has approved cost, token, time, retry, and concurrency limits plus explicit stop conditions; routing reasons, estimates, fallbacks, and actual usage remain attributable so continuous failure cannot silently consume an open-ended budget.
