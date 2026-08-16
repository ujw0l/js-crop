<h1 align="center">js-crop</h1>

<p align="center">
  <a href="https://www.npmjs.com/package/js-crop">
    <img alt="npm version" src="https://img.shields.io/npm/v/js-crop.svg" />
  </a>
  <a href="https://github.com/ujw0l/js-crop#readme">
    <img alt="Documentation" src="https://img.shields.io/badge/documentation-yes-brightgreen.svg" />
  </a>
  <a href="https://github.com/ujw0l/js-crop/graphs/commit-activity">
    <img alt="Maintenance" src="https://img.shields.io/badge/Maintained%3F-yes-green.svg" />
  </a>
  <a href="https://github.com/ujw0l/js-crop/blob/master/LICENSE">
    <img alt="License: MIT" src="https://img.shields.io/badge/license-MIT-yellow.svg" />
  </a>
</p>

> A lightweight, dependency-free image cropper with a responsive built-in UI for mouse, touch, and keyboard input.

## Features

- Works with existing `<img>` elements and `<input type="file">` controls
- Responsive editor for desktop, mobile, tablets, and touchscreens
- Resizable crop selection with undo, redo, and reset controls
- JPEG and PNG output with configurable quality
- Built-in download button and custom callback buttons
- Customizable overlay, toolbar, and button colors
- No framework or runtime dependency

## Install

```sh
npm install js-crop
```

### Browser script

Load the minified file from a CDN. The constructor is exposed as `window.jsCrop`.

```html
<script src="https://cdn.jsdelivr.net/npm/js-crop@3.1.2/js-crop.min.js"></script>
```

To follow the latest published version instead of pinning a release:

```html
<script src="https://cdn.jsdelivr.net/npm/js-crop/js-crop.min.js"></script>
```

You can also serve `node_modules/js-crop/js-crop.min.js` from your own application.

### CommonJS

```js
const jsCrop = require('js-crop');
```

`js-crop` runs in a browser and requires DOM, canvas, `Image`, and `FileReader` APIs. If you bundle it on the server, create an instance only in the browser.

## Quick start

### Crop an uploaded image

```html
<input id="avatar" type="file" accept="image/png,image/jpeg" />

<script src="https://cdn.jsdelivr.net/npm/js-crop@3.1.2/js-crop.min.js"></script>
<script>
  new jsCrop('#avatar', {
    imageType: 'jpeg',
    imageQuality: 0.9,
    extButton: {
      buttonText: 'Use image',
      buttonTitle: 'Use the cropped image',
      callBack: function (dataUrl) {
        document.querySelector('#preview').src = dataUrl;
      }
    }
  });
</script>
```

Selecting a file opens the crop editor automatically.

### Crop an existing image

```html
<img class="crop-image" src="/images/photo.jpg" alt="Select an area to crop" />

<script>
  new jsCrop('.crop-image');
</script>
```

Clicking any matching image opens it in the editor. A selector may match one or many elements.

## API

```js
new jsCrop(selector, options?, customButtons?);
```

Creating an instance attaches listeners to every element that matches `selector`. The constructor returns the cropper instance; normal use does not require storing it.

### `selector`

Type: `string` (required)

Any selector accepted by `document.querySelectorAll()`. Matching elements can be:

- `<input type="file">`: opens the first selected file when the input changes.
- `<img>`: opens the image when it is clicked.
- Another element with a `src` property: opens that source when the element is clicked.

```js
new jsCrop('#profile-photo');
new jsCrop('.croppable');
new jsCrop('input[type="file"][data-crop]');
```

### `options`

Type: `object` (optional)

| Option | Type | Default | Description |
| --- | --- | --- | --- |
| `imageType` | `'png'` or `'jpeg'` | `'png'` | Output format used by downloads and callbacks. Values other than `'jpeg'` fall back to PNG. |
| `imageQuality` | `number` | `1` | Canvas export quality from `0` to `1`. It mainly affects JPEG output. |
| `saveButton` | `boolean` | `true` | Set to `false` to hide the built-in Download image button. |
| `customColor` | `object` | See below | Overrides colors in the editor UI. |
| `extButton` | `object` | None | Adds one callback button after the built-in controls. |

#### `customColor`

All color fields accept any valid CSS color value and are optional.

```js
new jsCrop('.crop-image', {
  customColor: {
    overlayBgColor: 'rgba(10, 10, 12, 0.98)',
    toolbarBgColor: 'rgba(18, 18, 20, 0.84)',
    buttonBgColor: 'rgba(255, 255, 255, 0.10)',
    buttonFontColor: '#ffffff'
  }
});
```

#### `extButton`

`extButton` is useful when you want the cropped result in application code instead of, or in addition to, the built-in download.

| Field | Type | Default | Description |
| --- | --- | --- | --- |
| `callBack` | `function` | Required | Called with the cropped image data URL when the button is clicked. The button is only added when this is a function. |
| `buttonText` | `string` | `'ext'` | Button content. The value is inserted as HTML, so only use trusted content. |
| `buttonTitle` | `string` | `'Extension'` | Tooltip and accessible label. |
| `buttonCSS` | `string` | `''` | Inline CSS declarations appended to the button style, for example `'background:#2563eb;'`. This is not a class name. |

```js
new jsCrop('#avatar', {
  saveButton: false,
  extButton: {
    buttonText: 'Save avatar',
    buttonTitle: 'Save the cropped avatar',
    buttonCSS: 'background:#2563eb;color:#fff;',
    callBack: function (dataUrl) {
      // dataUrl looks like: data:image/png;base64,...
      document.querySelector('#preview').src = dataUrl;
    }
  }
});
```

Despite the historical callback examples calling this value `blob`, the library currently returns a base64-encoded data URL string from `canvas.toDataURL()`.

### `customButtons`

Type: `Array<object>` (optional)

The third constructor argument adds any number of application-specific toolbar buttons.

| Field | Type | Default | Description |
| --- | --- | --- | --- |
| `callBack` | `function` | None | Receives `(dataUrl, relParam)` when `buttonEvent` fires. |
| `buttonText` | `string` | `'ext'` | Button content, inserted as HTML. |
| `buttonTitle` | `string` | `Button N` | Tooltip and accessible label. |
| `buttonEvent` | `string` | `'click'` | DOM event name that triggers the callback. |
| `buttonCSS` | `string` | `''` | Inline CSS declarations appended to the button style. |
| `relParam` | any | `undefined` | Application-defined value passed unchanged as the callback's second argument. |

```js
new jsCrop(
  '.crop-image',
  {
    imageType: 'png',
    saveButton: false
  },
  [
    {
      buttonText: 'Preview',
      buttonTitle: 'Preview this crop',
      relParam: { destination: 'avatar-preview' },
      callBack: function (dataUrl, metadata) {
        document.getElementById(metadata.destination).src = dataUrl;
      }
    },
    {
      buttonText: 'Upload',
      buttonTitle: 'Upload this crop',
      buttonCSS: 'background:#15803d;',
      callBack: async function (dataUrl) {
        await fetch('/api/avatar', {
          method: 'POST',
          headers: { 'Content-Type': 'application/json' },
          body: JSON.stringify({ image: dataUrl })
        });
      }
    }
  ]
);
```

### Converting the callback result to a `Blob`

If an upload API expects a `Blob` or `File`, convert the returned data URL first:

```js
async function dataUrlToBlob(dataUrl) {
  return fetch(dataUrl).then(function (response) {
    return response.blob();
  });
}

new jsCrop('#avatar', {
  extButton: {
    buttonText: 'Upload',
    callBack: async function (dataUrl) {
      const blob = await dataUrlToBlob(dataUrl);
      const formData = new FormData();
      formData.append('image', blob, 'crop.png');

      await fetch('/api/avatar', {
        method: 'POST',
        body: formData
      });
    }
  }
});
```

## Using the editor

1. Open an image by clicking it or choosing a file.
2. Select the crop tool, then drag across the image to create a crop area.
3. Move or resize the selection, then select the crop tool again to apply it.
4. Use Reset, Undo, or Redo as needed.
5. Download the result or use one of your callback buttons.

Press `Escape` to close the editor. While a crop selection is visible, use the arrow keys to move it by one pixel or `Shift` + an arrow key to move it by ten pixels.

## Cross-origin images

The browser must allow the image to be drawn to a canvas. Use same-origin images or images selected through a file input. A remote image that is not canvas-safe will let the editor open but the browser may block download and callback export with a canvas security error.

## Contributing

Contributions, issues, and feature requests are welcome. See the [issues page](https://github.com/ujw0l/js-crop/issues) and [contributing guide](https://github.com/ujw0l/js-crop/blob/master/CONTRIBUTING.md).

## Author

**ujw0l**

- Twitter: [@bastakotiujwol](https://twitter.com/bastakotiujwol)
- GitHub: [@ujw0l](https://github.com/ujw0l)

## Support

If this project helped you, please star the repository or [buy me a coffee](https://www.buymeacoffee.com/ujw0l).

## License

Copyright © 2019 [ujw0l](https://github.com/ujw0l).

Licensed under the [MIT License](https://github.com/ujw0l/js-crop/blob/master/LICENSE).
