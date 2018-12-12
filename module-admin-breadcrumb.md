# Module Admin Breadcrumbs

`Breadcrumb` facade is very helpful for adding an breadcrumb for your custom module admin views. Let say you want add a breadcrumb for your subscribe module of AvoRed E commerce. You can do that simply adding into your `module.php` files `boot` method by registering an Breadcrumb.

```php
use AvoRed\Framework\Breadcrumb\Facade  as BreadcrumbFacade;


BreadcrumbFacade::make('admin.subscribe.index', function ($breadcrumb) {
        $breadcrumb->label('Subscribe')
            ->parent('admin.dashboard');
    });

    BreadcrumbFacade::make('admin.subscribe.create', function ($breadcrumb) {
        $breadcrumb->label('Create')
            ->parent('admin.dashboard')
            ->parent('admin.subscribe.index');
    });

    BreadcrumbFacade::make('admin.subscribe.edit', function ($breadcrumb) {
        $breadcrumb->label('Edit')
            ->parent('admin.dashboard')
            ->parent('admin.subscribe.index');
    });
```

