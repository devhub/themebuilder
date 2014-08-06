## Setting Site Widths with Custom CSS

Previously a lot of the themes had set widths that were not configurable within the style settings. This required the production team to write custom CSS to set widths on the header/body. Now with the Master Theme, it has a "Site Width" option within the style controls. This should be used in preference of the custom CSS, as it will correctly handle the responsive styles for you on the mobile views.

## Reseting Static Widths in Responsive

If you decide to set static widths on elements within the navigation, content area, or header using custom CSS, you need to make sure that you also add responsive styles to set these back to "width:auto" or "width:100%" on the mobile view.

Here is the CSS media query we normally use for mobile responsive styling:

	@media only screen and (max-width: 700px) {...}

## Learning the DOM

The Master Theme and future themes that will be created based on the Master Theme all share a common codebase as it relates to the HTML structure of the main elements (header, footer, body, etc)

After you gain experience working and styling the Master Theme, you will be able to understand which style controls control which elements, and which CSS selectors to use to accomplish particular custom CSS.

## Layout Options

We pretty much have 3 different layout configurations for each of the main elements (Header, Body, Footer, Slider)

![Master Theme Layouts](https://cloud.githubusercontent.com/assets/1208/3831373/cfd1470e-1d92-11e4-9486-86632bc39199.png)

* Static
 * More of a traditional website feel
 * Static width element that is centered
 * The Site's Background Color which show on the left/right side
 * Width is configured with the "Site Width" setting
* Inner-static
 * Used for more modern designs, Inner-static header works great with responsive layouts
 * Contains a static width element that is centered, but that is contained within a fluid/100% width element that contains a configurable Background Color (i.e. "Header Background Color")
 * Width of the inner-element is based on the "Site Width"
* Fluid
 * Mainly used for the header and Slider elements
 * This element stretches 100% of the width of the page
 * The "Site Width" setting is ignored here

## Requesting New Master Theme Features

As you add custom CSS to style various parts of the sites, if there are particular things you do frequently (i.e. adding a background image to the header), feel free to let our team know so we can make sure to add that option to our list of features to add to the Master Theme.
