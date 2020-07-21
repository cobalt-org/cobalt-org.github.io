---
title: "Docs::Install"
layout: docs.liquid
data:
  route: install
---
## Installation

Cobalt supports Windows, Linux, and Mac.

### OS Package

**Arch Linux**
`pacman -S cobalt`

### Pre-built Binary

Requirements: *None*

Download a [release](https://github.com/cobalt-org/cobalt.rs/releases).

or the following will install cobalt to `~/.cargo/bin`:
```
$ curl -LSfs https://japaric.github.io/trust/install.sh | sh -s -- --git cobalt-org/cobalt.rs --crate cobalt
```

### From Source

#### Requirements

##### Debian 9 (stretch)

``console
# Install needed packages with
$ sudo apt install cmake git curl build-essential libssl-dev

# Install rust (do **not** use the package `sudo apt install rust`
# as it will install an old rust version). Use:
$ curl https://sh.rustup.rs -sSf | sh

# Source the Rust environment
$ source $HOME/.cargo/env
```

##### Windows

Without syntax highlighting / sass (requires `cargo ... --no-default-features`):

1. Ensure [Rust is installed](https://rustup.rs/).

With syntax highlighting / sass:

1. Ensure [Rust is installed](https://rustup.rs/) using [Build Tools for Visual
   Studio](https://visualstudio.microsoft.com/downloads/) instead of
   MinGW/MSYS2.
2. Install [Windows 10 SDK](https://developer.microsoft.com/en-us/windows/downloads/sdk-archive)
3. Run `"<VS Path>\vcvarsall.bat" amd64` in your command prompt you'll build from.

#### Compile Steps
1. Either
  `git clone https://github.com/cobalt-org/cobalt.rs.git`
  or
  Download a [zip archive](https://github.com/cobalt-org/cobalt.rs/archive/master.zip)
2. `cargo build --release`
3. Check if all tests are passing with:
    `cargo test`

You can also customize the build, including adding support for unstable [features](https://github.com/cobalt-org/cobalt.rs/blob/master/Cargo.toml#L66):

```text
$ cargo build --release --features=sass
```
