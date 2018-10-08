title: "Docs::Documents"
layout: docs.liquid
data:
  route: documents
---
# Documents

A document can be a page, a post or a draft.

## Pages

A page is any file found in the [`source`](/docs/config.html) directory that
- Has an extension in [`template_extensions`](/docs/config.html)
- isn't hidden (leading `.` or `_`)
- isn't excluded through [`ignore`](/docs/config.html)

Pages go through several transformations:
1. Evaluate Liquid template expressions.
2. (If `.md` extension) Convert [Markdown](http://commonmark.org/help/) to HTML.
3. Wrap the content in a Liquid [layout](/docs/layouts.html).
4. Write the results to a parallel location in the [`destination`](/docs/config.html) but with a `.html` extension.

You can customize this behavior with the [frontmatter](/docs/front.html).

## Posts

Posts are special [pages](/docs/pages.html) that live in
[`posts`](/docs/directory.html).  You can use a different directory for posts with the
[`posts.dir`](/docs/config.html) in your `_cobalt.yml`.

## Drafts

Cobalt supports leaving posts in "draft" state. Drafts will not be
rendered unless Cobalt is run with the `--drafts` flag.

To mark a post as draft you can either set `is_draft: true` in your
[frontmatter](/docs/front.html) or add it to the drafts folder
([`_drafts`](/docs/directory.html) by [default](/docs/config.html)).
