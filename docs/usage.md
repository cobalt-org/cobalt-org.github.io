---
title: "Docs::Usage"
layout: docs.liquid
data:
  route: usage
---
## Usage

### init

Create a site with an example pages, posts, and layouts:
```
# Create site in current directory
$ cobalt init
# Create site in `myBlog` sub-directory
$ cobalt init myBlog
```

### serve

Serve your site at `127.0.0.1:3000`
```
$ cobalt serve
# Include drafts
$ cobalt serve --drafts
```
This provides live reload; it will re-generate your site as you add or change content.

Use the `--host` argument to listen on a different address (ex. 0.0.0.0/INADDR\_ANY);
the default is `localhost`.  Use `--port` (or `-P`) to listen on a different TCP port
number (default: 3000).

### new

Add a new page or post to your site:
```
# Creates page `cats-around-the-world.md` in the current directory
$ cobalt new "Cats Around the World"
# Creates post `cats-around-the-world.md` in the `posts` directory
$ cobalt new "Cats Around the World" --file posts
# Creates post `cats.md` in the `posts` directory
$ cobalt new "Cats Around the World" --file posts/cats.md
```

You can modify the template used for `new` by editing the files in [`_defaults`](/docs/directory).

### publish

Once your post is ready, you can publish it:
```
$ cobalt publish posts/cats-around-the-world.md
```

The page will no longer be a "draft" and the `published_date` will be set to today. 

You can also publish from the `drafts` folder:
```
$ cobalt publish drafts/dogs-around-the-world.md
```

It will move it to `posts` folder besides changing "draft" status and `published_date`.

For posts only: by default, the date (`YYYY-MM-DD-`) will be prepend to your posts
filename in order to keep them in chronological order. This can be disabled by manually
setting `publish_date_in_filename: false` in your configuration.

### build

Once the states of your documents are in a position to be put online − by using
`publish` on the documents you want to make visible, or manually setting
`is_draft: false` − it's time to build the website:

```
$ cobalt build
```

All the documents not in draft state will be build into a html file ready to be serve by
your web server.

### clean

Cleans/prunes the `destination` directory.

### debug

Displays site debug information.  There are subcommands that output various information,
ex. `config`, `files`, and `highlight`.  Refer to [Troubleshooting](/docs/trouble) for
further details.

### More

To see all the available commands, run
```
$ cobalt --help
```

You can then get help with those commands by running
```
$ cobalt <command> --help
```
