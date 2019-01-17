---
title: "Docs::Posts"
layout: docs.liquid
data:
  route: posts
---
## Posts

Posts are special [pages](/docs/pages) that live in
[`posts`](/docs/directory).  You can use a different directory for posts with the
[`posts.dir`](/docs/config) in your `_cobalt.yml`.

### Drafts

Cobalt supports leaving posts in "draft" state. Drafts will not be
rendered unless Cobalt is run with the `--drafts` flag.

To mark a post as draft you can either set `is_draft: true` in your
[frontmatter](/docs/front) or add it to the drafts folder
([`_drafts`](/docs/directory) by [default](/docs/config)).

## Pagination

This feature is currently experimental and need to be enabled by installing Cobalt [from
source](https://cobalt-org.github.io/docs/install) with the `pagination-unstable` feature.

Currently, we can paginate on all posts only, sorted by date or title.

### Activation

In the page that will be used as the index, turn on the pagination feature in the
frontmatter. All non mandatory fields have a default value as show below:

{% raw %}
```yml
---
pagination:
  include: All // mandatory
  per_page: 5 
  permalink: "/{{parent}}/{{include}}/_p/{{ num }}/"
  order: Desc
  sort_by: ["published_date"]
---
```
{% endraw %}

Setting                 | Format           | Description
------------------------|------------------|-------------
`include`               | `All`            | Defines how we index the posts, only `All` is available at the moment.
`per_page`              | Integer          | Defines how many posts we got per index.
`permalink`             | String           | Defines where the subsequent indexes after the first are stored.
`order`                 | `Desc` or `Asc`  | Defines the sorting order.
`sort_by`               | Array of Strings | Defines the sorting criteria.


### Paginator

In a page with pagination activated, we access the posts through the `paginator` object
instead of `collection`:

Variable                   | Format           | Description
---------------------------|------------------|------------
`pages`                    | Array of Object  | The list of [pages objects](/docs/variables) that belong to this pagination index.
`total_pages`              | Integer          | Total number of pages contained in this paginator.
`index`                    | Integer          | Current index.
`index_permalink`          | String           | The relative Url path of the current pagination index.
`total_indexes`            | Integer          | Total number of pagination pages created.
`previous_index_permalink` | String           | The relative Url of the previous page. Nil if no previous page is available.
`next_index_permalink`     | String           | The relative Url of the next page in the pagination. Nil if there is no next page available.
`first_index_permalink`    | String           | The relative Url of the first page in the pagination.
`last_index_permalink`     | String           | The relative Url of the last page in the pagination.


