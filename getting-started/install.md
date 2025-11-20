---
layout: default
title: Installing the server
parent: Getting Started
nav_order: 5
---

# Pre Installation Requirements

The installation process describes installing the Wyrm C2 framework on a server for production use. Anywhere where there
is a caveat for localhost testing, this will be explicitly called out. The guide is set out to describe the installation on 
a Debian server, targeting a Windows host.

Before beginning the installation process, the following requirements must be satisfied:

- C2 platform, this may be either:
  - A server for production (any Linux or Windows server will work, but the docs are specifically tailored for Debian), or
  - A localhost machine (can be a Windows PC, VM, Linux PC, etc)
- Docker installed on the C2 target platform
- At least 40 GB of storage
- At least 2 GB RAM
- A method of obtaining a TLS certificate (either from a paid-for CA, LetsEncrypt, or a trusted localhost CA [for localhost testing only]). If you do not know what this means, no fear, we cover TLS generation in the install docs.


Once you have satisfied the above requirements, please clone the [repository](https://github.com/0xflux/Wyrm) with the command: `git clone https://github.com/0xflux/Wyrm` and `cd` into the newly created dir.