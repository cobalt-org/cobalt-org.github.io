extends: docs.liquid
title: "Cobalt::Docs::Liquid Variables"
route: variables
---

## Variables

Cobalt makes a variety of data availale as Liquid variables.

This is can be helpful for:
- Theming
- Easier maintenance for only having one place to update things

Example:
```html
<html>
  <head>
    <title>{% raw %}{{ title }}{% endraw %}</title>
  </head>
  <body>
  {% raw %}{{ content }}{% endraw %}
  </body>
</html>
```

### Global variables

Variable | Format | Description
---------|--------|-------------
`site`   | Object | Site-wide information
`page`   | Object | Current-page information

### Site Variables

Variable           | Format | Description
-------------------|--------|------------
`site.title`       | String | The title of the entire site, see [`_cobalt.yml`](/docs/config.html).
`site.description` | String | The description of the entire site, see [`_cobalt.yml`](/docs/config.html).
`site.base_url`    | String | The URL of your site, see [`_cobalt.yml`](/docs/config.html).  This is helpful for making absolute URLs, particularly when run within [`cobalt watch`](/docs/usage.html).
`site.data`        | Object | The merged result of [`_data`](/docs/directory.html) and [`site: data`](/docs/config.html).

### Page Variables

In the context of your [page content](/docs/pages.html):

Variable              | Format          | Description
----------------------|-----------------|------------
`page.permalink`      | String          | Relative path to the page, see [frontmatter](/docs/front.html).
`page.title`          | String          | The title of the page, see [frontmatter](/docs/front.html).
`page.description`    | String          | The description of the page, see [frontmatter](/docs/front.html).
`page.categories`     | List of Strings | Hierarchical categories this page lives under, see [frontmatter](/docs/front.html).
`page.published_date` | `YYYY-MM-DD HH:MM:SS TZ` | The date the page was initially published, see [frontmatter](/docs/front.html).
`page.is_draft`       | Boolean         | See [frontmatter](/docs/front.html).
`page.file.permalink` | String          | Relative path to the source file.
`page.data`           | Object          | User-defined data, see [frontmatter](/docs/front.html).

Additionally, in the context of your [page layout](/docs/layouts.html):

Variable       | Format | Description
---------------|--------|------------
`page.content` | String | The rendered page content (i.e. excludes the layout).
`page.excerpt` | String | The rendered excerpt of a page, see [`excerpt` / `excerpt_separator`](/docs/front.html).
