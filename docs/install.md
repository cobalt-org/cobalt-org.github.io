title: "Docs::Install"
layout: docs.liquid
data:
  route: install
---
## Installation

Cobalt supports Windows, Linux, and Mac.

### OS Package

*None available yet*

### Pre-built Binary

Requirements: *None*

Download a [release](https://github.com/cobalt-org/cobalt.rs/releases).

or the following will install cobalt to `~/.cargo/bin`:
```
$ curl -LSfs https://japaric.github.io/trust/install.sh | sh -s -- --git cobalt-org/cobalt.rs --crate cobalt
```

### From Source

Requirements: [Rust](https://www.rust-lang.org/en-US/install.html)

Steps
1. Either
  `git clone https://github.com/cobalt-org/cobalt.rs.git`
  or
  Download a [zip archive](https://github.com/cobalt-org/cobalt.rs/archive/master.zip)
2. `cargo build --release`

You can also customize the build, including adding support for unstable [features](https://github.com/cobalt-org/cobalt.rs/blob/master/Cargo.toml#L66):

```bash
$ cargo build --release --features=sass
```
