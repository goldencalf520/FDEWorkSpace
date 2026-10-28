# Orchestrate agents from a development task graph

Multi-agent development will begin from a dependency graph whose tasks declare inputs, outputs, owned code scope, interface contracts, acceptance criteria, and prohibited changes. The user sets a concurrency limit while the scheduler runs only tasks whose dependencies and code boundaries make parallel work safe; implementation occurs in isolated workspaces and an integration agent merges and verifies changes incrementally in dependency order rather than attempting one final bulk merge.
