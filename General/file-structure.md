---
title: File Structure
layout: default
parent: General
nav_order: 2
---

# File Structure

The file structure will follow the standard Shopify theme structure, with the addition of an includes folder for our SASS and javascript files. **Bear in mind that anything in this includes folder will not be uploaded to Shopify and therefore only files which are being compiled should be put here**. Anything else should go in the assets folder. 

## CSS Files

Any variables go in the _variables.scss file. Mixins go in _mixins.scss. 

You will not need to use _normalise.scss, which has already been setup. 

_elements.scss are for any css styles that are likely to be used in lots of places for example, form, input, select, table. They tend to be selectors for html tags rather than lots of classes and ids. 

_text.scss is like elements but specific for text. You shouldn’t really need to add to this much as I should have most general text styles now but just to be aware. 

_main.scss is essentially for anything else that isn’t specific enough to have its own file like the sections. If it doubt, put it at the bottom of main and it can be moved elsewhere later on. 

_responsiveness.scss is currently used for all responsiveness. 

Every section should have its own partial file.

Make every effort to keep similar styles together or we will be in chaos. If in doubt, ctrl + f to see which file a style is in. 


## CSS Files

The main aim of this site is to avoid writing anything twice.

The css variables.scss file contains css variables. Please add to it. 

Check out and use the mixins where appropriate. Again, please add to it. 

When specifying text styles, you should always use a text element such as h1-h6, p or li to surround text. These text styles will have both the font mixins automatically applied to them. 

If you need to specify another text element for a specific reason, please remember to apply both the font style and font size mixin to the element in CSS. 

To keep font sizes consistent, please use the font_size_ratio mixin with either whole numbers or .5 numbers. In specific circumstances, you can use either .2 or .7, or an actual font-size (mainly for responsiveness) but try to avoid this. Using the mixin means we can re-size the entire theme’s font sizing easily.  

Do not go smaller than 0 unless it’s for a very specific reason. To go smaller than 0, you can use 0.7 (yes 0.7 is larger than 0, but it’s just how maths works in my function). Bear in mind we must not go smaller than 14px anywhere. 

Some more important mixins are display_grid(). You can put the grid-gap as a parameter such as display_grid(60px). It defaults to 20px if you don’t add anything. 

Add @includes text_container_edge_margin_reset() to a div and the top margin of the first element and the bottom margin of the last element will be removed. This is really handy for vertical centring to make sure the box is the right size and not being distorted by additional margins from the text. 

