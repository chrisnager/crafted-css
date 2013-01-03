Crafted CSS
===========

My personal CSS styleguide

> All code in any code-base should look like a single person typed it, no matter how many people contributed. – _@necolas from idomatic.css_



General
-------

- Don't use IDs in CSS if at all possible. Stick to classes.
- Do not be overly specific.



Formatting
----------

- Write one declaration per line.
- Always use a leading zero before a decimal number. (e.g. `opacity: 0.8;`)
- Always end declarations with a semicolon.
- Make class/ID names human readable, but as short as possible. (e.g. `.nav` and `.btn` are fine, but use `.gallery` instead of `.glry`)
- Use dashes, not underscores or camel case with class/ID names. (e.g. `.btn-large`, not `.btn_large` or `.btnLarge`)
- Color names (`red`) and shorthand hexcodes (`#eee`) are preffered. Regular hexcodes, `hsla`, and `rgba` may be used for additional color control.
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



Vendor prefixes
---------------

- Do not indent vendor prefixed declarations.
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
