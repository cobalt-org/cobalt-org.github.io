extends: docs.liquid
title: "Cobalt::Docs::Usage"
route: usage
---
## Usage

```
$ cobalt -h
USAGE:
    cobalt [FLAGS] [OPTIONS] <SUBCOMMAND>

FLAGS:
        --drafts     Include drafts.
    -h, --help       Prints help information
        --silent     Suppress all output
        --trace      Log ultra-verbose (trace level) information
    -V, --version    Prints version information

OPTIONS:
    -c, --config <FILE>            Config file to use [default: .cobalt.yml]
    -d, --destination <DIR>        Destination folder [default: ./]
        --dump <dump>...           Dump the specified internal state [values: Liquid]
    -l, --layouts <DIR>            Layout templates folder [default: ./_layouts]
    -L, --log-level <log-level>    Log level [default: info] [values: error, warn, info, debug, trace, off]
    -p, --posts <DIR>              Posts folder [default: ./posts]
    -s, --source <DIR>             Source folder [default: ./]

SUBCOMMANDS:
    build     build the cobalt project at the source dir
    clean     cleans directory set as destination
    help      Prints this message or the help of the given subcommand(s)
    import    moves the contents of the dest folder to the gh-pages branch
    init      create a new cobalt project
    new       Create a new post or page
    serve     build and serve the cobalt project at the source dir
    watch     build, serve, and watch the project at the source dir
```