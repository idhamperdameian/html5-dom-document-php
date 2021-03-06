# HTML5DOMDocument

HTML5DOMDocument extends the native [DOMDocument](http://php.net/manual/en/class.domdocument.php) library. It fixes some bugs and adds some new functionality.

[![Build Status](https://travis-ci.org/ivopetkov/html5-dom-document-php.svg)](https://travis-ci.org/ivopetkov/html5-dom-document-php)
[![Latest Stable Version](https://poser.pugx.org/ivopetkov/html5-dom-document-php/v/stable)](https://packagist.org/packages/ivopetkov/html5-dom-document-php)
[![codecov.io](https://codecov.io/github/ivopetkov/html5-dom-document-php/coverage.svg?branch=master)](https://codecov.io/github/ivopetkov/html5-dom-document-php?branch=master)
[![License](https://poser.pugx.org/ivopetkov/html5-dom-document-php/license)](https://packagist.org/packages/ivopetkov/html5-dom-document-php)
[![Codacy Badge](https://api.codacy.com/project/badge/Grade/dafa5722288b409a9d447fa6aabd572b)](https://www.codacy.com/app/ivo_2/html5-dom-document-php)

## Differences to the native DOMDocument library

- Preserves white spaces
- Preserves html entities
- Preserves void tags
- Allows **inserting HTML code** that moves the correct parts to their proper places (head elements are inserted in the head, body elements in the body)
- Allows **querying the DOM with CSS selectors** (currently avaiable: *, tagname, tagname#id, #id, tagname.classname, .classname, tagname[attribute="value"], [attribute="value"], tagname[attribute], [attribute])

## Install via Composer

```shell
composer require ivopetkov/html5-dom-document-php
```

## Usage

HTML5DOMDocument is really easy to use - just like you should use DOMDocument.
```php
<?php
require 'vendor/autoload.php';

$dom = new IvoPetkov\HTML5DOMDocument();
$dom->loadHTML('<!DOCTYPE html><html><body>Hello</body></html>');
echo $dom->saveHTML();
```

## Documentation

List of classes added by the library:

- [IvoPetkov\HTML5DOMDocument](https://github.com/ivopetkov/html5-dom-document-php/blob/master/docs/classes/IvoPetkov-HTML5DOMDocument.md)
- [IvoPetkov\HTML5DOMElement](https://github.com/ivopetkov/html5-dom-document-php/blob/master/docs/classes/IvoPetkov-HTML5DOMElement.md)
- [IvoPetkov\HTML5DOMNodeList](https://github.com/ivopetkov/html5-dom-document-php/blob/master/docs/classes/IvoPetkov-HTML5DOMNodeList.md)

## Examples

Querying the document with CSS selectors and getting the innerHTML and the outerHTML of the elements:

```php
$dom = new IvoPetkov\HTML5DOMDocument();
$dom->loadHTML('<!DOCTYPE html><html><body><h1>Hello</h1><div class="content">This is some text</div></body></html>');

echo $dom->querySelector('h1')->innerHTML;
// Hello

echo $dom->querySelector('.content')->outerHTML;
// <div class="content">This is some text</div>
```

Inserting HTML code into a HTML document (other HTML code):

```php
$dom = new IvoPetkov\HTML5DOMDocument();
$dom->loadHTML('
    <!DOCTYPE html>
    <html>
        <head>
            <style>...</style>
        </head>
        <body>
            <h1>Hello</h1>
        </body>
    </html>
');

$dom->insertHTML('
    <html>
        <head>
            <script>...</script>
        </head>
        <body>
            <div>This is some text</div>
        </body>
    </html>
');

echo $dom->saveHTML();
// <!DOCTYPE html>
//     <html>
//         <head>
//             <style>...</style>
//             <script>...</script>
//         </head>
//         <body>
//             <h1>Hello</h1>
//             <div>This is some text</div>
//         </body>
//     </html>
```

## License
This project is licensed under the MIT License. See the [license file](https://github.com/ivopetkov/html5-dom-document-php/blob/master/LICENSE) for more information.

## Contributing
Feel free to open new issues and contribute to the project. Let's make it awesome.
This project is released with a [Contributor Covenant Code of Conduct](https://github.com/ivopetkov/html5-dom-document-php/blob/master/CODE-OF-CONDUCT.md). By participating in this project you agree to abide by its terms.

## Authors
This library is created and maintained by [Ivo Petkov](https://github.com/ivopetkov/) ([ivopetkov.com](https://ivopetkov.com)) and some [awesome folks](https://github.com/ivopetkov/html5-dom-document-php/graphs/contributors).
