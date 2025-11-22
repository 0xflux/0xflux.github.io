---
layout: default
title: Obfuscation
parent: Profiles
nav_order: 2
---

# Obfuscation

Obfuscation (my definition) is the act of hiding something either through deception or making something so complex it becomes a chore
for a human to analyse (either manually, or to create automation for).

The below profile keys will assist you in obfuscating the post exploitation payload (not concerning droppers / loaders, etc).

Please refer to the parent page to see where the relevant keys should go in the `toml`.

## Timestomping

[Timestomping](https://attack.mitre.org/techniques/T1070/006/) is the act of modifying timestamps of a file, artifact or metadata 
which is often done to hide changes to the system, or outright cause deniability. I have 
written a [blog post about timestomping](https://fluxsec.red/timestomping-pe-compile-time) in more detail if you are interested!

To timestomp the binary, you can use the `timestomp` key with a british date/time format as follows:

```toml
evasion.timestomp = "08/04/2022 19:53:15"
``

This will change the Time-Date Stamp in the binary as follows:

![coff-header](coff-header.png)