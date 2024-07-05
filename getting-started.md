---
---
<section class="introduction">
<div class="inner">

### Installation

Download a [release](https://github.com/cobalt-org/cobalt.rs/releases).

or

```console
$ curl -LSfs https://raw.githubusercontent.com/crate-ci/gh-install/master/v1/install.sh | sh -s -- --git cobalt-org/cobalt.rs --crate cobalt
```

### Usage

#### Start

Create a site with an example pages, posts, and layouts:
```console
$ mkdir myBlog && cd myBlog
$ cobalt init
```

#### Preview

To serve your site locally, run:
```console
$ cobalt serve
Building from `.` into `/tmp/.tmpgYpScM`
Watching . for changes
Serving /tmp/.tmpgYpScM through static file server
Server Listening on http://localhost:1024
Ctrl-c to stop the server
```

#### Add a Page

Add a new page or post to your site:
```console
$ cobalt new "Cats Around the World"
```

A file `cats-around-the-world.md` will be created in the current directory.
The type of file created is based on which directory you put it in.

Posts start out as "drafts".  For them to show up on `serve`, you'll need to
pass the `--drafts` flag:
```console
$ cobalt serve --drafts
```

#### Publish a Post

Once your post is ready, you can publish it:
```console
$ cobalt publish posts/cats-around-the-world.md
```

The page will no longer be a "draft" and the `published_date` will be set to today.

#### Build the site

Once the post is in published state, build the site:
```console
$ cobalt build
```

The site is sitting in `_site` and ready to be uploaded!
