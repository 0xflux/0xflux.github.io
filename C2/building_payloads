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

## Build process

To build your implants (exe, dll and svc [svc not yet implemented]) you need to navigate using the menu 
to `Preparation -> Build all agents`. From there, simply enter the profile name of your customised profile (**remember** you should NOT
use the `profile.example.toml` file and instead migrate this to a NEW file).

So, if you created `Wyrm\c2\profiles\default.toml`, in the input box enter: `default.toml` and hit build.

The C2 will begin building your binaries - note this takes place on the server, so be patient whilst it does this (time can vary depending on
CPU / RAM on the server). Once built, the C2 will return a 7z archive containing your implant binaries that you can then stage on the server.