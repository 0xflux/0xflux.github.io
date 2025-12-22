---
layout: default
title: Commands
parent: C2
nav_order: 4
---

# Commands

Here you can find instructions on how to use the commands. For those which are a little more complex, or need additional
explanation, you can see detailed pages under the menu. Otherwise, the commands will be listed here which are self
explanatory.

- `whoami`: Natively, without powershell/cmd, retrieves your SID, domain\username and token privileges.
- `ka` or `kill_agent`: Kills the selected implant.
- `ra` or `remove_agent`: Removes an agent from your console without explicitly terminating it (useful for dead agents)
- `clear` or `cls`: Clears your console
- `export_db`: Will export the database to /data/exports/{agent_id}
- `set sleep [time SECONDS]`: Sets the new sleep time of the agent
- `ps`: List running processes
- `cd`: Change directory
- `pwd`: Prints the current working directory of the implant
- `ls`: Directory listing
- `cp <from> <to>`: Copy a file
- `mv <from> <to>`: Move a file
- `rm <path to file>`: Removes file (this command cannot remove a directory) - accepts relative or absolute paths
- `rm_d <path to dir>`: Removes a directory
- `pillage`: Searches the system for files of interest (this can be long running and may cause the beacon to appear dead whilst it runs)
- `run <command/s>`: Uses PowerShell to run a command
- `kill <pid>`: Terminate a process
- Registry commands: See the dedicated page
- Executing dotnet: See the dedicated page
- Exfiltrating files: See the `pull` dedicated page
- Dropping files on disk: See the dedicated `drop` page