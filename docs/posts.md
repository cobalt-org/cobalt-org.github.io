extends: docs.liquid
title: "Cobalt::Docs::Posts"
route: posts
---
## Posts

Posts are special [pages](/docs/pages.html) that live in
`posts`.  You can use a different directory for posts with the
`-p` flag or by setting the `posts` variable in
your .cobalt.yml.

Example:
```
extends: posts.liquid

title:   My first Blogpost
date:    01 Jan 2016 21:00:00 +0100
---
Hey there this is my first blogpost and this is super awesome.

My Blog is lorem ipsum like, yes it is..
```

The `date` attribute will be used to sort blog posts (from last to first).
`date` must have the format `%dd %Mon %YYYY %HH:%MM:%SS %zzzz`, so for example
`27 May 2016 21:00:30 +0100`.

### Drafts

Cobalt supports leaving posts in "draft" state. Drafts will not be
rendered unless Cobalt is run with the `--drafts` flag.

To mark a post as draft you can either set draft: true in your front
matter or add it to the drafts folder (`_drafts` by default). The draft
folder location can be specified using the draft key in your
`.cobalt.yml`.
