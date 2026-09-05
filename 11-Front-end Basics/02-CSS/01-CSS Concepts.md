---
Content: CSS Topics
Description: CSS (Cascading Style Sheets) is the language used to style and visually present HTML elements on a webpage.
Resources:
  - "[CSS Course — Elzero Web School](https://elzero.org/category/courses/css-course/)"
  - "[CSS Useful Features — Elzero Web School](https://elzero.org/category/courses/css-features/)"
  - "[MDN CSS Reference](https://developer.mozilla.org/en-US/docs/Web/CSS/Reference)"
  - "[CSS Tricks](https://css-tricks.com/)"
Tools:
  - "[Can I Use — Browser Support](https://caniuse.com/)"
  - "[Cubic Bezier Generator](https://cubic-bezier.com/)"
Games:
  - "[Flexbox Froggy — Interactive Game](https://flexboxfroggy.com/)"
  - "[Grid Garden — Interactive Game](https://cssgridgarden.com/)"
Foundations:
  - "[Syntax](#syntax)"
  - "[Selectors](#selectors)"
  - "[Adding CSS to HTML](#adding-css-to-html)"
  - "[The Cascade & Specificity](#the-cascade--specificity)"
  - "[Colors](#colors)"
  - "[Background](#background)"
  - "[Box Model](#box-model)"
  - "[Display](#display)"
  - "[Visibility](#visibility)"
  - "[Dimensions](#dimensions)"
  - "[Overflow](#overflow)"
  - "[Text & Typography](#text--typography)"
  - "[Inheritance](#inheritance)"
  - "[Mouse Cursor](#mouse-cursor)"
  - "[Float & Clear](#float--clear)"
  - "[CSS calc()](#css-calc)"
  - "[Opacity](#opacity)"
  - "[Position](#position)"
  - "[Z-index](#z-index)"
  - "[Lists & Tables](#lists--tables)"
  - "[Pseudo-Classes](#pseudo-classes)"
  - "[Pseudo-Elements](#pseudo-elements)"
  - "[Vendor Prefixes](#vendor-prefixes)"
  - "[Border Radius](#border-radius)"
  - "[Box Shadow](#box-shadow)"
  - "[Box Sizing](#box-sizing)"
  - "[Grouping & Nesting Selectors](#grouping-&-nesting-selectors)"
Layout:
  - "[Flexbox](#flexbox)"
  - "[Filters](#filters)"
  - "[CSS Grid](#css-grid)"
Advanced:
  - "[Gradients](#gradients)"
  - "[Pointer Events & Caret Color](#pointer-events--caret-color)"
  - "[2D Transforms](#2d-transforms)"
  - "[3D Transforms](#3d-transforms)"
  - "[Animations](#animations)"
  - "[Selectors Reference (Advanced)](#selectors-reference-advanced)"
  - "[Media Queries & Responsive Design](#media-queries-&-responsive-design)"
  - "[CSS Global Values](#css-global-values)"
---

> Cascading means styles flow from top to bottom, and more specific rules override general ones.

## Syntax

Every CSS rule follows the same structure:

```css
selector {
  property: value;
}
```

- **Selector** — targets the HTML element(s) you want to style.
- **Property** — the style attribute you want to change (e.g., `color`, `font-size`).
- **Value** — what you set the property to.

```css
/* Example */
h1 {
  color: navy;
  font-size: 32px;
}
```

---

## Selectors

Selectors tell CSS which elements to style.

```css
/* Universal — targets ALL elements */
* {
  margin: 0;
  padding: 0;
}

/* Element selector — targets all <p> tags */
p {
  color: gray;
}

/* Class selector — targets elements with class="btn" */
.btn {
  background-color: blue;
}

/* ID selector — targets the element with id="header" */
#header {
  background-color: black;
}
```

> **Best Practice:** Prefer **classes** (`.class`) over IDs (`#id`) for styling. IDs have very high specificity and are harder to override. Reserve IDs for JavaScript hooks.

---

## Adding-CSS-to-HTML

There are three ways to apply CSS. They differ in **scope** and **specificity**.

### External Stylesheet _(Recommended)_

A separate `.css` file linked in the `<head>`. Best for maintainability.

```html
<link rel="stylesheet" href="css/master.css" />
```

### Internal Style

CSS written inside a `<style>` tag in the `<head>`. Good for single-page overrides.

```html
<style>
  .special {
    color: green;
  }
</style>
```

### Inline Style

CSS written directly on an element using the `style` attribute. **Strongest specificity**, but hardest to maintain. Avoid unless necessary.

```html
<p style="color: purple;">This is a paragraph</p>
```

#### Key Takeaway: Priority Order

```
Inline > Internal > External
```

> Inline styles override both internal and external styles because they have the highest specificity.

---

## The-Cascade-&-Specificity

CSS applies rules based on **specificity** — a scoring system that decides which rule wins when multiple rules target the same element.

|Selector Type|Specificity Score|
|---|---|
|Inline style|1000|
|ID (`#id`)|100|
|Class (`.class`), Pseudo-class|10|
|Element (`p`, `h1`)|1|

```css
/* Specificity = 1 */
p { color: black; }

/* Specificity = 10 — wins over element selector */
.highlight { color: yellow; }

/* Specificity = 100 — wins over class */
#title { color: red; }
```

> **Common Mistake:** Adding `!important` to "fix" specificity issues. This makes CSS hard to debug. Instead, understand the cascade and write more specific selectors.

---

## Colors

CSS supports multiple color formats — all are equally valid, choose based on context.

```css
/* Color name */
color: red;

/* Hex code — #RRGGBB */
color: #FF5733;

/* Short hex (when pairs repeat) */
color: #F53;    /* same as #FF5533 */

/* RGB */
color: rgb(255, 87, 51);

/* RGB with Alpha (transparency, 0 = invisible, 1 = opaque) */
color: rgb(255 87 51 / 50%);

/* HSL — Hue, Saturation, Lightness */
color: hsl(14, 100%, 60%);
```

> **Tip:** Use **CSS variables** for your color palette so you can change theme colors in one place:

```css
:root {
  --primary: #FF5733;
  --text: #222;
}
p { color: var(--text); }
```

---

## Background

### background-color

```css
background-color: red;
background-color: #FF0000;
background-color: rgb(255 0 0 / 50%);
```

### background-image

```css
background-image: url("../imgs/hero.png");
```

### background-repeat

```css
background-repeat: no-repeat;   /* Show once, no tiling */
background-repeat: repeat-x;    /* Tile horizontally only */
background-repeat: repeat-y;    /* Tile vertically only */
background-repeat: repeat;      /* Tile in both directions (default) */
```

### background-attachment

```css
/* Image scrolls with the page (default) */
background-attachment: scroll;

/* Image is fixed — creates a parallax effect */
background-attachment: fixed;
```

### background-position

```css
background-position: center center;  /* Centered */
background-position: left top;        /* Top-left corner */
background-position: 50% 20%;         /* Custom offset */
```

### background-size

```css
background-size: auto;      /* Original image size */
background-size: cover;     /* Fill container, may crop */
background-size: contain;   /* Fit entirely inside, may leave gaps */
background-size: 300px 200px; /* Explicit dimensions */
```

### Shorthand

```css
/* background: color image repeat attachment position / size */
background: #222 url("hero.png") no-repeat center center / cover;
```

---

## Box-Model

Every HTML element is a rectangular box made up of four layers:

```
┌──────────────────────────┐
│         MARGIN           │  ← Space outside the element
│  ┌────────────────────┐  │
│  │      BORDER        │  │  ← The visible border
│  │  ┌──────────────┐  │  │
│  │  │   PADDING    │  │  │  ← Space inside, between content & border
│  │  │  ┌────────┐  │  │  │
│  │  │  │CONTENT │  │  │  │  ← Actual text/image
│  │  │  └────────┘  │  │  │
│  │  └──────────────┘  │  │
│  └────────────────────┘  │
└──────────────────────────┘
```

### Padding

Space **inside** the element, between the content and the border.

```css
/* All four sides */
padding: 10px;

/* Top & Bottom | Left & Right */
padding: 10px 20px;

/* Top | Left & Right | Bottom */
padding: 10px 20px 15px;

/* Top | Right | Bottom | Left (clockwise) */
padding: 10px 20px 15px 25px;

/* Individual sides */
padding-top: 10px;
padding-right: 20px;
padding-bottom: 15px;
padding-left: 25px;
```

### Margin

Space **outside** the element, creating separation between elements.

```css
margin: 20px;
margin: 10px 20px;
margin: auto;       /* Centers block elements horizontally */

/* Negative margins are valid — pull elements closer */
margin-top: -10px;
```

> **Tip:** `margin: 0 auto` is the classic way to center a block element horizontally (requires a defined `width`).

### Border

```css
/* Longhand */
border-width: 2px;
border-style: solid;   /* solid | dashed | dotted | double | none */
border-color: #333;

/* Shorthand */
border: 2px solid #333;

/* Individual sides */
border-top: 3px dashed red;
border-bottom: 1px solid #ccc;
```

### Outline

Similar to border but **does not affect layout** (no space is reserved for it).

```css
outline: 2px solid blue;
outline-offset: 4px;   /* Space between element and outline */
```

> **Common Use:** Outlines are often used for **focus indicators** on interactive elements (important for accessibility). Don't remove `outline: none` without providing an alternative.

---

## Display

The `display` property controls how an element participates in the layout.

```css
display: block;
display: inline;
display: inline-block;
display: none;
display: flex;
display: grid;
```

### Block

```css
div { display: block; }
```

- Takes **full available width** by default.
- Starts on a **new line** (adds line break before and after).
- Respects `width`, `height`, `margin`, and `padding` on all sides.
- Common block elements: `div`, `p`, `h1–h6`, `section`, `article`

### Inline

```css
span { display: inline; }
```

- Takes only as much **width as its content** needs.
- Does **not** start on a new line.
- **Ignores** `width` and `height`.
- **Only respects** horizontal `padding` and `margin` (left & right).
- Common inline elements: `span`, `a`, `strong`, `em`

### Inline-Block

```css
span { display: inline-block; }
```

- Sits **inline** (no forced line break).
- **Respects** `width`, `height`, `padding`, and `margin` on all sides.
- Best of both worlds — use when you need inline elements with box dimensions.

#### Comparison Table

|Property|`block`|`inline`|`inline-block`|
|---|---|---|---|
|New line|✅|❌|❌|
|Full width|✅|❌|❌|
|Respects width/height|✅|❌|✅|
|Respects all margins|✅|❌ (only L/R)|✅|

---

## Visibility

Two ways to hide an element — they behave differently:

```css
/* Removes the element entirely from layout — no space reserved */
display: none;

/* Element is invisible but still occupies space in layout */
visibility: hidden;
```

> **Use Case:** Use `visibility: hidden` when you don't want the page layout to shift when toggling visibility (e.g., keeping a placeholder).

---

## Dimensions

```css
width: 300px;
height: 200px;

/* Responsive constraints */
min-width: 200px;   /* Never shrink below this */
max-width: 800px;   /* Never grow beyond this */
min-height: 100px;
max-height: 500px;

/* Fit the element to its content width */
width: fit-content;

/* Fill available space */
width: 100%;
```

> **Best Practice:** Use `max-width` instead of a fixed `width` for responsive layouts. Combine with `width: 100%` and `margin: auto`:

```css
.container {
  width: 100%;
  max-width: 1200px;
  margin: 0 auto;
}
```

---

## Overflow

Controls what happens when content is **larger than its container**.

```css
overflow: visible;   /* Default — content spills outside (no clipping) */
overflow: hidden;    /* Clips excess content — invisible */
overflow: scroll;    /* Always shows scrollbars */
overflow: auto;      /* Shows scrollbars only when needed (recommended) */

/* Control each axis separately */
overflow-x: hidden;
overflow-y: scroll;
```

> **Common Use:** `overflow: hidden` on a parent is the "clearfix hack" for float-based layouts — it forces the parent to contain floated children.

---

## Text-&-Typography

### Color & Text Shadow

```css
color: #333;

/* text-shadow: x-offset y-offset blur color */
text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.3);

/* Multiple shadows */
text-shadow: 1px 1px 0 #000, 2px 2px 0 #555;
```

### Text Alignment

```css
text-align: left;      /* Default for LTR languages */
text-align: right;
text-align: center;
text-align: justify;   /* Stretches text to fill the line width */

/* Page direction — affects layout flow */
direction: ltr;   /* Left to Right (default) */
direction: rtl;   /* Right to Left (Arabic, Hebrew, etc.) */
```

### Vertical Alignment

Aligns **inline** or **inline-block** elements relative to surrounding text:

```css
img {
  vertical-align: middle;  /* top | middle | bottom | baseline */
}
```

### Text Decoration

```css
text-decoration: none;           /* Removes underline (e.g., from links) */
text-decoration: underline;
text-decoration: line-through;   /* Strikethrough */
text-decoration: overline;

/* Shorthand with style and color */
text-decoration: underline dashed red;
```

### Text Transform

```css
text-transform: uppercase;    /* ALL CAPS */
text-transform: lowercase;    /* all lowercase */
text-transform: capitalize;   /* First Letter Of Each Word */
text-transform: none;
```

### Spacing

```css
letter-spacing: 2px;    /* Space between individual characters */
word-spacing: 5px;      /* Space between words */
line-height: 1.6;       /* Space between lines — unitless is recommended */
text-indent: 2em;       /* Indents the first line */
white-space: nowrap;    /* Prevents text from wrapping */
word-break: break-all;  /* Breaks long words to fit container */
```

> **Best Practice:** Use a unitless `line-height` (e.g., `1.5`) so it scales proportionally with the font size.

### Text Overflow

Used when text overflows a container in a single line — creates the "..." effect.

```css
/* Requires these three properties together */
white-space: nowrap;
overflow: hidden;
text-overflow: ellipsis;
```

### Font Family

```css
/* Serif fonts — have decorative strokes at ends of letters */
font-family: 'Times New Roman', Times, serif;

/* Sans-serif fonts — clean, no strokes */
font-family: Arial, Helvetica, sans-serif;

/* Google Fonts (import in <head> first) */
font-family: 'Roboto', sans-serif;
```

> **Tip:** Always end your font stack with a generic family (`serif`, `sans-serif`, `monospace`) as a fallback.

### Font Size & CSS Units

```css
font-size: 16px;    /* Pixels — absolute, predictable */
font-size: 1em;     /* Relative to parent's font size (1em = parent size) */
font-size: 1rem;    /* Relative to root (<html>) font size — more predictable */
font-size: 100%;    /* Percentage of parent's font size */
font-size: 5vw;     /* 5% of the viewport width — responsive */
```

#### CSS Units Summary

|Unit|Relative To|Use Case|
|---|---|---|
|`px`|Screen pixels|Fixed sizes, borders|
|`em`|Parent's font size|Component-level scaling|
|`rem`|Root (`<html>`) font size|Global consistent sizing|
|`%`|Parent element|Fluid layouts|
|`vw`|Viewport width|Full-width responsive elements|
|`vh`|Viewport height|Full-screen sections|

### Font Style, Weight & Variant

```css
font-style: normal;
font-style: italic;

font-weight: normal;   /* 400 */
font-weight: bold;     /* 700 */
font-weight: 300;      /* Light */
font-weight: 900;      /* Extra Bold */

font-variant: small-caps;   /* Displays lowercase as small uppercase letters */
```

---

## Inheritance

Some CSS properties **inherit** their value from the parent element automatically (e.g., `color`, `font-family`, `font-size`). Others do not (e.g., `border`, `margin`, `padding`).

```css
/* Force any property to inherit from parent */
color: inherit;
border: inherit;
```

```html
<!-- Example: child inherits color from parent -->
<div style="color: red;">
  <p>This text will be red (inherited).</p>
</div>
```

---

## Mouse-Cursor

```css
cursor: pointer;     /* Hand — use for clickable elements */
cursor: default;     /* Default arrow */
cursor: text;        /* Text input beam */
cursor: not-allowed; /* Indicates disabled state */
cursor: grab;        /* For draggable elements */
```

---

## Float-&-Clear

`float` was historically used for layouts but is now mainly used for **text wrapping around images**. For layouts, use **Flexbox** or **Grid**.

```css
img {
  float: left;    /* Text wraps to the right of the image */
  margin-right: 15px;
}
```

### Clearing Floats

Floated elements are removed from normal flow, which can collapse their parent container. Use `clear` to fix this:

```css
.clearfix {
  clear: both;    /* Stops wrapping — both | left | right */
}
```

```html
<div class="parent">
  <div style="float: left;">Item 1</div>
  <div style="float: left;">Item 2</div>
  <div class="clearfix"></div>  <!-- Resets flow -->
</div>
```

> **Modern Alternative:** Instead of the clearfix hack, set `overflow: hidden` or `display: flow-root` on the parent:

```css
.parent {
  overflow: hidden; /* Contains floated children */
}
```

---

## CSS-calc()

Allows you to perform **math operations** in CSS, mixing different units.

```css
width: calc(100% - 60px);
padding: calc(1rem + 5px);
```

**Real-world use case — Equal-width columns with gaps:**

```css
/* 5 columns with 10px gaps between them */
.column {
  float: left;
  width: calc((100% - 60px) / 5);
  margin-left: 10px;
}
```

> **Operators:** `+`, `-`, `*`, `/` — always add spaces around `+` and `-` operators!

---

## Opacity

Controls transparency of an **entire element** (including children).

```css
/* 0 = fully transparent, 1 = fully opaque */
opacity: 0.5;   /* 50% transparent — affects the whole element */
```

**vs. RGB alpha channel** — only affects the background color, not child content:

```css
/* Only the background is 50% transparent — text remains fully visible */
background-color: rgb(255 0 0 / 0.5);
```

> **Key Difference:** `opacity` makes everything (text, children, borders) transparent. `rgba`/`rgb(.../ alpha)` only affects that specific color.

---

## Position

Controls how an element is placed in the page layout.

```css
position: static;    /* Default — normal document flow */
position: relative;  /* Offset from its normal position */
position: absolute;  /* Positioned relative to nearest non-static ancestor */
position: fixed;     /* Fixed to viewport — stays visible while scrolling */
position: sticky;    /* Sticks at a threshold when scrolling */
```

### static (Default)

Element flows normally. `top`, `left`, `right`, `bottom` have no effect.

### relative

Element stays in the flow but can be nudged with offset properties.

```css
.box {
  position: relative;
  top: 10px;   /* Move 10px down from original position */
  left: 20px;  /* Move 20px right from original position */
}
```

> Also used to make a container the **reference point** for absolutely positioned children.

### absolute

Removed from normal flow. Positioned relative to the **nearest ancestor with a non-static position**.

```css
.parent {
  position: relative;  /* Acts as the reference frame */
}
.child {
  position: absolute;
  top: 0;
  right: 0;   /* Placed at top-right corner of .parent */
}
```

### fixed

Removed from flow. Positioned relative to the **viewport** — doesn't move on scroll.

```css
.navbar {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
}
```

### sticky

Behaves like `relative` until you scroll to a threshold, then behaves like `fixed`.

```css
.section-header {
  position: sticky;
  top: 0;   /* Sticks when it reaches the top of the viewport */
}
```

---

## Z-index

Controls the **stacking order** of positioned elements (which appears on top).

- Higher value = on top.
- Only works on elements with a non-static `position`.

```css
.one {
  position: absolute;
  background-color: red;
  z-index: 3;   /* On top */
}
.two {
  position: absolute;
  background-color: green;
  z-index: 2;
}
.three {
  position: absolute;
  background-color: blue;
  z-index: 1;   /* Behind */
}
```

> **Tip:** Avoid arbitrary large z-index values like `z-index: 9999`. Use a scale (1, 2, 3...) or CSS variables to manage layers.

---

## Lists-&-Tables

### List Styling

```css
/* Remove default bullets */
ul {
  list-style: none;
  padding: 0;
}

/* Shorthand: type | position | image */
list-style: square inside url("bullet.png");

list-style-type: disc;     /* • */
list-style-type: circle;   /* ○ */
list-style-type: square;   /* ■ */
list-style-type: decimal;  /* 1, 2, 3 */
```

### Table Styling

```css
table {
  width: 100%;
  border-collapse: collapse;   /* Merges double borders into one */
  border-spacing: 0;
}
td, th {
  padding: 12px 15px;
  border: 1px solid #ccc;
  text-align: left;
}
thead tr {
  background-color: #f44336;
  color: white;
  font-weight: bold;
  text-align: center;
}
tbody tr:nth-child(even) {
  background-color: #f5f5f5;  /* Zebra striping for readability */
}
tbody tr:hover {
  background-color: #e0e0e0;  /* Row hover highlight */
}
```

---

## Pseudo-Classes

Target elements based on their **state** or **position** — no class needed in HTML.

```css
/* Link states */
a:link    { color: blue; }       /* Unvisited link */
a:visited { color: purple; }     /* Visited link */
a:hover   { color: red; }        /* Mouse is over the element */
a:active  { color: orange; }     /* Being clicked */

/* Form states */
input:focus    { border-color: blue; outline: none; }
input:checked  { display: none; }
input:disabled { opacity: 0.5; }

/* Structural pseudo-classes */
li:first-child  { font-weight: bold; }
li:last-child   { border-bottom: none; }
li:nth-child(2) { color: red; }
li:nth-child(odd)  { background: #f0f0f0; }
li:nth-child(even) { background: #fff; }

/* Empty elements */
:empty { border: 2px dashed red; }
```

---

## Pseudo-Elements

Target a **specific part** of an element or insert virtual content.

```css
/* Style the first letter */
p::first-letter {
  font-size: 3em;
  font-weight: bold;
  float: left;
  margin-right: 4px;
}

/* Style the first line */
p::first-line {
  font-weight: bold;
  color: navy;
}

/* Style selected text */
::selection {
  background-color: black;
  color: yellow;
}
```

### `::before` and `::after`

Insert virtual elements **before** or **after** an element's content. Requires `content` property.

```css
/* Add decorative quotes */
blockquote::before { content: "\201C"; }   /* " */
blockquote::after  { content: "\201D"; }   /* " */

/* Common pattern: decorative triangle using borders */
.tooltip::before {
  content: "";
  position: absolute;
  top: 50%;
  left: -10px;
  margin-top: -5px;
  border: 5px solid transparent;
  border-right-color: #333;
}
```

### `content` Values

```css
/* String */
content: "Read more →";

/* Attribute value */
content: attr(data-label);   /* Reads from data-label="..." on the element */

/* Counter */
.parent { counter-increment: section; }
.parent::after { content: counter(section); }

/* Empty (for decorative boxes) */
content: "";
```

---

## Vendor-Prefixes

Some newer CSS features required **browser-specific prefixes** during experimental phases before becoming standard.

|Prefix|Targets|
|---|---|
|`-webkit-`|Chrome, Safari, modern Opera|
|`-moz-`|Firefox|
|`-ms-`|Internet Explorer, Edge (old)|
|`-o-`|Old Opera|

```css
.box {
  -webkit-border-radius: 10px;
  -moz-border-radius: 10px;
  border-radius: 10px;   /* Standard — always put LAST */
}
```

> **Modern Reality:** Most modern CSS features no longer need prefixes. Tools like **Autoprefixer** or VS Code extensions can add them automatically. Always include the unprefixed version last.

---

## Border-Radius

Rounds the corners of an element's border.

```css
border-radius: 6px;         /* All corners */
border-radius: 10px 0;      /* Top-left & bottom-right | top-right & bottom-left */
border-radius: 50%;          /* Creates a circle (on a square element) */

/* Individual corners */
border-top-left-radius: 10px;
border-top-right-radius: 5px;
border-bottom-right-radius: 10px;
border-bottom-left-radius: 5px;

/* Elliptical corners (horizontal-radius / vertical-radius) */
border-radius: 50px / 20px;
```

---

## Box-Shadow

Adds shadow effects to elements. Multiple shadows can be layered.

```css
/* Syntax: h-offset v-offset blur spread color inset */
box-shadow: 2px 4px 8px 0 rgba(0, 0, 0, 0.2);

/* Inner shadow */
box-shadow: inset 0 2px 4px rgba(0,0,0,0.3);

/* Multiple shadows (layered) */
box-shadow:
  0 1px 3px rgba(0,0,0,0.12),
  0 1px 2px rgba(0,0,0,0.24);
```

|Value|Description|
|---|---|
|`h-offset`|Horizontal shadow position (positive = right)|
|`v-offset`|Vertical shadow position (positive = down)|
|`blur`|Blur radius — larger = softer shadow|
|`spread`|Expands or shrinks the shadow|
|`color`|Shadow color|
|`inset`|Makes shadow appear inside the element|

---

## Box-Sizing

Controls **how `width` and `height` are calculated**.

```css
/* Default — width/height = CONTENT ONLY. Padding & border add to total size. */
box-sizing: content-box;

/* width/height = includes padding and border. Much more intuitive. */
box-sizing: border-box;
```

**Example:**

```css
/* content-box (default): total width = 200px + 20px + 4px = 224px */
.box {
  box-sizing: content-box;
  width: 200px;
  padding: 10px;
  border: 2px solid black;
}

/* border-box: total width = exactly 200px */
.box {
  box-sizing: border-box;
  width: 200px;
  padding: 10px;
  border: 2px solid black;
}
```

> **Best Practice:** Apply `border-box` globally at the top of your stylesheet:

```css
*, *::before, *::after {
  box-sizing: border-box;
}
```

---

## Grouping-&-Nesting-Selectors

### Grouping

Apply the same styles to multiple selectors by separating them with commas:

```css
h1, h2, h3, h4 {
  font-family: Georgia, serif;
  color: #222;
}

.card, .panel, .modal {
  border-radius: 8px;
  padding: 20px;
  box-shadow: 0 2px 8px rgba(0,0,0,0.1);
}
```

### Nesting (Descendant Selector)

Target elements **inside** other elements without needing extra classes:

```css
/* Only targets <p> elements that are INSIDE a <div> */
div p {
  color: gray;
}

/* Only targets .special inside a div (not .special elsewhere) */
div .special {
  color: red;
}

/* Direct child only (not grandchildren) */
div > p {
  font-weight: bold;
}

/* Adjacent sibling — p immediately after h2 */
h2 + p {
  font-size: 1.2em;
}
```

---

# PART 2 — LAYOUT & ADVANCED

---

## Flexbox

> Flexbox is a one-dimensional layout system. You set a container to `display: flex` and it arranges its **direct children** in a row (or column). It's perfect for navigation bars, centering content, and flexible UI components.

### Mental Model

```
Parent (flex container) controls the overall layout direction and alignment.
Children (flex items) control their own growth, shrink, order, and self-alignment.
```

---

### Parent Properties (Flex Container)

#### `display: flex`

Turns the element into a flex container. All direct children become flex items.

```css
.container {
  display: flex;         /* block-level flex container */
  display: inline-flex;  /* inline-level flex container */
}
```

#### `flex-direction` — Main Axis Direction

```css
flex-direction: row;            /* → Default: left to right */
flex-direction: row-reverse;    /* ← Right to left */
flex-direction: column;         /* ↓ Top to bottom */
flex-direction: column-reverse; /* ↑ Bottom to top */
```

#### `flex-wrap` — Wrapping Behavior

```css
flex-wrap: nowrap;       /* Default: all items on one line (may overflow) */
flex-wrap: wrap;         /* Items wrap to next line when needed */
flex-wrap: wrap-reverse; /* Items wrap to previous line */
```

#### `flex-flow` — Shorthand for direction + wrap

```css
/* flex-flow: [flex-direction] [flex-wrap] */
flex-flow: row wrap;
flex-flow: column nowrap;
```

#### `justify-content` — Alignment along the Main Axis

```css
justify-content: flex-start;    /* Default: items at start */
justify-content: flex-end;      /* Items at end */
justify-content: center;        /* Items centered */
justify-content: space-between; /* Equal space BETWEEN items */
justify-content: space-around;  /* Equal space AROUND items */
justify-content: space-evenly;  /* Equal space between and at edges */
```

#### `align-items` — Alignment along the Cross Axis (single line)

```css
align-items: stretch;     /* Default: items stretch to fill container height */
align-items: flex-start;  /* Items at the top of the cross axis */
align-items: flex-end;    /* Items at the bottom */
align-items: center;      /* Items centered vertically */
align-items: baseline;    /* Items aligned by text baseline */
```

#### `align-content` — Alignment of Multiple Lines (when `flex-wrap` is active)

```css
/* Only works when there are multiple rows/columns of flex items */
align-content: stretch;       /* Default */
align-content: flex-start;
align-content: flex-end;
align-content: center;
align-content: space-between;
align-content: space-around;
```

> **Tip:** Perfectly center content both horizontally and vertically:
> 
> ```css
> .center {
>   display: flex;
>   justify-content: center;
>   align-items: center;
> }
> ```

---

### Child Properties (Flex Items)

#### `flex-grow` — How much an item grows to fill space

```css
flex-grow: 0;   /* Default: item does not grow */
flex-grow: 1;   /* Item takes up remaining space */
flex-grow: 2;   /* Item takes TWICE as much remaining space as flex-grow: 1 */
```

#### `flex-shrink` — How much an item shrinks when space is tight

```css
flex-shrink: 1;   /* Default: item shrinks proportionally */
flex-shrink: 0;   /* Item does NOT shrink (useful for fixed-width items) */
```

#### `flex-basis` — Initial size before growing/shrinking

```css
flex-basis: auto;    /* Default: based on width/height */
flex-basis: 200px;   /* Item starts at 200px then grows/shrinks */
flex-basis: 0;       /* Item starts at 0 and grows from there */
```

#### `flex` — Shorthand for grow, shrink, basis

```css
/* flex: [flex-grow] [flex-shrink] [flex-basis] */
flex: 0 1 auto;   /* Default */
flex: 1;          /* Shorthand for flex: 1 1 0 — commonly used */
flex: 1 0 200px;  /* Grow, don't shrink, start at 200px */
```

#### `order` — Visual Order of Items

```css
order: 0;   /* Default — all items are 0 */
order: -1;  /* Move to the front */
order: 1;   /* Move to the end */
```

#### `align-self` — Override `align-items` for a single item

```css
align-self: auto;        /* Default: follows align-items */
align-self: flex-start;
align-self: flex-end;
align-self: center;
align-self: stretch;
```

---

### Complete Reference Table

|Property|Applies To|Default|Description|
|---|---|---|---|
|`display`|Parent|—|`flex` or `inline-flex`|
|`flex-direction`|Parent|`row`|Main axis direction|
|`flex-wrap`|Parent|`nowrap`|Wrap behavior|
|`flex-flow`|Parent|`row nowrap`|Shorthand|
|`justify-content`|Parent|`flex-start`|Main axis alignment|
|`align-items`|Parent|`stretch`|Cross axis (single line)|
|`align-content`|Parent|`stretch`|Cross axis (multiple lines)|
|`flex-grow`|Child|`0`|Grow factor|
|`flex-shrink`|Child|`1`|Shrink factor|
|`flex-basis`|Child|`auto`|Initial size|
|`flex`|Child|`0 1 auto`|Shorthand|
|`order`|Child|`0`|Visual order|
|`align-self`|Child|`auto`|Override align-items|

---

## Filters

CSS filters apply visual effects to elements (images, backgrounds, etc.) — similar to image editing software.

```css
/* Syntax */
filter: function(value);

/* Grayscale — converts image to black and white */
filter: grayscale(100%);   /* Fully grayscale */
filter: grayscale(0);      /* Original color */

/* Common filter functions */
filter: blur(4px);            /* Gaussian blur */
filter: brightness(0.5);      /* Darken — 0 is black, 1 is normal, >1 brightens */
filter: contrast(200%);       /* Increase contrast */
filter: saturate(300%);       /* Boost color saturation */
filter: hue-rotate(90deg);    /* Shift hue around the color wheel */
filter: invert(100%);         /* Invert colors */
filter: opacity(50%);         /* Transparency */
filter: sepia(100%);          /* Warm vintage effect */
filter: drop-shadow(2px 4px 6px black); /* Like box-shadow but follows shape */

/* Combine multiple filters */
filter: grayscale(50%) blur(2px) brightness(0.8);
```

**Practical Example — Hover to reveal color:**

```css
img {
  transition: filter 0.3s ease;
  filter: grayscale(100%);
}
img:hover {
  filter: grayscale(0);
}
```

---

## Gradients

Gradients are smooth transitions between colors, used as `background-image` values.

### Linear Gradient

```css
/* Syntax: linear-gradient(direction/angle, color-stop-1, color-stop-2, ...) */

/* Direction keywords */
background-image: linear-gradient(to right, #2980b9, #27ae60);
background-image: linear-gradient(to bottom, red, blue);
background-image: linear-gradient(to top right, red, blue);

/* Angle — 0deg = bottom to top, 90deg = left to right */
background-image: linear-gradient(90deg, red, blue);
background-image: linear-gradient(45deg, red, yellow, blue);

/* Color stops — control where each color starts */
background-image: linear-gradient(
  to right,
  #2980b9 0%,    /* Blue starts at 0% */
  #2980b9 20%,   /* Blue ends at 20% */
  #27ae60 20%,   /* Green starts immediately at 20% (hard stop) */
  #27ae60 40%,   /* Green ends at 40% */
  #d35400 40%,
  #d35400 60%,
  #8e44ad 60%,
  #8e44ad 80%,
  #c0392b 80%
);
```

### Radial Gradient

```css
/* Radiates outward from a center point */
background-image: radial-gradient(circle, red, blue);
background-image: radial-gradient(ellipse, red 20%, blue 80%);
background-image: radial-gradient(circle at top left, #ff6b6b, #4ecdc4);
```

### Conic Gradient

```css
/* Rotates around a center point — great for pie charts */
background-image: conic-gradient(red 0deg, yellow 90deg, green 180deg, blue 270deg);
```

> **Tip:** Hard color stops (same position for two colors) create sharp lines — useful for striped patterns and rainbow dividers.

---

## Pointer-Events-&-Caret-Color

### `pointer-events`

Controls whether an element can be the target of mouse/touch events.

```css
/* Disable all mouse interaction — clicks pass through the element */
pointer-events: none;

/* Default — element responds to mouse events normally */
pointer-events: auto;
```

**Use cases:**

- Disable a link without removing it from HTML: `a { pointer-events: none; }`
- Create click-through overlays
- Disable buttons during loading states

### `caret-color`

Controls the color of the text cursor (caret) inside text inputs.

```css
input {
  caret-color: red;       /* Red cursor */
  caret-color: #2980b9;   /* Custom color */
  caret-color: transparent; /* Invisible cursor */
}
```

---

## CSS-Grid

> Grid is a two-dimensional layout system. Unlike Flexbox (one direction), Grid handles both rows AND columns simultaneously. Perfect for full-page layouts, card grids, and complex UI structures.

### Mental Model

```
Grid Parent defines the column/row structure.
Grid Children are placed automatically into cells, or manually positioned.
```

---

### Parent Properties (Grid Container)

#### `display: grid`

```css
.container {
  display: grid;        /* block-level grid */
  display: inline-grid; /* inline-level grid */
}
```

#### `grid-template-columns` — Define Columns

```css
/* Fixed widths */
grid-template-columns: 200px 200px 200px;  /* 3 equal fixed columns */

/* Fractions (fr) — divide available space */
grid-template-columns: 1fr 1fr 1fr;         /* 3 equal columns */
grid-template-columns: 2fr 1fr;             /* 2:1 ratio */

/* Auto — size to content */
grid-template-columns: auto auto auto;

/* repeat() — shorthand for repeated values */
grid-template-columns: repeat(3, 1fr);      /* Same as 1fr 1fr 1fr */
grid-template-columns: repeat(4, 200px);

/* Mix units */
grid-template-columns: 200px 1fr 1fr;       /* Fixed sidebar + 2 fluid columns */
grid-template-columns: repeat(2, auto) repeat(2, 1fr);
```

#### `grid-template-rows` — Define Rows

```css
grid-template-rows: 50px auto 50px;         /* Header, content, footer */
grid-template-rows: repeat(3, 1fr);
```

#### `gap` — Space Between Grid Cells

```css
gap: 10px;           /* Same gap for rows and columns */
gap: 20px 10px;      /* Row gap | Column gap */
row-gap: 20px;
column-gap: 10px;
```

#### `justify-content` — Align the entire grid horizontally

```css
justify-content: start;          /* Default */
justify-content: end;
justify-content: center;
justify-content: space-between;
justify-content: space-around;
justify-content: space-evenly;
```

#### `align-content` — Align the entire grid vertically

```css
align-content: start;
align-content: center;
align-content: space-between;
align-content: space-around;
```

#### `grid-template-areas` — Visual Layout with Named Areas

```css
.page {
  display: grid;
  grid-template-columns: repeat(10, 1fr);
  grid-template-rows: 50px auto 50px;
  grid-template-areas:
    "logo logo nav  nav  nav  nav  nav  nav  nav  nav"
    "cont cont cont cont cont cont cont .    side side"
    "foot foot foot foot foot foot foot foot foot foot";
}

/* Assign elements to named areas */
h2      { grid-area: logo; }
nav     { grid-area: nav; }
section { grid-area: cont; }
aside   { grid-area: side; }
footer  { grid-area: foot; }
```

> **Tip:** A dot (`.`) in `grid-template-areas` represents an empty cell.

---

### Child Properties (Grid Items)

#### `grid-column` — Span Across Columns

```css
/* grid-column: start / end (line numbers) */
grid-column: 1 / 3;     /* Span from line 1 to line 3 (2 columns wide) */
grid-column: 1 / -1;    /* Span ALL columns (from start to end) */
grid-column: span 2;    /* Span 2 columns from current position */
```

#### `grid-row` — Span Across Rows

```css
grid-row: 1 / 3;        /* Span from row line 1 to 3 */
grid-row: 1 / 5;        /* Span 4 rows */
grid-row: span 2;       /* Span 2 rows */
```

#### `grid-area` — Shorthand or Named Area

```css
/* Named area (pairs with grid-template-areas) */
grid-area: logo;

/* Shorthand: row-start / column-start / row-end / column-end */
grid-area: 2 / 2 / 5 / 6;
```

---

### `minmax()` and `auto-fill` — Responsive Grids

```css
/* minmax(min, max) — set a flexible range for column/row size */
grid-template-columns: repeat(3, minmax(200px, 1fr));

/* auto-fill — create as many columns as will fit */
grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));

/* auto-fit — like auto-fill but collapses empty tracks */
grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
```

> **Practical Tip:** `repeat(auto-fill, minmax(200px, 1fr))` is the one-liner for a fully responsive card grid — no media queries needed!

---

### Grid vs Flexbox — When to Use Which

|Use Case|Flexbox|Grid|
|---|---|---|
|Navigation bar|✅||
|Single row/column|✅||
|Card grid||✅|
|Full page layout||✅|
|Content alignment|✅||
|Complex 2D layouts||✅|

---

## 2D-Transforms

CSS transforms let you move, resize, rotate, or skew elements without affecting document flow.

> **Key Point:** Transforms do NOT affect surrounding elements — they happen visually while the original space is preserved.

### `transform` Functions

#### Scale — Resize

```css
transform: scale(1.5);       /* Scale both axes to 150% */
transform: scaleX(2);        /* Double width only */
transform: scaleY(0.5);      /* Half height only */
transform: scale(1.2, 0.8);  /* Different X and Y */
```

#### Rotate — Spin

```css
transform: rotate(45deg);    /* Clockwise 45 degrees */
transform: rotate(-90deg);   /* Counter-clockwise 90 degrees */
transform: rotate(1turn);    /* Full 360° rotation */
transform: rotate(0.5turn);  /* Half turn = 180deg */
transform: rotate(0.25turn); /* Quarter turn = 90deg */
```

#### Translate — Move

```css
transform: translateX(100px);           /* Move right 100px */
transform: translateY(-50px);           /* Move up 50px */
transform: translate(100px, -50px);     /* Move right and up */
transform: translate(-50%, -50%);       /* Common centering trick */
```

#### Skew — Tilt/Shear

```css
transform: skewX(20deg);         /* Tilt along X axis */
transform: skewY(10deg);         /* Tilt along Y axis */
transform: skew(10deg, 10deg);   /* Both axes */
```

**Practical skew example — slanted background:**

```css
h2 {
  position: relative;
  color: white;
}
h2::before {
  content: "";
  background-color: red;
  position: absolute;
  left: 0; top: 0;
  width: 100%; height: 100%;
  z-index: -1;
  transform: skewX(20deg); /* Slanted background, straight text */
}
```

#### Matrix — All transforms in one function

```css
/* matrix(scaleX, skewY, skewX, scaleY, translateX, translateY) */
transform: matrix(1.2, 0.2679, 0, 1.2, 20, 20);

/* Equivalent chained transforms */
transform: translateX(20px) translateY(20px) scaleX(1.2) skewY(15deg);
```

### Combining Multiple Transforms

```css
/* Multiple transforms in one declaration — ORDER MATTERS */
transform: rotate(45deg) scale(1.2) translateX(100px);
```

### `transform-origin` — Change the Pivot Point

```css
/* Default is center: 50% 50% */
transform-origin: 0 0;           /* Top-left corner */
transform-origin: 100% 100%;     /* Bottom-right corner */
transform-origin: left center;   /* Left middle edge */
transform-origin: 0 50%;         /* Same as left center */

/* Example: rotate from top-left corner */
div {
  transform-origin: 0 0;
  transform: rotate(45deg);
}
```

---

## 3D-Transforms

Extends 2D transforms into 3D space with depth (Z-axis).

### Rotate in 3D

```css
transform: rotateX(50deg);               /* Flip vertically (like opening a lid) */
transform: rotateY(50deg);               /* Spin like a door */
transform: rotateZ(50deg);               /* Same as 2D rotate */
transform: rotate3d(x, y, z, angle);    /* Custom axis rotation */
transform: rotate3d(0, 1, 1, 65deg);    /* 45° between Y and Z axes */
```

### Translate in 3D

```css
transform: translateZ(100px);            /* Move toward/away from viewer */
transform: translate3d(x, y, z);
transform: translate3d(0, 0, 100px);     /* Same as translateZ(100px) */
```

### `perspective` — Create Depth Effect

Without perspective, 3D transforms look flat. `perspective` defines how far the viewer is from the scene.

```css
/* Applied to the PARENT — affects all 3D children */
.container {
  perspective: 600px;           /* Smaller = more dramatic effect */
  perspective-origin: center center; /* Viewpoint position */
}

/* Or applied directly to the element */
transform: perspective(600px) rotateY(45deg);
```

### `transform-style: preserve-3d`

Makes 3D transforms propagate to children (needed for card flips).

```css
.card {
  transform-style: preserve-3d; /* Children live in the same 3D space */
}
```

### `backface-visibility` — Show/Hide Back of Element

```css
backface-visibility: hidden; /* Hide element when its back faces the camera */
backface-visibility: visible; /* Default */
```

**Complete Card Flip Example:**

```css
.container {
  perspective: 600px;
}
.box {
  position: relative;
  width: 200px;
  height: 200px;
  transform-style: preserve-3d;
  transition: transform 1s;
  transform-origin: right center;
}
.box:hover {
  transform: translateX(-100%) rotateY(-180deg);
}
.face {
  position: absolute;
  width: 100%; height: 100%;
  backface-visibility: hidden;
  display: flex;
  justify-content: center;
  align-items: center;
}
.front { background-color: red; }
.back  {
  background-color: green;
  transform: rotateY(180deg); /* Pre-rotated to face backward */
}
```

---

## Animations

CSS animations let you animate property changes over time using keyframes.

### Step 1 — Define the Keyframes

```css
/* Using from/to (simple start and end) */
@keyframes change-color {
  from { background-color: red; }
  to   { background-color: blue; }
}

/* Using percentages (multiple steps) */
@keyframes change-color {
  0%   { background-color: red; }
  50%  { background-color: blue; }
  100% { background-color: black; }
}

/* Spinner keyframe */
@keyframes spin {
  0%   { transform: rotate(0deg); }
  100% { transform: rotate(360deg); }
}
```

### Step 2 — Apply the Animation

```css
.element {
  animation-name: change-color;    /* Name of the @keyframes */
  animation-duration: 2s;          /* How long one cycle takes */
  animation-iteration-count: 3;    /* How many times to repeat (or infinite) */
  animation-timing-function: ease; /* Speed curve */
  animation-direction: normal;     /* Play direction */
  animation-delay: 1s;             /* Wait before starting */
  animation-fill-mode: forwards;   /* State when animation ends */
  animation-play-state: running;   /* running | paused */
}
```

### Animation Shorthand

```css
/* animation: name duration timing-function delay iteration-count direction fill-mode */
animation: spin 1s linear infinite;
animation: coloring 3s linear 2s infinite reverse;
```

### All Animation Properties Explained

|Property|Values|Description|
|---|---|---|
|`animation-name`|keyframe name|Which `@keyframes` to use|
|`animation-duration`|`2s`, `500ms`|Length of one cycle|
|`animation-iteration-count`|`1`, `3`, `infinite`|How many times to repeat|
|`animation-timing-function`|`ease`, `linear`, `ease-in`, `ease-out`, `cubic-bezier()`|Speed curve|
|`animation-direction`|`normal`, `reverse`, `alternate`, `alternate-reverse`|Play direction|
|`animation-delay`|`1s`, `-2s`|Start delay (negative = start mid-animation)|
|`animation-fill-mode`|`none`, `forwards`, `backwards`, `both`|State before/after playing|
|`animation-play-state`|`running`, `paused`|Pause/resume|

### Timing Functions

```css
animation-timing-function: linear;      /* Constant speed */
animation-timing-function: ease;        /* Default: slow-fast-slow */
animation-timing-function: ease-in;     /* Starts slow, ends fast */
animation-timing-function: ease-out;    /* Starts fast, ends slow */
animation-timing-function: ease-in-out; /* Slow at both ends */
animation-timing-function: steps(4);    /* Jumps in 4 discrete steps */
animation-timing-function: cubic-bezier(0.42, 0, 0.58, 1); /* Custom curve */
```

### Fill Mode

```css
animation-fill-mode: none;       /* Default: returns to original state */
animation-fill-mode: forwards;   /* Stays at the last keyframe (100%) */
animation-fill-mode: backwards;  /* Starts at first keyframe immediately (before delay) */
animation-fill-mode: both;       /* Combines forwards and backwards */
```

### Practical Example — Spinner Loader

```css
.spinner {
  width: 100px;
  height: 100px;
  border-radius: 50%;
  border: 5px solid #e91e63;
  border-left-color: transparent;  /* Creates the gap in the circle */
  animation: spin 1s linear infinite;
}
@keyframes spin {
  0%   { transform: rotate(0deg); }
  100% { transform: rotate(360deg); }
}
```

### Pause on Hover

```css
.animated-element:hover {
  animation-play-state: paused;
}
```

---

## Selectors-Reference-(Advanced)

A comprehensive reference of all CSS selector types.

### Basic Selectors

```css
*              { }   /* Universal — all elements */
p              { }   /* Element type */
.class-name    { }   /* Class */
#id-name       { }   /* ID */
```

### Combinator Selectors

```css
div p          { }   /* Descendant — any p inside a div */
.parent .child { }   /* Descendant class */
div > p        { }   /* Direct child only */
div + p        { }   /* Adjacent sibling — p immediately after div */
p ~ div        { }   /* General sibling — all divs after a p */
.one.two       { }   /* Element with BOTH classes */
p.class-name   { }   /* <p> element with that class */
```

### Attribute Selectors

```css
[href]                  { }   /* Has the attribute */
input[type]             { }   /* <input> with any type attribute */
[type="submit"]         { }   /* Exact value match */
input[type="submit"]    { }   /* Element + attribute + value */
[class~="word"]         { }   /* Contains the word (space-separated) */
[class*="string"]       { }   /* Contains the substring anywhere */
[href^="https"]         { }   /* Starts with value */
[href$=".pdf"]          { }   /* Ends with value */
```

### Structural Pseudo-Classes

```css
:first-child        { }   /* First child of its parent */
:last-child         { }   /* Last child */
:first-of-type      { }   /* First of its element type */
:last-of-type       { }   /* Last of its element type */
:only-child         { }   /* Only child (no siblings) */
:nth-child(n)       { }   /* nth child (1-based) */
:nth-last-child(n)  { }   /* nth from the end */
:nth-of-type(n)     { }   /* nth of element type */
:nth-last-of-type(n){ }   /* nth of type from the end */
:not(selector)      { }   /* Elements that do NOT match the selector */

/* nth-child patterns */
:nth-child(odd)     { }   /* All odd children */
:nth-child(even)    { }   /* All even children */
:nth-child(3n)      { }   /* Every 3rd child */
:nth-child(3n+1)    { }   /* 1st, 4th, 7th... */
```

### State & UI Pseudo-Classes

```css
:root        { }   /* The <html> element — use for CSS variables */
:checked     { }   /* Checked checkbox or radio */
:empty       { }   /* Element with no children or text */
:disabled    { }   /* Disabled form element */
:required    { }   /* Required input field */
:focus       { }   /* Element in focus */
:hover       { }   /* Mouse is over element */
:active      { }   /* Being clicked */
:visited     { }   /* Visited link */
:link        { }   /* Unvisited link */
```

### Pseudo-Elements (Selectors)

```css
::selection    { }   /* Currently selected text */
::placeholder  { }   /* Input placeholder text */
::before       { }   /* Inserts content before element */
::after        { }   /* Inserts content after element */
::first-letter { }   /* First character */
::first-line   { }   /* First line of text */
```

---

## Media-Queries-&-Responsive-Design

Media queries apply styles conditionally based on device characteristics — the foundation of responsive design.

### Basic Syntax

```css
@media media-type and (condition) {
  /* CSS rules applied when condition is true */
}
```

### Media Types

```css
@media screen { }   /* Screens (default) */
@media print  { }   /* When printing */
@media all    { }   /* All devices (default) */
```

### Common Conditions

```css
/* Width-based (most common) */
@media (min-width: 768px)  { }   /* Viewport is at least 768px wide */
@media (max-width: 767px)  { }   /* Viewport is at most 767px wide */
@media (min-width: 992px) and (max-width: 1199px) { }  /* Range */

/* Combining with AND / OR */
@media (min-width: 600px) and (max-width: 900px) { }   /* AND */
@media (max-width: 600px), (min-width: 1200px)   { }   /* OR (comma) */
```

### Standard Breakpoints (Bootstrap-style)

```css
/* Mobile — up to 767px (default styles, no query needed) */

/* Small Screens (tablets) */
@media (min-width: 768px) and (max-width: 991px) {
  /* tablet styles */
}

/* Medium Screens (small laptops) */
@media (min-width: 992px) and (max-width: 1199px) {
  /* small laptop styles */
}

/* Large Screens (desktops) */
@media (min-width: 1200px) {
  /* desktop styles */
}
```

### Mobile-First vs Desktop-First

```css
/* Mobile-First: write mobile styles first, add complexity for larger screens */
.container { width: 100%; }        /* Mobile */
@media (min-width: 768px) {
  .container { width: 750px; }     /* Tablet */
}
@media (min-width: 992px) {
  .container { width: 970px; }     /* Desktop */
}

/* Desktop-First: write desktop styles first, scale down */
.container { width: 1200px; }      /* Desktop */
@media (max-width: 991px) {
  .container { width: 100%; }      /* Mobile/Tablet */
}
```

> **Best Practice:** Use **mobile-first** — it forces you to think about essential content first, and `min-width` queries generally have better performance.

### Applying Media Queries via HTML

```html
<!-- Separate stylesheet only loaded for print -->
<link rel="stylesheet" href="css/print.css" media="print" />

<!-- Separate stylesheet for a specific width range -->
<link rel="stylesheet" href="css/tablet.css" media="(min-width: 768px) and (max-width: 991px)" />

<!-- Internal style tag with media attribute -->
<style media="print">
  .nav { display: none; }
</style>
```

### Viewport Meta Tag — Required for Mobile

```html
<!-- Always add this to <head> for proper mobile rendering -->
<meta name="viewport" content="width=device-width, initial-scale=1.0" />
```

Without this, mobile browsers zoom out to display the "desktop" version — responsive CSS won't work!

### Responsive Flexbox Layout Example

```css
.parent {
  display: flex;
  flex-wrap: wrap;
  gap: 20px;
}

.parent > div {
  width: calc(25% - 15px);  /* 4 columns on desktop */
}

@media (max-width: 991px) {
  .parent > div {
    width: calc(50% - 10px); /* 2 columns on tablet */
  }
}

@media (max-width: 767px) {
  .parent > div {
    width: 100%; /* 1 column on mobile */
  }
}
```

---

## CSS-Global-Values

Every CSS property accepts these universal keyword values.

### `inherit`

Forces the property to take the same value as its parent element.

```css
button {
  font-family: inherit; /* Use parent's font, not browser default */
  color: inherit;
}
```

### `initial`

Resets the property to its **CSS specification default** (not the browser default).

```css
p {
  color: initial;  /* Resets to black (CSS default), ignores inheritance */
}
```

### `unset`

A smart combination:

- If the property is **normally inherited** → acts like `inherit`
- If the property is **not inherited** → acts like `initial`

```css
p {
  color: unset;   /* color is inherited, so behaves like inherit */
  border: unset;  /* border is not inherited, so behaves like initial */
}
```

### `revert` _(CSS Level 4)_

Resets the property to the **browser's default stylesheet** value (more useful than `initial`).

```css
button {
  all: revert; /* Restore all properties to browser defaults */
}
```

### `all` — Reset Everything at Once

```css
/* Reset all properties of an element */
.element {
  all: inherit;  /* All properties inherit from parent */
  all: initial;  /* All properties reset to CSS defaults */
  all: unset;    /* Smart reset */
  all: revert;   /* Reset to browser defaults */
}
```

**Summary Table:**

|Value|Meaning|
|---|---|
|`inherit`|Take value from parent element|
|`initial`|Use CSS spec default|
|`unset`|`inherit` if inheritable, else `initial`|
|`revert`|Use browser stylesheet default|
|`all`|Apply a global value to ALL properties|

---
