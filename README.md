Artisan Make Model (Mongo)
==========================


[![Release](https://img.shields.io/badge/release-v1.0-green.svg)](https://github.com/TilakPutta/laravel-make-mongo/issues) 
[![GitHub license](https://img.shields.io/github/license/TilakPutta/laravel-make-mongo.svg)](https://github.com/TilakPutta/laravel-make-mongo/blob/master/LICENSE) [![Donate](https://img.shields.io/badge/donate-paypal-blue.svg)](https://www.paypal.me/tilakputta)

*A Composer Package written to generate boiler-plate code of Mongo Model with Jenssegers/MongoDb using Laravel Artisan*

Table of contents
-----------------
* [Installation](#installation)
* [Usage](#usage)
* [Examples](#examples)

Installation
------------

Installation using composer:

```
composer require tilakputta/laravel-make-mongo
```

And add the command to commands array in Kernel.php

```php
protected $commands = [
    \TilakPutta\Console\ModelMakeCommand::class
];
```

Usage
-----

For usage with `Artisan` type in this command:

```
php artisan make:model ModelName
```

Examples
--------

```
php artisan make:model Models/PermissionRole
```

creates app/Models/PermissionRole.php

```php
<?php

namespace App\Models;

use Jenssegers\Mongodb\Eloquent\Model;

class PermissionRole extends Model
{
    protected $collection = 'permission_roles';

    protected $fillable = [
        
    ];

    protected $primaryKey = 'id';

    public $incrementing = false;

    /**
     * model life cycle event listeners
     */
    public static function boot(){
        parent::boot();

        static::creating(function ($instance){
            if (!$instance->exists) {
                $instance->id = uniqid();
            }
        });

        static::created(function ($instance){
            
        });
    }
}
```
Authors
-------

[**TilakPutta**](https://github.com/TilakPutta)

Contributing
------------

Please make your contributions to make it more useful.
