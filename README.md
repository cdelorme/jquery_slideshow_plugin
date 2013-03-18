
# jQuery Image Slide Show Plugin

Plugin extends jQuery allowing simplified creation.

Attach to an image object and load images from an array of strings or objects.  Objects can override delay for individual images, and be used to load ranges of numbered images with optional prefix and delay overrides.

Features include image pre-loading, smooth faded transitions, and keyboard and mouse controls.

Controls:

- Click to go to next image
- Space to pause or continue
- Arrow keys move forwards and backwards


### Examples:

Basic example using an array of strings, and overriding the default delay:

	$("img").first().ss({
		delay: 3000,
		images: [
			'images/one.png',
			'images/two.png',
			'images/three.png',
			'images/four.png'
		]
	});


Example with delay overrides for one image:

	$("img").first().ss({
		images: [
			'images/one.png',
			{
				image: 'images/two.png',
				delay: 8000
			},
			'images/three.png',
			'images/four.png'
		]
	});


Example using ranges, the prefix and custom delays are optional:

	$("img").first().ss({
		images: [
			{
				range: {
					start: 1,
					end: 12,
					type: '.jpg',
					prefix: 'image',
					delays: {
						number: 1,
						delay: 1000
					}
				},
				delay: 4000
			}
		]
	});


### Missing / Planned Features:

This plugin does not manage image sizes, as ideally they should be controlled through CSS.

Future revisions may feature image size management.
