# themebuilder

Example themes for the DevHub platform

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

**Examples:**

* `{{ settings.site_width }}`
* `{{ settings.site_background_color }}`

### `{{ settings.* }}`

These are the theme settings. There are default settings that are defined by the `settings.html` form which are then overridden by any user-configured settings.

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

