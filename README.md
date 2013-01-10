Crafted CSS
===========

This is a personal compilation of CSS practices I follow.

Inspiration was drawn from Nicholas Gallagher's Idomatic CSS, Jonathan Snook's SMACSS, Harry Robert's HTML/CSS Coding Style, Yandex's BEM, Github's CSS Style Guide, Google's HTML/CSS Style Guide and my own experience with CSS over the years.

> All code in any code-base should look like a single person typed it, no matter how many people contributed.
> – _Nicholas Gallagher_



General
-------

- Don't use IDs in CSS if at all possible. Stick to classes.
- Do not be overly specific.



Formatting
----------

- Write one declaration per line.
- Always use a leading zero before a decimal number. (e.g. `opacity: 0.8;`)
- Don't attach a unit to a zero value if it's not needed. (e.g. Use `padding: 1em 0 0` instead of `padding: 1em 0em 0px`. However, it is neccesarry to leave `%` on some zero values like `color: hsla(130, 0%, 50%, 0.2);`.)
- Always end declarations with a semicolon.
- Make class/ID names human readable, but as short as possible. (e.g. `.nav` and `.btn` are fine, but use `.gallery` instead of `.glry`)
- Use dashes, not underscores or camel case with class/ID names. (e.g. `.btn-large`, not `.btn_large` or `.btnLarge`)
- Use double quotes. (`font-family: "Lucida Sans", sans-serif`)
- Your closing brace should line up vertically with the first character in the ruleset.
- Don't use quotation marks around `url`s.
- Keep `url`s relative by not including `http:` or `https:`.

---

    .example {
        background-image: url(//chrisnager.com/images/image.png);
    }



Whitespace
----------

- Properties should be indented four spaces.
- Use soft tabs that span four spaces.
- When indenting, do not mix tabs and spaces. Only use spaces. (I turn on Show Invisibles in my editor to check this.)
- Always put a space between a selector and its opening curly brace.
- Put a space after the colon between your property and value.
- Never leave trailing white space. (I use a plugin that deletes trailing white space on each save.)
- Use spaces between values like hsla/rgba color values to improve readability. /* 1 */

---

    .selector {
        property: value;
    }
    
    /* 1 */
    .btn {
        background-color: hsl(4, 100%, 43%);
    }



Colors
------

- Color names (`red`) and shorthand hexcodes (`#eee`) are preffered. Regular hexcodes, `hsla`, and `rgba` may be used for additional color control.
- Use lowercase only when dealing with colors. (e.g. `cadetblue`, `#dabb1e`, `#b2b`)



Vendor prefixes
---------------

- Do not indent vendor prefixed declarations.
- Order them from longest prefix name to shortest.
- Always use the non-prefixed property last.

        .btn {
            -webkit-transition: background-color 0.4s ease-in-out;
            -moz-transition: background-color 0.4s ease-in-out;
            -o-transition: background-color 0.4s ease-in-out;
            transition: background-color 0.4s ease-in-out;
        }



Font-size / line-height
-----------------------

Set base `font-size` in pixels and additional `font-size`s in `rem`s/`em`s.
Set `line-height` with a unitless number. (e.g. `line-height: 1.4;`)

    html {
        font: 16px/1.6 sans-serif;
    }
    h1 {
        font-size: 40px; /* Fallback */

        font-size: 2.5rem;
        /* h1 is now 40px/64px */
    }



Comments
--------

- Comment often.
- First level comments should always be followed by an empty line.
- Except for the first one on the page, first level comments should be preceded by six empty lines.
- Three empty lines before second level comments and one empty line after.
- Use sentence case when writing comments.

---

    /* Comment level 1
       -------------------------------------------------- */
    
    .selector {
        property: value;
    }
    
    
    
    
    
    
    /* Here's another level 1 comment
       -------------------------------------------------- */
    
    /* Have you seen level 2 comments?
       ---------------------------------------- */
    
    .selector {
        property: value;
    }
    
    
    
    /* And...comment level 3
       ------------------------------ */
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
        property: value; /* A wild inline comment appeared! */
    }



Order
-----

1. Base
2. Layout
3. Module
4. State
5. Theme

---

    .btn {
        width: auto;
        height: auto;
        min-width: 0;
        max-width: none;
        min-height: 0;
        max-height: none;

        margin: 0 auto;
        border: 0;
        border-radius: 0.15em;
        padding: 0.5em 1em;

        position: relative;
        top: 0;
        right: auto;
        bottom: auto;
        left: 0;

        display: inline-block;
        float: none;

        font-family: sans-serif;
        font-size: 1.5rem;
        font-weight: bold;
        font-style: italic;

        line-height: 1.5;
        letter-spacing: -0.1em;

        text-align: center;
        text-decoration: underline;

        color: white;

        background-color: red;
        background-image: url(btn-bg.png);
        background-position: right center;
        background-repeat: no-repeat;
        background-size: contain;
    }



Exceptions
----------

- Note the spacing.

        .grid-10 { width: 10%; }
        .grid-20 { width: 20%; }
        .grid-30 { width: 30%; }
        .grid-40 { width: 40%; }



BEM
---

This is the only time underscores are cool to use.

`.block__element--modifier {}`



Preprocessors
-------------

I encourage splitting your SCSS/Less/Stylus files into a maintainable folder structure with chunks of related styles.

Like this:

project-name.scss
vars.scss
