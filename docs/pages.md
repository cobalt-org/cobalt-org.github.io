extends: docs.liquid
title: "Cobalt::Docs::Pages"
route: pages
---
## Pages

All files and directories in the source folder will be recursively
added to your destination folder (including assets).  You can exclude
some files by setting `igmore` in your .cobalt.yml file.

Any file with the .md or .liquid file extension is considered a liquid
template and will be parsed for metadata and compiled using liquid, like
a post.  You can specify different template extensions by setting the
`template_extensions` field in your config file:

`template_extensions: ['txt', 'lqd']`

### Defining Attributes

Front matter is the content before `---` in a page and
where meta attributes are defined using yaml.

Example:

```
extends: posts.liquid

title:   My first Blogpost
date:    01 Jan 2016 21:00:00 +0100
---
Hey there this is my first blogpost and this is super awesome.

My Blog is lorem ipsum like, yes it is..
```

#### Special Attributes

##### extends

`extends` specifies which [layout](/docs/layouts.html) will be
used.

##### excerpt_separator

`excerpt_separator` specifies up to what point of the page
will be used in an excerpt.  Setting `excerpt_separator` to `""`
will cause the entire page to be used.  This can also be set globally in
`.colbalt.yml`.  By default `\n\n` is used.

##### description

`description` will be used in your RSS post, if
available.  Otherwise `excerpt` will be used.

##### path

`path see "Custom Paths" below

### Accessing Attributes

All template files (including layouts) have access to a set of
attributes.

In example above title is accessible via `{% raw %}{{ title }}{% endraw %}` and
date via `{% raw %}{{ date }}{% endraw %}`, for the layout template as well as the
post template.

#### Special Attributes

##### content

`{% raw %}{{ content }}{% endraw %}` is accessible only to layouts and contains
the compiled text below the front matter of the page.

##### excerpt

`{% raw %}{{ excerpt }}{% endraw %}` contains the compiled text between the
front matter and the `excerpt_separator`.

##### posts

`{% raw %}{{ posts }}{% endraw %}` is a list of the attributes of all templates
in the `posts` directory in `date` order.  All
attributes defined for your post are available. Example usage on a page
listing all blog posts:

```
{% raw %}{% for post in posts %}{% endraw %}
{% raw %}  <a href="{{post.path}}">{{ post.title }}</a>{% endraw %}
{% raw %}{% endfor %}{% endraw %}
```

##### is_post

`{% raw %}{{ is_post }}{% endraw %}` can be used to alter templates based on if
the page is a post.

##### draft
`{% raw %}{{ draft }}{% endraw %}` can be used to alter templates or indexes
based on if the post is a draft.

### Custom Paths

Custom paths are much like permalinks in Jekyll, but with a bit more
flexibility. You can specify a `path` attribute in the front
matter of any document to give it a custom path. The path is always
relative to the document root, independent of where the file is
located.

Example:

```
extends: posts.liquid

title:   My first Blogpost
path: /some/other/path/
```

would result in a file with the url
`your-website.com/some/other/path/index.html`

You can also set a global attribute `post_path` in your
.cobalt.yml that will be used for all posts.

Any attribute in the front matter can be interpolated into the path.
See below for more information on attributes

If you set a `date` attribute you have access to several
other custom attributes. See the [Jekyll documentation](https://jekyllrb.com/docs/permalinks/#template-variables).

More examples:

```
date: 01 Jan 2016 21:00:00 +0100
path: /:year/:month/:day/thing.html
```
-> `/2016/01/01/thing.html`

```
date: 01 Jan 2016 21:00:00 +0100
author: johann
path: /:author/:year/:month/:day/title
```
-> `/johann/2016/01/01/title/index.html`

### Syntax Highlighting

This feature is currently experimental and causes installation to fail on
Windows. To enable syntax highlighting, you need to install Cobalt using cargo
like this:

`cargo install cobalt-bin --features="syntax-highlight"`

If you [annotate your Markdown code
blocks](https://help.github.com/articles/creating-and-highlighting-code-blocks/#syntax-highlighting)
, Cobalt will automatically highlight source code using
[Syntect](https://github.com/trishume/syntect/").
