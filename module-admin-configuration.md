# Module Admin Configuration

`AdminConfiguration` facade is very helpful for adding an configuration for your custom module. Let say you want add a configuration for your shipping module of AvoRed E commerce. You can do that simply adding into your `module.php` files `boot` method by registering an AdminConfiguration.

```php
use AvoRed\Framework\AdminConfiguration\Facade as AdminConfigurationFacade;


// How to add a new Configuration Tab/Accordion
$configurationGroup = AdminConfigurationFacade::add('my_custom_accordion')->label('My Custom Accordion');

// How to add a new Configuration Tab/Accordion
$paymentGroup = AdminConfigurationFacade::get('payment');

$paymentGroup->addConfiguration('shipping_free_shipping_enabled')
        ->label('Is Free Shipping Enabled')
        ->type('select')
        ->name('shipping_free_shipping_enabled')
        ->options(function (){
            $options = [1 => 'Yes' , 0 => 'No'];
            return $options;
        });
```

