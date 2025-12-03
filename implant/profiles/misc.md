---
layout: default
title: Implant
parent: Profiles
nav_order: 10
---

# Implant

The top level implant malleable options are outlined below. Note that subkeys, such as network, evasion, are covered in their own sections.

## Required

- `svc_name`: This is the name passed to the Windows Service Control Manager when you deploy the Windows service (**.svc**) binary. Ideally this should be an OPSEC safe name.

## Optional

- `debug`: If set to true will build the binary in debug mode, giving you verbose output of the binary. If set to false, or this key is not present, the implant will build in release mode with binary obfuscation optimisations turned on.
- `mutex`: You can set a global [Mutex](https://learn.microsoft.com/en-us/windows/win32/api/synchapi/nf-synchapi-createmutexa) value which is registered on the system, which ensures only one copy of that implant will run at one time. This could be useful for DLL Search-Order-Hijacking whereby there are a large number of subprocesses loading your implant. You can use this optionally in one profile (perhaps an initial access via side loading), with your second phase implant ready using a different (non-mutex) profile. You likely do **not** want this set for second phase (post initial compromise) operations, as you often want to spawn multiple agents on the same system for different reasons.