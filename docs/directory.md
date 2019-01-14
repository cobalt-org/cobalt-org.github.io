---
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
|- _defaults
|  |- pages.md
|  |- posts.md
|- posts
|  |- cats.md
|- _drafts
|  |- dogs.md
|- index.liquid
```

File / Directory | Description
-----------------|------------
`.`              | Root directory for your content.  Can be modified in [`_cobalt.yml`](/docs/config).
`_cobalt.yml`    | Site-wide [configuration](/docs/config) file
`_layouts`       | [Templates](/docs/layouts) that wrap pages.  The layout is chosen in the [frontmatter](/docs/pages)
`_includes`      | Liquid snippets of content to be shared among [layouts](/docs/layouts) or pages.
`_data`          | Data files that will be loaded as part of the `{%raw%}{{ site.data }}{%endraw%}` variable.
`_sass`          | Sass snippets that can be imported into your `.scss` files.
`_site`          | The output directory of cobalt.  Can be modified in [`_cobalt.yml`](/docs/config).
`_defaults`      | `cobalt new` initializes files from here based on the collection name.
`posts`          | Pages in this directory will be treated as [blog posts](/docs/posts).  Can be modified in [`_cobalt.yml`](/docs/config).
`_drafts`        | Pages in this directory will be treated as [draft blog posts](/docs/posts).  Can be modified in [`_cobalt.yml`](/docs/config).
`index.liquid`   | Any other [pages](/docs/pages) found will be transformed by cobalt.
Other files      | Assets will be copied directly over from the source directory to the output directory.
