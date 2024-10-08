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

## Quantity Input w/buttons

The Quantity input is an input of type `[number]` with two buttons that can be used to increase/decrease the number input. 

It can be rendered in the following way:

```html
{% raw %}
    {% render 'quantity-input'
        min: min,
        value: value,
        max: max,
        label: label,
        decrease_button_label: decrease_button_label,
        increase_button_label: increase_button_label,
        id: id,
        name: name
        data_attributes: data_attributes
    %}
{% endraw %}
```

| Argument | Function |
|--- | --- |
| `min` | minimum value of inout (default: 1)
| `max` |  maximum value of input (optional)
| `value` | default value of input (default: 1)
| `decrease_button_label` | Label for accessibility on decreasing value button
| `increase_button_label` | Label for accessibility on increasing value button
| `label` | input label
| `id` | input id
| `name` | input name
| `data_attributes` | extra attributes for the input

To detect changes in the quantity, you can subscribe to the `change` event on the `quantity-input` object:

```js
const element = 'your element here';
const quantityInput = element.querySelector('quantity-input');
const quantityInputElement = quantityInput.input;
quantityInput.addEventListener('change', e => {
    //do something when it changes

    //access the actual input element
    quantityInputElement.id...
})
```

## Images

Images can be rendered either by using the default image tag, or by using the `image-container-responsive` snippet.

The `image-container-responsive` snippet takes a few arguments:

| Argument | Function |
|--- | --- |
| `aspect_ratio` | 'natural', 'portrait', 'square', 'landscape'
| `default_width` | default width of image (default: image max width)
| `widths` | widths of image to use in srcset
| `lazyload` | true or false (default: true)
| `preload` | true or false (default: false)
| `image` | the image to render
| `container_class` | extra class for container
| `image_class` | extra class list for image

For more information on how to use the widths and sizes variable, see this link <https://performance.shopify.com/pages/liquid-image_tag-demo#fixing-oversized-mobile-images>

In practice, this snippet will be used as follows:

```html{% raw %}
{% assign sizes = '100vw' %}
{% assign widths = '500, 1200, 2400' %}
{% render 'image-container-responsive' image: section.settings.image, aspect_ratio: 'landscape', widths: widths, sizes: sizes, preload: true %}{% endraw %}
```

Using the Shopify default `image_tag` object will ensure that alt tags are added, as well as focal points


## Accordions

There are two **core** types of accordions built-in to the theme: `disclosure`s and `dropdown`s

They can be used interchangeably, and the structure of the code is basically the same.

Accordions make use of the `details/summary` HTML elements. There is also a custom element to wrap around the elements, which will handle some additional behaviour, and accessibility.

```html
<details-disclosure data-auto-close>
    <details class='open_highlight'>
        <summary class='border_standard padding_small'>
            <span>Default disclosure</span>
            <span>{% raw %}{% render 'icon-chevron-down' %}{% endraw %}</span>
        </summary>
        <div id="dropdown-1" class='fade_in padding_small'>Testing</div>
    </details>
</details-disclosure>
```

In this example, the `details-disclosure` wraps around the `details/summary` elements. It has the `data-auto-close` attribute which will mean that when the element loses focus, the dropdown will close.

The `content` of the dropdown is whatever is in the element immediately after the `summary` element. If you give this element an `id`, then the custom element will set up some appropriate aria-labels. 

The icon being rendered by the liquid snippet is optional, and will rotate on open.

In this example, we have also added some additional utility classes for styling, but these could be styled with normal class names, as well

| Class / Attribute | Element | Function |
|--- | --- | --- |
| `data-auto-close` | details-disclosure | Causes the dropdown to autoclose when focus is lost
| `.dropdown` | details | The content will 'float' above other content, and be displayed in a narrow, scrollable box
| `.open_highlight` | details | Will highlight the summary text (and icon) in the current primary colours on open
| `.fade_in` | content | Will cause the content to fade in on open


## Modal / Dialog / Modal Opener

The Modal/Dialog custom element makes use of the `dialog` HTML Element. This element is useful because it is **semantic** (meaning browsers know what type of element it is). It also always renders itself above all other content on the screen, so we don't have to worry about anything with a z-index of 9999999 anymore.

The structure of the modal-dialog element is as this:

```html
<modal-dialog id='example-modal-1'>
    <dialog>
        <div class='relative'>
            <button data-modal-close class='button button_secondary button_icon no_bg no_border close_button'>
                <span>Close Modal</span>
            </button>
        </div>
    </dialog>
</modal-dialog>
```

The `modal-dialog` element should have a unique ID so that it can be opened by a button. If you plan on opening it programmatically, then an ID would still be useful, or you can use a data-attribute to identify it.

The content of the actual `dialog` element is going to depend on what you need to use it for. The `button` element (along with the `data-modal-close` attribute) is important so that the dialog can be closed (though it can also be closed by presseing ESC or clicking outside the modal itself). The `<div class='relative'>` component ensures that the button is positioned in the top right of the modal.

### Styling the modal

The modal will be positioned in the centre of the screen, and will fill 90% of the screens width and a maximum of 95% of the screens height (depending on content). By default, the max-width of the modal will be `750px`, but this can be changed by altering the CSS variable `--dialog-max-width`. This can be done by either adding a class to the `modal-dialog` element and setting the variable inside your class or by adding it directly to the HTML:

```html
<modal-dialog id='example-modal-1' style='--dialog-max-width:500px;'>
    <dialog>
        ...
```

### Modal Opener

The `modal-opener` custom element works in tandem with the modal element. 

``` html
<modal-opener data-modal='#example-modal-1'>
    <button class='button button_with_icon'>
        <span class='button_text'>Open Modal</span>
    </button>
</modal-opener>
```

The `data-modal` attribute takes in the ID of the `modal-dialog` element that you want to open with the button. The button can be any type of button. 

When the modal is closed, focus will be returned to the button that opened it.

### API

You can open and close the modal by using `show()` or `hide()` on the modal-dialog element

```js
const popup = document.querySelector('modal-dialog.my_custom_popup`);
popup.show();

popup.hide();

```