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
- Do not be overly specific. (e.g. `.my-list > li` rather than `body .content .wrapper .my-list li`)
- Instead of targetting an element like this: `body .header .box a.btn`, `.btn` is much better.
- Avoid over-qualified selectors when possible. (e.g. Use `.btn` instead of `a.btn`)
- Make your code as future-proof and easily editable for the next developer that will be working on it.
- A note on shorthand, be explicit. If an element only needs `padding-bottom: 0;`, do not use the shorthand property `padding: 0`. It may come back to bite you later on because you'll need to overwrite CSS that shouldn't have been there in the first place.
- When debugging your CSS, remove code rather than add more.



Formatting
----------

- Write one declaration per line.
- Always use a leading zero before a decimal number. (e.g. `opacity: 0.8;`)
- Don't attach a unit to a zero value if it's not needed. (e.g. Use `padding: 1em 0 0` instead of `padding: 1em 0em 0px`. However, it is neccesarry to leave `%` on some zero values like `color: hsla(130, 0%, 50%, 0.2);`.)
- Always end declarations with a semicolon.
- Make class/ID names human readable, but as short as possible. (e.g. `.nav` and `.btn` are fine, but use `.gallery` instead of `.glry`)
- Use lowercase with dashes, not underscores or camelcase for class/ID names. (e.g. `.btn-large`, not `.btn_large` or `.btnLarge`)
- Use double quotes. (`font-family: "Lucida Sans", sans-serif`)
- Your closing brace should line up vertically with the first character in the ruleset.
- Don't use quotation marks around `url`s.
- Keep `url`s relative by not including `http:` or `https:`.

Relative url example:

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
- Use spaces between subvalues in values like hsla/rgba color values to improve readability. (e.g. `hsl(4, 100%, 43%)`)

Example showing the proper use of whitespace:

    .selector {
        property: value;
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

<br>

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
        property: value;
    }
    
    
    
    /* Level 2 comment
       ---------------------------------------- */
    
    .selector {
        property: value;
    }






    /* Another level 1 comment
       -------------------------------------------------- */
    
    .selector {
        property: value; /* A wild inline comment appeared! */
    }



Order
-----

You should follow this five-group model for crafting your CSS.

1. Base - includes your elements without classes
    html {}
    a {}
    a:hover {}

2. Layout - includes elements that make up the structure of the page
    .l-module {}
    .l-content {}

3. Module - includes typical elements that contain the content
    .nav
    
4. State - define your JS state classes here
    .is-active

5. Theme - includes variations of module elements
    .btn--dark

General declaration order:

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



Responsive Design
-----------------

- Write your media queries straight into your code and not all at the end of your CSS document.
- Build in a flexible way where you do not need to set widths.
- Craft your layouts with `rem`s, `em`s, and percentage-based units for fluidity.



OOCSS and BEM
-------------

- OOCSS is all about finding design patterns that can be abstrated into reusable components.
- BEM is the only time underscores are cool to use. BEM takes OOCSS to another level that establishes logical class names and keeps specificity to a bare minimum.

<br>

OOCSS example:

    .btn
    .btn--primary
    .btn--secondary


How BEM should be written:

    .block__element--modifier {}



JavaScript
----------

- Classes added by JS should be prefixed with "is" to denote the JS state that was added to the element. (e.g. `.is-active`)



Preprocessors
-------------

I encourage splitting your SCSS/Less/Stylus files into a maintainable folder structure with chunks of related styles.

Like this:

project-name.scss
vars.scss

More on this to come...
