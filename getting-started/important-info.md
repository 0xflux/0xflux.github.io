---
layout: default
title: Important Info
parent: Getting Started
nav_order: 1
---

# Important Info

## Release cycle

This project is under active development, and as such, it is possible a new release causes breaking changes.

Before pulling an update; please check the [release notes](https://github.com/0xflux/Wyrm/blob/master/RELEASE_NOTES.md) to see whether there are any breaking changes - for example if the
**configurable C2 profile** changes in a breaking way from a previous profile you have, you will want to make sure you backup and migrate
your profile. I will be excluding `/c2/profiles/*` and `.env` from git once the project is published in pre-release to prevent accidentally overwriting
your previous profile when running `git pull` to update your software.

## Licence

MIT License

Copyright (c) 2025 flux

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.

## Legal statement

The Software is intended **exclusively** for **authorised** penetration testers, Red Teams, Purple Teams, hobbyists, and security researchers who have obtained **explicit, written authorisation from the owner of each target system**.

Any use of the Software on systems for which you do not hold such authorisation is **strictly prohibited** and may constitute a criminal offence under the UK Computer Misuse Act 1990 (including sections on Unauthorised access to computer material, Unauthorised access with intent to commit further offences, and Unauthorised acts impairing operation) or equivalent laws elsewhere.

### Prohibited Conduct
You must not use, distribute, or facilitate use of the Software for:

- Unauthorised Access (CMA 1990, Section 1) — hacking into systems or accounts without permission.
- Unauthorised Modification (CMA 1990, Section 3) — altering, deleting, or corrupting data or programs you have no right to modify.
- Denial-of-Service (CMA 1990, Section 3A) — disrupting or interrupting any service, network, or application.
- Malware/Ransomware Creation — writing, incorporating, or deploying code intended to extort, damage, or hold data hostage.
- Any other malicious, unlawful, or harmful activities.

Or equivalent offenses in other jurisdictions.

**No Encouragement of Misuse:**

The Author expressly **does not condone, support, or encourage** any illegal or malicious activity. This Software is provided purely for legitimate security-testing purposes, in environments where full authorisation has been granted.

### Compliance with Laws & Regulations

**Local Laws**: You alone are responsible for ensuring your use of the Software complies with all applicable local, national, and international laws, regulations, and corporate policies.

### No Warranty

The Software is provided “as is” and “as available”, without warranties of any kind, express or implied.

We make no warranty of merchantability, fitness for a particular purpose, or non-infringement.

We do not warrant that the Software is error-free, secure, or uninterrupted.

### Limitation of Liability

To the fullest extent permitted by law, neither the Author nor contributors shall be liable for any:

- Direct, indirect, incidental, special, punitive, or consequential damages.
- Loss of revenue, profits, data, or goodwill.
- Costs of procurement of substitute goods or services.

This limitation applies even if we have been advised of the possibility of such damages. It is the responsibility of the professional operator to
use this tool safely.

### Solo

Wyrm C2 is a solo project by 0xflux and in no way represents views or qualities of my employer(s).
