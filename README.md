Crafted CSS
===========

My personal CSS styleguide



General
-------

- Don't use IDs in CSS if at all possible. Stick to classes.
- Do not be overly specific.



Formatting
----------

- Always use a zero before a decimal number. (e.g. `opacity: 0.8;`)
- Always end declarations with a semicolon.



Indenting and white-space
-------------------------

- Properties should be indented four spaces.
- Use soft tabs that span four spaces.
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

First level comments should always be followed by an empty line. Except for the first one on the page, first level comments should be preceded by six empty lines.
Three empty lines before second level comments and one empty line after.

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
