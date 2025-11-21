---
title: FAQ
layout: default
nav_order: 100
---

# FAQ

1. I deleted my containers and reinstalled the C2 but I get an error saying a migration failed when trying to start the C2.

Make sure you delete your docker volumes as well as containers when doing a fresh build.

2. I have built this on localhost but I cannot login and/or a beacon will not call back?

You most likely have not configured your TLS certificates for use on localhost. 
I have [provided a guide](https://fluxsec.red/wyrm-c2-localhost-self-signed-certificate-windows) on how to do this - ensure you follow that.
If you have followed that correctly, please raise an issue on the [repo](https://github.com/0xflux/Wyrm).