# theme-views

## AvoRed Theme Views

View files contains the Html markup used by your shopping cart app. For example your Product Page or Checkout Page Html. View Files stores into `themes/vendor/theme-name/views` folder where Vendor & Theme Name is your Activated Theme. But we have a fallback views if AvoRed don't find a file into your activated theme then it use defaults views supply by AvoRed.

A Simple Hello World file should look like below

AvoRed

## Hello World

As view is created inside a `themes/vendor/theme-name/views/hello-world.blade.php` inside your controller you can simply use `view("hello-world")`

```text
public function helloWorld() {
    return view('hello-world');
}
```

### How to pass an Variable from Controller to View

If you want to Greet a Person with his/her name inside a `hello-world` views you can simply use `with` method as shown below

```text
public function helloWorld() {
    $name = "John Doe";
    return view('hello-world')->with('name', $name);
}
```

Inside a View or Blade file you can simply use as an Variable:

AvoRed

## Hello {{ $name }}

### How to check if a View Exists

If you want to check if the view exists or not before you return view inside you controller you can simply use an `exists` method like below:

```text
use Illuminate\Support\Facades\View;

if (View::exists('hello-world')) {
    //
}
```

