---
layout: default
title: Spawn
parent: Commands
nav_order: 6
---

# Spawn (Early Cascade)

`spawn` launches a **new Wyrm agent in a fresh child process** using the **Early Cascade Injection** technique.  
Unlike `inject`, which targets an existing PID, `spawn` creates its own suspended process and boots the payload inside it. The
technique was first published by [Outflank](https://www.outflank.nl/blog/2024/10/15/introducing-early-cascade-injection-from-windows-process-creation-to-stealthy-injection/).

The process is as follows:

- Creates a suspended process using the configured **spawn-as image**.
- Copies the staged payload into the new process (PE indicators are stomped for extra stealth).
- Finds the `Shim` export inside the payload and arms Early Cascade by patching `g_ShimsEnabled` and `g_pfnSE_DllLoaded`.
- Resumes the thread so the shim triggers the reflective loader (`Load`) in the process.

## Requirements

- **Windows x64**.
- A staged **Wyrm DLL payload** that exports `Shim` (the reflective DLL build includes this).
- A valid **spawn-as executable path** (defaults to `C:\Windows\System32\svchost.exe`).

## Configuration (spawn-as image)

The spawn-as image is compiled into the implant:

- Profile field: `evasion.spawn_as`
- Build env: `DEFAULT_SPAWN_AS`
- Fallback: `C:\Windows\System32\svchost.exe`

Example profile snippet:

```toml
evasion.spawn_as = "C:\\Windows\\System32\\notepad.exe"
```

## Usage

Stage a payload (upload the Wyrm DLL to the C2 staged resources).

From the operator console:

```shell
spawn <staged_name>
```

Use the staged resource internal name shown in the C2 UI. A new agent should check in with a new ID.
Output and troubleshooting

On success, the agent returns `Process created via Early Cascade Injection.`

On failure, the error includes a Win32 code (e.g., Failed to create process. Error code: 0x...).

### If no new agent appears:

1) Verify the staged file is the Wyrm DLL (must export Shim).
2) Confirm architecture is x64.
3) Ensure the spawn-as path exists on the target.
