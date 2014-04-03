Anyone who wants to contribute is more than welcome to do so! Wappalyzer has been improved by [many](https://github.com/ElbertF/Wappalyzer/graphs/contributors).

To get started, please read the guidelines below as well as the [specification](https://github.com/ElbertF/Wappalyzer/wiki/Specification). For instructions on how to install Wappalyzer to test your changes, see the [[Drivers]] page.

## Adding a new application

* Edit [`share/apps.json`](https://github.com/ElbertF/Wappalyzer/blob/master/share/apps.json) (use a JSON 
  [validator](http://jsonformatter.curiousconcept.com)).
* Add a 32x32 PNG image to [`share/images/icons`](https://github.com/ElbertF/Wappalyzer/tree/master/share/images/icons) matching the application name 
  (use [Smush.it](http://www.smushit.com) or [OptiPNG](http://optipng.sourceforge.net) for compression).

## Adding a new category

Please [open an issue](https://github.com/ElbertF/Wappalyzer/issues) to discuss. Adding a category involves updating `apps.json`,
preference pages, locales and [wappalyzer.com](http://wappalyzer.com).

## Adding a new translation

### Mozilla Firefox

Copy [`drivers/firefox/locale/en-US`](https://github.com/ElbertF/Wappalyzer/tree/master/drivers/firefox/locale/en-US) and update its contents.

### Google Chrome

Copy [`drivers/chrome/_locales/en`](https://github.com/ElbertF/Wappalyzer/tree/master/drivers/chrome/_locales/en) and update its contents.

## Refactoring or adding new features

I'm much more likely to merge a pull request if it's an incremental change rather than rewritten or added functionality. If you have an idea please [open an issue](https://github.com/ElbertF/Wappalyzer/issues) to discuss it first. I'm interested to hear it.