# Want to use AvoRed Framework as a package in your existing laravel project

AvoRed framework package contains the core features for the avoRed e commerce for laravel.


##### How to use it in your existing laravel project

 First of all install the package via composer 
 
     composer require avored/framework
     
 Next step is to publish the file with these command
 
     php artisan vendor:publish --provider="AvoRed\Framework\AvoRedProvider"
     
  Next step is to finished the framework last few finishing touch.
  
      php artisan avored:install
      
Last step to create your admin account

    php artisan avored:admin:make
    
    
That's It.

Now you can simply visit your Admininistrator via

    yoursiteurl.com/admin
