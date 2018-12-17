# Installation

* [Installation](#installation)
  * [Server Requirements](#server-requirements)
  * [Installing AvoRed E cimmerce](#installing-avored-ecommerce)

## Installation

<a name="server-requirements"></a>
> ### Server Requirements

The AvoRed E commerce framework has a few system requirements.

Below is the list which you will need to make sure your server meets the following requirements:

* PHP &gt;= 7.1.3
* OpenSSL PHP Extension
* PDO PHP Extension
* GD Library \(Image Processing\)
* Mbstring PHP Extension
* Tokenizer PHP Extension
* XML PHP Extension
* Ctype PHP Extension
* JSON PHP Extension
* Curl PHP Extension

<a name="installing-avored-ecommerce"></a>
### Installing AvoRed E commerce

AvoRed E commerce utilizes [Composer](https://getcomposer.org) to manage its dependencies. So, before using AvoRed E commerce, make sure you have Composer installed on your machine.

#### Via Composer Create-Project

Alternatively, you may also install Laravel by issuing the Composer `create-project` command in your terminal:

```text
composer create-project --prefer-dist avored/laravel-ecommerce
```

#### Set up your Envirionment\(.env\) file

```text
laravel-ecommerce/.env 
```

### Execute the AvoRed Install Command

```text
php artisan avored:install
```

### Execute the AvoRed Admin Make Command

```text
php artisan avored:admin:make
```

Once you finished the Installation Command for the Admin Access you can just visit

```text
yoursite.com/admin
```

That's it!

#### Directory Permissions

After installing AvoRed E commerce, you may need to configure some permissions. Directories within the `storage` and the `public/uploads` directories should be writable by your web server or AvoRed E commerce will not run.

#### Application Key

The next thing you should do after installing AvoRed E commerce is set your application key to a random string. If you installed AvoRed E commerce via Composer, this key has already been set for you by the `php artisan key:generate` command.

Typically, this string should be 32 characters long. The key can be set in the `.env` environment file. If you have not renamed the `.env.example` file to `.env`, you should do that now. **If the application key is not set, your user sessions and other encrypted data will not be secure!**

