---
layout: default
title: Network
parent: Profiles
nav_order: 3
---

# Network

The profiles allow you to specify the network configuration of the implant, and in fact, must be set up 
correctly to communicate with the C2.

For full examples, and to see where the keys in the `toml` must go, please see the parent page.

## C2 connectivity

Primarily, you must configure the implant to be able to call back to your C2. You may wish to do this via 
redirectors, or straight up to the C2's IP or domain name. In either case, the configuration is the same.

**Importantly** the C2 must support HTTPS (due to CORS, a design decision re the client), and currently, this is the only
supported method of communication back to the C2.

You must supply the following keys:

- `protocol`: The protocol in which the implant talks to the server.
- `address`: The domain name (including protocol) or IP address of your C2 (or redirector).
- `port`: The port in which to communicate with the C2 (if you are running non-standard).
- `token`: A unique token for the implant to authorise it to communicate with the C2. This is optional under the implant sub-profile (if you want custom tokens issued to different implants), but required at the `server` level for the server configuration.
- `uri`: Defined at the `server` level, this is an array of URIs which the agent will randomly select to beacon out to. For example: `["/submit.aspx", "/login", "/about"]`.

The following keys are optional:

- `sleep`: The default sleep time for a newly spawned beacon. If this field is not set, it will default to 3600 seconds (1 hour). This key can be supplied at the `implant` level in the `toml`, or the top level.
- `jitter`: This is defined at the `server` level of the `toml` and specifies jitter as a % of the max sleep time. If sleep is 10 seconds, setting jitter to 50% will cause the implant to check-in between every 5 seconds and 10 seconds.
- `useragent`: The user-agent which the implant appears as. If not set, the user-agent will default to `Mozilla/5.0 (Windows NT 6.1; WOW64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/55.0.2883.87 Safari/537.36`, the most common user-agent across the web (according to statistics I looked at).

## Periods