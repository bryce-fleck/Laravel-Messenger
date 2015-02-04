[![Build Status](https://img.shields.io/travis/cmgmyr/laravel-messenger/develop.svg?style=flat-square)](https://travis-ci.org/cmgmyr/laravel-messenger)
[![Code Climate](https://img.shields.io/codeclimate/github/cmgmyr/laravel-messenger.svg?style=flat-square)](https://codeclimate.com/github/cmgmyr/laravel-messenger)
[![Latest Version](https://img.shields.io/github/release/cmgmyr/laravel-messenger.svg?style=flat-square)](https://github.com/cmgmyr/laravel-messenger/releases)
[![Total Downloads](https://img.shields.io/packagist/dt/cmgmyr/messenger.svg?style=flat-square)](https://packagist.org/packages/cmgmyr/messenger)
[![Software License](https://img.shields.io/badge/license-MIT-brightgreen.svg?style=flat-square)](LICENSE)

# Laravel Messenger
This package will allow you to add a full user messaging system into your Laravel application.

## Features
* Multiple conversations per user
* Optionally loop in additional users with each new message
* View the last message for each thread available
* Returns either all messages in the system, all messages associated to the user, or all message associated to the user with new/unread messages
* Return the users unread message count easily
* Very flexible usage so you can implement your own acess control

## Common uses
* Open threads (everyone can see everything)
* Group messaging (only participants can see their threads)
* One to one messaging (private or direct thread)

## Installation (Laravel 5.x)
In composer.json:

    "require": {
        "cmgmyr/messenger": "dev-develop"
    }

Run:

    composer update

Add the service provider to `config/app.php` under `providers`:

    'providers' => [
        'Cmgmyr\Messenger\MessengerServiceProvider'
    ]

Publish Assets

	php artisan vendor:publish --provider="Cmgmyr\Messenger\MessengerServiceProvider"
	
Update config file to reference your User Model:

	config/messenger.php
	
Create a `users` table if you do not have one already. If you need one, simply use [this example](https://github.com/cmgmyr/laravel-messenger/blob/develop/src/Cmgmyr/Messenger/examples/create_users_table.php) as a starting point, then migrate.

__Note:__ if you already have a `users` table and run into any issues with foreign keys, you may have to make the `id` unsigned.

Migrate your database:

    php artisan migrate

Add the trait to your user model:

    use Cmgmyr\Messenger\Traits\Messagable;
    
    class User extends Model {
    	use Messagable;
    }


## Examples
* [Controller](https://github.com/cmgmyr/laravel-messenger/blob/develop/src/Cmgmyr/Messenger/examples/MessagesController.php)
* [Routes](https://github.com/cmgmyr/laravel-messenger/blob/develop/src/Cmgmyr/Messenger/examples/routes.php)
* [Views](https://github.com/cmgmyr/laravel-messenger/tree/develop/src/Cmgmyr/Messenger/examples/views)

## Contributing? 
Please format your code before creating a pull-request:

    vendor/bin/php-cs-fixer fix --level psr2 .

### Special Thanks
This package used [AndreasHeiberg/laravel-messenger](https://github.com/AndreasHeiberg/laravel-messenger) as a starting point.