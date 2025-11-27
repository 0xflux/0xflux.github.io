---
layout: default
title: Implant
nav_order: 4
---

# Implant

The implant represents the base building block of the Wyrm C2 from an 'actions on objective' perspective. The base implant 
comes in several (Windows) flavours -

- Exe
- DLL
- Svc

This is excluding stagers etc.

The implant itself is designed to communicate over HTTPS, with support coming for SMB and DNS.

The implant itself is designed to be highly customisable through the use of toml profiles, which are outlined in the documentation. The core implant
itself is likely to become detected through hashing and yara, but there are some techniques you can apply to make it less likely for your core
implant to be detected on a red team operation. More information can be found in the `Profiles` section.

## The service binary

Wyrm will produce a `.svc` Windows service as part of the build process which can be used for local privilege escalation (unquoted service
paths for example). There are some caveats with this, in that some malleable options cannot be applied to it. See the specific remarks against
such items in the docs where applicable.

The service is designed not to be stoppable, except via the operator running the **kill_agent** (or **ka**) command. This will not prevent
an EDR running as a driver from killing the agent, but it should at least stop most stop human intervention.