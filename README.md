digest-brunch
=============

A [Brunch][] plugin that appends a unique SHA digest to asset filenames. Allows
for [far-future caching][am] of assets.

_Note: This plugin is not compatible with [gzip-brunch][]._

Usage
-----

`npm install --save digest-brunch`

Identify assets that you want to be digested with `DIGEST(filename.ext)`.

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <script src="DIGEST(test.js)"></script>
  <link rel="stylesheet" href="DIGEST(test.css)">
</head>
<body>
  <script src="DIGEST(js/nested.js)"></script>
</body>
</html>
```

Run `brunch build --production` and you'll see something like the following:

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <script src="test-75570c26.js"></script>
  <link rel="stylesheet" href="test-e3eda643.css">
</head>
<body>
  <script src="js/nested-4df52a0a.js"></script>
</body>
</html>
```

Options
-------

_Optional_ You can override digest-brunch's default options by updating your
`config.coffee` with overrides.

These are the default settings:

```coffeescript
exports.config =
  # ...
  plugins:
    digest:
      # RegExp that matches files that contain DIGEST references.
      referenceFiles: /\.html$/
      # How many digits of the SHA1 to append to digested files.
      precision: 8
      # Force digest-brunch to run in all environments when true.
      alwaysRun: false
```

Contributing
------------

1. Add some code
1. Add some tests
1. Run `npm test`
1. Send a pull request

License
-------

MIT

[Brunch]: http://brunch.io
[am]: http://blog.alexmaccaw.com/time-to-first-tweet
[gzip-brunch]: https://github.com/banyan/gzip-brunch
