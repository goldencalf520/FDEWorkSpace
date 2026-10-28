---
status: proposed
---

# Concentrate the application runtime stack

The spike will evaluate React and TypeScript for desktop and web interaction, TypeScript and Node for the control plane and primary orchestration logic, Rust for the Tauri shell and necessary privileged or high-performance local behavior, and isolated Python workers only where speech, document, or model ecosystems materially justify them. Business delivery areas may not independently introduce backend languages, because a concentrated runtime stack improves module depth, testing locality, and cross-platform maintenance.
