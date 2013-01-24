jQuery.PrettyTextDiff
=====================

A wrapper around Google's
[`diff_match_patch`](http://code.google.com/p/google-diff-match-patch/)
library. Google's libabry is awesome and can be fine-tuned in
multiple ways, but their API is a bit awkward, probably cause they
support the same API in 8 different languages.

Also, the library does not provide any beautification of the diff-ed
output. They provide a reference implementation (look for
`diff_prettyHtml` in the
[API docs](http://code.google.com/p/google-diff-match-patch/wiki/API)
) but recommend developers to write their own - and the given method is
[not customizable](http://stackoverflow.com/questions/13894514/google-diff-match-avoid-showing-new-lines)
.

This library is an alternative to embedding
 [30+ lines of cryptic JS](http://stackoverflow.com/a/13894720/117750)
 in your code. In short, it tries to bridge the gap between the
 awesome `diff_match_patch` library and a simple user-experience.

## Usage
#### First, include the libraries
+ include `jquery.js`, `diff_match_patch.js` and
`jquery.pretty-text-diff.js` in your page, something like:

```html
<script src="/path/to/jquery.min.js" type="text/javascript"></script>
<script src="/path/to/diff_match_patch.js" type="text/javascript"></script>
<script src="/path/to/deal_override_requests.min.js" type="text/javascript"></script>
```

#### Next sprinkle a bit of JS
+ something like:

```js
  $(selector).prettyTextDiff({
    // options
  });
```
Check out the [customizable options](#customizable-options) below.

#### Optionally, style the diff
+ Style `<ins>` and `<del>` as much as you want. A simple example is
in the [jsfiddle demo](#demo).

#### Customizable options
+ Either mark up your HTML to use the default selectors, or use these options below:

<table>
  <tr>
    <th>option</th>
    <th>default</th>
    <th>explanation</th>
  </tr>
 
  <tr>
    <td>originalContainer</td>
    <td>.original</td>
    <td>CSS-selector for the element that holds the original text. $(elem).text() will be used to extract the text.</td>
  </tr>

  <tr>
    <td>changedContainer</td>
    <td>.changed</td>
    <td>CSS-selector for the element that holds the changed text. $(elem).text() will be used to extract the text.</td>
  </tr>

  <tr>
    <td>diffContainer</td>
    <td>.diff</td>
    <td>CSS-selector for the element where the diff will be put.</td>
  </tr>

  <tr>
    <td>cleanup</td>
    <td>true</td>
    <td>Whether diff_match_patch's diff_cleanupSemantic() will be used or not. true will produce a human-redable diff, whereas false will be more to the liking of machines. See the demo for the effect.</td>
  </tr>

  <tr>
    <td>debug</td>
    <td>false</td>
    <td>see some debug output in your browser's console</td>
  </tr>
</table>


## Demo
[jsfiddle demo](http://jsfiddle.net/arnab/YwSVY/)

## Development
+ Install [`node`](http://nodejs.org/) and `npm` (comes with node now)
+ Install [`coffeescript`](http://coffeescript.org/#installation) and
    [`uglify`](https://github.com/mishoo/UglifyJS2):
    `npm install -g coffee-script uglify-js`
+ `cake build` to produce the output JS (minified)

## License
Copyright (c) 2013 Arnab Deka. Licensed under
[MIT LICENSE](https://github.com/arnab/jQuery.PrettyTextDiff/blob/master/LICENSE)
for details.
