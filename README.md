# Laravel 9.0 blog



The purpose of this repository is to show good development practices on [Laravel](http://laravel.com/) as well as to present cases of use of the framework's features like:

- [Authentication](https://laravel.com/docs/9.x/authentication)
- API
  - Token authentication
  - [API Resources](https://laravel.com/docs/9.x/eloquent-resources)
  - Versioning
- [Blade](https://laravel.com/docs/9.x/blade)
- [Broadcasting](https://laravel.com/docs/9.x/broadcasting)
- [Cache](https://laravel.com/docs/9.x/cache)
- [Email Verification](https://laravel.com/docs/9.x/verification)
- [Filesystem](https://laravel.com/docs/9.x/filesystem)
- [Helpers](https://laravel.com/docs/9.x/helpers)
- [Horizon](https://laravel.com/docs/9.x/horizon)
- [Localization](https://laravel.com/docs/9.x/localization)
- [Mail](https://laravel.com/docs/9.x/mail)
- [Migrations](https://laravel.com/docs/9.x/migrations)
- [Policies](https://laravel.com/docs/9.x/authorization)
- [Providers](https://laravel.com/docs/9.x/providers)
- [Requests](https://laravel.com/docs/9.x/validation#form-request-validation)
- [Seeding & Factories](https://laravel.com/docs/9.x/seeding)
- [Testing](https://laravel.com/docs/9.x/testing)
- [Homestead](https://laravel.com/docs/9.x/homestead)

Beside Laravel, this project uses other tools like:

- [Bootstrap 5.x](https://getbootstrap.com/)
- [Pint](https://github.com/laravel/pint)
- [Travis CI](https://travis-ci.org/)
- [Font Awesome](https://fontawesome.com/)
- [Hotwired](https://hotwired.dev/)
- [Redis](https://redis.io/)
- [spatie/laravel-medialibrary](https://github.com/spatie/laravel-medialibrary)
- [hotwired-laravel/turbo-laravel](https://github.com/hotwired-laravel/turbo-laravel)
- Many more to discover.

## Some screenshots

You can find some screenshots of the application on : [https://imgur.com/a/Jbnwj](https://imgur.com/a/Jbnwj)

## Installation

To create your development environment [follow these instructions](https://laravel.com/docs/10.x/installation).

Setting up your development environment on your local machine:
```bash
$ git clone https://github.com/guillaumebriday/laravel-blog.git
$ cd laravel-blog
$ cp .env.example .env
$ php artisan key:generate
$ php artisan horizon:install
$ php artisan telescope:install
$ php artisan storage:link
```

## Before starting
You need to run the migrations with the seeds :
```bash
$ php artisan migrate --seed
```

This will create a new user that you can use to sign in :
```yml
email: darthvader@deathstar.ds
password: 4nak1n
```

And then, compile the assets :
```bash
$ yarn dev # or yarn watch
```

Starting job for newsletter :
```bash
$ php artisan tinker
> PrepareNewsletterSubscriptionEmail::dispatch();
```

## Useful commands
Seeding the database :
```bash
$ php artisan db:seed
```

Running tests :
```bash
$ php artisan test
```

Running Laravel Pint :
```bash
$ ./vendor/bin/pint --verbose --test
```

Generating backup :
```bash
$ php artisan vendor:publish --provider="Spatie\Backup\BackupServiceProvider"
$ php artisan backup:run
```

Generating fake data :
```bash
$ php artisan db:seed --class=DevDatabaseSeeder
```

Discover package
```bash
$ php artisan package:discover
```

In development environment, rebuild the database :
```bash
$ php artisan migrate:fresh --seed
```

## Accessing the API

Clients can access to the REST API. API requests require authentication via token. You can create a new token in your user profile.

Then, you can use this token either as url parameter or in Authorization header :

```bash
# Url parameter
GET http://laravel-blog.app/api/v1/posts?api_token=your_private_token_here

# Authorization Header
curl --header "Authorization: Bearer your_private_token_here" http://laravel-blog.app/api/v1/posts
```

API are prefixed by `api` and the API version number like so `v1`.

Do not forget to set the `X-Requested-With` header to `XMLHttpRequest`. Otherwise, Laravel won't recognize the call as an AJAX request.

To list all the available routes for API :

```bash
$ php artisan route:list --path=api
```

## Contributing

Do not hesitate to contribute to the project by adapting or adding features ! Bug reports or pull requests are welcome.


