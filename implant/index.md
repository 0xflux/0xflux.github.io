---
layout: default
title: Implant
nav_order: 3
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
