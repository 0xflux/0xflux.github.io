---
layout: default
title: Building payloads
parent: C2
nav_order: 2
---

# Building payloads

Payloads with the Wyrm C2 are built on needing a profile. Whilst the profiles allow for customisation of things such as evasion,
obfuscation and networking - they also provide basic requirements such as the C2 address, URI's, etc.

See the section on [profiles](https://docs.wyrm-c2.com/implant/profiles/) for more information on building this out.

The C2 will give you the following, for each agent profile:

- Exe, Dll, Svc which is a `reflective loader`. These are the **recommended** payloads to use. You may use the profile builder to also include DLL proxying (search order hijacking etc) and custom exports to the DLL loader. These payloads are prepended with **loader_{profile name}**.
- Exe, Dll, Svc of the raw `Wyrm` payload. This is good for use with your own loaders / other tooling. The DLL provided comes with a reflective loader, located at the export named `Load`. If you wish to use the Reflective DLL feature of the DLL, you can simply invoke the DLL from that export. Support is coming for a shellcode bootstrap at the beginning of the RDLL such that it will auto load when executed from byte 0x0.

## Build process

To build your implants (exe, dll and svc) you need to navigate using the menu 
to `Preparation -> Build all agents`. 

From there, simply enter the name of your implant within the profile, for example - if you used the 
provided [profile](https://docs.wyrm-c2.com/implant/profiles/), you would enter default. You can add as many implant profiles as you wish,
and they should be sub-headed with `[implants.name]` where name is the name of your unique implant build.

If you wish to build all implant profiles at once - simply enter `all` instead of a specific implant name.

The C2 will begin building your binaries - note this takes place on the server, so be patient whilst it does this (time can vary depending on
CPU / RAM on the server). Once built, the C2 will return a 7z archive containing your implant binaries that you can then stage on the server.