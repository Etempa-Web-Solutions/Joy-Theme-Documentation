---
title: Coding Style
layout: default
parent: General
nav_order: 1
---

# Coding Style

**Above all, please match the coding style used in the existing files.**

## Brackets

Brackets on new lines

```js
if(x == z)
{
    //do something
}
```

## Naming Conventions

- Custom HTML Elements
    - Dash notation
    - e.g. `predictive-search`
- CSS Class Names, IDS, SCSS mixin names
    - Underscore Notation
    - e.g. `this_is_a_class_name`
- Javascript variables
    - Camel Case
    - e.g. `thisIsAVariable`
- Javascript Class Names
    - Upper Camel Case
    - e.g. `ClassName`
- File Names
    - Lower Case with dashes
    - e.g. `this-is-a-file-name.liquid`


## Indentation

All code to be properly indented. A tab is 4 spaces

---

## CSS Coding Style

Put any `@includes` at the top of the selector styles list and try to group similar styles

```css
.my_class
{
    @include a_mixin();

    text-align: center;
    text-transform: uppercase;

    width: 100px;
    height: auto;

    color: #000;
}

```

{: .warning }
> !important
>
> Try to avoid `!important` where possible and do not rely on CSS positioning to overwrite styles. Use more specific definitions.

All partial file names to begin with _ 

### Variables / Custom properties

The SCSS code makes heavy use of CSS Custom Properties (variables). Rather than define brand-new styles for different classes, try to use Custom Properties to alter the styles.


### Responsiveness

- Account for screen sizes 280px – 2500px 

- Use definitions including min and max widths so it is clear when the styles should apply i.e (min-width: 700px) and (max-width: 749px). Exceptions apply where the max width would otherwise be 2499px or the min width would be 280px

- Structure the responsive file based on min width order (low to high) followed by max width order (within the same min width) 

- Min widths should be in 50px gaps, either 00, or 50. Max widths should also be in 50px gaps, either 49 or 99. Exceptions apply where the styling specifically requires it to be more precise. 

- Inside media queries, try to keep section code together, with the exception of styles which apply to multiple elements, which should be at the top of the media query. Try to avoid multiple instances of the same styles in one query. Instead, group the selectors such as .oneclass, .anotherclass etc. 

- Please be responsible for the responsiveness of any CSS you code

---

## Javascript Coding Style


Consider a javascript class where possible, before adding javascript code in the procedural style

Although a javascript object doesn’t require you to declare a variable in the object before using it, nor does it require every variable have a get / set method, do not define variables in the code that aren’t referenced in the class to ensure everyone understands the possibilities of the class. 

A list of variables used in the class should be added to a commented list at the top of the class, including any variables set in the constructor and any variables available from get / set methods

Variables saved in a set method should follow the naming format of `_nameOfSetMethod` i.e if the set method is name, the variable saved should be `_name`


## JSON Coding Style

Unless order is important for displaying options to the user, position JSON key / value pairs in alphabetical order so it is easier to find things. The only exception is where we have a ‘header / heading / title’ key – this makes sense to be at the top to give context to the rest of the settings. 

## Liquid Coding Style

All HTML elements to be properly indented.

If an HTML element has **over three attributes (that aren't class or id)** then these can be placed on new lines to make readability better

e.g.

```html
<button class='button' id='button'
    type='button'
    data-id='123434'
    data-behaviour='add'
    data-submit='false'
>
    <span>Click Me</span>
</button>
```

When a block of liquid codes goes over **5 lines** use the `liquid` tag to enclose the code

{% raw %}
```
{% liquid
    assign my_variable = 'text'
    if my_variable contains 'text'
        for product in collection.products
            assign my_variable = product.id
        endfor
    endif
%}
```
{% endraw %}