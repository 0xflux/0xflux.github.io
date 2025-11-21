---
layout: default
title: Profiles
parent: Implant
nav_order: 1
---

**Important note**: If you make changes to the profiles (`c2/profiles/*`) then you will need to re-run the docker 
container for the `c2`, ensuring you pass the `--build` flag for the updated profile changes to have effect. After 
changing updating your profile(s), run: `docker compose up -d --build c2`.