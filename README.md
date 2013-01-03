Crafted CSS
===========

My personal CSS styleguide



General
-------

- Always put a space between a selector and its opening curly brace.
- Properties should be indented four spaces.
- Soft tabs that span four spaces must be used.
- Put a space after the colon before values.
- Always use a zero before a decimal number. (e.g. opacity: 0.8;)
- Always end declarations with a semicolon.
- Don't use IDs in CSS if at all possible.
- Do not be overly specific.

---

        .selector {
            property: value;
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

Set base <code>font-size</code> in pixels and additional <code>font-size</code>s in <code>rem</code>s/<code>em</code>s.
Set <code>line-height</code> with a unitless number. (e.g. line-height: 1.4;)

    html {
        font: 16px/1.6 sans-serif;
    }
    h1 {
        font-size: 2.5em;
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
