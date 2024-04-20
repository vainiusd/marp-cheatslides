---
marp: true
theme: default
description: "This slide deck contains a collection of publicly available info and examples of MARP usage. It's intention is to simplify slide creation and MARP feature use for new users by copying and modifying presented examples."
author: Vainius Dangovas
style: |
    .columns {
      display: grid;
      grid-template-columns: repeat(2, minmax(0, 1fr));
      gap: 1rem;
    }
    h2 {
      color: #808080
    }
    h3 {
      color: #606060
    }
    a:hover {
      font-weight: bold;
      color: green
    }
    section.center_h3 h3 {
      text-align: center;
    }
    section.slide_form {

    }
---
![bg left:40% 80%](./img/marp_logo.png)
# **Cheatslides**

## Markdown Presentation Ecosystem <!--fit-->

---
# Contents

<div class="columns">
<div style="font-size:1.25em">


- MARP: about & features
- VS Code integration
- Slide file structure
- Examples
- Reference links
</div>
<div>

<div style="font-size:1.25em">
Examples
</div>

- Headers & Footers
- Hyperlinks
- Styles
- Images
- Miscellaneous

</div>
</div>

Source <ins>markdown file</ins> and slides are stored [in this repo](https://github.com/vainiusd/marp-cheatslides).

---
## About

### What's Marp?
> Marp (Markdown Presentation Ecosystem) provides a great experience for writing presentations with Markdown.

from [Marp Team Github](https://github.com/marp-team/marp/blob/main/website/docs/introduction/whats-marp.md)


---
## Features

- Write in markdown, present in PDF, PPTX or HTML like this one.
  - Version control
  - Images files separate from slides
- VS Code plugin for live editing & rendering experience.
- CLI or VS Code to export desired format.
- Extend as much as You want or just by writing some HTML.

---
## VS Code integration

Just a copy of official [instructions](https://github.com/marp-team/marp/blob/main/website/docs/introduction/install.md#installing-marp-cli):
1. Install Visual Studio Code.
2. Install the Marp for VS Code extension.
3. Create and open a new Markdown file (with .md extension).
4. Select the Toggle Marp feature for current Markdown command from the Marp icon in editor actions (toolbar).
5. Open VS Code Markdown preview, and start writing your presentation! 

---
## Slide file structure

Minimal slide deck definition (empty slide deck) starts with YAML front-matter and marp enabled:
```yaml
---
marp: true
---
```

---
<!--
_footer: Source: [Marpit markdown](https://marpit.marp.app/markdown?id=marpit-markdown)
-->
## Slide file structure

### Slide separation (ruler)

Default `---` requires empty line before the ruler (according CommonMarks spec)
Other ruler options that work and not require empty lines:
- `___`
- `***`
- `- - -`

---
<!-- 
_footer: "Built-in [themes](https://github.com/marp-team/marp-core/blob/main/themes/README.md)"
-->
## Slide file structure
[Global directives](https://marpit.marp.app/directives?id=global-directives) impact the whole slide deck and are also defined in front matter:
```yaml
---
marp: true
theme: default
style: |
    /* multiline css definitions */
---
```

---
<!--
_backgroundImage: url('./img/custom_background.png')
-->
## Slide file structure
[Local directives](https://marpit.marp.app/directives?id=local-directives-1) can be used in front matter to influence all slides or in a specific slide as a HTML comment (impacts that slide and all subsequent slides).
In order to cheange only that exact slide use local directives prefixed with "_" ([spot direcitve](https://marpit.marp.app/directives?id=apply-to-a-single-page-spot-directives)).
```html
<!--
class: css_name (Specify HTML class of slide’s <section> element.)
backgroundImage: url('./img/custom_background.png')
-->
```

<!--
backgroundColor: 

-->

---

## Slide syntax

### HTML tags

- HTML tags are disabled by default for **security**.
- Allowed by default: `<style>` and `<br />`.
- To enable HTML tags via VS Code togle `markdown.marp.enableHtml` option or go to extension settings:
![](./img/vscode_enable_html.png)

---
### Headers & Footers
<!-- 
header: "Header *text* supports some **markdown** styling, images and hyperlinks"
footer: "Footer *text* also supports some **markdown** styling, images and hyperlinks"
-->

Header set for all subsequent slides or until changed:
```html
<!-- 
header: "Header *text* supports some **markdown** styling, images and hyperlinks"
-->
```
Footer too:
```html
<!-- 
footer: "Footer *text* supports some **markdown** styling, images and hyperlinks"
-->
```

---
<!-- 
_header: "A different header....."
-->

### Headers & Footers

Header set only for this slide. Next slide will have the continuing header or no header if it was not present.
```html
<!-- 
_header: "A different header....."
-->
```

Reverting to no header/footer:
```html
<!-- 
header: ""
footer: ""
-->
```

---
<!-- 
header: ""
footer: ""
paginate: true
-->

### Pagination

Just like header and footer, page numbers are available as a local/spot directive:

```html
<!-- 
paginate: true
-->
```

paginate | page number | increment | comment
-|-|-|-|
<b style="color:orange">true</b> | <span style="color:green">Show</span> | <div style="color:red">Yes</div> | Slide number incremented and shown
false | Hide | Yes | Slide number incremented, but not shown
hold | Show | No | Holds the same number for few slides
skip | Hide | No | Unnumbered slide
 

---
<!-- 
_footer: Footer link to [contents](#contents) slide
-->
### Hyperlinks

Links support reference to:
- Text: https://marp.app/
- Markdown: [link](https://marp.app/)
- Slide/heading(h1-6) by slug: slide "[Pagination](#pagination)"
- Slide by number: slide: [#10](#10)
- In footnote<sup>[1][named-link]</sup>

<!--
All links are coverted to <a> tags so You can style them with CSS like this:
a {
    key: value
}  
-->

Markdown and <a href="https://marp.app/"> HTML syntax links </a> work too*

[named-link]: #pagination

---
### Styles

- [Slide](#slide-styles)
- [Text](#text-styles)

---
<!--
_backgroundColor: black
_color: white
-->
## Slide styles
<style scoped>
a:link {
  color: hotpink;
}
a:visited {
  color: lightpink;
}
</style>

Style of this slide is changed with spot directives.
```html
<!--
_backgroundColor: black
_color: white
-->
```
<br>
<div style="text-align:center">
Other background directives:
</div>
<br/>
</div>
<div class="columns">
<div>

* backgroundImage ([w3scools link][background-image])
* backgroundPosition ([w3scools link][background-position])
</div>
<div>

* backgroundRepeat ([w3scools link][background-repeat])
* backgroundSize ([w3scools link][background-size])
</div>
</div>

<!--
List defined with hyphen comes up at once. Defined with asterics is revealed step by step.
-->


[background-image]: https://www.w3schools.com/cssref/pr_background-image.php
[background-position]: https://www.w3schools.com/cssref/pr_background-position.php
[background-repeat]: https://www.w3schools.com/cssref/pr_background-repeat.php
[background-size]: https://www.w3schools.com/cssref/css3_pr_background-size.php

---
<!--
_class: center_h3
-->
### Slide styles

#### H4

Slide layout can also be modified with the help of CSS.
CSS 



---
### Scoped CSS

<style scoped>
pre {
   font-size: 2rem;
}
</style>
Code block font size has been changed with a local style defintion that is valid only in this slide. Keyword **`scoped`** is mandatory. Otherwise all styles of all slides that have the tag are affected.
```html
<style scoped>
pre {
   font-size: 2rem;
}
</style>
```

---
<!--
_footer: "Registered languages: [Marp-core hilightjs instance](https://github.com/marp-team/marp-core/blob/main/src/highlightjs.ts)"
-->
### Text styles

- Code block syntax highlighting (uses highlight.js)
> All previous code snippets are highlited as HTML comments using **```html** at the begining of the code block

A python highlighting example:
```python
>>> l = [i for i in range(1,8)]
>>> l
[1, 2, 3, 4, 5, 6, 7]
>>> [a**2 for a in l if a%2 == 0]
[4, 16, 36]
```


---
### Images

- [Background](#background-images)
- [Inline](#inline-images)
- [HTML](#html-img-tag)

---
<!--
_footer: Official slide background **[docs](https://marpit.marp.app/image-syntax?id=slide-backgrounds)**   
-->
![bg right:40% 90%](./img/marpit_logo.png)
### Background images

Keyword `bg` in alt-text of image.
Split the slide into 60% : 40% ratio.
Resized image to 90% of the allocated area.
Syntax: `![bg right:60% 90%](path-to-img)`


---
<style scoped>
img {
    float: left;
}
div {
    text-align: center;
    border:1px solid #000000
}
h3 {
    text-align: center;
}
</style>
<!-- _footer: "Image source: [marpit.marp.app](https://marpit.marp.app/marpit.png)" -->
### Inline images

Original image in previous slide. Slide and text layout created with simple HTML and CSS. Images inserted with markdwon syntax.

<div>

![invert h:150](./img/marpit_logo.png)
Keyword `invert`
</div>
<div>

![blur h:150](./img/marpit_logo.png)
Keyword `blur`
</div>
<div>

![sepia h:150](./img/marpit_logo.png)
Keyword `sepia`
</div>

---
### HTML img tag

---
## Miscellaneous

- [Math](#math-formulas)
- [draw.io](#drawio-iframes)
- [Presenter view comments](#presenter-comments)

---
<!--
_footer: More in [MathJax basic tutorial and quick reference](https://math.meta.stackexchange.com/questions/5020/mathjax-basic-tutorial-and-quick-reference)
-->
### Math formulas

When $a \ne 0$, there are two solutions to $(ax^2 + bx + c = 0)$ and they are 
$$ x = {-b \pm \sqrt{b^2-4ac} \over 2a} $$



---
### draw.io iframes


---
### Presenter mode and comments
This slide has comments that are shown in presenter view.

Comments are put into HTML comment syntax:
```html
<!-- 
HTML comments are shown in presenter view. 
-->
```

<!-- 
HTML comments are shown in presenter view. 
-->

You can have multiple comments:
```html
<!-- Comment one -->
<!-- Comment two -->
```

<!-- Comment one -->
<!-- Comment two -->

---
## Not covered

- Inline SVG
- Using other (not built-in) themes
- Developing themes

---

## Links

- Online slide editor [web.marp.app](https://web.marp.app/).
- [GitHub Flavored Markdown Spec](https://github.github.com/gfm/) - good reference for markdown syntax for tables, images etc.
- Unified documentation issue in [marp-team github](https://github.com/orgs/marp-team/discussions/126).
- Github topic [marp-themes](https://github.com/topics/marp-themes).
- Color [names](https://developer.mozilla.org/en-US/docs/Web/CSS/named-color) and [code picker](https://www.w3schools.com/colors/colors_picker.asp).


---
### Marp guides

- [Tutorial: Marp for VS Code](https://dev.to/sc0v0ne/tutorial-marp-for-vs-code-5d6k)
- [Write your tech talk slides rapidly with Marp](https://dev.to/andyhaskell/write-your-tech-talk-slides-rapidly-with-marp-2c7g)
- [Markdown to Slides with Marp for VS Code - A Comprehensive Tutorial](https://laravel-school.com/posts/markdown-to-slides-with-marp-for-vs-code-a-comprehensive-tutorial-100/)

---
### Helping answers

- [Center content horizontally](https://stackoverflow.com/questions/47216198/get-marp-to-center-some-content-horizontally-and-vertically)
- [Styling code blocks](https://stackoverflow.com/questions/67012975/how-do-i-style-my-code-blocks-in-a-marp-presentation)
- [How to create full slide size stretched three columns in Marp/Marpit](https://stackoverflow.com/questions/69692460/how-to-create-full-slide-size-stretched-three-columns-in-marp-marpit)
- [Footer link examples](https://stackoverflow.com/questions/62510648/add-internal-links-to-a-marp-presentation)
- [Directive backgroundImage usage](https://github.com/orgs/marp-team/discussions/67)