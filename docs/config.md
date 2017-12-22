extends: docs.liquid
title: "Cobalt::Docs::Config"
route: config
---
## Config File

In addition to change the defaults through cli options cobalt allows to
specify a config file (.cobalt.yml per default) where you can write these
configurations in.

You can see a config file used by [amethyst's
website](https://github.com/amethyst/website/blob/master/src/.cobalt.yml).

### Full Config File

```yaml
source: PATH_TO_FOLDER
dest: PATH_TO_FOLDER
layouts: PATH_TO_FOLDER
posts: PATH_TO_FOLDER
template_extensions: ['template', 'lqd', 'whatever']
rss: PATH_FOR_XML_FILE_TO_GENERATE
name: Cool name
description: My awesome blog
link: http://example.com
```
