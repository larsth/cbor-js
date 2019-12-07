This fork
=========

This repo is a fork of of https://github.com/paroga/cbor-js 

"paroga/cbor-js" has 7 unmerged pull requests that has not been merged in this repo fork. 

The unmerged (not copied to this repo fork of "paroga/cbor-js") pull requests are:

- String encoding breaks in several edge cases #27 , https://github.com/paroga/cbor-js/issues/27
- Requirejs and CBOR-js #26 https://github.com/paroga/cbor-js/issues/26
- Error: Maximum call stack size exceeded #24 https://github.com/paroga/cbor-js/issues/24
- Handle ArrayBuffer encoding #21 https://github.com/paroga/cbor-js/issues/21
- TypeScript definition file #13 https://github.com/paroga/cbor-js/issues/13
- Performance #11 https://github.com/paroga/cbor-js/issues/11
- Pluggable encoders and decoders for tagged values #3 https://github.com/paroga/cbor-js/issues/3

If I was going solve this I would probably use [Rust](https://www.rust-lang.org/) and make a WASM file. There are anumber of crates (Rust packages) that could e a candiadate for doing that, look at https://cbor.io/impls.html

cbor-js
=======

The Concise Binary Object Representation (CBOR) data format ([RFC 7049](http://tools.ietf.org/html/rfc7049)) implemented in pure JavaScript.

[![Build Status](https://api.travis-ci.org/paroga/cbor-js.svg)](https://travis-ci.org/paroga/cbor-js)
[![Coverage Status](https://coveralls.io/repos/paroga/cbor-js/badge.svg?branch=master)](https://coveralls.io/r/paroga/cbor-js?branch=master)
[![Dependency status](https://david-dm.org/paroga/cbor-js/status.svg)](https://david-dm.org/paroga/cbor-js#info=dependencies&view=table)
[![Dev Dependency Status](https://david-dm.org/paroga/cbor-js/dev-status.svg)](https://david-dm.org/paroga/cbor-js#info=devDependencies&view=table)
[![Selenium Test Status](https://saucelabs.com/buildstatus/paroga-cbor-js)](https://saucelabs.com/u/paroga-cbor-js)

[![Selenium Test Status](https://saucelabs.com/browser-matrix/paroga-cbor-js.svg)](https://saucelabs.com/u/paroga-cbor-js)

API
---

The `CBOR`-object provides the following two functions:

CBOR.**decode**(*data*)
> Take the ArrayBuffer object *data* and return it decoded as a JavaScript object.

CBOR.**encode**(*data*)
> Take the JavaScript object *data* and return it encoded as a ArrayBuffer object.

Usage
-----

Include `cbor.js` in your or HTML page:
```html
<script src="path/to/cbor.js" type="text/javascript"></script>
```

Then you can use it via the `CBOR`-object in your code:
```javascript
var initial = { Hello: "World" };
var encoded = CBOR.encode(initial);
var decoded = CBOR.decode(encoded);
```
After running this example `initial` and `decoded` represent the same value.

### Combination with WebSocket

The API was designed to play well with the `WebSocket` object in the browser:
```javascript
var websocket = new WebSocket(url);
websocket.binaryType = "arraybuffer";
...
websocket.onmessage = function(event) {
  var message = CBOR.decode(event.data);
};
...
websocket.send(CBOR.encode(message));
```
