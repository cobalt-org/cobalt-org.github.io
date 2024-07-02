---
title: "Docs::Site generation"
layout: docs.liquid
data:
  route: site-gen
---
## Site generation

[`cobalt serve`](/docs/usage) and `cobalt build` process your entire source directory the same
way.  Both write asset files, transformed files, and generated pages to an output
directory; `cobalt serve` writes to a temporary directory while `cobalt build`
writes to a [`destination`](/docs/config) directory (default `./_site`).  `cobalt serve` also
runs a web server to serve this static content, and then continues to watch the
source directory for changes.

### Generation process

The generation process is, approximately,
1. Cobalt considers every file in the [`source`](/docs/config)directory.
2. It skips directories and file names beginning with dot `.` or underscore
   `_`, and other files and directories. You can specify additional files and
   directories to skip using the [`ignore`](/docs/config) configuration
   variable.
3. It treats all remaining files that aren't pages and posts (see later) as
   [assets](/docs/assets) and copies them to the output directory. It may
   preprocess Sass files to turn them into CSS.
4. If a file has an extension in [`template_extensions`](/docs/config) (the
   default extensions are `.html` and `.md`), then Cobalt treats it as a
   [page](/docs/pages):
   - Cobalt looks for a [frontmatter](/docs/front) section (lines between a pair
     of `---`) in it, if any, and evaluates metadata settings in it.
   - If the site [configuration](/docs/configuration) or the page's
     frontmatter specifies a [layout](/docs/layout), Cobalt wraps the file in
     that layout's Liquid template.
   - Cobalt evaluates any [liquid template](https://shopify.github.io/liquid/)
     expressions in the file (to simplify, directives inside curly braces `{...}`).
   - Cobalt writes the transformed file to the output directory with, by
     default, a `.html` extension. A file with no frontmatter or liquid
     template expressions will be unchanged.
5. If a file with a template extension is in the [`posts`](/docs/posts)
   directory, Cobalt processes it further, such as draft handling. A page's
   frontmatter can direct Cobalt to generate a list of pages, for example a
   paginated list of blog posts.
6. Cobalt may generates additional files, such as an `rss.xml` feed.

### Generating from an existing static site

You can run `cobalt serve` or `cobalt build` in your existing static site's
directory.
- They will create a lot of files in the output directory, but will not create
  new files or modify existing files in your source directory. _Caution_,
  `cobalt build` will overwrite files in an existing destination directory
  (which defaults to `./_site`).
- The commands will complain if you don't have a `_config.yml` file or specify
  the path to one, nevertheless Cobalt will do default processing.
- Even if your existing files have extensions that Cobalt treats as pages, as
  explained in "Generation process" they will not be transformed if they don't
  contain liquid templates and a frontmatter section, and you don't specify a
  default [`layout`](/docs/config).
- Some assets that you want to appear in the output directory, such as
  `.htaccess` files and the `.well-known` directory, may not appear;
  conversely, unintended files may appear.

To start adjusting Cobalt's site generation you need to provide a
[configuration](/docs/config) file. Running [`cobalt init`](docs/usage/) will
create a `_config.yml` file and a few sample files and layout. If files
already exist with the same names, `cobalt init` will not overwrite them but
fail, so you could run it in your existing site directory, or you can run it
in an empty directory and copy over files as needed. You can specify the path
to your configuration file with the `--config` _\<FILE>_ command-line option.
