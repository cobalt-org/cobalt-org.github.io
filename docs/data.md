---
title: "Docs::Data Files"
layout: docs.liquid
data:
  route: data
---
## Data Files

Cobalt supports loading [yaml](http://yaml.org), [json](http://json.org), and
[toml](https://github.com/toml-lang/toml.html) from [`_data`](/docs/directory)
and making it available as [`site.data.<DIR>.<FILE>`](/docs/variables).

### Example

In `_data/animals/dogs.yml`:
```yml
- name: Corgi
- name: Malamute
```
which can be accessed via `site.data.animals.dogs`.

You can now render the list in a template:
```html
<ul>
{%raw%}{% for breed in site.data.animals.dogs %}{%endraw%}
  <li>{%raw%}{{ breed.name }}{%endraw%}</li>
{%raw%}{% endfor %}{%endraw%}
</ul>
```
