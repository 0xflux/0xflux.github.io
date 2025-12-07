---
layout: default
title: Registry Operations (reg)
parent: Commands
nav_order: 5
---

# Registry Operations

The `reg` command group provides a set of registry manipulation primitives for querying, adding, and deleting keys and values on the target host.  
All operations behave similarly to their Windows counterparts but execute directly within the agent.

Whitespace in registry paths must be wrapped in quotes.

---

# reg query

## Overview

`reg query` retrieves information from the registry using a full path to a key, with optional filtering on a specific value.

## Usage

```shell
reg query <path_to_key> <optional_value>
```

Where:

- **<path_to_key>**: The registry key path to query.  
- **<optional_value>**: If provided, only that specific value under the key will be queried.

If the path contains whitespace, wrap it in quotes.

Example:  `reg query "HKLM\Software\Microsoft\Windows NT\CurrentVersion" ProductName`

---

# reg add

## Overview

`reg add` creates or updates a registry value.  
If the key does not already exist, it will be created automatically.

## Usage

```shell
reg add <path_to_key> <value_name> <value_data> <data_type>
```

Where:

- **<path_to_key>**: The key to create or modify.  
- **<value_name>**: The name of the registry value to set.  
- **<value_data>**: The data to store in the value.  
- **<data_type>**: One of `string`, `DWORD`, or `QWORD`.

Example: `reg add HKCU\Software\Wyrm BeaconEnabled 1 DWORD`

You can verify modifications with a follow-up `reg query`.

---

# reg del

## Overview

`reg del` removes a registry key or value.  
Deleting a key also removes all subkeys beneath it, so use caution.

## Usage

```shell
reg del <path_to_key> <optional_value_name>
```

Where:

- **<path_to_key>**: The key path to remove.  
- **<optional_value_name>**: If provided, only that specific value will be removed; otherwise, the entire key is deleted.

Example: `reg del HKCU\Software\Wyrm BeaconEnabled`

---

## Important Notes

- **Quoted Paths**: If a path contains whitespace, wrap it in quotes.  
- **Destructive Operations**: `reg del` can remove full key trees recursively.  
- **Data Types**: Ensure you use the correct data type (`string`, `DWORD`, `QWORD`) for `reg add`.  
- **Verification**: After `reg add` or `reg del`, use `reg query` to validate changes.
