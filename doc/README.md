# Adding Custom HTML & CSS to a GitHub Readme

If you're a visual creative (or just visually creative) and hosting projects at GitHub, you've probably found yourself feeling frustrated at some point for the impressive, yet restrictive palette GitHub makes available to you by default.

What if I told you there was a way you could very quickly and easily implement your own custom HTML & CSS in any of your Repository README files!  The trick, is to include a custom SVG file into the mix ...

## Custom CSS & HTML in an SVG File

GitHub has been pretty generous in their implementation of HTML within Markdown, but they aggressively remove anything which might provide the opportunity to be exploited.  Unfortunately, this includes many of the elements you're used to turning to when attempting to create a custom layout.

And this is where SVG charges in to save the day!

There is a technique you can use to display custom HTML & CSS _inside_ an SVG file using the `foreignObject` element, and use the provisions of the file format to render your code for display.  So, let's get on with it ...

First, create a basic SVG file using your preferred editor, and name it something like `display.svg`:

```html
<svg fill="none" viewBox="0 0 600 100" width="600" height="100" xmlns="http://www.w3.org/2000/svg">
	<style>
		.container {
			width: 100%;
			height: 100px;

			display: flex;
			justify-content: center;
			align-items: center;

			color: #ffffdd;
			background-color: black;

			font-family: 'Colonna MT', 'Times New Roman', serif;
			font-size: 13px;
		}
	</style>
	<foreignObject width="100%" height="100%">
		<div xmlns="http://www.w3.org/1999/xhtml">
			<div class="container">
				<h1>YOU CAN EVEN INCLUDE UNICODE EMOJIS 👋</h1>
			</div>
		</div>
	</foreignObject>
</svg>
```

Which will render as:

<img src="../src/svg/display-1.svg" height="100" width="100%" />

I know ... right now you're wondering what all the hype is about (and probably saying something rude about my Mum)

> Oh, ye of little faith and clichéd taunting ... have you so soon forgotten the legendary power of CSS?

Let's add a few keyframes to `display.svg`:

```html
<svg fill="none" viewBox="0 0 600 100" width="600" height="100" xmlns="http://www.w3.org/2000/svg">
	<style>
		@keyframes hi {
			  0% { transform: rotate( 0.0deg) }
			 10% { transform: rotate(14.0deg) }
			 20% { transform: rotate(-8.0deg) }
			 30% { transform: rotate(14.0deg) }
			 40% { transform: rotate(-4.0deg) }
			 50% { transform: rotate(10.0deg) }
			 60% { transform: rotate( 0.0deg) }
			100% { transform: rotate( 0.0deg) }
		}
		.container {
			width: 100%;
			height: 75px;

			display: flex;
			justify-content: center;
			align-items: center;

			color: #ffffdd;
			background-color: black;

			font-family: 'Colonna MT', 'Times New Roman', serif;
			font-size: 13px;
		}
		.hi {
			animation: hi 1.5s linear -0.5s infinite;
			display: inline-block;
			transform-origin: 75% 75%;
		}
		@media (prefers-reduced-motion) {
			.hi { animation: none; }
		}
	</style>
	<foreignObject width="100%" height="100%">
		<div xmlns="http://www.w3.org/1999/xhtml">
			<div class="container">
				<h1>YOU CAN EVEN INCLUDE UNICODE EMOJIS <div class="hi">👋</div></h1>
			</div>
		</div>
	</foreignObject>
</svg>
```

So now we have:

<img src="../src/svg/display-2.svg" height="100" width="100%" />

And by now I hope you're getting the idea that you have almost limitless directions you can go from here.

Below you can find some links to the CSS, SVG and other design resources I find most useful, along with a few of the banners I've created for myself using this technique, and I've left many more interesting trinkets for you to find in the GitHub Repository attached to this article.

## SVG Examples

#### Pre-Release Project:

<img src="../src/svg/pre-release.svg" height="100" width="100%" />

#### Work In Progress:

<img src="../src/svg/wip-banner.svg" height="100" width="100%" />

#### Loading:

<img src="../src/svg/dots-loading.svg" height="100" width="100%" />

## Resources

- [**CSS Gradient Backgrounds @ cssGradient.io**](https://cssgradient.io/gradient-backgrounds/)
- [**Animated CSS Background Demonstrating the Bokeh Effect**](https://codepen.io/Mamboleoo/full/BxMQYQ/)
- [**Various CSS Background Animations**](https://freefrontend.com/css-animated-backgrounds/)
- [**SVG Gradient Wave Generator**](https://www.outpan.com/app/9aaaf27303/svg-gradient-wave-generator)
- [**CSS Animation Generator**](https://animista.net/play/basic)
- [**CSS Drop-ins for Simple Websites**](https://github.com/kognise/water.css)
- [**Augmented UI**](https://augmented-ui.com/)
- [**Retro NES CSS Style Library (because, why not?)**](https://nostalgic-css.github.io/NES.css/)
- [**CSS Clip-Path Generator**](https://bennettfeely.com/clippy/)
