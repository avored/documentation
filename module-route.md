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
    
    Route::post('auth', function() {});
    
    Route::put('product', function() {});
    
    Route::delete('category', 'CategoryController@destroy')->name('admin.category.destroy');
    
  ###  Module Route Parameter
  
  You can specify an Parameter in route url like below
  
      Route::get('user/{id}', 'UserController@editProfile')->name('admin.user.edit');
      
      // Route with Optional Parameter in Url If Id does not exist then it will destroy Current Login Profile to update
      Route::put('user/{id?}', 'UserController@destory')->name('admin.user.update');
