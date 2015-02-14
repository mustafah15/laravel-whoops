# Whoops for Laravel 5

Unlike previous versions, Laravel 5 doesn't come with Whoops error handling
out of the box. To get this awesome error handler back in Laravel 5, I
created this package that hooks your application up with Whoops once again.

## Installation

First open up a console in your project root and let composer fetch Whoops
for you
```
composer require guidovanbiemen/laravel-whoops
```

Now go into your config/app.php and add the service provider:
```
'Gvb\Whoops\ServiceProvider',
```

To make sure you also catch any exceptions thrown during the bootstrap you
should also change the binding in bootstrapp/app.php like this:
```php
$app->singleton(
 	'Illuminate\Contracts\Debug\ExceptionHandler',
 	'Gvb\Whoops\ExceptionHandler'
);
```

Thats it! Enjoy your errors :)

## Troubleshooting

Not seeing any difference? Either there was no error (hooray!) or you've got
debugging disabled, which means laravel will (and should) not disclose any
details regarding the error that has occurred.

To enable Whoops, open up your 'config/app.php' configuration file, find the
debug setting and change it into true. As soon as you encounter an error,
you should be able to tell the difference pretty easily.

## What about AJAX requests?
 
Whenever an AJAX request triggers the error handler, it will be recognized
and the so called PrettyPageHandler will be exchanged for a
JsonResponseHandler that returns a JSON response that you can parse on the
client side.

## Authors

This integration package was created by
[Guido van Biemen](https://github.com/guidovanbiemen), but of course credits
for Whoops itself go where they are due:

* [Filipe Dobreira](https://github.com/filp) for creating Whoops
* [Denis Sokolov](https://github.com/denis-sokolov) for maintaining Whoops
