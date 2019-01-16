---
title: "Docs::Usage"
layout: docs.liquid
data:
  route: usage
---
## Usage

### init

Create a site with an example pages, posts, and layouts:
```bash
# Create site in current directory
$ cobalt init
# Create site in `myBlog` sub-directory
$ cobalt init myBlog
```

### serve

Serve your site at `127.0.0.1:3000`
```bash
$ cobalt serve
# Include drafts
$ cobalt serve --drafts
```
This provides live reload; it will re-generate your site as you add or change content.

### new

Add a new page or post to your site:
```bash
# Creates page `cats-around-the-world.md` in the current directory
$ cobalt new "Cats Around the World"
# Creates post `cats-around-the-world.md` in the `posts` directory
$ cobalt new "Cats Around the World" --file posts
# Creates post `cats.md` in the `posts` directory
$ cobalt new "Cats Around the World" --file posts/cats.md
```

You can modify the template used for `new` by editing the files in [`_defaults`](/docs/directory.html).

### publish

Once your post is ready, you can publish it:
```bash
$ cobalt publish posts/cats-around-the-world.md
```

The page will no longer be a "draft" and the `published_date` will be set to today. 

For posts, by default, the date (`YYYY-MM-DD-`) will be prepend to your posts filename in
order to keep them in a chronological order. This can be turn off in the configuration
(see `publish_date_in_filename`). This setting is disabled for pages (and can be turn on
in configuration).

### build

Once the states of your documents are in a position to be put online − by using
`publish` on the documents you want to make visible, or manually setting
`is_draft: false` − it's time to build the website:

```bash
$ cobalt build
```

All the documents not in draft state will be build into a html file ready to be serve by
your web server.

### More

To see all the available commands, run
```bash
$ cobalt --help
```

You can then get help with those commands by running
```bash
$ cobalt <command> --help
```
