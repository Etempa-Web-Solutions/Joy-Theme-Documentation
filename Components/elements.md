---
title: Elements
layout: default
nav_order: 1
parent: Components
---

# Elements
{: .no_toc }

**Elements** refers to the smallest components in the theme. For example, buttons or form fields.

In some cases, these elements are basic HTML elements with specific classess applied. In others, there may be one or two more syntactical/structural additions.

1. TOC
{:toc}

## Buttons

The primary button style is:

```html
<button class='button' type='button'>Button Text</button>
```

For a secondary style:

```html
<button class='button button_secondary' type='button'>Button Text</button>
```

Links can be styled as buttons:
```html
<a class='button' href='/'>Link Text</a>
```


Additional styles can be found in the table below:

| Class | Function |
|--- | --- |
| `.button` | Sets up button styling. Defaults to 'primary' colours
| `.button_secondary` | Adds secondary colours
| `.button_tertiary` | Adds tertiary colours
| `.button_large` | Large version of button
| `.disabled [disabled]] or [aria-disabled='true']` | Disabled button, no pointer-events
| `.no_hover_style` | Remove hover styles

### Button Loading State
{: .no_toc }

Use the following markup for buttons with a loading state:

```html
<button-loading-container 
    data-loading-text='Loading'
    data-loading-text-visible='true'
    data-finished-text='Finished'
    data-reset-timer='2000'
    data-prevent-double-click='false'
>
    <button class='button' type='button'>
        <span class='button_text'>Loading Button</span>
        {% raw %}{% render 'loading_spinner' %}{% endraw%}
    </button>
</button-loading-container>
```

The `button-loading-container` element will handle the loading state of the button, with the option to add loading text, and finished state text. Using this element will mean that the loading state remains accessible while loading. You can also use it to stop repeat clicks on a 'loading' button. You can customise the behaviour with data attributes.

| Attributes | Function |
|--- | --- |
| `data-loading-text` | Sets the text for the loading state
| `data-loading-text-visible` | Sets whether the loading text will be visible. If 'false', the text will be only be accessible by screen readers. Default: false
| `data-finished-text` | Optionally add a message to display when the process has finished
| `data-reset-timer` | Set the time in ms for the 'Finished' message to display. Default: 4000
| `data-prevent-double-click` | When true, this will prevent the button from being clicked whilst it is in the loading state. Default: true

**Note** The 'loading_spinner' is a liquid snippet in the theme, and is required to be added to the button.

#### Button loading API
{: .no_toc }

To set the button to its loading state:

```js
    let button = document.querySelector('.button')
    let buttonLoader = button.closest('button-loading-container')
    buttonLoader.loading = true
```

You can also pass in a callback so that the element will keep track (and optionally reject) any additional clicks

```js
    let button = document.querySelector('.button')
    let buttonLoader = button.closest('button-loading-container')
    buttonLoader.addEventHandler('click', () => {
        //do something
    })

```

### Button With Icon
{: .no_toc }

Use the following markup for a button with an icon:

```html
<button class='button button_with_icon'>
    <span class='button_text'>Button with icon</span>
    {% raw %}{% render 'icon-arrow-right' %}{% endraw %}
</button>
```

### Icon Button
{: .no_toc }

Use the following markup for an icon button:

```html
<button class='button icon_button no_bg no_border'>
    <span class='visually_hidden'>Search</span>
    {% raw %}{% render 'icon-search' %}{% endraw %}
</button>
```

The classess `no_bg` and `no_border` remove the background and border respectively. Otherwise, all other button styles can be used


## Text Elements

Where possible, use appropriate heading types for the heading that you need. However, sometimes you need to make something look like a different heading level, in which case you can use classes: `.h0` - `.h6` Where `.h0` is the largest size.

Section headings can be defined by using `.section_heading` which will remove the top margin of the heading.

### Text Container

Using the class `.text_content_container` will add a small amount of padding as well as adding the `text_content_container` mixin (meaning the margins are tidied up around the first and last elements). If you need any extra padding, or no padding at all then these can be added as classes (e.g. `.no_padding`)