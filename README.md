# hover.css

A collection of CSS3 powered hover effects to be applied to links, buttons, logos, SVG, featured images and so on. Easily apply to your own elements, modify or just use for inspiration. Available in CSS and SASS.

[Demo](http://ianlunn.github.io/Hover)  |
[Tutorial](http://ianlunn.co.uk/articles/hover-css-tutorial-introduction/)

## How To Use
hover.css can be used in a number of ways; either copy and paste the effect you'd like to use in your own stylesheet or reference the stylesheet. Then just add the class name of the effect to the element you'd like it applied to.

###Copy and Paste an Effect
If you plan on only using one or several effects, it's better practice to copy and paste an effect into your own stylesheet, so a user doesn't have to download hover.css in its entirety.

Assuming you want to use the `Grow` effect:

1. Download hover.css
2. In hover.css, find the 'Grow' CSS (each effect is named using a comment above it):

    ```css
    /* Grow */

    .hvr-grow {
      -webkit-transition-duration: 0.3s;
      transition-duration: 0.3s;
      -webkit-transition-property: -webkit-transform;
      transition-property: transform;
      -webkit-tap-highlight-color: rgba(0, 0, 0, 0);
      -webkit-transform: translateZ(0);
      -ms-transform: translateZ(0);
      transform: translateZ(0);
      box-shadow: 0 0 1px rgba(0, 0, 0, 0);
    }

    .hvr-grow:hover {
      -webkit-transform: scale(1.1);
      -ms-transform: scale(1.1);
      transform: scale(1.1);
    }
    ```
3. Copy this effect and then paste it into your own stylesheet.
4. In the HTML file which you'd like the effect to appear, add the class of `.hvr-grow` to your chosen element.

Example element before applying hover.css effect:

```html
<a href="#">Add to Basket</a>
```

Example element after applying hover.css effect:

```html
<a href="#" class="hvr-grow">Add to Basket</a>
```

Note: As of 2.0.0 all hover.css class names are prefixed with `hvr-` to prevent conflicts with other libraries/stylesheets. If using SASS, this can easily be changed using the `$nameSpace` variable in `scss/_options.scss`.

### Reference hover.css

If you plan on using many hover.css effects, you may like to reference the entire hover.css stylesheet.

1. Download `hover-min.css`
2. Add `hover-min.css` to your websites files, in a directory named `css` for example
3. Reference `hover-min.css` in `<head>` of the HTML page you'd like to add hover.css effects to:
```html
<head>
	<link href="css/hover-min.css" rel="stylesheet">
</head>
```
4. Assuming you want to use the 'Grow' effect, in the HTML file you'd like to use this effect, add the class of `.hvr-grow` to your chosen element.

Example element before applying hover.css effect:

```html
<a href="#" class="button">Add to Basket</a>
```

Example element after applying hover.css effect:

```html
<a href="#" class="button hvr-grow">Add to Basket</a>
```

### A Note on the `display` Property

To make an element "transformable", hover.css  gives the following to all elements it is applied to:

```css
display: inline-block;
vertical-align: middle;
```

Should you wish to override this behavior, either remove the above CSS from hover.css or change the `display` property for the element. Be sure to declare the override after the hover.css declarations so the CSS cascade will take effect. Alternatively, if you are using the SASS version of hover.css, you can remove/comment out the `forceBlockLevel()` mixin found in `scss/_hacks.scss`.

For more information about Transformable elements, see the [CSS Transforms Module](http://www.w3.org/TR/css3-transforms/#transformable-element).

## What's Included?

The project consists of the following folders and files:

### css

- **demo-page.css** - Contains styles to demonstrate Hover. Not required in your projects
- **hover-min.css** - The minified/production version of hover.css
- **hover.css** - The development version of hover.css

### scss

- **effects** - Contains each individual effect sorted into categorized folders
- **_hacks.scss, _mixins.scss, _options.scss** - SASS Utilities
- **hover.scss** - Development/SCSS version of hover.css

### Other

Other files of note include:

- **index.html** - Demonstrates all hover.css effects
- **Gruntfile.js** - Used for [development of hover.css via Grunt](#using-grunt-for-development).

## Browser Support
Many hover.css effects rely on CSS3 features such as transitions, animations, transforms and pseudo-elements, for that reason, effects may not fully work in older browsers.

- [Transitions](http://caniuse.com/#search=transitions) and [Animations](http://caniuse.com/#search=animations) - not supported below Internet Explorer 9
- [Transforms](http://caniuse.com/#search=transforms) - not supported below Internet Explorer 10
- [Generated Content (pseudo-elements)](http://caniuse.com/#search=pseudo-elements) - not supported below Internet Explorer 8

Aside from the above mentioned browsers, hover.css is supported across all major browsers. Please see [caniuse.com](http://caniuse.com/) for full support for many web technologies and test your webpages accordingly. It is recommended to apply fallback effects for older browsers, using CSS supported by those browsers or a feature testing library such as [Modernizr](http://modernizr.com/).

## Using Grunt for Development

Grunt is non-essential but can speed up development. With [Grunt installed](http://gruntjs.com/getting-started), run `grunt` from the command line to set up a development server accessed at [http://127.0.0.1:8000/](http://127.0.0.1:8000/). With Grunt running, SASS will be preprocessed and CSS files will be minified.

**Note:** Originally Grunt was set up to autoprefix CSS properties but to make the project as accessible as possible, this is no longer the case. The `prefixed(property, value)` SASS mixin should be used for browser prefixing instead. See [Using SASS for Development](#using-sass-for-development).

## Using SASS for Development

SASS is non-essential but can speed up development. Preprocess SASS with your favourite software or the environment provided via [Grunt](#using-grunt-for-development).

SASS is used in the hover.css project to separate various CSS into specific files. Each effect is within its own file in the `effects` directory. hover.css also uses the following `.scss` files:

### _hacks.scss
Contains some hacks applied to certain effects. [Hacks explained here](https://github.com/IanLunn/Hover/wiki/Hacks-Explained).

### _mixins.scss
Contains `prefixed(property, value)` and `keyframes(keyframe-name)` mixins that apply the necessary prefixes you specify in `_options.scss` to properties and keyframes.

`prefixed(property, value)` can be used like so:

```
@include prefixed(transition-duration, .3s);
```

The `prefixed(property, value)` mixin is passed the property you want to prefix, followed by its value.

`keyframes(keyframe-name)` can be used like so:

```
@include keyframes(my-animation) {
  to {
    color: red;
  }
}
```

The `keyframes(keyframe-name)` mixin is passed the keyframe name, followed by the content of your keyframe within parenthesis `{}`.

### _options.scss
Contains default options, various effect options and the browser prefixes you'd like to use with the `prefixed()` mixin. By default, only the `-webkit-` prefix is set to `true` (due to most browsers not requiring prefixes now).

As of 2.0.0, `_options.scss` also includes a `$nameSpace` option which allows you to change the name all classes are prefixed with. The default namespace is `hvr`.

## License
hover.css is open source, and made available under a [MIT License](http://www.opensource.org/licenses/mit-license.php). Distribute, use as-is, or modify to your liking in personal and commercial projects. Please retain the original readme and license files.

Retaining the author information at the top of `hover.css` and placing it on your credits page or humans.txt is much appreciated.

## Hire Ian Lunn

[Ian Lunn](http://ianlunn.co.uk) is a Freelance Front-end Developer and author of [CSS3 Foundations](http://css3foundations.com/).

Hire [Ian](http://ianlunn.co.uk) for responsive websites, WordPress websites, animation, and optimization.

## Support Future Development

To support the future development of hover.css and other open source projects created by [Ian Lunn](https://github.com/IanLunn), please consider making a donation.

Your donation is not-for-profit (or beer!), and will allow Ian to spend a little less time on client projects and more time supporting and creating open source software.

Thank you.

**Bitcoin:**

Bitcoin donations may be sent to the following address:

<div style="text-align: center;">
<a href="bitcoin:1KEbFvcXL8m6LogG2wjSUFz2xH6PeN6jRd?label=hover.css%20Development"><img src="http://ianlunn.co.uk/images/btc-donate.jpg" /></a>
<p>1KEbFvcXL8m6LogG2wjSUFz2xH6PeN6jRd</p>
</div>
