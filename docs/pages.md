extends: docs.liquid
title: "Docs::Pages"
route: pages
---

## Pages

A page is any file found in the [`source`](/docs/config.html) directory that
- Has an extension in [`template_extensions`](/docs/config.html)
- isn't hidden (leading `.` or `_`)
- isn't excluded through [`ignore`](/docs/config.html)

Pages go through several transformations:
1. Evaluate Liquid template expressions.
2. (If `.md` extension) Convert [Markdown](http://commonmark.org/help/) to HTML.
3. Wrap the content in a Liquid [layout](/docs/layouts.html).
4. Write the results to a parallel location in the [`destination`](/docs/config.html) but with a `.html` extension.

You can customize this behavior with the [frontmatter](/docs/front.html).

### Syntax Highlighting

This feature is currently experimental and causes installation to fail on
Windows. To enable syntax highlighting, you need to install Cobalt [from
source](/docs/install.html) with the `syntax-highlight` feature.

You can highlight your code using the `{%raw%}{% highlight LANG %}{%endraw%}` / `{%raw%}{% endhighlight %}{%endraw%}` Liquid tags.

Alternatively, if your using Markdown, you can [annotate your code
blocks](https://help.github.com/articles/creating-and-highlighting-code-blocks/#syntax-highlighting).
