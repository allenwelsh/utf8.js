# utf8.js [![Build status](https://travis-ci.org/mathiasbynens/utf8.js.png?branch=master)](https://travis-ci.org/mathiasbynens/utf8.js) [![Dependency status](https://gemnasium.com/mathiasbynens/utf8.js.png)](https://gemnasium.com/mathiasbynens/utf8.js)

_utf8.js_ is a well-tested UTF-8 encoder/decoder written in JavaScript. Unlike many other JavaScript solutions, it is designed to be a _proper_ UTF-8 encoder/decoder: it can encode/decode any given Unicode code point, including astral symbols and unpaired surrogates.

Feel free to fork if you see possible improvements!

## Installation

Via [npm](http://npmjs.org/):

```bash
npm install utf8
```

Via [Bower](http://bower.io/):

```bash
bower install utf8
```

Via [Component](https://github.com/component/component):

```bash
component install mathiasbynens/utf8.js
```

In a browser:

```html
<script src="utf8.js"></script>
```

In [Narwhal](http://narwhaljs.org/), [Node.js](http://nodejs.org/), and [RingoJS ≥ v0.8.0](http://ringojs.org/):

```js
var utf8 = require('utf8');
```

In [Rhino](http://www.mozilla.org/rhino/):

```js
load('utf8.js');
```

Using an AMD loader like [RequireJS](http://requirejs.org/):

```js
require(
  {
    'paths': {
      'utf8': 'path/to/utf8'
    }
  },
  ['utf8'],
  function(utf8) {
    console.log(utf8);
  }
);
```

## API

### `utf8.encode(string)`

Encodes any given JavaScript string (`string`) as UTF-8, and returns the UTF-8-encoded version of the string.

```js
// U+00A9 COPYRIGHT SIGN; see http://codepoints.net/U+00A9
utf8.encode('\xA9');
// → '\xC2\xA9'
// U+10001 LINEAR B SYLLABLE B038 E; see http://codepoints.net/U+10001
utf8.encode('\uD800\uDC01');
// → '\xF0\x90\x80\x81'
```

### `utf8.decode(byteString)`

Decodes any given UTF-8-encoded string (`byteString`) as UTF-8, and returns the UTF-8-decoded version of the string. It throws an error when malformed UTF-8 is detected.

```js
utf8.decode('\xC2\xA9');
// → '\xA9'

utf8.decode('\xF0\x90\x80\x81');
// → '\uD800\uDC01'
// → U+10001 LINEAR B SYLLABLE B038 E
```

### `utf8.version`

A string representing the semantic version number.

## Support

utf8.js has been tested in at least Chrome 27-29, Firefox 3-22, Safari 4-6, Opera 10-12, IE 6-10, Node.js v0.10.0, Narwhal 0.3.2, RingoJS 0.8-0.9, PhantomJS 1.9.0, and Rhino 1.7RC4.

## Unit tests & code coverage

After cloning this repository, run `npm install` to install the dependencies needed for development and testing. You may want to install Istanbul _globally_ using `npm install istanbul -g`.

Once that’s done, you can run the unit tests in Node using `npm test` or `node tests/tests.js`. To run the tests in Rhino, Ringo, Narwhal, PhantomJS, and web browsers as well, use `grunt test`.

To generate [the code coverage report](http://rawgithub.com/mathiasbynens/utf8.js/master/coverage/utf8.js/utf8.js.html), use `grunt cover`.

## FAQ

### Why is the first release named v2.0.0? Haven’t you heard of [semantic versioning](http://semver.org/)?

Long before utf8.js was created, the `utf8` module on npm was registered and used by another (slightly buggy) library. @ryanmcgrath was kind enough to give me access to the `utf8` package on npm when I told him about utf8.js. Since there has already been a v1.0.0 release of the old library, and to avoid breaking backwards compatibility with projects that rely on the `utf8` npm package, I decided the tag the first release of utf8.js as v2.0.0 and take it from there.

## Author

| [![twitter/mathias](http://gravatar.com/avatar/24e08a9ea84deb17ae121074d0f17125?s=70)](http://twitter.com/mathias "Follow @mathias on Twitter") |
|---|
| [Mathias Bynens](http://mathiasbynens.be/) |

## License

utf8.js is dual licensed under the [MIT](http://mths.be/mit) and [GPL](http://mths.be/gpl) licenses.
