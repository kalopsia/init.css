#init.css

[![Join the chat at https://gitter.im/kalopsia/element](https://badges.gitter.im/Join%20Chat.svg)](https://gitter.im/kalopsia/element?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge&utm_content=badge) <img align="right" height="300" src="https://dl.dropboxusercontent.com/u/2930233/server/initcss/initcss.png">

**init.css** is reset stylesheet for those who wants start styling from a blank sheet. The goal of init.css is similar to popular Eric Meyer's [Reset CSS](http://meyerweb.com/eric/tools/css/reset/):

> reduce browser inconsistencies in things like default line heights, margins and font sizes of headings, and so on

However, it also synchronizes vertical rhythm to make sure all elements have consistent line height according to document's line-height and reset elements so that they looks like ordinary `div`/`span` tag: correct property inheritance, no borders, background, margin etc.

**[Download v1.0](https://github.com/kalopsia/init.css/archive/master.zip)**

##Install

3. Optionally, you change exoposed CSS properties the tags only affects vertical
   rhtyhm in accordenance with your document's line-height. (see the last section)
Next, place your css file after init.css and start to stylize as you want.

##What does it do?

1. Corrects default property inheritance of all elements in accordance with W3C specifications.
2. Brings consistent look of *almost* all elements across different browsers - the same font, font-weight, line-height, no borders, no background etc.
3. Make sure all elements have the same line height.
3. Doesn't use high order selectors (like `input[type="text"]`) to be sure you can overwrite them by regular `.class`.

##How it looks like?

`initcss.html` page opened in Firefox 40.0a2 running on Ubuntu:

1. Using nothing (default UA styles) - [screenshot](https://dl.dropboxusercontent.com/u/2930233/server/initcss/screenshots/default.png)
2. Using init.css - [screenshot](https://dl.dropboxusercontent.com/u/2930233/server/initcss/screenshots/initcss.png)
3. Using [Reset CSS 2.0](http://meyerweb.com/eric/tools/css/reset/) - [screenshot](https://dl.dropboxusercontent.com/u/2930233/server/initcss/screenshots/resetcss.png)
4. Using [Normalize.css 3.0.2](https://necolas.github.io/normalize.css/) *(for fun :)* - [screenshot](https://dl.dropboxusercontent.com/u/2930233/server/initcss/screenshots/normalizecss.png)

There is no very much difference doing the same in the last versions of Chrome, Opera, Safari and IE.

##How it works?
Here are the main sections of init.css source code in sequence in which it goes in the code flow:

1. Correcting the displaying of new html5 tags across different browsers. Sample from the source:
```CSS
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
```

2. Normalizing each group of tags. It makes UA (User agent) styles consistent across different browsers. Samples from source:
```CSS
...
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
```

3. Resetting each tag group. It leads tags' look to uniform state - the same font, color, line-height etc. Samples from source:
```CSS
...
form, label,
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

##License

Copyright (c) 2015 init.css [Authors]()

Licensed under the MIT License
