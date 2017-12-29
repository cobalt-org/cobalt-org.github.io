extends: docs.liquid
title: "Cobalt::Docs::Frontmatter"
route: front
---
## Frontmatter

All [pages](/docs/pages.html) optionally support having some metadata
associated with them, called the frontmatter.

The frontmatter metadata is formatted using [yaml](http://yaml.org/) and
separated by the main content by `---`.

Example:

```
title:   My first Blogpost
published_date:    01 Jan 2016 21:00:00 +0100
layout: posts.liquid
---
Hey there this is my first blogpost and this is super awesome.

My Blog is lorem ipsum like, yes it is..
```

### Default Frontmatter

```yaml
title: ~
description: ~
published_date: ~
format: Raw
layout: ~
is_draft: false
permalink: path
slug: ~
excerpt_separator: "\n\n"
excerpt: ~
categories: []
data: {}
---
```

#### Overriding defaults from filename

Cobalt will infer some information from the filename.

Recognized name formats include:
- `YYYY-MM-DD-slug.extension`
- `YYYY-MM-DD slug.extension`
- `slug.extension`

Metadata         | Inferred Default
-----------------|-----------------
`slug`           | The `slug` portion of the name.
`title`          | A best-effort at making a title from the `slug` portion.
`published_date` | The `YYYY-MM-DD` portion, if present.
`format`         | `Markdown` if `extension` is `md`.
`is_draft`       | `true` if in the [drafts folder](/docs/directory.html).

### Field Descriptions

Metadata            | Format           | Description
--------------------|------------------|-------------
`title`             | String           | The user-friendly name of the page.
`description`       | String           | The description of the page's content.
`published_date`    | `DD Month YYYY HH:MM:SS TZ` | The date the page was initially published.
`format`            | `Raw`, `Markdown`        | Content format that needs [parsing](/docs/pages.html).
`layout`            | String or `null` | The layout template that wraps the page content, if present.
`is_draft`          | Boolean          | If true, not published by default.
`permalink`         | [String](/docs/permalink.html) | The path for the generated page in [`destination`](/docs/directory.html).
`slug`              | String           | The path-friendly name of the file for use in [permalinks](/docs/permalink.html)
`excerpt_separator` | String           | A marker for what leading content should be extracted from the content as an excerpt.  `""` will cause no excerpt to be generated.
`excerpt`           | String           | Manually override the extracted excerpt.  This will be processed like a [page](/docs/pages.html).
`categories`        | List of Strings  | Hierarchical categories this page lives under.
`data`              | Object           | User-defined data available at [`page.data`](/docs/variables.html).
