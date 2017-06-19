[![Latest Stable Version](https://poser.pugx.org/jackiedo/workbench/v/stable)](https://packagist.org/packages/jackiedo/workbench)
[![Total Downloads](https://poser.pugx.org/jackiedo/workbench/downloads)](https://packagist.org/packages/jackiedo/workbench)
[![Latest Unstable Version](https://poser.pugx.org/jackiedo/workbench/v/unstable)](https://packagist.org/packages/jackiedo/workbench)
[![License](https://poser.pugx.org/jackiedo/workbench/license)](https://packagist.org/packages/jackiedo/workbench)


# Laravel 5 Workbench

Bring workbench back to Laravel 5+

# Overview
Look at one of the following topics to learn more about Laravel 5 Workbench

* [Versions and compatibility](#versions-and-compatibility)
* [Installation](#installation)
* [Usage](#usage)
* [Other documentation](#other-documentation)

## Versions and compatibility

Each branch of Laravel 5 Workbench is similarities with each version of Laravel 5+. Example:

| Branch                                                | Laravel version  |
| ----------------------------------------------------- | ---------------- |
| [5.0](https://github.com/sitedirect/workbench/tree/5.0) | 5.0              |
| [5.1](https://github.com/sitedirect/workbench/tree/5.1) | 5.1              |
| [5.2](https://github.com/sitedirect/workbench/tree/5.2) | 5.2              |
| [5.3](https://github.com/sitedirect/workbench/tree/5.3) | 5.3              |
| [5.4](https://github.com/sitedirect/workbench/tree/5.4) | 5.4              |

In each branch we have multiple versions, tagged syntax as `5.0.*`, `5.1.*`, `5.2.*`, `5.3.*`, `5.4.*`...

## Installation

You can install this package through [Composer](https://getcomposer.org).

- First, edit your project's `composer.json` file to require `sitedirect/workbench`:

```php
...
"require": {
    ...
    "sitedirect/workbench": "{{laravel-version}}.*"
},
```

> Note: `{{laravel-version}}` string above is main version of Laravel that you want to install Laravel Workbench on it. Example, if you want to install this package on Laravel 5.4, you have to set require is `"sitedirect/workbench": "5.4.*"`

- Next step, we update Composer from the Terminal on your project source:

```shell
$ composer update
```

- Once update operation completes, on the third step, we add the service provider. Open `config/app.php` file, and add a new item to the providers array:

```php
...
'providers' => array(
    ...
    sitedirect\Workbench\WorkbenchServiceProvider::class,
),
```

- On the fourth step, we publish configuration file:

```shell
$ php artisan vendor:publish
```

- And the final step is add autoload the workbench to your `bootstrap/autoload.php` file. Put this following code at the very bottom of script.

```php
/*
|--------------------------------------------------------------------------
| Register The Workbench Loaders
|--------------------------------------------------------------------------
|
| The Laravel workbench provides a convenient place to develop packages
| when working locally. However we will need to load in the Composer
| auto-load files for the packages so that these can be used here.
|
*/

if (is_dir($workbench = __DIR__.'/../workbench'))
{
    sitedirect\Workbench\Starter::start($workbench);
}
```

## Usage

Now, you can use workbench commands to create your packages same as on Laravel 4.2.

> Note: Before you create a package, you need to update `name` and `email` config value in your `config/workbench.php` file.

#### Creating a basic package.

```shell
$ php artisan workbench vendor/package
```

#### Creating a package with generating some scaffold resources.

```shell
$ php artisan workbench vendor/package --resources
```

## Other documentation

> For more documentation about package development, you can visit Official Laravel Documentation pages:

- [Laravel 4.2 Package Development](https://laravel.com/docs/4.2/packages)
- [Laravel 5.0 Package Development](https://laravel.com/docs/5.0/packages)
- [Laravel 5.1 Package Development](https://laravel.com/docs/5.1/packages)
- [Laravel 5.2 Package Development](https://laravel.com/docs/5.2/packages)
- [Laravel 5.3 Package Development](https://laravel.com/docs/5.3/packages)
- [Laravel 5.4 Package Development](https://laravel.com/docs/5.4/packages)