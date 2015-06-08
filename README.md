

# String handling evolved

[![Latest Version on Packagist](https://img.shields.io/packagist/v/spatie/string.svg?style=flat-square)](https://packagist.org/packages/spatie/string)
[![Software License](https://img.shields.io/badge/license-MIT-brightgreen.svg?style=flat-square)](LICENSE.md)
[![Build Status](https://img.shields.io/travis/spatie/string/master.svg?style=flat-square)](https://travis-ci.org/spatie/string)
[![Quality Score](https://img.shields.io/scrutinizer/g/spatie/string.svg?style=flat-square)](https://scrutinizer-ci.com/g/spatie/string)
[![SensioLabsInsight](https://insight.sensiolabs.com/projects/23a69b38-e4d1-4893-bd14-c45c8b6f07a7/mini.png)](https://insight.sensiolabs.com/projects/23a69b38-e4d1-4893-bd14-c45c8b6f07a7)

This package provides a handy way to work with strings in php.

## Install

You can install this package via composer:

``` bash
composer require spatie/string
```

## Usage

First you must wrap a native string in a String-object. This can be done with the `string`-function.
```php
string('myFirstString');
```

From then on you can chain methods like there's no tomorrow:

```php
echo string('StartMiddleEnd')->between('Start', 'End')->toUpper(); // outputs "MIDDLE"
```

Of course you can keep concatenate the output with the `.`-operator we all know and love.

```php 
echo 'stuck in the ' . string('StartMiddleEnd')->between('Start', 'End')->toLower() . ' with you';
```

You can also use offsets to manipulate a string.

```php
echo string('hello')[1]->toUpper(); // outputs "E"

$string = string('gray');
$string[2] = 'e'; //
echo $string->toUpper(); //outputs "GREY"
```

## Provided methods
### between
```php
/**
 * Get the string between the given start and end.
 *
 * @param $start
 * @param $end
 * @return \Spatie\String\String
 */
public function between($start, $end)
```

Example:
```php
string('StartMiddleEnd')->between('Start', 'End')->toUpper(); // MIDDLE
```

### toUpper
```php
/**
 * Convert the string to uppercase.
 *
 * @return \Spatie\String\String
 */
public function toUpper()
```

Example:
```php
string('string')->toUpper(); // STRING
```

### toLower
```php
/**
 * Convert the string to lowercase.
 *
 * @return \Spatie\String\String
 */
public function toLower()
```

Example:
```php
string('STRING')->toLower(); // string
```

### tease
```php
/**
 * Shortens a string in a pretty way. It will clean it by trimming
 * it, remove all double spaces and html. If the string is then still
 * longer than the specified $length it will be shortened. The end
 * of the string is always a full word concatinated with the
 * specified moreTextIndicator.
 *
 * @param int $length
 * @param string $moreTextIndicator
 * @return \Spatie\String\String
 */
public function tease($length = 200, $moreTextIndicator = '...')
```

Example:
```php
$longText = 'Now that there is the Tec-9, a crappy spray gun from South Miami. This gun is advertised as the most popular gun in American crime. Do you believe that shit? It actually says that in the little book that comes with it: the most popular gun in American crime.'
string($longText)->tease(10); // Now that...
```

### replaceLast
```php
/**
 * Replace the last occurrence of a string.
 *
 * @param $search
 * @param $replace
 * @return \Spatie\String\String
 */
public function replaceLast($search, $replace)
```

Example:
```php
$sentence = 'A good thing is not a good thing.';
string($sentence)->replaceLast('good', 'bad'); // A good thing is not a bad thing.
```

### prefix
```php
/**
 * Prefix a string.
 *
 * @param $string
 * @return \Spatie\String\String
 */
public function prefix($string)
```

Example:
```php
string('world')->prefix('hello '); //hello world
```

### suffix
```php
/**
 * Suffix a string.
 *
 * @param $string
 * @return \Spatie\String\String
 */
public function suffix($string)
```

Example:
```php
string('hello')->suffix(' world'); // hello world
```

### concat
This is identical to the `suffix`-function.

### possessive
```php
/**
 * Get the possessive version of a string.
 *
 * @return \Spatie\String\String
 */
public function possessive()
```

Example:
```php
string('Bob')->possessive(); // Bob's
string('Charles')->possessive(); // Charles'
```

## Integration with underscore.php
In addition to the methods described above, you can also 
use [all string methods](https://github.com/Anahkiasen/underscore-php/blob/master/src/Methods/StringsMethods.php) provided
by [Maxime Fabre's underscore package](https://github.com/Anahkiasen/underscore-php).

For example:
```php
string('i am a slug')->slugify()` // returns 'i-am-a-slug'
``` 

Of course, you can chain underscore's methods with our own.
```php
string('i am a slug')->slugify()->between('i', 'a-slug`) // returns '-am-'
``` 

Be aware that some underscore methods do not return a string value. Such methods are not chainable.
```php
string('freek@spatie.be')->isEmail() // returns true;
``` 

## Change log

Please see [CHANGELOG](CHANGELOG.md) for more information what has changed recently.

## Testing

You can run the tests with:

```bash
vendor/bin/phpunit
```

## Contributing

We are very happy to receive pull requests to add functions to this class. Please see [CONTRIBUTING](CONTRIBUTING.md) for details.


## Security

If you discover any security related issues, please email freek@spatie.be instead of using the issue tracker.

## Credits

- [Freek Van der Herten](https://github.com/freekmurze)
- [All Contributors](../../contributors)

## Alternatives

This package is primarily built for usage in our own projects. If you need a more full fledged string package take at look at these ones:
- [Anahkiasen/underscore-php](https://github.com/Anahkiasen/underscore-php)
- [danielstjules/Stringy](https://github.com/danielstjules/Stringy)

## License

The MIT License (MIT). Please see [License File](LICENSE.md) for more information.
