extends: docs.liquid
title: "Cobalt::Docs::Data Files"
route: data
---

## Data Files

Cobalt supports loading [yaml](http://yaml.org), [json](http://json.org), abd
[toml](https://github.com/toml-lang/toml) from [`_data`](/docs/directory.html)
and making it available as [`site.data.<DIR>.<FILE>`](/docs/variables.html).

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
