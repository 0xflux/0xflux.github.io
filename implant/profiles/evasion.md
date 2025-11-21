---
layout: default
title: Evasion
parent: Profiles
nav_order: 1
---

# Evasion

Please refer to the parent page for where the below keys should go in the profile `toml`.

## Anti-sandbox

The implant can be configured for sandbox evasion with the following settings:

- `ram`: This will make the implant check that there is at least 4 GB of memory installed on the machine.
- `trig`: This checks for trigonometric movements of a mouse on the screen which are more likely to be done by a human. This is inspired by some anti-sandbox implemented by LummaC2 as reported on by [Outpost24](https://outpost24.com/blog/lummac2-anti-sandbox-technique-trigonometry-human-detection/).

## In memory 

### ETW

The implant is capable of performing in-memory evasion tactics. Currently, the implant supports ETW patching, which interestingly (from my testing)
completely defeats Defender's dynamic machine learning / heuristic detection models (no more `Win32/Wacatac`)!

Patching ETW has many benefits, you can read some useful links on this below, including from my own blog!

- [https://fluxsec.red/etw-patching-rust]
- [https://fluxsec.red/event-tracing-for-windows-threat-intelligence-rust-consumer]
- [https://www.mdsec.co.uk/2020/03/hiding-your-net-etw]
- [https://reprgm.github.io/2023/08/30/lets-make-malware-part-11]
- [https://www.bordergate.co.uk/unhooking-event-tracing-for-windows]
- [https://fluxsec.red/full-spectrum-event-tracing-for-windows-detection-in-the-kernel-against-rootkits]

To enable this feature, simply set:

```toml
patch_etw = true
```