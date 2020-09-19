# Module Admin Configuration

Admin configuration is a way to storing the system level values into a database and as a module developer can use those values into different stages of an module.

Admin Configuration is now part of an `\AvoRed\Framework\Support\Facades\Tab` facade. Only the thing that have to keep in mind that when you register a tab for a Admin Configuration make the key stay intact with the existing `avored/framework`.

Let me give you an example: Let say you want to add a configuration for a AvoRed Pickup shipping module and you want to add configuration regarding that. In this situation you can simple open your `Module.php@boot` method and add the below code to register an tab.


```php
use AvoRed\Framework\Support\Facades\Tab;
use AvoRed\Framework\Tab\TabItem;


// How to add a new Admin Configuration Tab
@note Check the Tab Key here. Make sure do not change the ***system.confuguration*** as a key.
Tab::put('system.configuration', function (TabItem $tab) {
            $tab->key('system.configuration.pickup')
                ->label('avored-pickup::system.config-title')
                ->view('avored-pickup::system.configuration.pickup');
        });
```

