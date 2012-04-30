# themebuilder

Example themes for the DevHub platform

Included in this doc:

* Creating a new theme
* The Theme Editor
* Required includes
* Templating variables
* Creating a `settings.html`

***

## Creating a new theme

* Browse to a base theme under "Themes & Colors" and change to it
* Click on "Edit HTML/CSS"

This should now create a new copy of that theme ("Custom Theme") that can be edited without effecting the original theme. You can continue to customize the theme HTML, CSS and settings until the theme is complete.

***

## The Theme Editor

Within the theme editor, there are 3 files that you can edit

* `theme.html` - This is the main HTML surrounding the column controls.
* `style.css` - This is the main CSS style for the theme
* `settings.html` - This is a HTML form that you can use to set user-controllable toggles and options for the theme. By setting default form values here, they will be used as the default values for the `settings.*` variables available in the `theme.html` and `style.css`

***

## Required includes

There are only a few includes that are required for a theme to work properly.

* `{% include "themes/header_content.html" %}` - This needs to be the last item in the head before `</head>`
* `{% include "themes/layout_content.html" %}` - This needs to be inside the `<body>` element wherever you want the column controls to be present
* `{% include "themes/footer_content.html" %}` - This needs to be the last item in the body before `</body>`

***

## Templating variables

Within the `theme.html` and `style.css` you have access to variables that can be used to display or conditionally show/hide elements within the theme.

### `{{ settings.* }}`

These are the theme settings. There are default settings that are defined by the `settings.html` form which are then overridden by any user-configured settings. The names and usage of these settings variables are up to the theme designer.

**Examples:**

* `{{ settings.site_width }}` - Site with in pixels
* `{{ settings.site_background_color }}` - Hex color for the site background (i.e. `#0033bb`)
* `{{ settings.show_search_box }}` - Toggle for showing/hidding the search box

### `{{ site.* }}`

This is the Site object and its attributes

* `{{ site.logo }}` - This is the HTML output for the site's logo. This must be wrapped by an element with `id="sitelogo"` for the logo controls to be visible
* `{{ site.title }}` - Name of the site

### `{{ page.* }}`

This is the current Page object and its attributes

* `{{ page.title }}` - Current page title
* `{{ page.path }}` - Path for the current page (i.e. `/about-us/`)

### `{{ linklists.mainmenu }}`

This is the array of navigation items for the site. It can be iterated to display the navigation. Here is an example of how to output the navigation:

	{% for item in linklists.mainmenu %}
	  <li{% if page.path == item.link %} class="selected"{% endif %}><a href="{{ item.link }}" title="{{ item.name|safe }}">{{ item.name|safe }}</a></li>
	{% endfor %}

***

## Creating a `settings.html`

The `settings.html` is essentially a `<table>` that contains form inputs. The input types that are supported are `input[type=text]`, `input[type=checkbox]`, `input[type=radio]`, `select`, `textarea`

Here is an example of a basic `input[type=text]` entry:

	<tr>
	  <th>
	    <label for="contact_label">Contact form label</label>
	  </th>
	  <td>
	    <input type="text" id="contact_label" name="contact_label" class="text" value="Contact Us" />
	  </td>
	</tr>

You can see that the input has a default value. That value will be used as the default, but will be overiden if the user customizes this string. This variable is accessible in the `theme.html` and `style.css` via `{{ settings.contact_label }}`

### Color controls

This is a special type of input that presents the user with a color picker *(notice the class="color")*

	<input type="text" id="site_background_color" name="site_background_color" class="color" value="#ffffff" />

Here is an example of its usage in the `style.css`

	body {
	    background-color: {{ settings.site_background_color }};
	}

### More examples

You can see more examples of field types you could have within your `settings.html` here: 