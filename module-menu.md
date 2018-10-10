# Module Menu

`Menu` facade is very helpful for adding an menu for your custom module. Let say you want add a simple menu for your contact us module into an front side of AvoRed E commerce. You can do that simply adding into your `module.php` files `boot` method by registering an Menu.

```text
use AvoRed\Framework\Menu\Menu;
use AvoRed\Framework\Menu\Facade as MenuFacade;

/**
 * Bootstrap any application services.
 *
 * @return void
 */
public function boot()
{

    // Below code to 
    MenuFacade::make('contact-us',function (Menu $menu){
        $menu->label('Contact Us')
            ->route('contact.index');
    });
}
```

