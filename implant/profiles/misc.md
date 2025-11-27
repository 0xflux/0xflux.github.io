---
layout: default
title: Implant
parent: Profiles
nav_order: 1
---

# Implant

The top level implant malleable options are outlined below. Note that subkeys, such as network, evasion, are covered in their own sections.

## Required

- `svc_name`: This is the name passed to the Windows Service Control Manager when you deploy the Windows service (**.svc**) binary. Ideally this should be an OPSEC safe name.

## Optional

- `debug`: If set to true will build the binary in debug mode, giving you verbose output of the binary. If set to false, or this key is not present, the implant will build in release mode with binary obfuscation optimisations turned on.
