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

---

## Layout

### Grid

| Class | Function |
|--- | --- |
| `.grid` | Sets `display:grid` on component with 4 columns
| `.grid_2`, `.grid_3` | 2 or 3 column variants.
| `.grid.vertical` | Vertical Grid
| `.align_centre`, ``.align_start`, `.align_end` | Align items in grid
| `.span_2`,`.span_3`,`.span_4` | For child elements in grid, adds `grid-column: span x` or `grid-row: span x` 

The grid class uses two key CSS variables:
- `--grid-columns` : the number of columns in the grid
- `--grid-gap`: the gap (in px) of the grid

When setting up a custom grid, you can change these variables to change the behaviour of the grid.

The `--grid-columns` variable is set as **4** by default on desktop. This changes to **2** at screens of less than **800px wide** and then to **1** at screens of less than **500px wide**

### Flex

---

## Text

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