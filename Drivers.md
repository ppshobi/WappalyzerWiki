A driver provides an interface between Wappalyzer's core code and a specific platform (such a web browser).

The [`src/drivers/`](https://github.com/AliasIO/Wappalyzer/tree/master/src/drivers) directory contains platform specific code. The remaining files in [`src/`](https://github.com/AliasIO/Wappalyzer/tree/master/src) are shared components, used by each of the drivers.

The page describes how to use the drivers.

## PhantomJS (recommended)

Requires: `[phantomjs](http://phantomjs.org/)`

`$ phantomjs driver.js https://wappalyzer.com`

### NPM

Alternatively, Wappalyzer can be installed through NPM and run as a Node.js module.

Requires: `node`, `npm`

`$ npm i wappalyzer`
`$ cd node_modules/wappalyzer`
`$ node index.js https://wappalyzer.com`

### Docker

You can also run Wappalyzer through Docker.

Requires: `[docker](https://www.docker.com/)`

`$ docker run wappalyzer/cli https://wappalyzer.com`

## Mozilla Firefox

* [Install the Add-on SDK](https://developer.mozilla.org/en-US/Add-ons/SDK/Tutorials/Installation).
* On the command line, from [`drivers/firefox/`](https://github.com/AliasIO/Wappalyzer/tree/master/src/drivers/firefox), execute `jpm run`.

## Google Chrome

* Navigate to `about:extensions`.
* Check "Developer mode".
* Click "Load unpacked extension...".
* Select [`drivers/chrome/`](https://github.com/AliasIO/Wappalyzer/tree/master/src/drivers/chrome).

## Bookmarklet

Beta version available for testing at 
[wappalyzer.com/bookmarklet](http://wappalyzer.com/bookmarklet).