## Blocks

----

A block element is composed of 3 files:
- `form.config.json` - The configuration file used to generate the form in the editor
- `module.html.twig` - The template file used to render the block on the website
- `screenshot.png` - The screenshot used to display the block preview in the editor block list

---

### form.config.json

The `form.config.json` file is used to generate the form in the editor. It is composed of an array of objects, each object representing a type of input in the form.

For every field, the `name` key will allow you to access the data in the twig component.

i.e. :
```json
[
  {
    "label": "Titre",
    "name": "title",
    "type": "text",
    "required": true,
    "design": {
      "col": "6"
    }
  },
  {
    "label": "Type",
    "name": "type",
    "type": "select",
    "required": true,
    "options": [
      { "value": "h1", "label": "H1" },
      { "value": "h2", "label": "H2" },
      { "value": "h3", "label": "H3" },
      { "value": "h4", "label": "H4" },
      { "value": "h4", "label": "H4" },
      { "value": "h5", "label": "H5" },
      { "value": "h6", "label": "H6" }
    ],
    "design": {
      "col": "6"
    }
  }
]
```

Render:<br />
![img.png](assets/img/img.png)

Every field object has the following base schema, every key in red is required, the rest is optional.
<pre>
{
    <b style="color: indianred">label</b>: string, 
    <b style="color: indianred">name</b>: string,
    <b style="color: indianred">type</b>: 'text' | 'textarea' | 'select' | 'btn' | 'file' | 'editor' | 'switch' | 'checkbox' | 'radio' | 'repeatable' | 'icon',
    <b style="color: indianred">required</b>: boolean,
    design: {
        col: string (i.e "6")
    }
}
</pre>

The design key is used to handle the form layout in the editor. The `col` key is used to define the width of the field in the editor. 
The value is a string representing the number of columns the field should take in the editor. 
The value should be between 1 and 12, as the layout is based on a 12 width grid.<br />
This key is available on every field type.

### Field types

#### Text

```json
{
    "label": "Titre",
    "name": "title",
    "type": "text",
    "required": true,
    "design": {
      "col": "6"
    }
}
```
![img_1.png](assets/img/img_1.png)

#### Select

In this example, the select is used to define the heading level of the title. The `options` key is used to define the available options in the select.

```json
{
    "label": "Type",
    "name": "type",
    "type": "select",
    "required": true,
    "options": [
      { "value": "h1", "label": "H1" },
      { "value": "h2", "label": "H2" },
      { "value": "h3", "label": "H3" },
      { "value": "h4", "label": "H4" },
      { "value": "h4", "label": "H4" },
      { "value": "h5", "label": "H5" },
      { "value": "h6", "label": "H6" }
    ],
    "design": {
      "col": "6"
    }
  }
```
![img_2.png](assets/img/img_2.png)

#### Textarea

```json
{
    "label": "Description",
    "name": "description",
    "type": "textarea",
    "required": true,
    "design": {
      "col": "12"
    }
}
```
![img_4.png](assets/img/img_4.png)

#### Btn

This field type will automatically generate a form with the following options:
 - Label
 - Link
 - A checkbox to define if the link should open in a new tab or not

```json
{
    "label": "Button",
    "name": "btn",
    "type": "btn",
    "required": true,
    "design": {
      "col": "12"
    }
}
```
![img_5.png](assets/img/img_5.png)

#### File

```json
{
    "label": "File",
    "name": "file",
    "type": "file",
    "required": true,
    "design": {
      "col": "12"
    }
}
```
![img_6.png](assets/img/img_6.png)

#### Editor

This field will generate a WYSIWYG editor in the form.

```json
{
    "label": "Content",
    "name": "content",
    "type": "editor",
    "required": true,
    "design": {
      "col": "12"
    }
}
```
![img_7.png](assets/img/img_7.png)

#### Switch

This field will generate a switch in the form.

```json
{
    "label": "Switch",
    "name": "switch",
    "type": "switch",
    "required": true,
    "design": {
      "col": "12"
    }
}
```

![img_8.png](assets/img/img_8.png)

#### Checkbox

This field will generate a checkbox in the form.<br />
The `options` key is used to define the available options for the checkboxes.

```json
{
    "label": "Checkbox",
    "name": "checkbox",
    "type": "checkbox",
    "required": true,
    "options": [
        { "value": "1", "label": "Value 1" },
        { "value": "2", "label": "Value 2" },
        { "value": "3", "label": "Value 3" },
        { "value": "4", "label": "Value 4" }
    ],
    "design": {
      "col": "12"
    }
}
```

![img_9.png](assets/img/img_9.png)

#### Radio

This field will generate a radio input in the form.<br />
The `options` key is used to define the available options for the radio.

```json
{
    "label": "Radio",
    "name": "radio",
    "type": "radio",
    "required": true,
    "options": [
        { "value": "1", "label": "Value 1" },
        { "value": "2", "label": "Value 2" },
        { "value": "3", "label": "Value 3" },
        { "value": "4", "label": "Value 4" }
    ],
    "design": {
      "col": "12"
    }
}
```
![img_10.png](assets/img/img_10.png)


#### Icon

This field will generate a select input with all the available icons in the form.<br />

```json
{
    "label": "Icon",
    "name": "icon",
    "type": "icon",
    "required": true,
    "design": {
      "col": "12"
    }
}
```
![img_11.png](assets/img/img_11.png)<br />
![img_12.png](assets/img/img_12.png)

#### Repeatable

This field will generate a repeatable field in the form.<br />
Repeatables are used to create a list of fields that can be repeated as many times as needed.<br />
Repeatables are not meant to be nested, and therefor can't be used inside another repeatable.<br />

```json
{
        "label": "Repeatable",
        "name": "repeatable",
        "type": "repeatable",
        "required": true,
        "schema": [
            {
                "label": "Titre",
                "name": "title",
                "type": "text",
                "required": true
            },
            {
                "label": "Editor",
                "name": "editor",
                "type": "editor",
                "required": true,
                "design": {
                    "col": "12"
                }
            },
            {
                "label": "Switch",
                "name": "switch",
                "type": "switch",
                "required": true,
                "design": {
                    "col": "12"
                }
            }
        ]
    }
```
![img_13.png](assets/img/img_13.png)<br />
![img_14.png](assets/img/img_14.png)

---


### module.html.twig

The `module.html.twig` file is used to render the module on the front of your site.<br />

The templating is handled by the [Twig](https://twig.symfony.com/) templating engine.<br />

If your module requires it, you can embed the needed styles and scripts in the `module.html.twig` file,
in their respective `<style>` and `<script>` tags.<br />

The `module.html.twig` file has access to the following variables:
- `content`: The content of the module, as defined in the `form.config.json`. For example, if you have a `title` field in your form, you can access it in the `module.html.twig` file by using `{{ content.title }}`. 
<br />
- `id`: The id of the module. This is used to identify the module in the DOM, and to make sure that the module is unique on the page. This id is automatically generated by the module builder, and is unique for each module on the page.

Example twig:
```html
<style></style>
<section data-module="card-1" data-module-id="{{ id }}">
    <div class="card-1-wrapper">
        <div class="card-1-header">
            <div class="card-1-header-title-container">
                {% if content.tagline is defined and content.tagline is not empty %}
                    <p class="card-1-header-tagline">{{ content.tagline }}</p>
                {% endif %}
                <{{ content.type }} class="card-1-header-title">{{ content.title }}</{{ content.type }}>
            </div>
            <div class="card-1-header-description">{{ content.paragraph|raw }}</div>
        </div>
        <div class="card-1-elements-container">
            {% if content.repeatable is defined and content.repeatable|length > 0 %}
                {% for card in content.repeatable %}
                    <div class="card-1-element-wrapper">
                        <img class="card-1-element-image" src="{{ basePathMedia }}{{ card.file }}" alt="">
                        <p class="card-1-element-legend">{{ card.subtitle }}</p>
                        <p class="card-1-element-title">{{ card.title }}</p>
                    </div>
                {% endfor %}
            {% endif %}
        </div>
    </div>
</section>
<script></script>
```

The `data-module` attribute on your first section can be used to scope your styles and scripts to the module.<br />

---

### screenshot.png

<br />
Pretty self explanatory, this file is used to display a preview of your module in the editor, in the block list.<br />
For best results, it is advised to use a 16/9 aspect ratio image.<br />