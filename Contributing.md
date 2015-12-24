Anyone who wants to contribute is more than welcome to do so! Wappalyzer has been improved by [many](https://github.com/ElbertF/Wappalyzer/graphs/contributors).

To get started, please read the [README](https://github.com/ElbertF/Wappalyzer/blob/master/README.md), the guidelines below and the [specification](https://github.com/ElbertF/Wappalyzer/wiki/Specification). For instructions on how to install Wappalyzer to test your changes, see the [[Drivers]] page.

## Adding a new application

* Edit [`src/apps.json`](https://github.com/ElbertF/Wappalyzer/blob/master/src/apps.json) (use a JSON 
  [validator](https://jsonformatter.curiousconcept.com/)).
* **You can now use SVGs.** These are preferred to PNGs, as they are vector graphics and can scale to any size. If you do anything with Inkscape, be sure to save it as a Plain SVG. They will be compressed later in the build script, so don't worry about that. Open it in any browser just to be sure that it displays correctly. Width and height doesn't matter, as it is a vector image. You can open EPS files with Inkscape and save them as SVGs if you install the [Ghostcript Postscript and PDF interpreter/renderer](http://www.ghostscript.com/download/gsdnld.html). The filename should be the same as the application name and should be added to  [`src/icons`](https://github.com/ElbertF/Wappalyzer/tree/master/src/icons).
* If you can't find an SVG, add a 32x32 PNG image to [`src/icons`](https://github.com/ElbertF/Wappalyzer/tree/master/src/icons) matching the application name 
  (use [iConvert Icons](http://iconverticons.com/online/) to convert from ICO format if needed; and then
  [Kraken](https://kraken.io/web-interface), [Tinypng.com](https://tinypng.com/) or [OptiPNG](http://optipng.sourceforge.net) for compression).

## Adding a new category

Please [open an issue](https://github.com/AliasIO/Wappalyzer/issues/new) to discuss. Adding a category involves updating `apps.json`, locales and [wappalyzer.com](https://wappalyzer.com).

## Adding a new translation

### Mozilla Firefox

Copy [`src/drivers/firefox/locale/en-US.properties`](https://github.com/AliasIO/Wappalyzer/blob/master/src/drivers/firefox/locale/en-US.properties) and update its contents.

### Google Chrome

Copy [`src/drivers/chrome/_locales/en`](https://github.com/ElbertF/Wappalyzer/tree/master/src/drivers/chrome/_locales/en) and update its contents.

## Refactoring or adding new features

I'm much more likely to merge a pull request if it's an incremental change rather than rewritten or added functionality. If you have an idea please [open an issue](https://github.com/ElbertF/Wappalyzer/issues/new) to discuss it first. I'm interested to hear it.

## Cleaning and improving the apps.json file

* Use these regular expressions to spot potential problems. Note that these patterns are not perfect (i.e. false positive can occur) and we are constantly trying to improve them so share your patterns to spot problems.

Syntax problems        | Regular expression
-----------------------|--------------------
Missing \\\\           | <code>^.\*[^\\\\];(?:version&#124;confidence).\*$</code>
Missing ?: in groups   | <code>^.\*[^\\\\]\\(\[^?\](?!.\*(?:version&#124;\\\\\\\\1)).\*$</code>
Missing ?: in groups 2 | <code>^.\*version:\\\\\\\\[^1].\*$</code>
Unescaped dot          | <code>^\t{3}"[^wi].\*[^\\\\][^\\\\\\[]\\.[^+\*\\]].\*$</code>
Replace 0-9 by \\\\d   | <code>^.\*0-9.\*$</code>
Useless array          | <code>^.\*\\[ "[^"]+" \\].\*$</code>
Backslash not escaped  | <code>^.\*[^\\\\]\\\\[^\\\\/"].\*$</code>
Useless ?:             | <code>^.\*\\\\\\(\?:.\*$</code>

Patterns problems            | Regular expression
-----------------------------|--------------------
HTML matching plain text     | <code>^.\*"html"[^<>\\n]\*$</code>
HTML slow matching           | <code>^.\*"html".\*\\.[+\*].\*$</code>
Useless http(s)              | <code>^.\* "http.\*$</code>
Useless group                | <code>^.\*\\(\\?:[^\\n&#124;]\*[^\\\\?]\\)[^?)\*&#124;].*$</code>
Useless .+ or .\* at the end | <code>^.\*"[^"]{2,}[\*+]".\*$</code>