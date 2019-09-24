<h1 align="center">Welcome to Js Crop 👋</h1>
<p>
  <img src="https://img.shields.io/badge/version-2.0.0-blue.svg?cacheSeconds=2592000" />
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

> Js Library to enable image cropping with built in UI(with color customization options to fit look and feel of you website/web app)

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

 new jsCrop('selector', (Image element or upload button selector/s)
            { 
              extButton : (optional,extension which adds button after save image button)
                        { 
                          buttonText : string, (Optional, text for button)
                          buttonTitle : string, (Optinal, title for button)
                          callBack : function, (Required, callback function  which is passed blob of cropped image, on button click )
                        },
               customColor : (Optional,Js object conataining options for UI color customization)
                        {  
                            overlayBgColor : string, (Optional, background color for overlay)
                            toolbarBgColor : string, (Optional, background color for toolbar)
                            buttonBgColor :string,    (Optional, background color for buttons)
                            buttonFontColor : string, (Optional, font color for button)
                            
                      }, 
              imageType:string,(optinal,cropped image type,either jpeg or png)
              imageQuality: number,(opaitional, cropped image quality range 0 to 1);                
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

## Show your support

Please ⭐️ this repository if this project helped you!
<ul>
<li>
<a href="https://www.patreon.com/ujw0l">
  <img src="https://c5.patreon.com/external/logo/become_a_patron_button@2x.png" width="160">
</a>
</li>
<li>
<a href="https://tidelift.com/subscription/pkg/npm-js-crop?utm_source=npm-js-crop&utm_medium=referral&utm_campaign=readme">Get supported js-crop with the Tidelift Subscription</a>
</li>
</ul>

## License

Copyright © 2019 [ujw0l](https://github.com/ujw0l).

📜 This project is [MIT](https://github.com/ujw0l/js-crop/blob/master/LICENSE) licensed.

***
_This README was generated with ❤️ by [readme-md-generator](https://github.com/kefranabg/readme-md-generator)_
