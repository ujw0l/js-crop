<h1 align="center">Welcome to Js Crop 👋</h1>

<p>
  <img src="https://img.shields.io/badge/version-3.0.0-blue.svg?cacheSeconds=2592000" />
  <a href="https://github.com/ujw0l/js-crop#readme">
    <img alt="Documentation" src="https://img.shields.io/badge/documentation-yes-brightgreen.svg" target="_blank" />
  </a>
  <a href="https://github.com/ujw0l/js-crop/graphs/commit-activity">
    <img alt="Maintenance" src="https://img.shields.io/badge/Maintained%3F-yes-green.svg" target="_blank" />
  </a>
  <a href="https://tidelift.com/subscription/pkg/npm-js-crop?utm_source=npm-js-crop&utm_medium=referral&utm_campaign=readme">
    <img alt="License: MIT" src="https://tidelift.com/badges/package/npm/js-crop" target="_blank" />
  </a>
</p>

> Lightweight JavaScript image cropping library with a built-in customizable UI and support for desktop, mobile, and touch devices.

## Features

- Image cropping with built-in UI
- 📱 Mobile and touch device support
- 🖱️ Desktop mouse support
- Touch-based crop movement and interaction
- Customizable UI colors
- JPEG and PNG output
- Configurable image quality
- Custom buttons and callbacks
- No framework required

## Install

```sh
npm i js-crop
```

## Script

```html
<script type="text/javascript" src="src/js-crop.js"></script>
```

Or use the minified version:

```html
<script type="text/javascript" src="src/js-crop.min.js"></script>
```

### CDN

```html
<script src="https://cdn.jsdelivr.net/npm/js-crop@3.0.0/js-crop.min.js"></script>
```

Or automatically use the latest published version:

```html
<script src="https://cdn.jsdelivr.net/npm/js-crop/js-crop.min.js"></script>
```

## Mobile Support

Starting with **Js Crop 3.0**, the crop interface supports mobile and touch-enabled devices.

Users can interact with the cropping interface using touch gestures on phones and tablets while desktop users can continue using mouse controls.

Supported input includes:

- Desktop mouse
- Mobile touch
- Tablets
- Touchscreen devices

No separate mobile version or additional dependency is required.

## Initialize

```js
new jsCrop(
  'selector',
  {
    extButton: {
      buttonText: 'Button Text',
      buttonTitle: 'Button Title',
      buttonCSS: 'your-custom-css',
      callBack: function(blob) {
        // Cropped image blob
      }
    },

    customColor: {
      overlayBgColor: '#000000',
      toolbarBgColor: '#ffffff',
      buttonBgColor: '#333333',
      buttonFontColor: '#ffffff'
    },

    imageType: 'jpeg',
    imageQuality: 1,
    saveButton: true
  },

  [
    {
      buttonText: 'Custom Button',
      buttonTitle: 'Custom Button',
      relParam: 'optional-data',
      buttonEvent: 'click',
      buttonCSS: 'your-custom-css',

      callBack: function(blob, relParam) {
        // blob = cropped image
        // relParam = optional supplied value
      }
    }
  ]
);
```

## Parameters

### Parameter 1 — Selector

**Required**

Selector for one or multiple images or upload controls.

Uses normal JavaScript `querySelector` / `querySelectorAll` selector syntax.

```js
new jsCrop('.crop-image');
```

### Parameter 2 — Options

**Optional**

```js
{
  extButton: {
    buttonText: string,
    buttonTitle: string,
    buttonCSS: string,
    callBack: function
  },

  customColor: {
    overlayBgColor: string,
    toolbarBgColor: string,
    buttonBgColor: string,
    buttonFontColor: string
  },

  imageType: string,
  imageQuality: number,
  saveButton: boolean
}
```

### `extButton`

Optional extension button displayed after the Save Image button.

```js
extButton: {
  buttonText: string,
  buttonTitle: string,
  buttonCSS: string,
  callBack: function
}
```

### `customColor`

Optional UI color customization.

```js
customColor: {
  overlayBgColor: string,
  toolbarBgColor: string,
  buttonBgColor: string,
  buttonFontColor: string
}
```

### `imageType`

Optional output image type.

Supported:

```text
jpeg
png
```

### `imageQuality`

Optional cropped image quality between:

```text
0 and 1
```

Example:

```js
imageQuality: 0.9
```

### `saveButton`

Set to `false` to hide the built-in save button.

```js
saveButton: false
```

## Custom Buttons

The third parameter accepts an array containing one or multiple custom buttons.

```js
[
  {
    buttonText: 'Upload',
    buttonTitle: 'Upload Cropped Image',
    relParam: 'my-data',
    buttonEvent: 'click',
    buttonCSS: 'custom-button-class',

    callBack: function(blob, relParam) {
      console.log(blob);
      console.log(relParam);
    }
  }
]
```

## Contributing

Contributions, issues and feature requests are welcome.

Feel free to check the [issues page](https://github.com/ujw0l/js-crop/issues).

## Author

👤 **ujw0l**

- Twitter 👉 [@bastakotiujwol](https://twitter.com/bastakotiujwol)
- GitHub 👉 [@ujw0l](https://github.com/ujw0l)

## Show Your Support

Please ⭐️ this repository if this project helped you!

<ul>
<li>
<a href="https://www.patreon.com/ujw0l">
  <img src="https://c5.patreon.com/external/logo/become_a_patron_button@2x.png" width="160">
</a>
</li>

<li>
<a href="https://www.buymeacoffee.com/ujw0l" title="Buy me Beer">🍺</a>
</li>

<li>
<a href="https://tidelift.com/subscription/pkg/npm-js-crop?utm_source=npm-js-crop&utm_medium=referral&utm_campaign=readme">
Get supported js-crop with the Tidelift Subscription
</a>
</li>
</ul>

## License

Copyright © 2019 [ujw0l](https://github.com/ujw0l).

📜 This project is [MIT](https://github.com/ujw0l/js-crop/blob/master/LICENSE) licensed.