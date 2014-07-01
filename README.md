Crafted CSS
===========

This is a personal compilation of CSS practices I follow.

Inspiration was drawn from Nicholas Gallagher's Idomatic CSS, Jonathan Snook's SMACSS, Harry Robert's HTML/CSS Coding Style, Nicole Sullivan's OOCSS, Yandex's BEM, Github's CSS Style Guide, Google's HTML/CSS Style Guide and my own experience with CSS over the years.

> All code in any code-base should look like a single person typed it, no matter how many people contributed.
> – _Nicholas Gallagher_



Contents
--------

- [General](#general)
- [Formatting](#formatting)
- [Whitespace](#whitespace)
- [Numbers](#numbers)
- [URLs](#urls)
- [Colors](#colors)
- [Vendor prefixes](#vendor-prefixes)
- [Font size / line height](#font-size--line-height)
- [Comments](#comments)
- [Order](#order)
- [Exceptions](#exceptions)
- [Responsive Design](#responsive-design)
- [OOCSS and BEM](#oocss-and-bem)
- [JavaScript](#javascript)
- [Preprocessors](#preprocessors)



General
-------

- Don't use IDs in CSS if at all possible. Stick to classes.
- Do not be overly specific with your selectors. (e.g. `.my-list > li` rather than `body .content div.wrapper .my-list li`)
- Instead of targetting an element based on it's parents like this: `body .header .box a.btn`, `.btn` is much better.
- Avoid over-qualified selectors when possible. (e.g. Use `.btn` instead of `a.btn`)
- Make your code as future-proof and easily editable for the next developer that will be working on it.
- A note on shorthand, be explicit. If an element only needs `padding-bottom: 0;`, do not use the shorthand property `padding: 0`. It may come back to bite you later on when you need to overwrite CSS that shouldn't have been there in the first place.
- When debugging your CSS, remove code rather than add more.



Formatting
----------

- Write one declaration per line.
- Always end declarations with a semicolon.
- Make class/ID names human readable, but as short as possible. (e.g. `.nav` and `.btn` are fine, but use `.gallery` instead of `.glry`)
- Use lowercase with dashes, not underscores or camelcase for class/ID names. (e.g. `.btn-large`, not `.btn_large` or `.btnLarge`)
- Use double quotes. (`font-family: "Lucida Sans", sans-serif`)
- Your closing brace should line up vertically with the first character in the ruleset.



Whitespace
----------

- Properties should be indented four spaces.
- Use soft tabs that span four spaces.
- When indenting, do not mix tabs and spaces. Only use spaces. (I turn on Show Invisibles in my editor to check this.)
- Always put a space between a selector and its opening curly brace.
- Put a space after the colon between your property and value.
- Never leave trailing white space. (I use a plugin that deletes trailing white space on each save.)
- Use spaces between subvalues in values like hsla/rgba color values to improve readability. (e.g. `hsl(4, 100%, 43%)`)

Example showing the proper use of whitespace:

```css
.btn {
    background-image: linear-gradient(to bottom, #0cf, rgba(255, 255, 255, 0.5));
}
```


Numbers
-----

- Always use a leading zero before a decimal number. (e.g. `opacity: 0.8;`)
- Don't attach a unit to a zero value if it's not needed. (e.g. Use `padding: 1em 0 0` instead of `padding: 1em 0em 0px`. However, it is neccesarry to leave `%` on some zero values like `color: hsla(130, 0%, 50%, 0.2);`.)



URLs
----

- Don't use quotes around `url`s.
- Use only protocol-relative `url`s by not including `http:` and `https:`.

Protocol-relative url example:

```css
.example {
    background-image: url(//chrisnager.com/images/image.png);
}
```



Colors
------

- [Short color names](//github.com/chrisnager/short-color-names) (`red`) and shorthand hexcodes (`#eee`) are preferred. Regular hexcodes, `hsla`, and `rgba` should be used for additional color control.
- Only use lowercase when dealing with colors. (e.g. `cadetblue`, `#dabb1e`, `#b2b`)



Vendor prefixes
---------------

- Do not indent vendor prefixed declarations.
- Order them from longest prefix name to shortest.
- Always use the non-prefixed property last.

```css
.btn {
    -webkit-transition: background-color 0.4s ease-in-out;
    -moz-transition: background-color 0.4s ease-in-out;
    -o-transition: background-color 0.4s ease-in-out;
    transition: background-color 0.4s ease-in-out;
}
```



Font-size / line-height
-----------------------

- You can set your base `font-size` in pixels but all additional `font-size`s should be set with `rem`s or `em`s.
- Root ems make sense for setting your `font-size`s because they are proportionally based on the initial `font-size` of the root element.
- Always set your `line-height` with a unitless number. (e.g. `line-height: 1.4;`)

```css
html {
    font: 16px/1.6 sans-serif;
}

h1 {
    font-size: 40px; /* Fallback */
    font-size: 2.5rem; /* This makes your h1 40px/64px. */
}
```



Comments
--------

- Comment often for future developers (and for future you).
- First level comments should always be followed by an empty line.
- Except for the first one on the page, first level comments should be preceded by six empty lines.
- Three empty lines before second and third level comments.
- Use sentence case when writing comments.

Commenting formats:

```css
/* ==========================================================================
   Comment level 1
   ========================================================================== */

.selector {
    property: value;
}






/* ==========================================================================
   Here's another level 1 comment
   ========================================================================== */

/* Have you seen level 2 comments?
   -------------------------------------------------------------------------- */
.selector {
    property: value;
}



/* And...comment level 3
   ------------------------------------------------------ */
   
.selector {
    property: value;
}
.selector {
    property: value;
}



/* But wait! There's more. Comment level 4 */
.selector {
    property: value;
}

.selector {
    property: value;
}



/* Level 2 comment
   -------------------------------------------------------------------------- */
.selector {
    property: value;
}






/* ==========================================================================
   Another level 1 comment
   ========================================================================== */

.selector {
    property: value; /* A wild inline comment appeared! */
}
```



Order
-----

You should follow this five-group model for crafting your CSS.

1. Base - includes your elements without classes
`html {}`,
`a {}`,
`a:hover {}`

2. Layout - includes elements that make up the structure of the page
`.l-module {}`,
`.l-content {}`

3. Module - includes typical elements that contain the content
`.nav {}`
    
4. State - define your JS state classes here
`.is-active {}`

5. Theme - includes variations of module elements
`.btn--dark {}`

General declaration order:

```css
.btn {
    /* Box model */
    content: " »";
    box-sizing: border-box;
    
    width: auto;
    min-width: 0;
    max-width: none;
    height: auto;
    min-height: 0;
    max-height: none;

    margin: 0 auto;
    margin-top: 0;
    margin-right: auto;
    margin-bottom: 0;
    margin-left: auto;
    border: 0;
    border-top: 0;
    border-top-width: 0;
    border-right: 0;
    border-right-width: 0;
    border-bottom: 0;
    border-bottom-width: 0;
    border-left: 0;
    border-left-width: 0;
    border-radius: 0.15em;
    padding: 0.5em 1em 0.55em;
    padding-top: 0.5em;
    padding-right: 1em;
    padding-bottom: 0.55em;
    padding-left: 1em;

    /* List your positioning properties in TRBL (top, right, bottom, left) order. */
    position: relative;
    top: 0;
    right: auto;
    bottom: auto;
    left: 0;

    /* Display properties */
    display: inline-block;
    float: none;
    clear: none;
    z-index: 1;

    list-style: katakana inside;
    list-style-type: katakana;
    list-style-image: url(list-disc.png);
    list-style-position: inside;

    opacity: 0.9;
    cursor: pointer;

    /* Tables */
    table-layout: auto;
    border-collapse: collapse;
    border-spacing: 0.5em;
    caption-side: top;
    empty-cells: show;
    speak-header: always;

    /* Typographic styles */
    font: 1.5rem sans-serif;
    font-family: sans-serif;
    font-variant: small-caps;
    font-size: 1.5rem;
    font-size-adjust: none;
    font-weight: bold;
    font-style: italic;
    font-stretch: normal;

    line-height: 1.5;
    letter-spacing: -0.1em;

    white-space: nowrap;
    word-spacing: normal;

    text-indent: 1em;
    text-align: center;
    text-transform: uppercase;
    text-decoration: underline;
    text-shadow: 0.1em -0.1em rgba(0, 0, 0, 0.8);

    /* Colors and backgrounds */
    color: #222;

    background: none;
    background-color: red;
    background-image: url(btn-bg.png);
    background-position: right center;
    background-repeat: no-repeat;
    background-size: contain;
    
    /* Other presentational properties */
    box-shadow: 0 0.1em 0.5em rgba(0, 0, 0, 0.25);
    transform: rotate(3deg);
    transition: color 1s ease-out;
    animation: flip 3s all;
}
```



Exceptions
----------

- Note the spacing inside the curly brackets.

Take for example a large sprited image of national flags:

```css
.icon--flag {
    width: 15px;
    height: 10px;
    border: 1px solid gold;
    display: inline-block;
    background-image: url(//path.to/sprite.png);
}

.icon--flag-1 { background-position: 0 -10px; }
.icon--flag-2 { background-position: 0 -20px; }
.icon--flag-3 { background-position: 0 -30px; }
.icon--flag-4 { background-position: 0 -40px; }
.icon--flag-5 { background-position: 0 -50px; }
.icon--flag-6 { background-position: 0 -60px; }
```



Responsive Design
-----------------

- Write your media queries right along with your code and not all at the end of your CSS document.
- Build in a flexible way where you do not need to set widths.
- Craft your layouts with `rem`s, `em`s, and percentage-based units for fluidity.



OOCSS and BEM
-------------

- OOCSS is all about finding design patterns that can be abstrated into reusable components.

OOCSS example:

```css
.btn {}
.btn--primary {}
.btn--secondary {}
```


- BEM is the only time underscores are cool to use. BEM takes OOCSS to another level that establishes logical class names and keeps specificity to a bare minimum.

How BEM should be written:

```css
.block__element--modifier {}

Block
.menu {}

Block + Modifier
.menu--vertical {}

Block + Element
.menu__menu-items {}

Block + Element + Modifier
.menu__menu-items--rev {}
```



Real world example of OOCSS in action using a BEM-style class structure:

```html
<a href="/" class="btn  btn--large  btn--positive">Submit</a>
```

```css
.btn {
    border-radius: 0.1em;
    padding: 0 0.75em;
    display: inline-block;
    line-height: 1.75em;
    white-space: nowrap;
    color: #fff;
    background-color: gray;
}



.btn--small {
    padding-right: 0.5em;
    padding-left: 0.5em;
    line-height: 1.5em;
}

.btn--large {
    padding-right: 1em;
    padding-left: 1em;
    line-height: 2em;
}



.btn--positive {
    background-color: lime;
}

.btn--negative {
    background-color: tomato;
}
```


JavaScript
----------

- Classes added by JS should be prefixed with "is" to denote the JS state that was added to the element. (e.g. `.is-active`)



Preprocessors
-------------

I encourage splitting your SCSS/Less/Stylus files into a maintainable folder structure with chunks of related styles.

Like this:

`project-name.scss`
`vars.scss`

More on this to come...
