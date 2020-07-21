---
title: "Docs:Layouts"
layout: docs.liquid
data:
  route: layouts
---
## Layouts

Layouts are templates in the [`_layouts`](/docs/directory) directory that contain
the common formatting for your pages.  They are compiled as
[liquid templates](https://shopify.github.io/liquid/)
(see [reference](https://shopify.github.io/liquid/basics/variations/)).  See
what [variables](/docs/variables) are available.

## Reusing Formatting

While different pages might need different layouts, there is generally some
shared formatting, like menus. You can use the `include` Liquid tag to pull in
shared formatting from the [`_includes` directory](/docs/directory).

Example layout:
```html
<!DOCTYPE html>
<html>
  <head>
    {%raw%}{% include "head.liquid" %}{%endraw%}
  </head>
  <body>
    <header>
      {%raw%}{% include "header.liquid" %}{%endraw%}
    </header>
    <main>
      {%raw%}{{ page.content }}{%endraw%}
    </main>
    <footer>
      {%raw%}{% include "footer.liquid" %}{%endraw%}
    </footer>
  </body>
</html>
```
