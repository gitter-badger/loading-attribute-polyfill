# loading="lazy" attribute polyfill

[![MIT license](https://img.shields.io/npm/l/loading-attribute-polyfill.svg "license badge")](https://opensource.org/licenses/mit-license.php)
[![loading-attribute-polyfill on Npmjs](https://img.shields.io/npm/v/loading-attribute-polyfill.svg "npm version")](https://npmjs.com/package/loading-attribute-polyfill "loading=\"lazy\"-attribute polyfill – on NPM")
[![Total downloads ~ Npmjs](https://img.shields.io/npm/dt/loading-attribute-polyfill.svg "Count of total downloads – NPM")](https://npmjs.com/package/loading-attribute-polyfill "loading=\"lazy\"-attribute polyfill – on NPM")
[![jsDelivr CDN downloads](https://data.jsdelivr.com/v1/package/npm/loading-attribute-polyfill/badge "Count of total downloads – jsDelivr")](https://www.jsdelivr.com/package/npm/loading-attribute-polyfill "loading-attribute polyfill – on jsDelivr")
[![Codacy Badge](https://api.codacy.com/project/badge/Grade/16c763924903400ca82cfed618a82a6e)](https://app.codacy.com/app/mfranzke_2/loading-attribute-polyfill?utm_source=github.com&utm_medium=referral&utm_content=mfranzke/loading-attribute-polyfill&utm_campaign=Badge_Grade_Dashboard)
[![dependencies Status](https://david-dm.org/mfranzke/loading-attribute-polyfill/status.svg "Count of dependencies")](https://david-dm.org/mfranzke/loading-attribute-polyfill "loading-attribute polyfill – on david-dm")
[![code style: prettier](https://img.shields.io/badge/code_style-prettier-ff69b4.svg?style=flat-square)](https://github.com/prettier/prettier)
[![XO code style](https://img.shields.io/badge/code_style-XO-5ed9c7.svg)](https://github.com/xojs/xo)
[![Conventional Commits](https://img.shields.io/badge/Conventional%20Commits-1.0.0-yellow.svg)](https://conventionalcommits.org)
[![Greenkeeper badge](https://badges.greenkeeper.io/mfranzke/loading-attribute-polyfill.svg)](https://greenkeeper.io/)

Fast and lightweight vanilla JavaScript polyfill for native lazy loading, meaning the behaviour to load elements right before they enter the viewport. Provides graceful degradation, and is - not just thatfor - SEO friendly. Handles images with `srcset` and within `picture`, as well as `iframe` elements. `loading="lazy"` will be a huge improvement for todays web performance challenges, so use and polyfill it today!

- Released under the MIT license
- Made in Germany

## Features

- Web standards: Supports the standard `loading="lazy"` attribute on `image` and `iframe` elements
- Performance: It's based on highly efficient, best practice code.
- SEO & crawlers: The image and iframe contents aren't being hidden from crawlers that aren't capable of scrolling.

## Core concepts

The polyfill was designed with the following concepts kept in mind:

- dependency-free
- Using JavaScript with graceful degradation

## Installation

Just integrate the JavaScript file into your code - et voilà.

You may optionally load via NPM or Bower:

    $ npm install loading-attribute-polyfill
    $ bower install loading-attribute-polyfill

You could even load the polyfill asynchronously: <https://output.jsbin.com/codelib/1>

Afterwards you'll need to wrap all of your `<img>` and `<iframe>` HTML tags that you'd like to lazy load (and thatfor added a `loading="lazy"` attribute as well) by an `<noscript>` HTML tag:

### Simple image

```html
<noscript class="loading-lazy">
	<img
		src="simpleimage.jpg"
		loading="lazy"
		alt=".."
		width="250"
		height="150"
	/>
</noscript>
```

### Image wrapped in a picture tag

```html
<picture>
	<noscript class="loading-lazy">
		<source
			media="(min-width: 40em)"
			srcset="
				simpleimage.huge.jpg 1x,
				simpleimage.huge.2x.jpg 2x
			"
		/>
		<source
			srcset="
				simpleimage.jpg 1x,
				simpleimage.2x.jpg 2x
			"
		/>
		<img
			src="simpleimage.jpg"
			loading="lazy"
			alt=".."
			width="250"
			height="150"
		/>
	</noscript>
</picture>
```

### Image with `srcset`

```html
<noscript class="loading-lazy">
	<img
		src="simpleimage.jpg"
		srcset="
			simpleimage.1024.jpg 1024w,
			simpleimage.640.jpg   640w,
			simpleimage.320.jpg   320w
		"
		sizes="(min-width: 36em) 33.3vw, 100vw"
		alt="A rad wolf"
		loading="lazy"
	/>
</noscript>
```

### Iframe

```html
<noscript class="loading-lazy">
	<iframe
		src="https://player.vimeo.com/video/87110435"
		width="320"
		height="180"
		loading="lazy"
	></iframe>
</noscript>
```

## Optional additional dependencies

In case you'd like to support [older versions of Microsoft EDGE, Microsoft Internet Explorer 11 or Apple Safari up to 12.0](https://caniuse.com/#feat=intersectionobserver), you could (conditionally) load an IntersectionObserver polyfill:

<https://www.npmjs.com/package/intersection-observer>

Nevertheless this polyfill would still work in those browsers without that other polyfill included, but [this small amount of users](<(https://caniuse.com/#feat=intersectionobserver)>) wouldn't totally benefit from the lazy loading functionality - we've at least got you partly covered by using the [Microsoft proprietary lazyloading resource hints](https://caniuse.com/#feat=lazyload).

## API

Nothing really, just plug it in, it ~~will~~ should work out of the box.

## Demo

See the polyfill in action either by downloading / forking this repo and have a look at `demo/index.html`, or at the hosted demo: <https://mfranzke.github.io/loading-attribute-polyfill/demo/>

## Further implementations - Kudos for that

### Wordpress

Nico23 has developed a Wordpress plugin: <https://wordpress.org/plugins/native-lazyload-polyfill/> (which is much better than the one by Google !)

### PHP Twig Extension

@tim-thaler has developed a PHP Twig Extension: <https://github.com/tim-thaler/twig-loading-lazy>

### Craft Twig Loading Lazy plugin

@tim-thaler has even also developed a Craft Twig Loading Lazy plugin: <https://github.com/tim-thaler/craft-twig-loading-lazy>

## Credits

Credits for the initial kickstarter / script to @Sora2455 for better expressing my ideas & concepts and support by @nextgenthemes, @diogoterremoto, @dracos and @Flimm. Thank you very much for that, highly appreciated !

## Tested with

-  Mac
	-  Mac OSX 10.14, Mozilla Firefox 68.0.1 (manually, localhost)
	-  Mac OSX 10.14, Safari 12 (via CrossBrowserTesting)
	-  Mac OSX 10.13, Safari 11 (via CrossBrowserTesting)

-  iOS
	-  iPad 6th Generation Simulator, Mobile Safari 12.0 (via CrossBrowserTesting)
	
-  Windows
	-  Windows 10, Google Chrome / versions latest & latest-1 (via CrossBrowserTesting)
	-  Windows 10, Microsoft EDGE / versions 17, 18 (via CrossBrowserTesting)
	-  Windows 10, Microsoft Internet Explorer / version 11 (via CrossBrowserTesting)

### Big Thanks

Cross-browser testing platform provided by [CrossBrowserTesting](https://crossbrowsertesting.com)

[![CrossBrowserTesting](https://crossbrowsertesting.com/blog/wp-content/uploads/2017/09/cbt-wp-logo.png "CrossBrowserTesting")](https://crossbrowsertesting.com)

## things to keep in mind

- The demo HTML code is meant to be simple
- This polyfill doesn't (so far) provide any functionality for the `loading="eager"` value, as this was released even already, but still seems to be in the measure, learn and improvements phase.

## More information on the standard

- [Specification](https://github.com/whatwg/html/pull/3752)
- [LazyLoad Explainer](https://github.com/scott-little/lazyload)

## Outro

If you're trying out and using my work, feel free to contact me and give me any feedback. I'm curious about how it's gonna be used.

And if you do like this polyfill, please consider even also having a look at the other polyfill we've developed: <https://github.com/mfranzke/datalist-polyfill/>
