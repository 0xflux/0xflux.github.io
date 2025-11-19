---
title: Home
layout: home
nav_order: 1
---

# Wyrm C2 Documentation

You can find the tool [here on GitHub](https://github.com/0xflux/Wyrm).

Wyrm (pronounced 'worm', an old English word for 'serpent' or 'dragon') is a post exploitation, open source, Red Team security testing framework framework, written in Rust designed to be used by Red Teams, Purple Teams, Penetration Testers, and general infosec hobbyists. 

This project is fully built in Rust, with extra effort going into obfuscating artifacts which could be present in memory. Project created and maintained by [flux](https://github.com/0xflux/), for **legal authorised security testing only**.

Wyrm currently supports only HTTPS agents using a custom XOR encryption scheme for encrypting traffic below TLS, with a unique packet design so that the packets cannot be realistically decrypted even under firewall level TLS inspection.

Updates are planned through versions 1,0, 2.0, 3.0, and 4.0. You can view
the planned roadmap in this project (see [Milestones.md](https://github.com/0xflux/Wyrm/blob/master/Milestones.md)). In time, this is designed to be an open source competitor to **Cobalt Strike**, **Mythic**, **Sliver**, etc.

### Features

- Implant uses a configurable profile to customise features and configurations
- IOCs encrypted in the payload to assist in anti-analysis and anti-yara hardening
- Implant transmits data encrypted below TLS, defeating perimeter inspection security tools out the box
- Dynamic payload generation
- Easy mechanism to stage files (such as built implants, PDF, zip, etc) on the C2 for download to support phishing campaigns and initial attack vectors
- Supports native Windows API commands, more planned in future updates
- Easy to use terminal client for the operator to task & inspect agents, and to manage staged resources
- Implant uses the most common User-Agent for comms to help it blend in covertly with traffic by default, this is also configurable to suit your engagement
- Easy, automated C2 infrastructure deployment with docker
- Anti-sandbox techniques which are highly configurable by the operator through profiles
- Backed by a database, fully timestamped to make reporting easier

This project is not currently accepting contributions, please **raise issues** or use **GitHub Discussions** and I will look into them, and help
answer any questions.

## Issues

For any bugs, or feature requests, please use the [Issues](https://github.com/0xflux/Wyrm/issues) tab, and for anything else - please use [GitHub Discussions](https://github.com/0xflux/Wyrm/discussions) on the project. I am active there, so I will be attentive to anything raised.

