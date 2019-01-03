# Are PSR-17 Implementations Interoperable?

This repository will grab [all known psr/http-factory providers](https://packagist.org/providers/psr/http-factory-implementation) (& [these](https://packagist.org/providers/psr/http-factory)) and run [the global unit tests](https://github.com/http-interop/http-factory-tests) for all of them.

## How to run the tests?

1. Clone this repository.
2. Run `composer install`.
3. Run `composer test`.

## How does this work?

There is a folder for every implementation with its own `composer.json` file. This makes sure we are not mixing dependencies in anyway and everything acts stand-alone. Every implementation folder also contains a `phpunit.xml.dist` file supplying the correct factory class names for the test suite.

The test suite and PHPUnit are installed once by the root `composer.json` in this directory. This root file also contains a number of scripts so all nested implementations are installed and updated whenever `composer install` and `composer update` are called in the root folder.

The same is true for testing, where the root test script is set to run PHPUnit for each implementation.

## Special cases

* aidphp/http, berlioz/http-message, slim/psr7 and viserio/http-factory do not have stable releases. Using `dev-develop` for the first two, `1.0.x-dev` for the latter.
* chillerlan/php-httpinterface does not include factories in its latest stable release, no matter what Packagist might make you think. Using `dev-develop`.
* tuupola/http-factory and bulldog/http-factory require external PSR-7 implementations. They are installed once per supported PSR-7 implementation.
* slim/http is currently not included as it consists of decorators that would be fully dependent on one of the already tested implementations.
* aidphp/http provides only 3 out of the 6 factories.
* devop-core/http, sheychen/colis, and vaibhavpandeyvpz/sandesh are currently not included as they seem to be built against http-interop/http-factory.
* narrowspark/framework is currently not included as it is marked as abandoned.
* slim/psr7 is included even though it is not yet listed as a provider by Packagist.

## Results

### aidphp/http

......S................SSSSSS.....SSSSSSS
Tests: 41, Assertions: 68, Skipped: 14.

### berlioz/http-message

......EEEEE...........................E.F
Tests: 41, Assertions: 93, Errors: 6, Failures: 1.

### bulldog/http-factory (Guzzle)

.....................................EE..
Tests: 41, Assertions: 98, Errors: 2.

### bulldog/http-factory (Diactoros)

..................................EE.EE..
Tests: 41, Assertions: 94, Errors: 4.

### chillerlan/php-httpinterface

.....................................EE..
Tests: 41, Assertions: 98, Errors: 2.

### chiron/http

.........................................
Tests: 41, Assertions: 106

### http-interop/http-factory-diactoros

.........................................
Tests: 41, Assertions: 106

### http-interop/http-factory-guzzle

.........................................
Tests: 41, Assertions: 106

### http-interop/http-factory-slim

.........................................
Tests: 41, Assertions: 106

### nyholm/psr7

.........................................
Tests: 41, Assertions: 106

### rancoud/http

.........................................
Tests: 41, Assertions: 106

### slim/psr7

.....................................EE..
Tests: 41, Assertions: 98, Errors: 2.

### sunrise/http-factory

.........................................
Tests: 41, Assertions: 106

### tuupola/http-factory (Guzzle)

.........................................
Tests: 41, Assertions: 106

### tuupola/http-factory (Nyholm)

.........................................
Tests: 41, Assertions: 106

### tuupola/http-factory (Slim)

.........................................
Tests: 41, Assertions: 106

### tuupola/http-factory (Diactoros)

.........................................
Tests: 41, Assertions: 106

### viserio/http-factory

.........................................
Tests: 41, Assertions: 106

### zendframework/zend-diactoros

.........................................
Tests: 41, Assertions: 106
