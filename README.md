Config manager for laravel-admin
========================

[![Packagist](https://img.shields.io/packagist/l/php-panel/ladmin-ext-config.svg?maxAge=2592000)](https://packagist.org/packages/php-panel/ladmin-ext-config)
[![Total Downloads](https://img.shields.io/packagist/dt/php-panel/ladmin-ext-config.svg?style=flat-square)](https://packagist.org/packages/php-panel/ladmin-ext-config)
[![Pull request welcome](https://img.shields.io/badge/pr-welcome-green.svg?style=flat-square)]()

Inspired by https://github.com/laravel-backpack/settings.

[Documentation](http://laravel-admin.org/docs/#/en/extension-config) | [中文文档](http://laravel-admin.org/docs/#/zh/extension-config)

## Screenshot

![wx20170810-100226](https://user-images.githubusercontent.com/1479100/29151322-0879681a-7db3-11e7-8005-03310686c884.png)

## Installation

```
$ composer require php-panel/ladmin-ext-config

$ php artisan migrate
```

Open `app/Providers/AppServiceProvider.php`, and call the `Config::load()` method within the `boot` method:

```php
<?php

namespace App\Providers;

use Ladmin\Config\Config;
use Illuminate\Support\Facades\Schema;
use Illuminate\Support\ServiceProvider;

class AppServiceProvider extends ServiceProvider
{
    public function boot()
    {
        $table = config('admin.extensions.config.table', 'admin_config');
        if (Schema::hasTable($table)) {
            Config::load();
        }
    }
}
```

Then run: 

```
$ php artisan admin:import config
```

Open `http://your-host/admin/config`

## Usage

After add config in the panel, use `config($key)` to get value you configured.

License
------------
Licensed under [The MIT License (MIT)](LICENSE).
