Crafted CSS
===========

My personal CSS styleguide



General
-------

- Always put a space between a selector and its opening curly brace.
- Properties should be indented four spaces.
- Soft tabs that span four spaces must be used.
- Put a space after the colon before values.
- Do not be overly specific.

        .selector {
            property: value;
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
