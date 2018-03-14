# Middleware

Middleware provide a convenient mechanism for filtering HTTP requests entering your application. For example, AvoRed includes a middleware that verifies the user of your application is authenticated. If the user is not authenticated, the middleware will redirect the user to the login screen. However, if the user is authenticated, the middleware will allow the request to proceed further into the application.

There are several middleware included in the AvoRed Ecommerce. 
 - front.guest // If user is Logged in and try to visit Login page it will redirect it to Account Page
 - front.auth  // To check if Front End User is Logged In.
 - admin.guest // If Admin User is Logged in and try to visit Login page it will redirect it to Dashboard Page
 - admin.auth  // To check if Admin User is Logged In.
 - visitor     // To record visit on the website into database
 - permission  // To Check if Admin User has permission to visit Particular Admin Page or not.
 
 ### Creating Middleware for your modules
  You can create your own middleware by simply providing details into you `src/Module.php` file. 
      <?php
      namespace AvoRed\Hello;

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
              $this->registerMiddleware();
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
           * Registering AvoRed Hello Middleware
           * @return void
           */
          protected function registerMiddleware()
          {
              $router = $this->app['router'];
              $router->aliasMiddleware('middlewareName', AvoRed\Hello\Http\Middleware\UserProductView::class);
          }


Once you Provider is register you can create an `UserProductView.php` file into your `src/Http/Middleware` folder.

    <?php
    namespace AvoRed\Hello\Http\Middleware;

    use Closure;

    class UserProductView
    {
        /**
         * Handle an incoming request.
         *
         * @param \Illuminate\Http\Request $request
         * @param \Closure $next
         * @param string|null $guard
         *
         * @return mixed
         */
        public function handle($request, Closure $next)
        {
            // Your Code Goes Here
            return $next($request);
        }
    }


#### How to use it into Route
    <?php 
    
    Route::middleware('middlewareName')
            ->group(function() {
                Route::get('product/{slug}','ProductViewController@show')->name('product.view');
            
            });
            
   
    
    

