---
title: "Docs::Troubleshooting"
layout: docs.liquid
data:
  route: trouble
---
## Troubleshooting

Every command supports logging additional detail that can be useful when troubleshooting cobalt.  For example:
```sh
$ cobalt build --log-level=debug # Show some additional context

$ cobalt build --trace # Show everything
$ cobalt build --log-level=trace # Same as above
```

### Useful commands

Show config after processing defaults, etc:
```sh
$ cobalt debug config
```

Show all files for a given collection:
```sh
$ cobalt debug files pages
$ cobalt debug files posts
$ cobalt debug files posts --draft
$ cobalt debug files assets
$ cobalt debug files assets --trace
```

`--trace` is useful to know
- What the final `ignore` pattern is
- Why files or directories where ignored
- etc

Supported code highlight themes:
```sh
$ cobalt debug highlight themes
```

Supported code highlight language syntaxes:
```sh
$ cobalt debug highlight syntaxes
```
