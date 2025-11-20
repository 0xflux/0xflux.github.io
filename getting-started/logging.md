---
layout: default
title: Server logs
parent: Getting Started
nav_order: 6
---

# Server logs

Within the `c2` container, you will find a `/data/logs` directory with three log files:

- `access.log`: This is a raw log of authenticated vs unauthenticated requests to your API endpoints on the C2.
- `error.log`: Errors which occurred on the C2 are logged here.
- `login.log`: Logs login attempts. The password is not logged for successful logins, however unsuccessful logins will have the password logged.

**Please note**: that there is no automatic log rotation; so these could grow (particularly access.log). If space is a concern, you should set up
logrotate. This is a planned default feature from v0.6 onwards.