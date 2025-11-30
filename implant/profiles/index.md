---
layout: default
title: Profiles
parent: Implant
nav_order: 1
---

# Profiles

**Important note**: If you make changes to the profiles (`c2/profiles/*`) then you will need to re-run the docker 
container for the `c2`, ensuring you pass the `--build` flag for the updated profile changes to have effect. After 
changing updating your profile(s), run: `docker compose up -d --build c2`.

I recommend you keeping your live profile settings in `/c2/profiles/` **outside** of Docker as the build process is designed to
copy this directory into the container. That directory is not tracked in git, so pulling updates to the project should not affect
your profile. As always, it is advisable to keep a backup of your profile between updates just in case.

As you should edit the profile which exists outside docker (as explained above), you should then run `docker compose up -d --build c2`
to re-ingest the changed profile.

# Profile layout

The profile comes in the form of a `toml` which must be located in `c2/profiles/*`. You can name it whatever you like, but one
must exist for the C2 to boot. Note that you **cannot** have more than one profile toml. You can however have multiple implant
definitions in here, and you can either build them selectively by entering the key name, or build them all by typing in 'all' in the
C2 agent builder page.

The profile is laid out as follows; see sub-sections within the docs for detail on each key.

```toml
[server]
token = "a_default_token" # A default value if not specified in a listener - a catch all requirement

[implants]

# Give the implant a name (in this case, it is called 'default'). You can choose to build all implants by entering 'all' on the C2,
# or you can build specific ones by passing in the implant's name, in this case, it is 'default'.
[implants.default]
debug = false # Optional, true specifies a debug build - note this will also mean strings are not encrypted if set to true
svc_name = "PrintScanService" # Name passed to SCM of the .svc binary

network.address = "https://localhost" # required
# The URI cannot match a download URI, the server will return an error
# Currently only the first URI is accepted by the implant, but you may specify many.
# v0.2 is going to ensure the implant can accept all specified URI's
network.uri = ["/submit.aspx", "/login", "/about"]
network.port = 443 # required
network.token = "my_unique_token"
network.sleep = 5
# If no UA is provided, it defaults to:
# Mozilla/5.0 (Windows NT 6.1; WOW64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/55.0.2883.87 Safari/537.36
network.useragent = "Mozilla/5.0 (Windows NT 6.1; WOW64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/55.0.2883.87 Safari/537.36"
# Optional, jitter time as a % of the max sleep time, if sleep is 10 seconds, setting jitter to 50% 
# will cause the implant to check-in between every 5 seconds and 10 seconds.
network.jitter = 50 

# Timestomping is an optional field; if set it must be in BRITISH format, dd/mm/YYYY hh:mm:ss or the build process will fail.
# This optional field sets the compile datetime of the binary, which may aid in opsec in terms of making your binary appear to be
# old. Note: This does not affect the timestamp of the file on disk when it is dropped, that is managed by the OS.
evasion.timestomp = "08/04/2022 19:53:15"
evasion.patch_etw = true # Optional, patches Events Tracing for Windows on the process

anti_sandbox.ram = true # Optional
anti_sandbox.trig = true # Optional (does not apply to the svc binary)

# Optional define custom DLL exports, including custom names which launch the agent, 
# or you can provide an export which runs machine code for anti-analysis
exports.ToWyrmOnly = {} # Optional
exports.WithMachineCode = { machine_code = [0x90, 0x90, 0xC3] } # Optional

# Optional
string_stomp.remove = [
    "library\\std\\src\\thread\\scoped.rs", 
]

# Optional
[implants.default.string_stomp.replace]
"library\\std\\src\\thread\\current.rs" = "string_one"
"Some\\path\\here" = "string_two"
```