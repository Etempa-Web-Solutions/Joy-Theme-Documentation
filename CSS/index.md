---
title: CSS
layout: default
nav_order: 3
has_children: true
---

# CSS

The main aim of this site is to **avoid writing anything twice**.

Before adding styles for a new section / element, do a quick search on the codebase or on the documentation to check that it hasn't already been covered by another section / element. 

If it seems as though your new code/class would be useful in other places, consider adding it to the relevant place in `main-partials`, make sure to name it sensibly and add it to the documentation once finished.

### Utility Classes

Included in `includes/scss/main-partials` is a file called _utilities.scss. This file contains a mixture of Utility classes that can be used when writing the theme code. These classes will be documented on here. We have tried to avoid having too many of these, and have only included classes that are most useful. Examples of this are the `grid` class which can be added to any element to add `display: grid` to it (along with a few other styles). The intention is that it means we have to repeat ourselves a bit less in the css, and get everything a bit more uniform across the theme.

### CSS Variables

The CSS/SCSS files make use of CSS Variables for a number of uses.

Firstly, anything inputted from the theme customiser is saved as a CSS Variable (this can be found in `snippets/layout-css-variables.liquid`). These CSS Variables are then accessed in the SCSS files using `var(--name-of-variable)`.

One other benefit of CSS Variables is that they can be modified by CSS rules.

e.g.
```css
::root
{
    --background-colour: #000;
}

.different_coloured_background_section
{
    --background-colour: #555;
}

.text_container
{
    background-color: var(--background-colour);
}
```

In the example above, we can change the background colour of the `.text_container` if it is inside the `.different_coloured_background_section` element. Otherwise, it will use the default background colour.

# SCSS

The CSS for this theme will be written using SCSS, which is then compiled to minified CSS.

### Useful Mixins

Check out and use the mixins where appropriate.

To keep font sizes consistent, please use the `font_size_ratio` mixin with either whole numbers or .5 numbers. In specific circumstances, you can use either .2 or .7, or an actual font-size (mainly for responsiveness) but try to avoid this. Using the mixin means we can re-size the entire theme’s font sizing easily.  

Do not go smaller than 0 unless it’s for a very specific reason. To go smaller than 0, you can use 0.7 (yes 0.7 is larger than 0, but it’s just how maths works in my function). Bear in mind we must not go smaller than 14px anywhere. 

Some more important mixins are `display_grid()`. You can put the grid-gap as a parameter such as `display_grid(60px)`. It defaults to 20px if you don’t add anything. 

Add @includes `text_container_edge_margin_reset()` to a div and the top margin of the first element and the bottom margin of the last element will be removed. This is really handy for vertical centring to make sure the box is the right size and not being distorted by additional margins from the text. 
