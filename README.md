# init.css

[![Join the chat at https://gitter.im/kalopsia/element](https://badges.gitter.im/Join%20Chat.svg)](https://gitter.im/kalopsia/element?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge&utm_content=badge) <img align="right" height="340" src="https://pictr.com/images/2017/10/05/6abeaa192022b7adcebbd772fa835d43.jpg">

[**init.css**](http://timfayz.github.io/init.css) is reset stylesheet for those who wants start styling from a blank sheet. The goal of init.css is similar to popular Eric Meyer's [Reset CSS](http://meyerweb.com/eric/tools/css/reset/):

> reduce browser inconsistencies in things like default line heights, margins and font sizes of headings, and so on

However, it also synchronizes vertical rhythm to make sure all elements have consistent line height according to your base `line-height`. **init.css** resets elements so that they looks like ordinary `div` or `span` tags: correct property inheritance, no borders, background, margin etc.

**[Download v1.0.0](https://github.com/timfayz/init.css/archive/master.zip)**


## What does it need for?

init.css arose as a result of developing [SEM methodology](https://github.com/timfayz/SEM) and [elementcss](https://github.com/timfayz/elementcss). The main idea is to style document from a *blank sheet* where HTML tags has no differences in appearance. So you can use much of tags more likely for the *semantic purposes* rather than basis for a particular style. Here are the main purposes:

0. To correct default property inheritance of all elements in accordance with W3C specifications;
0. To bring consistent look of *almost* all HTML elements across different browsers - the same font, font-weight, line-height, no borders, no background etc;
0. To make sure all elements have the same line height;

init.css doesn't use high order selectors (like `input[type="text"]`) to be sure you can overwrite any "defaults" by regular `.class`.

## How it looks like?

[`test.html`](http://timfayz.github.io/init.css) page opened in Firefox 40.0 running on Ubuntu:

1. **Using nothing** (default UA styles) - [screenshot](https://pictr.com/images/2017/10/05/beabb0b1830ffb108c31e6e85651a4f2.png)
2. **Using init.css** - [screenshot](https://pictr.com/images/2017/10/05/013821b3526ff8c4ada7403d84b4df11.png)
3. **Using [Reset CSS 2.0](http://meyerweb.com/eric/tools/css/reset/)** - [screenshot](https://pictr.com/images/2017/10/05/03993af40c239be8d3b1b14f05bccd36.png)
4. **Using [Normalize.css 3.0.2](https://necolas.github.io/normalize.css/)** (for fun :) - [screenshot](https://pictr.com/images/2017/10/05/d7de295cc8867f2aa7e5d9a8cefd6c72.png)

There is no very much difference doing the same in the last versions of Chrome, Opera, Safari and IE.

## Quick start

- Get **init.css**. There are several ways:
  - [Download the latest release](https://github.com/timfayz/init.css/archive/master.zip)
  - Clone the repo: `git clone https://github.com/timfayz/init.css.git`
  - Install with [Bower](http://bower.io/): `bower install init.css`

- Link `init.css` into your `<head>` and place your own stylesheet(s) **after** the file:
```HTML
<!DOCTYPE html>
<html>
<head>
    <meta charset="UTF-8">
    <link rel="stylesheet" href="path-to/init.css">
    <link rel="stylesheet" href="your-styles.css">
    <title></title>
</head>
<body>
...
</body>
</html>
```
- Now you can start to stylize as you want. Optionally, place the following code at the top of your styles. It needs to make sure no elements break you vertical rhythm.
```CSS
/* Here are tags having random `height` values across different browsers.
 * Set them manually to make sure all tags obey to your vertical rhythm
 * preferences, else set to `auto` or remove. As a rule, `height` is based
 * on document's `line-height` value. Rendering is more precise when the
 * resulting value is integer pixel. For example:
 *    Note: 1em = 16px if user didn't touch UA's default `font-size` preference
 *    html { font-size: 1em; line-height: 1.2; }   16*1.2 = 19.2px (wrong)
 *    html { font-size: 1em; line-height: 1.25; }  16*1.25 = 20px  (correct)
 *    img, textarea { height: 2.5rem; } (or 1.25rem, 3.75rem, 20px,40px etc)
 *
 * To calculate integer-pixel divide a required value by 16: 19px/16 = 1,1875
 */

html {
  box-sizing: border-box;
  -moz-box-sizing: border-box;
  font-size: 1em;
  line-height: 1.25;
}

img, iframe, object, svg,
input, textarea, select, progress, keygen, meter {
  height: 1.25rem;
}

video, audio, select[multiple] {
  height: 2.5rem;
}
```
## How it works?
Here are the main steps of what init.css actually do. The sequence is the same as in source code:

0. **HTML5 display correction**. It corrects the displaying of the new HTML5 tags across different browsers.
0. **Normalize**. It normalize each group of tag and makes UA (User agent) styles consistent across different browsers.
0. **Reset**. It leads a look of each tag to uniform state - the same font, color, line-height etc.

So here are the short samples of each step from the source code:
```CSS
/* ==========================================================================
   1. HTML5 display correction
   ========================================================================== */
...
article,
aside,
details,
figcaption,
figure,
footer,
header,
main,
menu,
nav,
section,
summary {
  display: block;
}
...

/* ==========================================================================
   2. Normalize
   ========================================================================== */
/*
 * We don't apply `border-box` model by default. `inherit` value gives easier way to
 * change the box-sizing in plugins or other components that leverage other behavior.
 */
*, *:before, *:after {
  -moz-box-sizing: inherit;
  -webkit-box-sizing: inherit;
  box-sizing: inherit;
}

/* Correct Windows 8 Metro split-screen snapping with IE10 */
@-ms-viewport{
  width: device-width;
}

/* Make sure editable elements brings up the keyboard in iOS7 WebKit. */
input,
textarea,
[contenteditable] {
  -webkit-user-select: text;
  user-select: text;
}
...

/* ==========================================================================
   3. Reset
   ========================================================================== */
..., form, label,
input, button, select, ...
{
  margin: 0;
  padding: 0;
  border: 0;
  color: inherit;
  font: inherit;
  cursor: inherit;
}

/* Reset `white-space` from `pre` to `inherit` for button-like inputs in WebKit, Firefox */
[type="submit"],
[type="reset"],
[type="button"] {
  white-space: inherit;
}

/*
 * Reset displaying an element using a platform-native styling based on the users'
 * operating system's theme.
 */
button, select {
  -webkit-appearance: none;
  -moz-appearance: none;
  appearance: none;
}
...
```
init.css is based on two main projects: [Normalize.css](https://necolas.github.io/normalize.css/) and [Reset CSS](http://meyerweb.com/eric/tools/css/reset/). However it's not just a copy-paste, but reconstruction, mix and much of additions.

## Browser Support

Note that Firefox and IE page layout rendering havn't perfect-pixel precise. So if you try to get "perfect-pixel" vertical rhythm you may see some tiny element displacement. Zooming page gives better precise.

![Chrome](https://raw.github.com/alrra/browser-logos/master/chrome/chrome_48x48.png) | ![Firefox](https://raw.github.com/alrra/browser-logos/master/firefox/firefox_48x48.png) | ![IE](https://raw.github.com/alrra/browser-logos/master/internet-explorer/internet-explorer_48x48.png) | ![Opera](https://raw.github.com/alrra/browser-logos/master/opera/opera_48x48.png) | ![Safari](https://raw.github.com/alrra/browser-logos/master/safari/safari_48x48.png)
--- | --- | --- | --- | --- |
Latest ✔ | Latest ✔ | 9+ ✔ | Latest ✔ | 5.1+ ✔ |

## License

Copyright (c) 2015 init.css Timur Fayzrakhmanov

Licensed under the MIT License
