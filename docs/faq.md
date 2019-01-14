---
title: "Docs::FAQ"
layout: docs.liquid
data:
  route: faq
---
## FAQ

### How can I add MathJax to my pages?

You can include an import for the MathJax library in the `<head>` element of a [layout](/docs/layouts). The following code snippet should be plug and play for getting basic MathJax to work in your [pages](/docs/pages).

```html
<script type="text/x-mathjax-config">
  MathJax.Hub.Config({
    extensions: ["tex2jax.js"],
    jax: ["input/TeX", "output/HTML-CSS"],
    tex2jax: {
      inlineMath: [ ['$','$'], ["\\(","\\)"] ],
      displayMath: [ ['$$','$$'], ["\\[","\\]"] ],
      processEscapes: true
    },
    "HTML-CSS": { fonts: ["TeX"] }
  });
</script>
<script src='https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.3/latest.js?config=TeX-MML-AM_CHTML' async></script>
```

After including the above snippet in your [layout](/docs/layouts), on any [page](/docs/pages) implementing that layout you can surround any text with `$ $` or `$$ $$` to have MathJax render it inline or on a new line, respectively.

You can read more about how to customize or configure MathJax [here](https://docs.mathjax.org/en/latest/configuration.html#configuring-mathjax). For Cobalt gaining built-in support for MathJax, see [the Github issue](https://github.com/cobalt-org/cobalt.rs/issues/280).
