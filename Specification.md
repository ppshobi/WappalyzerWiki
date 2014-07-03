## apps.json

Wappalyzer uses a long list of regular expressions to evaluate web pages and detect web applications. The list is located at [`share/apps.json`](https://github.com/ElbertF/Wappalyzer/blob/master/share/apps.json).

#### Example

```javascript
"Application Name": { 
        "website": "example.com", 
	"cats":    [ 1 ], 
	"headers": { "X-Powered-By": "Application Name" },
	"url":     ".+\\.application-name\\.com",
	"html":    "<link[^>]application-name\\.css", 
	"meta":    { "generator": [ "Application Name", "Alternative Application Name" ] },
	"script":  "application-name-([0-9.]+)\\.js\\;confidence:50\\;version:\\1",
	"env":     "ApplicationName",
	"implies": "PHP\\;confidence:50",
	"excludes": "Other Application Name"
	}
```

### JSON fields

field      | type           | description  | Example
-----------|----------------|--------------|--------------
website    | string         | URL of the application's website, with the protocol left off. | `"example.com"`
cats       | array          | List of category IDs. See [apps.json](https://github.com/ElbertF/Wappalyzer/blob/master/share/apps.json) for the complete list. | `[ 1, 6 ]`
env        | array / string | Global JavaScript variables, e.g. `jQuery`.<br>**Note that this will only detect *top-level* variables**; e.g. the following will **not** work: `^jQuery\\.fooBar$`. | `"^jQuery$"`
headers    | object         | HTTP Response headers, e.g. `X-Powered-By`. | <code>{ "X-Powered-By": "^Hello(?:World&#124;Universe)" }</code>
html       | array / string | Full HTML response body. | `"<a [^>]*href=\"[^\"]+/foo/bar"`
implies    | array / string | The presence of one application can imply the presence of another, e.g. Drupal means PHP is also in use. | `[ "PHP", "jQuery" ]`
excludes   | array / string | Opposite of implies. The presence of one application can exclude the presence of another. | `"Apache"`
url        | array / string | URL of the page, e.g. `http://wordpress.com/index.php`. | `"/cart/checkout\\?(?:.*&)?shopname_sess="`
meta       | object         | HTML meta tags, e.g. `generator`. | <code>{ "generator": "^Hello(?:World&#124;Universe)" }</code>
script     | array / string | `src` attribute of HTML script tags, e.g. `jquery.js`. | `"my_js_lib\\.js"`

Except `cats` and `website` all fields are optional and accept one or more patterns (either a string or an array of regular expressions).

### Patterns

Patterns are case insensitive [regular expressions](https://developer.mozilla.org/en-US/docs/JavaScript/Guide/Regular_Expressions). No surrounding delimiters or flags are used. Note that escape characters need to be escaped themselves for the JSON to be valid. Slashes (`/`) do not need to be escaped.

Optional fields may be appended, separated by `\\;`:

field      | description
-----------|------------
confidence | Indicates less reliable patterns that may cause false positives. The aim is to achieve a combined confidence of 100%. Defaults to 100% for unspecified fields.
version    | Gets the version number from a pattern match using a special syntax.

The confidence field may also be applied to the `implied` field. The `implied` confidence is multiplied by confidence of the pattern that identified the original application.

#### Version syntax

example    | description
-----------|------------
`\\1`      | Returns the first match
`\\1?a:`   | Returns `a` if the first match contains a value, nothing otherwise
`\\1?a:b`  | Returns `a` if the first match contains a value, `b` otherwise
`\\1?:b`   | Returns nothing if the first match contains a value, `b` otherwise
`foo\\1`   | Returns `foo` with the first match appended