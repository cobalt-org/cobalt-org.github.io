extends: default.liquid
path: /:filename/
---
<section class="introduction">
<div class="inner">

### Installation

Download a [release](https://github.com/cobalt-org/cobalt.rs/releases).

or

```
$ curl -LSfs https://japaric.github.io/trust/install.sh | sh -s -- --git cobalt-org/cobalt.rs --crate cobalt
```

### Usage

#### init

Create a site with an example pages, posts, and layouts:
```
$ cobalt init myBlog
$ cd myBlog
```

#### watch

Serve your site at `127.0.0.1:3000`
```
$ cobalt watch
```
This provides live reload; it will re-generate your site as you add or change content.

#### new

Add a new page or post to your site:
```
$ cobalt new "Cats Around the World"
```

A file `cats-around-the-world.md` will be created in the current directory.
The type of file created is based on which directory you put it in.

Posts start out as "drafts".  For them to show up on `watch`, you'll need to
pass the `--drafts` flag:
```
$ cobalt watch --drafts
```

#### publish

Once your post is ready, you can publish it:
```
$ cobalt publish posts/cats-around-the-world.md
```

The page will no longer be a "draft" and the `published_date` will be set to today.
