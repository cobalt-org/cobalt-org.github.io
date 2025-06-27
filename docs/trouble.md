---
title: "Docs::Troubleshooting"
layout: docs.liquid
data:
  route: trouble
---
## Troubleshooting

Every command supports logging additional detail that can be useful when troubleshooting cobalt.  For example:
```console
$ cobalt build --verbose # Show some additional context

$ cobalt build --verbose --verbose # Show everything
$ cobalt build -vv # Same as above
```

### Useful commands

Show config after processing defaults, etc:
```console
$ cobalt debug config
```

Show all files for a given collection:
```console
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
```console
$ cobalt debug highlight themes
```

Supported code highlight language syntaxes:
```console
$ cobalt debug highlight syntaxes
```
