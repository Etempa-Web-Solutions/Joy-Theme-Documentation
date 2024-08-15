---
title: Utility Classes
layout: default
nav_order: 1
parent: CSS
---

# Utility Classes
{: .no_toc }

1. TOC
{:toc}

---

## Structure

| Class | Function |
|--- | --- |
| `.main_container` | Constrains element to page width size
| `.content_section` | Adds vertical spacing to element.
| `.content_section_large` `.content_section_small` | Adds small/large vertical spacing to element.
| `.content_section.top_spacing_only` `.content_section.bottom_spacing_only` | Adds vertical spacing to top/bottom only.
| `.content_section.content_section_has_background` | Add additional class if content section has coloured background to re-instate padding


## Box Model

You can add **margin** and **padding** to elements with classes by using the following format:

`.spacing_direction_size`

| Spacing | Function |
|--- | --- |
| `margin` | Adds margin to element
| `padding` | Adds padding to element

| Direction | Function |
|--- | --- |
| `x` | Adds style to top and bottom
| `y` | Adds style to left and right
| `top` | Adds style to top only
| `bottom` | Adds style to bottom only
| `left` | Adds style to left only
| `right` | Adds style to right only

| Size | Function |
|--- | --- |
| `normal` | Adds default amount of spacing
| `small` | Adds small amount of spacing
| `large` | Adds large amount of spacing
| `smallest` | Adds 5px of spacing

For example

```html
<div class='margin_x_large'>
    Lorem Ipsum....
</div>
```

```html
<div class='padding_top_small'>
    Lorem Ipsum....
</div>
```

### Additional margin/padding classes

These are all self-explanatory (hopefully):

- `.no_margin`
- `.no_x_margin`
- `.no_y_margin`
- `.no_padding`
- `.no_x_padding`
- `.no_y_padding`

---

## Layout

### Grid

| Class | Function |
|--- | --- |
| `.grid` | Sets `display:grid` on component with 4 columns
| `.grid_2`, `.grid_3` | 2 or 3 column variants.
| `.grid.vertical` | Vertical Grid
| `.align_centre`, `.align_start`, `.align_end` | Align items in grid
| `.span_2`,`.span_3`,`.span_4` | For child elements in grid, adds `grid-column: span x` or `grid-row: span x` 

The grid class uses two key CSS variables:
- `--grid-columns` : the number of columns in the grid
- `--grid-gap`: the gap (in px) of the grid

When setting up a custom grid, you can change these variables to change the behaviour of the grid.

The `--grid-columns` variable is set as **4** by default on desktop. This changes to **2** at screens of less than **800px wide** and then to **1** at screens of less than **500px wide**

### Flex

| Class | Function |
|--- | --- |
| `.flex`, `.flex_column`, `.flex_row` | Sets `display:flex` on component (dif just `.flex` is used then it defaults to `flex-direction:column`
| `.flex_wrap` | Adds `flex-wrap:wrap`
| `.justify_start`, `.justify_end`, `.justify_around`, `.justify_evenly`, `.justify_between` | Adds justification rule to container
| `.flex_grow`,`.flex_shrink` | For child elements in flexbox, adds `flex-grow:1` or `flex-shrink:2` to element

As with `.grid`, the element with have a variable of `--flex-gap` which determines the gap in the flexbox (default `20px`)


### Width/Height of Element

| Class | Function |
|--- | --- |
| `.width_100`, `.width_50`, `.width_25`, `.width_10`  | Sets width to be 100%, 50%, 25%, 10% respectively
| `.height_100`, `.height_50`, `.height_25`, `.height_10`  | Sets height to be 100%, 50%, 25%, 10% respectively

---

## Text

| Class | Function |
|--- | --- |
| `..bold`, `.font_bold` | Sets font-weight to be `800`
| `.font_italic` | Sets font-style to italic
| `.font_regular` | Sets font-weight to body weight
| `.font_light` | Sets font-weight to 300
| `.font_normal` | Sets font style to normal (use to undo parent style)
| `.text_colour_body` | Sets text colour to main foreground colour (use to override other styles)
| `.text_colour_primary` | Sets text colour to primary colour (e.g. the colour of the primary button)
| `.text_colour_secondary` | Sets text colour to secondary colour (e.g. the colour of the secondary button)
| `.font_size_small`, `.font_size_large` , `.font_size_xl`, `.font_size_2xl` | Sets relative font-size, accordingly
| `.uppercase`, `.lowercase` | Sets case of text
| `.text_centre` | Centres text in element

---

## Visibility

| Class | Function |
|--- | --- |
| `.hidden` | Adds `display:none;` to element
| `.visibility_hidden` | Adds `visibility: hidden;` to element
| `.visually_hidden` | Visually hides element, but can still be detected by screen-readers


---

## Functionality

| Class | Function |
|--- | --- |
| `.disable_pointer_events` | Disables poitner-events (i.e. click, hover etc)

---

## Box Shadow

| Class | Function |
|--- | --- |
| `.box_shadow_subtle`, `.box_shadow_medium` `.box_shadow_bold`,  | Varying degrees of box-shadow

---

## Animations

| Class | Function |
|--- | --- |
| `.fade-in`, `.fade-out` | Animates element to 'fade-in' (or out) by transforming it to appear from the top

**NB If the user has prefers-reduced-motion on, then no animations will display**