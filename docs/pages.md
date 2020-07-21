---
title: "Docs::Pages"
layout: docs.liquid
data:
  route: pages
---
## Pages

A page is any file found in the [`source`](/docs/config) directory that:
- Has an extension in [`template_extensions`](/docs/config)
- isn't hidden (leading `.` or `_`)
- isn't excluded through [`ignore`](/docs/config)

Pages go through several transformations:
1. Evaluate Liquid template expressions.
2. (If `.md` extension) Convert [Markdown](http://commonmark.org/help/) to HTML.
3. Wrap the content in a Liquid [layout](/docs/layouts).
4. Write the results to a parallel location in the [`destination`](/docs/config), but with an `.html` extension.

You can customize this behavior with the [frontmatter](/docs/front).

### Syntax Highlighting

You can highlight your code using the `{%raw%}{% highlight LANG %}{%endraw%}` / `{%raw%}{% endhighlight %}{%endraw%}` Liquid tags.

Alternatively, if you are using Markdown, you can [annotate your code
blocks](https://help.github.com/articles/creating-and-highlighting-code-blocks/#syntax-highlighting).

To see what syntaxes are supported:
```
$ cobalt debug highlight syntaxes
```

The theme is taken from your [`_cobalt.yml`](/docs/config).  To see the list of supported themes:
```
$ cobalt debug highlight themes
```
