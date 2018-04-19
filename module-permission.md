
# Module Permission

`Permission` facade is very helpful for adding an permisison for your custom module admin routes. Let say you want add a simple permission for your subscribe user routes into an Admin of AvoRed E commerce. You can do that simply adding into your `module.php` files `boot` method by registering an Permission. Only the thing that needs to be make sure here is you use a routes name property and into your routes makes sure you named all routes as it mention in route docs. 

    use AvoRed\Framework\Permission\Facade as PermissionFacade;
    
    
    $permissionGroup = PermissionFacade::add('subscribe')
            ->label('Subscriber Permissions');

        $permissionGroup->addPermission('admin-subscribe-list')
            ->label('Subscriber List')
            ->routes('admin.subscribe.index');

        $permissionGroup->addPermission('admin-subscribe-create')
            ->label('Subscriber Create')
            ->routes('admin.subscribe.create,admin.subscribe.store');

        $permissionGroup->addPermission('admin-subscribe-update')
            ->label('Subscriber Update')
            ->routes('admin.subscribe.edit,admin.subscribe.update');

        $permissionGroup->addPermission('admin-subscribe-destroy')
            ->label('Subscriber Destroy')
            ->routes('admin.subscribe.destroy');


So as mention above once the permission gets Register with `PermissionFacade` then AvoRed E commerce Administrator can simple go to User Roles menu and manage the permission easily by ticking on checkboxes.
