## apps.json

#### Example

```javascript
"Application Name": { 
	"cats":    [ 1 ], 
	"headers": { "X-Powered-By": "Application Name" },
	"url":     ".+\\.application-name\\.com",
	"html":    "<link[^>]application-name\\.css", 
	"meta":    { "generator": [ "Application Name", "Alternative Application Name" ] },
	"script":  "application-name-([0-9.]+)\\.js\\;confidence:50\\;version:\\1",
	"env":     "ApplicationName",
	"implies": "PHP\\;confidence:50",
	}
```

### JSON fields

field      | type   | description
-----------|--------|------------
cats       | array  | List of category IDs. See [apps.json](https://github.com/ElbertF/Wappalyzer/blob/master/share/apps.json) for the complete list.
env        | string | Global JavaScript variables, e.g. `jQuery`.
headers    | object | HTTP Response headers, e.g. `X-Powered-By`.
html       | string | Full HTML response body.
implies    | array  | The presence of one application can imply the presence of another, e.g. Drupal means PHP is also in use.
url        | string | URL of the page, e.g. `http://wordpress.com/index.php`.
meta       | object | HTML meta tags, e.g. `generator`.
script     | string | `src` attribute of HTML script tags, e.g. `jquery.js`.

Except `cats`, all fields are optional.

Except `cats` and `implied` all fields accept one or more patterns (either a string or an array of regular expressions).



### Patterns

Patterns are case insensitive [regular expressions](https://developer.mozilla.org/en-US/docs/JavaScript/Guide/Regular_Expressions). No surrounding delimiters or flags are used.

Optional fields can be added, separated by `\\;`:

field      | description
-----------|------------
confidence | Indicates less reliable patterns that may cause false positives. The aim is to achieve a combined confidence of 100%. Defaults to 100% for unspecified fields.
version    | Gets the version number from a pattern match using a special syntax.

The confidence field can also be applied to the `implied` field.

#### Version syntax

example    | description
-----------|------------
`\\1`      | Returns the first match
`\\1?a:`   | Returns `a` if the first match contains a value, nothing otherwise
`\\1?a:b`  | Returns `a` if the first match contains a value, `b` otherwise
`\\1?:b`   | Returns nothing if the first match contains a value, `b` otherwise
`foo\\1`   | Returns `foo` with the first match appended