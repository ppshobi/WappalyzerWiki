A driver provides an interface between Wappalyzer's core code and a specific platform (such a web browser).

The [`src/drivers/`](https://github.com/ElbertF/Wappalyzer/tree/master/src/drivers) directory contains platform specific code. The remaining files in [`src/`](https://github.com/ElbertF/Wappalyzer/tree/master/src) are shared components, used by each of the drivers.

The page describes how to use the drivers.

## Mozilla Firefox

* [Install the Add-on SDK](https://developer.mozilla.org/en-US/Add-ons/SDK/Tutorials/Installation).
* On the command line, from [`drivers/firefox/`](https://github.com/ElbertF/Wappalyzer/tree/master/drivers/firefox), execute `jpm run`.

## Google Chrome

* Navigate to `about:extensions`.
* Check "Developer mode".
* Click "Load unpacked extension...".
* Select [`drivers/chrome/`](https://github.com/ElbertF/Wappalyzer/tree/master/drivers/chrome).

## Bookmarklet

Beta version available for testing at 
[wappalyzer.com/bookmarklet](http://wappalyzer.com/bookmarklet).

## HTML

The HTML driver serves purely as an example. It's a good starting point if you
want to [port](https://github.com/ElbertF/Wappalyzer/wiki/Unofficial-drivers-and-ports) Wappalyzer to a new platform.

* Open `index.html` a web browser.

## PhantomJS (recommended)

Install [PhantomJS](http://phantomjs.org/) on your system or run this in the Vagrant development environment.

`$ phantomjs driver.js https://wappalyzer.com`

To enable debugging, add `-v` or `--verbose`:

`$ phantomjs driver.js https://wappalyzer.com -v`

The return value is a JSON string.

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

## Python

The Python driver requires [PyV8](https://code.google.com/p/pyv8/). If you are running on Mac, download  [PyV8 (Mac Build)](http://www.dcl.hpi.uni-potsdam.de/home/loewis/pyv8/) and use the command: `otool -L _PyV8.so` linked library.

You can use pip install pyv8:

    pip install -v pyv8

or manually install:

    sudo apt-get install -y libboost-thread-dev libboost-all-dev python-dev git-core autoconf libtool
    svn checkout http://v8.googlecode.com/svn/trunk/ v8
    svn checkout http://pyv8.googlecode.com/svn/trunk/ pyv8
    cd v8
    export PyV8=`pwd`
    cd .. /pyv8
    sudo python setup.py build
    sudo python setup.py install

Runnning Wappalyzer from the command line:

    $ python drivers/python/wappalyzer.py http://github.com
    {"Ruby on Rails":{"categories":["web-frameworks"],"confidence":50,"version":""},"Ruby":{"categories":["programming-languages"],"confidence":50,"version":""}}

Running Wappalyzer inside a Python module:

```python
from wappalyzer import Wappalyzer

if __name__ == '__main__':
    w = Wappalyzer('http://github.com')
    output = w.analyze()
    print(output)
```


## Unofficial drivers

See [unofficial drivers and ports](https://github.com/ElbertF/Wappalyzer/wiki/Unofficial-drivers-and-ports) for more.