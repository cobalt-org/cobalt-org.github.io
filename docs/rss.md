extends: docs.liquid
title: "Cobalt::Docs::RSS"
route: rss
---
## RSS

To generate an RSS file from the metadata of your `_posts`,
you need to provide the following data in your config.file:

```yml
# path where the RSS file should be generated
rss: rss.xml
name: My blog!
description: Blog description
link: http://example.com
```

None of these fields are optional, as by the RSS
2.0 spec.

Make sure to also provide the fields `title`,
`date`, and `description` in the front matter of
your posts.
