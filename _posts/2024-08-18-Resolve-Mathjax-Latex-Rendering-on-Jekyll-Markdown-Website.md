---
title: Hi again and Resolve Mathjax Latex rendering issues on Jekyll Markdown website
date: 2024-08-18
toc: false
tags:
  - web
  - markdown
  - tutorials
  - latex
header:
  teaser: /images/2024-08-18-Resolve-Mathjax-Latex-Rendering-on-Jekyll-Markdown-Website/2024-08-18-Resolve-Mathjax-Latex-Rendering-on-Jekyll-Markdown-Website-20240818234059807.jpg
---
{: .notice--primary}
*This post serves as a short catch-up and a quick fix to a Latex rendering issue I recently noticed on my web posts.* 

Hey folks! Long time no see! Hope you're all doing awesome!

After about a 2 year hiatus, I thought I would try and get back into blogging on a more consistent basis. I've been postdoc-ing at Duke since the Summer of 2022 and I'd say it's been quite an eventful journey since I  defended my Ph.D. dissertation and moved to Durham, NC from the Wild and Wonderful West Virginia. Durham has treated me quite nicely. I've met a bunch of wonderful people and there's a lot to do around here. I went on a backpacking trip in the Appalachian Mountains of Western North Carolina,  explored the beautiful beach towns of Outer Banks, and bought a new car (Crosstrek FTW!).

Anyways, the actual reason that motivated me to write this post was noticing the Latex rendering on my website was broken. After doing a bit of digging[^1] [^2], the reason seemed to be an update to [MathJax](https://www.mathjax.org) v3. The fix was quite simple. Adding the following snippet to `_includes/script.html` did the job. 

```html
<script src="https://polyfill.io/v3/polyfill.min.js?features=es6"></script>
<script id="MathJax-script" async src="https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-mml-chtml.js"></script>
<script>
 MathJax = {
  tex: {
    inlineMath: [['$', '$'], ['\\(', '\\)']],
	displayMath: [ ['$$','$$'], ["\\[","\\]"] ],
    processEscapes: true,
  }
}
</script>
```

This also ensures that in-line math enclosed within single `'$LaTex$'` renders too. 

That's it for now. Hope to see you all soon!

# References

[^1]: [https://www.cross-validated.com/How-to-render-math-on-Minimal-Mistakes/](https://www.cross-validated.com/How-to-render-math-on-Minimal-Mistakes/)
[^2]: [https://tex.stackexchange.com/questions/27633/mathjax-inline-mode-not-rendering](https://tex.stackexchange.com/questions/27633/mathjax-inline-mode-not-rendering)