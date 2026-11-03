<!--
SPDX-FileCopyrightText: 2026 roolrz
SPDX-License-Identifier: Apache-2.0
-->

# less

Fullscreen pager for files and piped input.

Uses `lib-text-ui` for rendering and key handling. Native process input and byte-channel
streams provide asynchronous reads while the terminal supplies independent keyboard
input.

See the [implementation entry](src/main.rs) and [component declaration](component.json)
for the public interfaces, build dependencies and delivered artifacts.

## Usage

In a Native session with the required capabilities:

```sh
less /etc/fstab
less --help
```

## Boundaries

A pipe’s empty byte-channel message is not EOF; peer closure ends it. Interactive
operation requires a terminal session. This is the implemented pager subset, not full
GNU less compatibility.

## Build and test

Use this checkout inside the [repo-managed workspace](https://github.com/HypeR-Proj/HypeR).
From this repository directory:

```sh
make
make test
```

An absolute `OUT=/path/to/out` selects a shared output directory. The module
entry delegates to build/system, which prepares the installed SDK and declared
dependencies. Native binaries require HypeR; host module checks cover the tests
selected by component.json. A standalone clone does not contain the workspace’s
other source repositories or Native SDK.
