title: "Docs::Directory"
layout: docs.liquid
data:
  route: directory
---
## Directory Structure

By default, cobalt mirrors your source file hierarchy in the destination,
helping you get closer to a What-You-See-Is-What-You-Get experience.

Files or folders that help generate the site but aren't directly part of the output
are "hidden" from cobalt by prefixing them with a `_`.

The default Cobalt site usually looks like this
```
.
|- _cobalt.yml
|- _layouts
|  |- default.liquid
|- _includes
|  |- header.liquid
|- _data
|  |- movies.json
|- _sass
|  |- base.scss
|- _site
|  |- index.html
|- posts
|  |- cats.md
|- _drafts
|  |- dogs.md
|- index.liquid
```

File / Directory | Description
-----------------|------------
`.`              | Root directory for your content.  Can be modified in [`_cobalt.yml`](/docs/config.html).
`_cobalt.yml`    | Site-wide [configuration](/docs/config.html) file
`_layouts`       | [Templates](/docs/layouts.html) that wrap pages.  The layout is chosen in the [frontmatter](/docs/pages.html)
`_includes`      | Liquid snippets of content to be shared among [layouts](/docs/layouts.html) or pages.
`_data`          | Data files that will be loaded as part of the `{%raw%}{{ site.data }}{%endraw%}` variable.
`_sass`          | Sass snippets that can be imported into your `.scss` files.
`_site`          | The output directory of cobalt.  Can be modified in [`_cobalt.yml`](/docs/config.html).
`posts`          | Pages in this directory will be treated as [blog posts](/docs/posts.html).  Can be modified in [`_cobalt.yml`](/docs/config.html).
`_drafts`        | Pages in this directory will be treated as [draft blog posts](/docs/posts.html).  Can be modified in [`_cobalt.yml`](/docs/config.html).
`index.liquid`   | Any other [pages](/docs/pages.html) found will be transformed by cobalt.
Other files      | Assets will be copied directly over from the source directory to the output directory.
