---
marp: true
description: From https://github.com/marp-team/marpit/issues/137
style: |
    section.title {
        --title-height: 130px;
        --subtitle-height: 70px;

        overflow: visible;
        display: grid;
        grid-template-columns: 1fr;
        grid-template-rows: 1fr var(--title-height) var(--subtitle-height) 1fr;
        grid-template-areas: "." "title" "subtitle" ".";
    }

    section.title h1,
    section.title h2 {
        margin: 0;
        padding: 0;
        text-align: center;
        height: var(--area-height);
        line-height: var(--area-height);
        font-size: calc(var(--area-height) * 0.7);

        border: 1px dashed gray; /* debug */
    }

    section.title h1 {
        grid-area: title;
        --area-height: var(--title-height);
    }

    section.title h2 {
        grid-area: subtitle;
        --area-height: var(--subtitle-height);
    }
    section.split {
        overflow: visible;
        display: grid;
        grid-template-columns: 500px 500px;
        grid-template-rows: 100px auto;
        grid-template-areas: 
            "slideheading slideheading"
            "leftpanel rightpanel";
    }
    /* debug */
    section.split h3, 
    section.split .ldiv, 
    section.split .rdiv { border: 1.5pt dashed dimgray; }
    section.split h3 {
        grid-area: slideheading;
        font-size: 50px;
    }
    section.split .ldiv { grid-area: leftpanel; }
    section.split .rdiv { grid-area: rightpanel; }

---

<!-- _class: title -->

# Title
## Subtitle

---
### A split slide
<!-- _class: split -->
<div class=ldiv>

#### Title for the left panel
- listed item
- listed item
- listed item
</div>
<div class=rdiv>

#### Title for the right panel
- listed item
- listed item
- listed item
</div>
