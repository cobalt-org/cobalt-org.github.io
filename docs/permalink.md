---
title: "Docs::Permalink Templates"
layout: docs.liquid
data:
  route: permalink
---
## Permalink Templates

Permalinks refer to the relative URL for your pages.  Cobalt supports a
flexible way to build permalinks, allowing you to leverage various Liquid
template variables.

Permalinks are configured in the [frontmatter](/docs/front).  When
configuring a permalink, you're most likely to want to set it as a
[default](/docs/config)

Example:
```yml
title: My first Blogpost
layout: posts.liquid
permalink: /some/other/file.html
```
Results in
- The file's URL: `your-website.com/some/other/file.html`
- [`page.permalink`](/docs/variables): `some/other/file.html`

Note: Permalinks templates must start with a `/`.

### Pretty URLs

When you omit the file extension (e.g. `.html`) in your permalink, Cobalt will
treat the permalink as a folder and create the file with the name `index.html`.

Example:
```yml
title:   My first Blogpost
layout: posts.liquid
permalink: /some/other/file
```
Results in
- The file's URL: `your-website.com/some/other/file/index.html`
- [`page.permalink`](/docs/variables): `some/other/file`

### Template Variables

Variable     | Description
-------------|------------
`parent`     | The directory path to the file.  e.g. If the file is `posts/some/file.md`, then `parent` will be `posts/some`.
`name`       | The file name without the extension.  e.g. If the file is `posts/some/file.md`, then `name` will be `file`.
`ext`        | The output file extension.
`slug`       | The page's [`slug`](/docs/front).
`categories` | The [`categories`](/docs/front) for the page, separated by `/`.  e.g. If the frontmatter's `categories` are `"Animals", "Dogs"`, then the permalink's `categories` is `animals/dogs`.
`year`       | The [`published_date`](/docs/front)'s year.
`i_month`    | The [`published_date`](/docs/front)'s month.
`month`      | The [`published_date`](/docs/front)'s month, with a leading `0`.
`i_day`      | The [`published_date`](/docs/front)'s day.
`day`        | The [`published_date`](/docs/front)'s day, with a leading `0`.
`hour`       | The [`published_date`](/docs/front)'s hour, 24-hour clock, with a leading `0`.
`minute`     | The [`published_date`](/docs/front)'s minute, with a leading `0`.
`second`     | The [`published_date`](/docs/front)'s second, with a leading `0`.
`data`       | The frontmatter [`data`](/docs/front).

Example:
```yml
title: Corgi
layout: posts.liquid
categories:
  - Animals
  - Dogs
permalink: /{%raw%}{{categories}}{%endraw%}/{%raw%}{{slug}}{%endraw%}
```
Results in
- The file's URL: `your-website.com/animals/dogs/corgi/index.html`
- [`page.permalink`](/docs/variables): `animals/dogs/corgi`

### Built-in Permalink Styles

Cobalt also provides some built-in permalink templates.

Permalink Style | URL Template
----------------|-------------
`path`          | `/{%raw%}{{parent}}{%endraw%}/{%raw%}{{name}}{%endraw%}{%raw%}{{ext}}{%endraw%}`

Example file `some/other/file.md`:
```yml
title:   My first Blogpost
layout: posts.liquid
permalink: path
```
Results in
- The file's URL: `your-website.com/some/other/file.html`
- [`page.permalink`](/docs/variables): `some/other/file.html`
