## Using Business and Location data

In your theme html

	{{ vertical.street }}
	{{ vertical.city }}, {{ vertical.state }} {{ vertical.postal_code }}
	{{ vertical.phone }}

## Color Picker

	<input type="text" id="header_border_color" name="header_border_color" class="color" value="#cccccc" />

## Resizable Logo

This should be placed outside of the `<table>` in your settings html

	<input type="hidden" id="logo_width" name="logo_width" class="text" value="" data-max-width="250" />
	
You will still want to set a max width in the CSS for the logo

	#logoimg {
		max-width: 250px;
	}

## Logo Font Size

This should be placed outside of the `<table>` in your settings html

	<input type="hidden" id="logo_font_size" name="logo_font_size" class="text" value="34px" data-font-size-max="50" data-font-size-min="12" data-font-size-unit="px" />

You should have references in your CSS. Usually it is a good idea to also set the `line-height`

	#logotext {
		font-size: {{ settings.logo_font_size }};
		line-height: {{ settings.logo_font_size }};
	}

## Regular Image

    <input type="file" id="id_background_image" name="background_image" data-file-type="image" />

## Cropable Image

Example of specific width, but flexible height

	<input type="file" name="custom_hero" data-file-type="image" data-width="925" />

Example of specific width and height
	
	<input type="file" name="custom_hero" data-file-type="image" data-width="900" data-height="300" />