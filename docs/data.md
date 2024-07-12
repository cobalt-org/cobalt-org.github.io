---
title: "Docs::Data Files"
layout: docs.liquid
data:
  route: data
---
## Data Files

Cobalt reads data from any [yaml](http://yaml.org), [json](http://json.org), and
[toml](https://github.com/toml-lang/toml.html) files in the [`_data` directory](/docs/directory)
and merges them into the [`site.data`](/docs/variables) variable, making
them available as `site.data.<DIR>.<FILE>`.

### Example

In `_data/animals/dogs.yml`:
```yml
- name: Corgi
- name: Malamute
```
which liquid templates can access via `site.data.animals.dogs`.

You can now render the list in a template:
```html
<ul>
{%raw%}{% for breed in site.data.animals.dogs %}{%endraw%}
  <li>{%raw%}{{ breed.name }}{%endraw%}</li>
{%raw%}{% endfor %}{%endraw%}
</ul>
```
