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
# Creates page `cats-around-the-world.md` in the current dirsctory
$ cobalt new "Cats Around the World"
# Creates post `cats-around-the-world.md` in the `posts` directory
$ cobalt new "Cats Around the World" --destination posts
# Creates post `cats.md` in the `posts` directory
$ cobalt new "Cats Around the World" --destination posts/cats.md
```

### publish

Once your post is ready, you can publish it:
```bash
$ cobalt publish posts/cats-around-the-world.md
```

The page will no longer be a "draft" and the `published_date` will be set to today.

### More

To see all the available commands, run
```bash
$ cobalt --help
```

You can then get help with those commands by running
```bash
$ cobalt <command> --help
```
