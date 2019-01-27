# CssParser

A library to evaluate CSS expressions.

This library can be used to select elements from a DOM Document using CSS selectors.

## Install

Simply execute the following command:
```bash
composer require soloproyectos-php/css-parser
```

## Examples

You can create instances of `CssParser` from different sources:
```php
// Evaluates from a DOMDocument
$doc = new DOMDocument("1.0", "UTF-8");
$doc->loadXML('<root><item id="101" /><item id="102" /></root>');
$selector = new CssParser($doc);

// Creates an instance from a DOMElement
$doc = new DOMDocument("1.0", "UTF-8");
$doc->loadXML('<root><item id="101" /><item id="102" /></root>);
$root = $doc->documentElement;
$selector = new CssParser($root);

// Creates an instance from a file
$selector = new CssParser('/path/to/my/document.xml');

// Creates an instance from an URL
$selector = new CssParser('http://www.my-site.com/document.xml');
```

Selects the first and the odd elements:
```php
$doc = new DOMDocument("1.0", "UTF-8");
$doc->loadXML(
    '<root><item id="101" /><item id="102" /></root>'
);
$selector = new CssSelector($doc);

// selects the first and the odd elements and prints them
$items = $selector->query('item:odd, item:first-child');
foreach ($items as $item) {
    echo $doc->saveXML($item) . "\n";
}
```
