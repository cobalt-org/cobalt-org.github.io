---
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

#### Start

Create a site with an example pages, posts, and layouts:
```
$ mkdir myBlog && cd myBlog
$ cobalt init
```

#### Preview

Serve your site at `127.0.0.1:3000`
```
$ cobalt serve
```
This provides live reload; it will re-generate your site as you add or change content.

#### Add a Page

Add a new page or post to your site:
```
$ cobalt new "Cats Around the World"
```

A file `cats-around-the-world.md` will be created in the current directory.
The type of file created is based on which directory you put it in.

Posts start out as "drafts".  For them to show up on `serve`, you'll need to
pass the `--drafts` flag:
```
$ cobalt serve --drafts
```

#### Publish a Post

Once your post is ready, you can publish it:
```
$ cobalt publish posts/cats-around-the-world.md
```

The page will no longer be a "draft" and the `published_date` will be set to today.

#### Build the site

Once the post is in published state, build the site:
```
$ cobalt build
```

The site is sitting in `_site` and ready to be uploaded!
