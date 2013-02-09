## Adding a new application

* Read the [specification](https://github.com/ElbertF/Wappalyzer/wiki/Specification).
* Edit `share/apps.json` (use a JSON 
  [validator](http://jsonformatter.curiousconcept.com)).
* Add a 16x16 PNG image to `share/images/icons` matching the application name 
  (use [Smush.it](http://www.smushit.com) or [OptiPNG](http://optipng.sourceforge.net) for compression).
* Provide the URL to the application's website when submitting a pull request.

## Creating a new driver or port

* Read the [specification](https://github.com/ElbertF/Wappalyzer/wiki/Specification).

## Adding a new category

Please [open an issue](https://github.com/ElbertF/Wappalyzer/issues) to discuss first. Adding a category involves updating `apps.json`,
preference pages, locales and [wappalyzer.com](http://wappalyzer.com).

## Adding a new translation

### Mozilla Firefox

Copy `drivers/firefox/locale/en-US` and update its contents.

### Google Chrome

Copy `drivers/chrome/_locales/en` and update its contents.