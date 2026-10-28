# Record selective domain event history

Material delivery changes such as confirmation, process revision, baseline approval, risk acceptance, testing, and review will be appended as domain events from which current engagement views are projected. High-volume progress, model logs, media chunks, and binary artifacts remain in purpose-built stores and contribute references rather than bloating the same event stream. This selective history preserves provenance and reconstruction without forcing every operational datum into full event sourcing.
