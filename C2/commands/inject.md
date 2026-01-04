---
layout: default
title: Inject
parent: Commands
nav_order: 7
---

# Inject (Remote Thread)

`inject` loads a **Wyrm reflective DLL** into an **existing process** by PID using a classic
CreateRemoteThread injection.

- The C2 reads the staged payload bytes for the provided name.
- The implant opens the target process with `PROCESS_ALL_ACCESS`.
- Allocates RW memory, writes the payload, resolves the `Load` export from the unmapped image.
- Marks the memory RWX and starts a remote thread at the `Load` reflective injector.

## Requirements

- **Windows x64**.
- A staged **Wyrm DLL** that exports `Load` (reflective DLL build).
- Sufficient privileges to open the target PID with full access.

## Usage

1. **Stage a payload** (upload the Wyrm DLL to the C2 staged resources).
2. Run: `inject <staged_name> <pid>`

- `staged_name` is the 'download' name in the staged resources panel.
- `pid` is the target process ID.

## Output and troubleshooting

- Success: `Injected into process <pid>`
- Common failures:
  - Access denied / invalid PID (cannot open target process).
  - Wrong payload type (no `Load` export).
  - Cross-arch (x64 payload into x86 target or vice‑versa).

## Notes

- `inject` targets an **existing** process. Use `spawn` if you want a new child process.
- The current method is a single injection technique (remote thread); no alternate methods are exposed yet.
