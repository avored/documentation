# Module Create

* [Create Module](module-create.md#create-module)
  * [Folder Structure](module-create.md#module-folder-structure)
  * [register.yaml](module-create.md#module-register-file)
  * [src](module-create.md#module-src)
  * [resources](module-create.md#module-resources)

## Create Module

Creating a module in AvoRed is a nice way to extend the features of AvoRed E commerce.

## Folder Strucuture

* modules
  * vendor-name \(avored\) 
    * module-name\(helloworld\)
      * resources
      * routes
        * web.php
      * src
        * Module.php
          * register.yaml

## Register Yaml File

Register.yaml file the key to register most information about the modules. Things that needs to be careful here is your identifier neeeds to be unique.

```text
identifier: avored-helloworld
description: AvoRed Hello World Module
namespace: Avored\Helloworld\
```

## Module Src

Module Source as it name suggest it contains all the `.php` files of your modules. You must have an `Provider.php` file and it should contain `boot` and `register` method where register method contains your module middleware or facade if you have any. `boot` method register your view, routes, database migration and lang paths. Let say if you are creating an helloworld module then your `provider.php` file should look like below.

```text
<?php
namespace Avored\Helloworld;

use Illuminate\Support\ServiceProvider;

class Module extends ServiceProvider
{


    /**
     * Bootstrap any application services.
     *
     * @return void
     */
    public function boot()
    {
        $this->registerResources();

    }

    /**
     * Register any application services.
     *
     * @return void
     */
    public function register()
    {


    }


    /**
     * Registering AvoRed Hello World Resource
     * e.g. Route, View, Database  & Translation Path
     *
     * @return void
     */
    protected function registerResources()
    {
        $this->loadRoutesFrom(__DIR__ . '/../routes/web.php');
        $this->loadTranslationsFrom(__DIR__ . '/../resources/lang', 'mage2-helloworld');
        $this->loadViewsFrom(__DIR__ . '/../resources/views', 'mage2-helloworld');
    }
}
```

