
# Module Admin Menu

`AdminMenu` facade is very helpful for adding an admin menu for your custom module. Let say you want add a simple admin menu for your subscribe user list menu into an Admin of AvoRed E commerce. You can do that simply adding into your `module.php` files `boot` method by registering an Menu.

    use AvoRed\Framework\AdminMenu\Facade as AdminMenuFacade;
    use AvoRed\Framework\AdminMenu\AdminMenu;
    
    
    AdminMenuFacade::add('promotion')
            ->label('Promotion')
            ->route('#')
            ->icon('fa fa-book');

        $promotionMenu = AdminMenuFacade::get('promotion');
        
        $subscribeListMenu = new AdminMenu();
        $subscribeListMenu->key('subscribe')
            ->label('Subscribe List')
            ->route('admin.subscribe.index')
            ->icon('fab fa-book');
            
        $promotionMenu->subMenu('subscribe', $subscribeListMenu);
