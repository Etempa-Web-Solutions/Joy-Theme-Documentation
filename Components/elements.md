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

## Form Fields

Form fields such as inputs, selects and textareas **should all have ids with labels associated with them**.

You can organise forms using the Grid or Flex layouts, or write custom css to style specific forms.

To structure a form, you can use a `<div>` with the `.field` class:

```html
<div class='field '>
    <label for="text_input" class='form_label'>Text input</label>
    <input id="text_input" type="text" class='form_input'> 
</div>
```

Labels should have the `.form_label` class.
Standard inputs (text, number, password, email) should have the `.form_input` class.

Text areas should have the `.form_text_area` class, and Selects should have the `.form_select` class.

There are a few ways to customise some ofthe for elements:

### Custom select
{:no_toc}

```html
<div class='field'>      
    <label for="select" class='form_label'>Select</label>
    <div class='select_container'>
        <select id="select" class='form_select'>
        <option value="option-1">Option 1</option>
        <option value="option-2">Option 2</option>
        <option value="option-3">Option 3</option>
        </select>
        {% raw %}{% render 'icon-chevron-down' %}{% endraw %}
    </div>
</div>
```

This will render a select element with a floating icon on the right, in this example a down-facing chevron

### Input list
{:no_toc}

To use an input list, such as for a radio group:

```html
<div class='field'>  
    <fieldset>
        <legend class='form_label'>Radio Options</legend>
        <div class='input_list'>
            <div class='input_list_row'> 
                <input id="option-1" type="radio" name="radio-options" class='form_radio'>
                <label for="option-1" class='form_label'>Option 1</label>
            </div>
            <div class='input_list_row'> 
                <input id="option-2" type="radio" name="radio-options" class='form_radio'>
                <label for="option-2" class='form_label'>Option 2</label>
            </div>
        </div>
    </fieldset>
</div>
```

### Custom checkboxes
{:no_toc}

```html
<div class='field'>  
    <fieldset>
        <legend class='form_label'>Checkbox Options</legend>
        <div class='input_list'>
            <div class='input_list_row custom_checkbox_container'> 
                <input id="option-3" type="checkbox" name="options" class='form_checkbox'>
                <label for="option-3" class='form_label'>Option 1</label>
            </div>
            <div class='input_list_row custom_checkbox_container'> 
                <input id="option-4" type="checkbox" name="options" class='form_checkbox'>
                <label for="option-4" class='form_label'>Option 2</label>
            </div>
        </div>
    </fieldset>
</div>
```
This will replace the standard checkboxes with custom boxes that are filled in with the current primary colour when checked. 

The boxes will scale with font size, so if you want them to be larger, you can increase the font size of the label (or the whole 'field')

### Input with button
{:no_toc}

```html
<div class='field'>
    <label for="email_newsletter" class='form_label'>Email input with button</label>
    <div class='input_with_floating_button'>
        <input id="email_newsletter" placeholder='Enter your email address' type="email" class='form_input'>
        <button type='button' class='button no_bg no_border button_icon'>
            <span class='button_text visually_hidden'>Submit email address</span>
            {% raw %}{% render 'icon-arrow-right' %}{% endraw %}
        </button> 
    </div>
</div> 
```

This will render a text input with a button. The button can be of any of the button styles