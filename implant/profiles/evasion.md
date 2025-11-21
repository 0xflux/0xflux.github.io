---
layout: default
title: Evasion
parent: Profiles
nav_order: 1
---

# Evasion

The implant can be configured for sandbox evasion with the following settings (refer to parent page for where they should go):

- `ram`: This will make the implant check that there is at least 4 GB of memory installed on the machine.
- `trig`: This checks for trigonometric movements of a mouse on the screen which are more likely to be done by a human. This is inspired by some anti-sandbox implemented by LummaC2 as reported on by [Outpost24](https://outpost24.com/blog/lummac2-anti-sandbox-technique-trigonometry-human-detection/).