title: "Docs::Syntax Highlighting"
layout: docs.liquid
data:
  route: syntax_highlighting
---
## Syntax Highlighting

This feature is currently experimental and causes installation to fail on
Windows. To enable syntax highlighting, you need to install Cobalt [from
source](/docs/install.html) with the `syntax-highlight` feature.

You can highlight your code using the `{%raw%}{% highlight LANG %}{%endraw%}` / `{%raw%}{% endhighlight %}{%endraw%}` Liquid tags.

Alternatively, if you are using Markdown, you can [annotate your code
blocks](https://help.github.com/articles/creating-and-highlighting-code-blocks/#syntax-highlighting).

To see what syntaxes are supported:
```sh
$ cobalt debug highlight syntaxes
```

The theme is taken from your [`_cobalt.yml`](/docs/config.html).  To see the list of supported themes:
```sh
$ cobalt debug highlight themes
```
