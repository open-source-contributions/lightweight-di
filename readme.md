# Lightweight Dependency Injection

| Build | Coverage | Downloads | Release | License |
|:--------:|:--------:|:--------:|:--------:|:--------:|
| [![Build Status](https://travis-ci.com/narokishi/lightweight-di.svg?branch=master&version=1.0.0)](https://travis-ci.com/narokishi/lightweight-di) | [![Coverage Status](https://coveralls.io/repos/github/narokishi/lightweight-di/badge.svg?branch=master&service=github&version=1.0.0)](https://coveralls.io/github/narokishi/lightweight-di?branch=master) | [![Total Downloads](https://poser.pugx.org/narokishi/lightweight-di/downloads?version=1.0.0)](https://packagist.org/packages/narokishi/lightweight-di) | [![Latest Stable Version](https://poser.pugx.org/narokishi/lightweight-di/v/stable?version=1.0.0)](https://packagist.org/packages/narokishi/lightweight-di) | [![License](https://poser.pugx.org/narokishi/lightweight-di/license?version=1.0.0)](https://packagist.org/packages/narokishi/lightweight-di) |



## Description

"Lightweight Dependency Injection" is a **PHP** package, which allows to inject your dependencies within services. It builds only required classes for the current request.

## Installation
### Composer
Installing via [Composer](https://getcomposer.org/download/) will keep this package up to date for you.
```bash
composer require narokishi/lightweight-di
```
### Usage
```php
use Narokishi\DependencyInjection\Container;

...

$container = new Container;
$container->registerService(ExampleService::class, function () {
    return new ExampleService(
        ...constructorArgs
    );
});
$container->registerService(SecondExampleService::class, function (Container $container) {
    return new SecondExampleService(
        $container->getService(ExampleService::class)
    );
});

...

$secondExampleService = $container->getService(SecondExampleService::class);
```

## Contributing
Thank you for considering contributing to the package.
