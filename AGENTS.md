# Agents

Static site hosted on Vercel at `https://spolu.sh`.

## Adding a new dated note

### 1. Create the page

Create `notes/YYYYMMDD_snake_case_title.html`. Use this structure:

```html
<!doctype html>
<html lang="en-US">
  <head>
    <title>Title Here</title>
    <link
      rel="stylesheet"
      href="https://cdnjs.cloudflare.com/ajax/libs/highlight.js/11.9.0/styles/github.min.css"
    />
    <link rel="stylesheet" type="text/css" href="../style.css" />
    <!-- Google tag (gtag.js) -->
    <script
      async
      src="https://www.googletagmanager.com/gtag/js?id=G-2VMKML2XVY"
    ></script>
    <script>
      window.dataLayer = window.dataLayer || [];
      function gtag() {
        dataLayer.push(arguments);
      }
      gtag("js", new Date());
      gtag("config", "G-2VMKML2XVY");
    </script>
  </head>
  <body>
    <a href="../index.html" class="home">&larr; HOME</a>
    <section id="wrapper">
      <p class="date">Month DD, YYYY</p>
      <h1>Title Here</h1>

      <!-- Content: <p> tags for paragraphs. -->
      <!-- Footnotes: link with [<a href="#fnN">N</a>] inline. -->
      <!-- Footnote definitions at the end in a <p class="footnotes"> block. -->

    </section>

    <script src="https://cdnjs.cloudflare.com/ajax/libs/highlight.js/11.9.0/highlight.min.js"></script>
    <script>
      document.querySelectorAll("pre code").forEach((el) => {
        el.textContent = el.textContent.trim();
      });
      hljs.highlightAll();
    </script>
  </body>
</html>
```

### 2. Add to `index.html`

Add a `<li>` at the top of the "Notes, ideas and scratchpads" `<ul>` (reverse-chronological):

```html
<li>
  <a href="notes/YYYYMMDD_snake_case_title.html">Title Here</a>
  <span class="date">— Month DD, YYYY</span>
</li>
```

### 3. Update `feed.xml`

Add a new `<item>` at the top of the `<channel>` (before existing items) and update `<lastBuildDate>`:

- `<pubDate>` format is RFC 2822: `Wed, 18 Mar 2026 00:00:00 +0000`
- `<description>` is a short plain-text summary (1-2 sentences).

The RSS `<link>` autodiscovery tag is on `index.html` only (standard practice).
