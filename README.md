
# jQuery Image Slide Show Plugin

Plugin extends jQuery allowing simplified creation by attaching to an html image tag, accepting option overrides and a set of images to load as strings or objects in up to three formats.

Raw strings can be supplied and will use the default or override delay for timing.  Can supply simple objects with string for image name and delay to override delay.  Finally whole ranges can be defined with prefix, type, start and finish, as well as delay overrides.

Built-in preloading as slideshows are defined, smooth faded transitions, and keyboard/mouse controls for desktop machines.

Controls:

- Click to go to next image
- Space to pause or continue
- Arrow keys move forwards and backwards

Made the fading transition optional, simply set it to 0 or false to override.

Implemented multiple named slideshow loading system, allows multiple sets of images (such as for animations) to be loaded separately by name, accepting the same format as the original instantiation process, and allowing instantiation to occur without any images as well.

Two methods to switch between loaded slideshows, one to change immediately and the other to change when the current slideshow set has completed allowing for a smooth transition.


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
					prefix: 'image'
				},
				delay: 4000
			}
		]
	});

Complex example demonstrating empty instantiation, loading multiple named sets, switching on click, and cuing:

	// Create slideshow with no transition
	$("img").first().ss({
		trans: 0
	});

	// Load set one
	ss.addImages('one', [
		'images/one.png',
		'images/two.png',
		'images/three.png',
		'images/four.png',
	]);

	// Load set two
	ss.addImages('two', [
		{
			range: {
				start: 1,
				end: 9,
				prefix: 'images/two',
				type: '.png'
			},
			delay: 40
		}
	]);

	// Start playing set one
	ss.changeNow('one');

	// Cue set two
	ss.changeTo('two');

	// Button event to play set One again
	$('button').on('click', function() {
		ss.changeTo('one');
	});


### Missing / Planned Features:

An optional loop parameter with a default of true to override the system so that the slideshow stops at the end.

Cue system to accept a line of waiting-transitions of loaded slideshows by name for more complex animation implementations.

Mobile controls and interfacing.

Image size controls, ideally these should be controlled through CSS but this may be added as a feature if I need it at some point or upon request.
