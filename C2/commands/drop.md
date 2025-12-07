---
layout: default
title: Drop
parent: Commands
nav_order: 3
---

# Drop File to Disk

## Overview

`drop` writes a staged file from the C2 onto the target system’s disk.  
The file **must** already be staged on the C2; if it is not present in the staged resources list, the command will fail.

The payload is written into the **current working directory** of the agent at execution time.

## Usage

```shell
drop <staged_name> <destination_filename>
```

Where:

- **<staged_name>**: The colloquial name of the staged file as shown in the *Name* column of the **Staged Resources** panel.  
- **<destination_filename>**: The filename to write to disk. If you want the file to have an extension, you must include it explicitly.

Example: `drop my_dll version.dll`

This retrieves the staged file named `my_dll` and saves it to disk as `version.dll` in the agent’s current working directory.

## Staging Files

Before using `drop`, the file must be staged so the C2 can provide it to the agent.

To stage a file use the GUI stage resources panel.

## Important Notes

- **Written to Current Directory**: Files are deposited into the agent’s current working directory.  
- **Explicit Filenames**: Extensions are not added automatically — specify the full filename (e.g., payload.exe, module.dll).  
