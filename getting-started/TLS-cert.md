---
layout: default
title: Generating a TLS Certificate
parent: Getting Started
nav_order: 4
---

# Generating a TLS Certificate

Note: This page also deals with the `nginx.conf` setup, as well as certificates.

## Certificates

Before you install the C2 server with Docker, you first need to generate some TLS certificates, as well as setting up the 
`nginx.conf`.

You will find in the `Wyrm` directory that by now you should have cloned, an `/nginx` dir. The docker configuration I have provided 
will automatically look in this directory for the `nginx.conf`, and it will look for a TLS certificate & private key within `/nginx/certs`.

First, please make the `certs` directory, under `Wyrm/nginx/certs`. This directory is not present when you clone the repo, I have excluded
it from git.

You now need to put the certificate and private key of your domain into this directory. The auto-deployment of nginx via docker only supports
one site, and one pair of certs. If you are an advanced user, you may generate multiple certs for multiple sites, and edit the `nginx.conf` to support
multiple sites. If you are doing that, you will need to edit the `docker-compose.yml`; or remove the nginx build from docker, and manually configure
nginx & certificates on your C2 VPS. This is particularly pertinent if you are using redirectors into the C2. I may cover this in a later article 
within the docs.

**IMPORTANT**: What you name your certificate and key matters, you will need the names when setting up `nginx.conf`.

### Generating certificates

To generate valid TLS certificates, you have several options. 

1) Easiest & cheapest - Use certbot (in cert only mode) to generate your certificates and move them into `Wyrm/docker/certs`. 
2) Cheap, better, a bit more involved - Use a free, well known CA to generate certificates, such as Fastly.
3) Costly - Use of paid services for a verified TLS certificate. This will provide you the best trust and OPSEC on a Red Team engagement if it is required for bypassing your client's security controls. Threat actors occasionally do this, and there is no reason Red Team's shouldn't consider it.

Once you have generated the cert and private key, please place them into `Wyrm/docker/certs`.

#### Important note for localhost testing

**Important note**: If you are testing the Wyrm C2 on your localhost network - you need a certificate issued by a CA which your computer
trusts. This is required for both the agent **and** the GUI web client. Because of the architecture of the server-client, authentication takes
place over CORS, using HTTPS secure only cookies. Because of this, HTTP cannot be used by the client. 
**If you fail to follow these instructions, you will not get Wyrm working on localhost for testing.** 

The process is simple. I have written a how-to guide for this on my personal blog, you can find
a link [here](https://fluxsec.red/wyrm-c2-localhost-self-signed-certificate-windows). Remember, if you are testing this on localhost, generating
a local trusted CA is required.

## Nginx conf

Now with the certificate and private key in the `Wyrm/docker/certs` directory, you can turn your attention to the `nginx.conf` located 
in `Wyrm/docker/`.

You want to edit the `server_name` field to be that of your domain, and to match your certificate. So say we own
example.com and www.example.com, then we would edit the **two** `server_name` fields as so:

`server_name example.com www.example.com;`

Finally, change the below key and cert names to match what you named your key and cert in `Wyrm/docker/certs`.

```shell
ssl_certificate     /etc/nginx/certs/cert.pem;
ssl_certificate_key /etc/nginx/certs/key.pem;
```

And with that, you are done, ready for the next step!