# Module Routes 

Module Routes file is the place to defined all the routes for your module. Once you Register your Route file in `routes/web.php`. Inside your Route file you can use a Clouser if you want like shown below

    Route::get('hello-world', function() {
        return "Hello World";
    });
    
    // Or you can simply use a view() helper method to pass and view file
    
     Route::get('hello-world', function() {
        return view('avored-ecommerce::hello.index');
    });
    
    // Or you can simply use different Request method too.
    Route::post('auth', 'LoginController@login')->name('admin.login.post');
    
    Route::put('product', 'ProductController@index')->name('admin.product.index');
    
    Route::delete('category', 'CategoryController@destroy')->name('admin.category.destroy');
    
 ### Route Parameter Required
  
  You can specify an Parameter in route url like below
  
      // Show Profile update form
      Route::get('user/{id}', 'UserController@editProfile')->name('admin.user.edit');
      
### Route Optional Parameter
      
      //Below route is the one where you can pass user if and if it doesn't exist then you can use Logged In User
      Route::put('user/{id?}', 'UserController@updateProfile')->name('admin.user.update');

### Use Route into your Blade or other .php Files

When it comes to using an route we always prefer to `name` all the routes so when you want to use the route into any of your PHP files you can simple use `route` helper function

    // Router with out argument
    route('admin.login'); / yoursite.com/admin/login
    
    // Router with  argument
    route('admin.user.edit',$user->id);  // yoursite.com/admin/user/edit/2
    
    // route with pagination argument
    route('admin.product.index',['page' => 2]);  // yoursite.com/admin/product?page=2
    
    
### Route Group

Route groups allow you to share route attributes, such as middleware or namespaces, prefix across a large number of routes without needing to define those attributes on each individual route.

##### Middleware
To assign middleware to all routes within a group, you may use the middleware method before defining the group.Let say you want group of routes to be authenticated you can simply do it with `front.auth` like below:

    Route::middleware('front.auth')->group(function() {
    
        Route::get('my-account', 'MyAccountController@index')->name('user.my-account.index');
        Route::post('my-account', 'MyAccountController@store')->name('user.my-account.store');
    
    });
    
    //If you want to pass multiple Middleware simply use an array 
    
    Route::middleware(['web','front.auth'])->group(function() {
    
        Route::get('my-account', 'MyAccountController@index')->name('user.my-account.index');
        Route::post('my-account', 'MyAccountController@store')->name('user.my-account.store');
    
    });
    
##### NameSpace
Another common use-case for route groups is assigning the same PHP namespace to a group of controllers using the namespace method:

    Route::->namespace('AvoRed\Ecommerce\Http\Controllers\Admin')->group(function() {
    
        Route::get('admin/product', 'ProductController@index')->name('admin.product.index');
        Route::post('admin/product', 'ProductController@store')->name('admin.product.store');
    
    });
    
##### Prefix
The prefix method may be used to prefix each route in the group with a given URI. For example, you may want to prefix all route URIs within the group with admin:

    Route::->prefix('admin')->group(function() {
    
         // Above uri example we don't use `admin/` in this case
        Route::get('product', 'ProductController@index')->name('admin.product.index');
        Route::post('product', 'ProductController@store')->name('admin.product.store');
    
    });
