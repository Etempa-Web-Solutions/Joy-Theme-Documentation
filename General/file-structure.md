---
title: File Structure
layout: default
parent: General
nav_order: 2
---

# File Structure

The file structure will follow the standard Shopify theme structure, with the addition of an includes folder for our SASS and javascript files. **Bear in mind that anything in this includes folder will not be uploaded to Shopify and therefore only files which are being compiled should be put here**. Anything else should go in the assets folder. 

## CSS Files

SASS files are found in **/includes/sass** and are split into two folders: **main-partials** and **sections**

### main-partials

The main-partials folder contains all of the partials files that make up the main css file

Any variables go in the _variables.scss file. These variables are only used in SCSS, and so cannot be accessed by the Shopify customiser. This file is useful for saving any variables that are for development purposes.

Mixins go in _mixins.scss.

You will not need to use _normalise.scss, which has already been setup. 

_elements.scss are for any css styles that are likely to be used in lots of places for example, form, input, select, table. They tend to be selectors for html tags rather than lots of classes and ids. 

_text.scss is like elements but specific for text. You shouldn’t really need to add to this much as I should have most general text styles now but just to be aware. 

_main.scss is essentially for anything else that isn’t specific enough to have its own file like the sections. If it doubt, put it at the bottom of main and it can be moved elsewhere later on. 

_responsiveness.scss is currently used for all responsiveness. 

_utilities.scss contains all of the CSS utility classes that can be used when writing the HTML

### sections

Every section should have its own partial file.

These will then be compiled into separate css files in assets. Each section file will have to be included at the top of a section file

The sections files are separated out, and so if you want to make use of mixins, remember to include the _mixins file at the top of the section SCSS file
