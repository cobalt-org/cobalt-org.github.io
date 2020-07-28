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
[frontmatter](/docs/front), or add it to the [drafts folder](/docs/directory).

## Pagination

### Activation

In the page that will be used as the index, turn on the pagination feature in the
frontmatter. All non mandatory fields have a default value as show below:

{% raw %}
```yml
---
pagination:
  include: All // mandatory
  per_page: 5 
  permalink_suffix: "./{{ num }}/"
  order: Desc
  sort_by: ["published_date"]
  date_index: ["Year", "Month"]
---
```
{% endraw %}

Setting                        | Format                                                             | Description
-------------------------------|--------------------------------------------------------------------|-------------
`include`                      | `All`, `Tags`, `Categories` or `Dates`                             | Defines how we index the posts.
`per_page`                     | Integer                                                            | Defines how many posts we got per index.
`permalink_suffix`             | String                                                             | Defines where the subsequent indexes after the first are stored.
`order`                        | `Desc` or `Asc`                                                    | Defines the sorting order.
`sort_by`                      | Array of Strings                                                   | Defines the sorting criteria.
`date_index`                   | Array of a combination of `Year`, `Month`, `Day`, `Hour`, `Minute` | For `include: Dates` only. Defines the date fields to index over.

### Paginator

In a page with pagination activated, we access the posts through the `paginator` object
instead of `collection`:

Variable                   | Format              | Description
---------------------------|---------------------|------------
`pages`                    | Array of Object     | The list of [pages objects](/docs/variables) that belong to this pagination index.
`total_pages`              | Integer             | Total number of pages contained in this paginator.
`index`                    | Integer             | Current index.
`index_permalink`          | String              | The relative Url path of the current pagination index.
`total_indexes`            | Integer             | Total number of pagination pages created.
`previous_index_permalink` | String              | The relative Url of the previous page. Nil if no previous page is available.
`next_index_permalink`     | String              | The relative Url of the next page in the pagination. Nil if there is no next page available.
`first_index_permalink`    | String              | The relative Url of the first page in the pagination.
`last_index_permalink`     | String              | The relative Url of the last page in the pagination.
`next_index`               | Integer             | Page number of the next index
`previous_index`           | Integer             | Page number of the previous index
`indexes`                  | Array of Paginators | If it's a meta paginator, list of paginators

#### Field `permalink_suffix`

This suffix is concatenated to the `permalink`. When the permalink has a extension, it is
removed before concatenation.

Some examples:
{% raw %}
```                              
permalink: /                     
pagination:                      
  include: All                   
  permalink_suffix: ./{{num}}/   
```
{% endraw %}
gives us:
* `/index.html`
* `/all/2/index.html`

{% raw %}
```
permalink: /tags_page.html
pagination:
  include: Tags
  permalink_suffix: ./{{num}}/
```
{% endraw %}
gives us:
* `/tags_page.html`
* `/tags_page/my_tag/index.html`
* `/tags_page/my_tag/2/index.html`

and
{% raw %}
```
permalink: /tags
pagination:
  include: Tags
  permalink_suffix: ./{{num}}/
```
{% endraw %}
gives us:
* `/tags/index.html`
* `/tags/my_tag/index.html`
* `/tags/my_tag/2/index.html`


#### Field `sort_by`

We can sort the posts in the paginator with multiples criteria at the same time. By
default we sort by `weight` then `published_date` but anything that makes sense in the
frontmatter can be used.

#### Field `indexes`

This field is present only with include values `Tags`, `Categories` and `Dates`. Only one
paginator, called "meta paginator", has it. Here we have the list of paginators, one per
value of the `include`.

An example with `include: Tags` will clear things out:

{% raw %}
```html
{% if paginator.indexes %} {% comment %} meta paginator case {% endcomment %}
  <h1>Tags</h1>
  <p>
    {% for ptag in paginator.indexes %}
      <span>
        <a href="/{{ ptag.index_permalink }}/" 
           style="font-size: {{ ptag.total_pages | times: 4 | plus: 80 }}%">
          {{ ptag.index_title }} ({{ ptag.total_pages }})
        </a>
      </span>
    {% endfor %}
  </p>
{% else %} {% comment %} normal paginator case {% endcomment %}
<h1>Tag: {{ paginator.index_title }}</h1>
<ul>
  {% for page in paginator.pages %}
    {% capture date_fr_raw %}{% include date_fr.liquid %}{% endcapture %}
    {% assign date_fr = date_fr_raw | strip %}
    <li><a href="/{{ page.permalink }}">{{ page.title }}</a> — <time 
           datetime="{{ date_fr }}" class="catalogue-time">{{ date_fr }}</time>
  {% endfor %}
</ul>
```
{% endraw %}

If `indexes` is present, we list all the tags in a tag cloud, each tag being clickable to
access to the posts that contain the tag.

If not present, we are in the paginator of a tag and list the pages contained in it.

#### Field `date_index`

This field is only valid with the `Dates` include. It defines which date field we want
to index the posts. The default value `["Year", "Month"]` means that the posts will be
classified per year and per month.

The value must be in a logical order: `["Month", "Year"]` will trigger an error.

#### Navigate the different pages of a paginator

Using fields like `previous_index_permalink` or `next_index_permalink`, we can construct
the navigation across the pages:

{% raw %}
```html
<div>
  {% if paginator.previous_index %}
  <span>
    <a
    href="/{{ paginator.previous_index_permalink }}">Previous</a>
  </span>
  {% endif %}
  {% if paginator.next_index %}
  <span>
    <a
    href="/{{ paginator.next_index_permalink }}">Next</a>
  </span>
  {% endif %}

  <div>
    {{ paginator.index }} / {{ paginator.total_indexes }}
  </div>
  <div>
    {% if paginator.previous_index %}
    <span>
      <a href="/{{ paginator.first_index_permalink }}">First</a>
    </span>
    {% endif %}
    {% if paginator.next_index %}
    <span>
      <a href="/{{ paginator.last_index_permalink }}">Last</a>
    </span>
    {% endif %}
  </div>
</div>
{% endif %}
```
{% endraw %}
