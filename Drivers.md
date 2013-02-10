A driver provides an interface between Wappalyzer's core code and a specific platform (such a web browser).

All shared components are located the [`share/`](https://github.com/ElbertF/Wappalyzer/tree/master/share) directory. Platform specific code lives in [`drivers/`](https://github.com/ElbertF/Wappalyzer/tree/master/drivers). The sections below describe how to set up
a development environment for the various drivers.

To keep shared files synchronised between drivers, run `links.sh` (UNIX-like systems)
or `links.cmd` (Windows).

## Mozilla Firefox

* Create a file called `wappalyzer@crunchlabz.com` in the `extensions` directory in
  your [profile folder](http://kb.mozillazine.org/Profile_folder_-_Firefox) containing the path to `drivers/firefox`.
* Restart Firefox.
* Navigate to `about:config` and set `extensions.wappalyzer.debug` to `true`.
* Ctrl+Shift+J brings up a console for debugging.

## Google Chrome

* Navigate to `about:extensions`.
* Check "Developer mode".
* Click "Load unpacked extension...".
* Select `drivers/chrome/`.

## Bookmarklet

Beta version available for testing at 
[wappalyzer.com/bookmarklet](http://wappalyzer.com/bookmarklet).

## HTML

The HTML driver serves purely as an example. It's a good starting point if you
want to [port](https://github.com/ElbertF/Wappalyzer/wiki/Unofficial-drivers-and-ports) Wappalyzer to a new platform.

* Navigate to `drivers/html/`

## PHP

The PHP driver requires the [V8js](http://php.net/manual/en/book.v8js.php) 
class. Installing V8js using [PECL](http://pecl.php.net/) on Debian Linux or 
Ubuntu should be straight forward:

* `# aptitude install php5-dev php-pear libv8-dev`
* `# pecl install channel://pecl.php.net/v8js-0.1.3`
* `# echo "extension=v8js.so" > /etc/php5/conf.d/v8js.ini`

Runnning Wappalyzer from the command line:

`$ php drivers/php/index.php wappalyzer.com`

Running Wappalyzer inside a PHP script:

```php
<?php
require('WappalyzerException.php');
require('Wappalyzer.php');

$wappalyzer = new Wappalyzer($url);

$detectedApps = $wappalyzer->analyze();
```

## Mozilla Jetpack

Work in progress, experimental. See https://wiki.mozilla.org/Jetpack.

## Unofficial drivers

See [unofficial drivers and ports](https://github.com/ElbertF/Wappalyzer/wiki/Unofficial-drivers-and-ports) for more.