---
layout: default
title: Components
parent: Getting Started
nav_order: 2
---

# Components

The Wyrm C2 is made up of the following components, which are deployable via a pre-configured docker setup:

- Implant: The `implant` is what it says on the tin! This is the binary which is designed to run on an endpoint as part of authorised Red Team testing. The implant is configurable via malleable profiles. See docs for more info.
- C2: The `C2` again, does what it says on the tin. This is the command-and-control server for deploying implants / tools and controlling them.
- Client: The `client` is a HTTP application that runs **separate** to the C2, and this can be 'taken with you'. It run's on localhost, allowing you to connect to the remote C2.
- Shared libraries: The project also includes some shared libraries, for structures and methods which are part of multiple components of this project.
- Nginx: The `nginx` directory of the project includes a `nginx.conf` designed to work with the `nginx` docker container, and permits CORS requests into the C2 which is required for the client. This directory must also contain your TLS certificate and private key. More information can be found in the setup guide.
- Docker: The project contains docker configuration to easily build and deploy infrastructure. For more information on this process, see the documentation.
