<h1 align="center">Welcome to Js Crop 👋</h1>
<p>
  <img src="https://img.shields.io/badge/version-1.6.0-blue.svg?cacheSeconds=2592000" />
  <a href="https://github.com/ujw0l/js-crop#readme">
    <img alt="Documentation" src="https://img.shields.io/badge/documentation-yes-brightgreen.svg" target="_blank" />
  </a>
  <a href="https://github.com/ujw0l/js-crop/graphs/commit-activity">
    <img alt="Maintenance" src="https://img.shields.io/badge/Maintained%3F-yes-green.svg" target="_blank" />
  </a>
  <a href="https://github.com/ujw0l/js-crop/blob/master/LICENSE">
    <img alt="License: MIT" src="https://img.shields.io/badge/License-MIT-yellow.svg" target="_blank" />
  </a>
</p>

> JS Library to enable image cropping

## Install

```sh
npm i js-crop
```

## Script

```sh
include js-crop.js
```

## Initialize 

```sh

 new jsCrop('selector',
            { 
              extButton : (extension which adds button to bottom of toolbar)
                        { 
                          buttonText : string, (optional, text for button)
                          buttonTitle: string, (optinal, title for button)
                          callBack: function, (required, callback function  which is passed blob of cropped image, on button click )
                        },
              saveButton:boolean (optional, set false to hide save button)
  }
  );

*parameter 1 (required) : selector for images to be cropped, one or multiple
*parameter 2 (optional): object with option to display extension button (extButton) and hide save button
```

## Contributing

Contributions, issues and feature requests are welcome. Feel free to check [issues page](https://github.com/ujw0l/js-crop/issues) if you want to contribute.

## Author

👤 **ujw0l**

* Twitter 👉 [@bastakotiujwol](https://twitter.com/bastakotiujwol)
* Github 👉 [@ujw0l](https://github.com/ujw0l)

## Show your support

Please ⭐️ this repository if you like it.

## License

Copyright © 2019 [ujw0l](https://github.com/ujw0l).

📜 This project is [MIT](https://github.com/ujw0l/js-crop/blob/master/LICENSE) licensed.

***
_This README was generated with ❤️ by [readme-md-generator](https://github.com/kefranabg/readme-md-generator)_