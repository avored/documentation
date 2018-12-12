# AvoRed Themes

When it comes to theme its one of the integral part for any e commerce store and we understand as each business are different so do their theme or the way they interact with their customer and vice versa. That's the one of the big reason we give all the freedom to build a custom theme with AvoRed E commerce. When it comes to themes we use blade template engine which is the same as laravel framework use. If you want to more about blade template engine you can always visit laravel blade [docs](https://laravel.com/docs/5.7/blade) for more information.

View files contains the Html/CSS markup used by your shopping cart store. View Files stores into `themes/company-name/theme-name/views` folder. But we have a fallback views if AvoRed don't find a file into your activated theme then it use defaults views supply by AvoRed which is stored in `themes/avored/default`.

A Simple Hello World file should look like below

AvoRed

## Hello World

As view is created inside a `themes/company-name/theme-name/views/hello-world.blade.php` inside your controller you can simply use `view("hello-world")`

```php
public function helloWorld() {
    return view('hello-world');
}
```

### How to pass an Variable from Controller to View

If you want to Greet a Person with his/her name inside a `hello-world` views you can simply use `with` method as shown below

```php
@extends('layouts.app')

@section('meta_title', 'Hello World - AvoRed Shopping Cart')
@section('meta_description', 'Hello World from AvoRed Shopping Cart')

@section('content')
    <div class="container">
        <div class="row">
            <div class="col-12">
                <h1>Hello World</h1>
                <p>Hello from: {{ $name }}</p> <!-- If you are passing an $name variable from controller it get render like below -->
            </div>
        </div>
    </div>
```


### How to check if a View Exists

If you want to check if the view exists or not before you return view inside you controller you can simply use an `exists` method like below:

```php
use Illuminate\Support\Facades\View;
if (View::exists('hello-world')) {
    return view('hello-world')
}
```
