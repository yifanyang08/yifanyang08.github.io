---
layout: archive
title: Posts
permalink: /posts.md 
---

Yes, there are several ways to embed a Markdown document into your personal website, depending on how you’ve built your site. Below are common approaches:

---

### ✅ 1. **Convert Markdown to HTML (Most Flexible & Compatible)**

Use a Markdown converter (like `pandoc`, `markdown-it`, or built-in support in static site generators) to convert your `.md` file into `.html`, then embed the result into your site.

#### Example using `pandoc`:

```bash
pandoc about.md -f markdown -t html -o about.html
```

Then include `about.html` using:

```html
<div id="markdown-content">
  <!-- Paste the HTML here or include with JS -->
</div>
```

Or load it via JavaScript:

```html
<div id="markdown-content"></div>
<script>
  fetch('about.html')
    .then(res => res.text())
    .then(data => {
      document.getElementById('markdown-content').innerHTML = data;
    });
</script>
```

---

### ✅ 2. **Use a Markdown Viewer Library (e.g., marked.js)**

You can load the raw `.md` file and render it using JavaScript.

#### Example:

```html
<script src="https://cdn.jsdelivr.net/npm/marked/marked.min.js"></script>
<div id="content"></div>
<script>
  fetch('README.md')
    .then(res => res.text())
    .then(md => {
      document.getElementById('content').innerHTML = marked.parse(md);
    });
</script>
```

---

### ✅ 3. **Static Site Generators (Hugo, Jekyll, Quarto, etc.)**

If your website uses a static site generator:

* Just place the `.md` file in the right folder
* It’ll be compiled to HTML automatically
* Then link to it like any other page

---

### ✅ 4. **Embed via iframe (Quick and Dirty)**

If the Markdown has been rendered to HTML (e.g., by GitHub or a public viewer), you can just embed it:

```html
<iframe src="https://yourdomain.com/docs/about.html" width="100%" height="600px"></iframe>
```

---

### Which to Choose?

| Use case                            | Best method                     |
| ----------------------------------- | ------------------------------- |
| Clean site integration              | Convert MD → HTML (method 1)    |
| Live Markdown rendering             | Use `marked.js` (method 2)      |
| Static site/blog with `.md` support | Use a site generator (method 3) |
| Quick external doc preview          | Use iframe (method 4)           |

Let me know what kind of website setup you have (e.g., HTML/CSS, Quarto, R Markdown, Hugo, etc.), and I can tailor the instructions.
