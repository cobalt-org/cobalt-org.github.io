---
title: "Docs::Posts"
layout: docs.liquid
data:
  route: posts
---
## Posts

Posts are special [pages](/docs/pages) that live in
[`posts`](/docs/directory).  You can use a different directory for posts with the
[`posts.dir`](/docs/config) in your `_cobalt.yml`.

### Drafts

Cobalt supports leaving posts in "draft" state. Drafts will not be
rendered unless Cobalt is run with the `--drafts` flag.

To mark a post as draft you can either set `is_draft: true` in your
[frontmatter](/docs/front) or add it to the drafts folder
([`_drafts`](/docs/directory) by [default](/docs/config)).
