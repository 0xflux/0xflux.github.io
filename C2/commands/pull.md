---
layout: default
title: Pull
parent: Commands
nav_order: 4
---

# Pull File From Target

## Overview

`pull` exfiltrates a file from the target machine to the C2.  
The supplied path may be **absolute or relative**, and the file will be uploaded directly to the server.

The file is stored on the C2 in the **docker container** under: `data/loot/<target hostname>/<full original file path>`

If a file already exists at that location, it will be overwritten.

## Usage

```shell
pull <file path>
```

Where:

- **<file path>**: The path to the file you want to exfiltrate. Can be relative or absolute.

Example: `pull C:\Windows\Temp\payload.bin`.

This retrieves the file from the target and uploads it to the C2 using its original full path as part of the storage location.

## Memory Considerations

Using `pull` causes the file to be **fully read into memory** on the target machine before exfiltration.  
For this reason, only use `pull` on files **smaller than the available system RAM**.

## Important Notes

- **Overwrites Existing Files**: If the same path exists in the C2 storage, it will be replaced.  
- **Full-Read Operation**: The entire file is loaded into memory on the target before transfer.  
- **Path Preservation**: The C2 saves the file using the target’s full path for organizational clarity.  
- **Future Enhancement**: Streamed transfer mode is planned for later releases.  
