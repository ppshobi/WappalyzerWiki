A driver provides an interface between Wappalyzer's core code and a specific platform (such a web browser).

The [`src/drivers/`](https://github.com/AliasIO/Wappalyzer/tree/master/src/drivers) directory contains platform specific code. The remaining files in [`src/`](https://github.com/AliasIO/Wappalyzer/tree/master/src) are shared components, used by each of the drivers.

The page describes how to use the drivers.

## PhantomJS

PhantomJS is a headless browser that can used to run Wappalyzer on any Linux, Mac or Windows machine. It can be installed either directly or through NPM or Docker. Information about websites is returned in JSON format.

Requires: [`phantomjs`](http://phantomjs.org/)

#### Usage

```shell
$ phantomjs driver.js https://wappalyzer.com
```

#### Arguments

```
-v, --verbose            Display debug output

-q, --quiet              Suppress errors

--resource-timeout=ms    Abort the connection after 'ms' milliseconds
```

### NPM

Alternatively, Wappalyzer can be installed through NPM and run as a Node.js module (see the [README](https://github.com/AliasIO/Wappalyzer/blob/master/src/drivers/phantomjs/README.md) for more information).

Requires: `node`, `npm`

#### Usage

```shell
$ npm i wappalyzer
$ cd node_modules/wappalyzer
$ node index.js https://wappalyzer.com
```

#### Arguments

See [above](#arguments).

### Docker

You can also run Wappalyzer through Docker.

Requires: [`docker`](https://www.docker.com/)

#### Usage

```shell
$ docker run wappalyzer/cli https://wappalyzer.com
```

#### Arguments

See [above](#arguments).

## Mozilla Firefox

* Navigate to `about:debugging`.
* Check "Load Temporary Add-on".
* Select [`src/drivers/webextension/manifest.json`](https://github.com/AliasIO/Wappalyzer/blob/master/src/drivers/webextension/manifest.json).

## Google Chrome

* Navigate to `about:extensions`.
* Check "Developer mode".
* Click "Load unpacked extension...".
* Select [`src/drivers/webextension/`](https://github.com/AliasIO/Wappalyzer/tree/master/src/drivers/webextension).

## Bookmarklet

Available at 
[wappalyzer.com/download#bookmarklet](https://wappalyzer.com/download#bookmarklet).