---
title: General
layout: home
nav_order: 2
has_children: true
---

# Tech Stack

We will be using the following tech stack for coding our Shopify theme:

- Liquid
- HTML
- CSS
    - SASS
        - Individual SASS files for each section
        - General files split by partials
        - 1 responsive SASS file
    - Locally compiled to minified CSS files
        - critical
        - main
        - css file for each section
- Javascript
    - Object Oriented Javascript
    - Custom Elements

# Working Environment

You will be coding the theme in a local environment using the Shopify CLI. 

The theme will be on a GIT repository with the main master branch representing the current fully working version of the theme, which will be represented on Shopify as the live theme (or main dev theme). 

While working locally, create a new branch and work locally on the new branch using theme serve. Rather than our usual master / develop branches, we will be working with more than just 2 branches. Either name the branch ‘develop-DEVELOPER’ or name the branch after the area of code you are developing such as develop-specific-section-name. 

To keep the branches tidy and to avoid massive merge conflicts, try to limit yourself to one develop branch unless strictly necessary. 

When you have finished your local work, merge your branch with the master branch and delete your branch. 

In the event of any conflicts, please work with the other developer to resolve. 

For help on working with Shopify CLI, git and creating / merging branches into the live theme, see the Team Handbook – Shopify Project Setup. 

## Developing

When running the project for the first time, make sure to run `npm install` to install any of the dependencies in the project

From then on, run `npm start` whenever you start developing. This will run all of the various SASS and JS compilers and put everything in the right place.

You will also need to run `shopify theme dev --store=etempa-joy-theme` to preview your work. You can run this in a separate Terminal tab in order to have both commands running simultaneously


