---
title: Home
layout: home
nav_order: 1
---

# Wyrm C2 Documentation

Wyrm (pronounced 'worm', an old English word for 'serpent' or 'dragon') is a post exploitation, open source, Red Team security testing framework framework, written in Rust designed to be used by Red Teams, Purple Teams, Penetration Testers, and general infosec hobbyists. 

This project is fully built in Rust, with extra effort going into obfuscating artifacts which could be present in memory. Project created and maintained by [flux](https://github.com/0xflux/), for **legal authorised security testing only**.

Wyrm currently supports only HTTPS agents using a custom XOR encryption scheme for encrypting traffic below TLS, with a unique packet design so that the packets cannot be realistically decrypted even under firewall level TLS inspection.

This project is a work in progress, currently released at v0.2 (Hatchling). Updates are planned through versions 1,0, 2.0, 3.0, and 4.0. You can view
the planned roadmap in this project (see [Milestones.md](https://github.com/0xflux/Wyrm/blob/master/Milestones.md)). In time, this is designed to be an open source competitor to **Cobalt Strike**, **Mythic**, **Sliver**, etc.

## Issues

For any bugs, or feature requests, please use the Issues tab, and for anything else - please use GitHub Discussions on the project. I am active on this project, so I will be attentive to anything raised.
