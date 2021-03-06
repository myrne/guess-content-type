# guess-content-type [![Build Status](https://travis-ci.org/meryn/guess-content-type.png?branch=master)](https://travis-ci.org/meryn/guess-content-type) [![Dependency Status](https://david-dm.org/meryn/guess-content-type.png)](https://david-dm.org/meryn/guess-content-type)

Guesses (MIME) Content-Type (including charset) based on file name.

This is based on [mime](https://github.com/broofa/node-mime) module, but has a more convenient interface if your goal is to explictly state that your content in text-based formats has UTF-8 encoding (which many editors have as output nowadays) . Without specifying a charset explicitly, most browsers will default to ISO-8859-1, or whatever the user preference is.

Don't use this module if you're not sure about the character encoding of the HTML or text content you're generating, because you'd be making things worse by specifying the wrong encoding. Check your editor's documentation first.

Note that problems with encoding (at least in Western countries) will only show up when you use non-ascii characters.

## Usage

```javascript
var guessType = require("guess-content-type")
var contentType = guessType(filename)
```

`contentType` is now the (guessed) media type for `filename`, or the media type including `charset=UTF-8` parameter if it's a text type. This can be put in the HTTP `Content-Type` header.

For convenience, `filename` may be an entire path or url as well.

## Example guesses, used as tests

```coffee
guesses =
  "a.txt":                        "text/plain; charset=UTF-8"
  "b.html":                       "text/html; charset=UTF-8"
  ".jpg":                         "image/jpeg"
  ".unknown-type":                "application/octet-stream"
  "/":                            "application/octet-stream"
  "/some/path":                   "application/octet-stream"
  "http://google.com/abc.html":   "text/html; charset=UTF-8"
  "http://google.com/abc.html?q": "text/html; charset=UTF-8"
  "http://google.com/abc.gif?q":  "image/gif"
```


## Credits

The initial structure of this module was generated by [Jumpstart](https://github.com/meryn/jumpstart), using the [Jumpstart Black Coffee](https://github.com/meryn/jumpstart-black-coffee) template.

## License

guess-content-type is released under the [MIT License](http://opensource.org/licenses/MIT).  
Copyright (c) 2013 Meryn Stol  