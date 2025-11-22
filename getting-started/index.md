---
layout: default
title: Getting Started
nav_order: 2
---

As a TL;DR checklist for getting started:

- Environment variables for `POSTGRES_USER`, `POSTGRES_PASSWORD` and `POSTGRES_DB` need to be set from where you run docker. I recommend using the provided .env, and changing the password before running the containers for the first time.
- If testing on localhost, set up TLS certificates to be trusted on your machine (instructions enclosed).
- Create a `profile.toml` file in `Wyrm/c2/profiles` as per the setup instructions.