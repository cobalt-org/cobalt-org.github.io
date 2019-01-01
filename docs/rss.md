---
title: "Docs::RSS"
layout: docs.liquid
data:
  route: rss
---
## RSS

To generate an RSS file from the metadata of your `_posts`,
you need to provide the following data in your `_cobalt.yml`:

```yml
# path where the RSS file should be generated
posts:
  title: My blog!
  description: Blog description
  rss: rss.xml
site:
  base_url: http://example.com
```

None of these fields are optional, as by the RSS
2.0 spec.

Make sure to also provide the fields `title`,
`published_date` in the front matter of
your posts.
