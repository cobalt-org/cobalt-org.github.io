---
title: "Docs::Liquid Variables"
layout: docs.liquid
data:
  route: variables
---
## Variables

Cobalt makes a variety of data available as Liquid variables.

This is can be helpful for:
- Theming
- Easier maintenance for only having one place to update things

Example:
```html
<html>
  <head>
    <title>{% raw %}{{ page.title }}{% endraw %}</title>
  </head>
  <body>
  {% raw %}{{ page.content }}{% endraw %}
  </body>
</html>
```

### Global variables

Variable     | Format | Description
-------------|--------|-------------
`site`       | Object | Site-wide information
`page`       | Object | Current-page information
`collection` | Object | Built-in [`posts`](/docs/posts).

### Site Variables

Variable           |  Format | Description
-------------------|---------|------------
`site.title`       |  String | The title of the entire site, see [`_cobalt.yml`](/docs/config).
`site.description` |  String | The description of the entire site, see [`_cobalt.yml`](/docs/config).
`site.base_url`    |  String | The URL of your site, see [`_cobalt.yml`](/docs/config).  This is helpful for making absolute URLs, particularly when run within [`cobalt serve`](/docs/usage).
`site.data`        |  Object  | The merged result of [`_data`](/docs/directory) and [`site: data`](/docs/config).
`site.time`        | DateTime | A `liquid_core::model::DateTime` representing the time of the website re-generation.

### Page Variables

In the context of your [page content](/docs/pages):

Variable              | Format          | Description
----------------------|-----------------|------------
`page.permalink`      | String          | Relative path to the page, see [frontmatter](/docs/front).
`page.title`          | String          | The title of the page, see [frontmatter](/docs/front).
`page.slug`           | String          | The identifier of the page, see [frontmatter](/docs/front).
`page.description`    | String          | The description of the page, see [frontmatter](/docs/front).
`page.categories`     | List of Strings | Hierarchical categories this page lives under, see [frontmatter](/docs/front).
`page.published_date` | `YYYY-MM-DD HH:MM:SS TZ` | The date the page was initially published, see [frontmatter](/docs/front).
`page.is_draft`       | Boolean         | See [frontmatter](/docs/front).
`page.file.permalink` | String          | Relative path to the source file.
`page.collection`     | String          | The slug of the page's collection.  `"posts"` for posts.
`page.data`           | Object          | User-defined data, see [frontmatter](/docs/front).

Additionally, in the context of your [page layout](/docs/layouts):

Variable       | Format | Description
---------------|--------|------------
`page.content` | String | The rendered page content (i.e. excludes the layout).
`page.excerpt` | String | The rendered excerpt of a page, see [`excerpt` / `excerpt_separator`](/docs/front).

### Collection Variables

Below, the built-in `posts` collection is demonstrated.

Variable                        | Format | Description
--------------------------------|--------|------------
`collections.posts.title`       | String | The title of the posts collection, see [`_cobalt.yml`](/docs/config).
`collections.posts.description` | String | The description of the posts collection, see [`_cobalt.yml`](/docs/config).
`collections.posts.slug`        | String | The identifier of the posts collection, see [`_cobalt.yml`](/docs/config).
`collections.posts.rss`         | String | The permalink for the posts' RSS feed, see [`_cobalt.yml`](/docs/config) and [RSS](/docs/rss).
`collections.posts.jsonfeed`    | String | The permalink for the posts' RSS feed, see [`_cobalt.yml`](/docs/config).
