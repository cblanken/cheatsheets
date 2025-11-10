# PHP

## Documentation

- [PHP Manual](https://www.php.net/manual/en/)

## Best Practices

- [PHP The Right Way](https://phptherightway.com/#language_highlights)
- [PHP Best Practices: A short, practical guide for common and confusing PHP tasks](https://phpbestpractices.org)

## Security

- [The 2018 Guide to Building Secure PHP Software](http://github.com/korijn/flake8-self)

## Debugging

- [Xdebug](https://xdebug.org)

## Standard PHP Library (SPL)

TODO

## PHP Types

- [PHP type comparison tables](https://www.php.net/manual/en/types.comparisons.php)
- [Type Juggling](https://www.php.net/manual/en/language.types.type-juggling.php)

## Unicode / UTF-8

If you aren't using a framework you probably need to be using the `mb_*` variants of string functions. Also watch out for databases storing string in encoding different from UTF-8.

See [https://phptherightway.com/#php_and_utf8](https://phptherightway.com/#php_and_utf8)

## Misc

- If you get a blank SOD, enable display of errors in `php.ini`. The location depends on the installation and web server but usually: `/etc/php/X.Y/apache2/php.ini` where `X.Y` is the PHP version.
