---
layout: default
title: Evasion
parent: Profiles
nav_order: 4
---

# Evasion

Please refer to the parent page for where the below keys should go in the profile `toml`.

## Anti-sandbox

Be **careful** when using the evasion options when sideloading; this can cause the target program to crash.

The implant can be configured for sandbox evasion with the following settings:

- `anti_sandbox.ram`: This will make the implant check that there is at least 4 GB of memory installed on the machine.
- `anti_sandbox.trig`: This checks for trigonometric movements of a mouse on the screen which are more likely to be done by a human. This is inspired by some anti-sandbox implemented by LummaC2 as reported on by [Outpost24](https://outpost24.com/blog/lummac2-anti-sandbox-technique-trigonometry-human-detection/). **Note**: This setting does not apply to the Windows service binary as there is no access to the cursor there.

## In memory 

### ETW

The implant is capable of performing in-memory evasion tactics. Currently, the implant supports ETW patching, which interestingly (from my testing)
completely defeats Defender's dynamic machine learning / heuristic detection models (no more `Win32/Wacatac`)!

Patching ETW has many benefits, you can read some useful links on this below, including from my own blog!

- [https://fluxsec.red/etw-patching-rust](https://fluxsec.red/etw-patching-rust)
- [https://fluxsec.red/event-tracing-for-windows-threat-intelligence-rust-consumer](https://fluxsec.red/event-tracing-for-windows-threat-intelligence-rust-consumer)
- [https://www.mdsec.co.uk/2020/03/hiding-your-net-etw](https://www.mdsec.co.uk/2020/03/hiding-your-net-etw)
- [https://reprgm.github.io/2023/08/30/lets-make-malware-part-11](https://reprgm.github.io/2023/08/30/lets-make-malware-part-11)
- [https://www.bordergate.co.uk/unhooking-event-tracing-for-windows](https://www.bordergate.co.uk/unhooking-event-tracing-for-windows)
- [https://fluxsec.red/full-spectrum-event-tracing-for-windows-detection-in-the-kernel-against-rootkits](https://fluxsec.red/full-spectrum-event-tracing-for-windows-detection-in-the-kernel-against-rootkits)

To enable this feature, simply set:

```toml
evasion.patch_etw = true
```

### AMSI

The implant supports the ability to patch AMSI via a `ret` instruction being written at the first byte of amsi.AmsiScanBuffer. This is
done by the agent when necessary if enabled, for instance, immediately before running a dotnet binary in memory via `dotex`.

To enable this feature, simply set:

```toml
evasion.patch_amsi = true
```