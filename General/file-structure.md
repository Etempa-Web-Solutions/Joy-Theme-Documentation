---
title: File Structure
layout: default
parent: General
nav_order: 2
---

# File Structure

1. TOC
{:toc}

---

The file structure will follow the standard Shopify theme structure, with the addition of an includes folder for our SASS and javascript files. **Bear in mind that anything in this includes folder will not be uploaded to Shopify and therefore only files which are being compiled should be put here**. Anything else should go in the assets folder. 

## SCSS Files

SASS files are found in **/includes/sass** and are split into two folders: **main-partials** and **sections**. All files in main-partials will be compiled into the main CSS file. All of the files in sections will be compiled into separate CSS files to be included on specific pages / sections.

### main-partials
{: .no_toc }

The `main-partials` folder contains all of the partials files that make up the main css file

Any SCSS variables go in the _contants.scss file. These variables are only used in SCSS, and so cannot be accessed by the Shopify customiser. For the purposes of this project, these variables can be thought of more as **constants** rather than variables that can be changed.

Mixins go in _mixins.scss.

You will not need to use _normalise.scss, which has already been setup. 

_elements.scss are for any css styles that are likely to be used in lots of places for example, form, input, select, table. They tend to be selectors for html tags rather than lots of classes and ids. 

_text.scss is like elements but specific for text. You shouldn’t really need to add to this much as I should have most general text styles now but just to be aware. 

_main.scss is essentially for anything else that isn’t specific enough to have its own file like the sections. If it doubt, put it at the bottom of main and it can be moved elsewhere later on. 

_responsiveness.scss is currently used for all responsiveness. 

_utilities.scss contains all of the CSS utility classes that can be used when writing the HTML

### sections
{: .no_toc }

Every section should have its own partial file.

These will then be compiled into separate css files in assets. Each section file will have to be included at the top of a section file

The sections files are separated out, and so if you want to make use of mixins, remember to include the _mixins file at the top of the section SCSS file


## JS Files

The Javascript files are organised like this:

```
├── includes
│   ├── javascript
│   │   ├── classes
|   │   │   ├── **.js
│   │   ├── global-custom-elements
|   │   │   ├── **.js
│   │   ├── section-custom-elements
|   │   │   ├── **.js
│   │   ├── sections
|   │   │   ├── **.js
│   │   ├── global.js

```

Files in `classes/` and `global-custom-elements/` will be combined with `global.js` into `javascript-main.js` which is included on every page. Files in `section-custom-elements/` and `sections/` are compiled into separate files which can be included on specific pages/sections.

### classes
Files in this folder will contain classes that **do not** relate to custom elements. For example the `JoyThemeHelper` class, which contains some functions such as `debounce` that can be used in other files.

### global-custom-elements
These files relate to any custom elements that are used on the majority of pages. Examples include the `quantity-input` element. Where possible, use one file per custom element, but combining multiple in one file is also possible if the classes are related.

### section-custom-elements
These files are for any custom elements that are not global. For example, a `collection-filters` element will only need to be loaded on a collection page.

### sections
These files are for general js files for use on particular sections. They might contain classes, but are primarily for setting up the functionality of that particular section

### global.js
This global file contains any functionality that is needed to run on every page.