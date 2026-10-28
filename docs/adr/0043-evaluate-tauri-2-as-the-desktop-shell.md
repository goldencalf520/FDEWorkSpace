---
status: proposed
---

# Evaluate Tauri 2 as the desktop shell

The preferred desktop candidate is Tauri 2 with a React and TypeScript interface, using its capability model, signed updater, and constrained sidecars while retaining Electron as the explicit fallback. The decision becomes accepted only after a Windows 11 x64 and macOS 13+ Apple Silicon and Intel spike verifies signing and updates, keychain access, sidecar lifecycle, large resumable transfer, offline recovery, browser evidence capture, million-line repository handling, and system-WebView consistency; Windows 10 and Windows ARM64 are Pilot-driven compatibility targets rather than initial External Beta commitments. Failure must trigger a recorded comparison rather than workaround-driven lock-in.
