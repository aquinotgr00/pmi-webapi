# pmi-webapi

REST API Server for both back end and mobile app users

## Getting Started

### Prerequisites
* [Laravel Passport](https://laravel.com/docs/5.8/passport)
```sh
composer require laravel/passport
php artisan migrate
php artisan passport:install
```
* [Queues](https://laravel.com/docs/5.8/queues#introduction)
```sh
php artisan queue:table
php artisan migrate
php artisan queue:work
```

## Installing packages
### PMI Admin
```bash
composer require bajaklautmalaka/pmi-admin
```
migrate all database tables necessary for this package
```sh
php artisan migrate
```

### PMI Donations
```bash
composer require bajaklautmalaka/pmi-donatur
```
migrate all database tables necessary for this package
```sh
php artisan migrate
```

### PMI Voluntaries
```bash
composer require bajaklautmalaka/pmi-relawan
```
migrate all database tables necessary for this package
```sh
php artisan migrate
```

## Usage
### Admin Authentication
#### Login
using API testing tools ([Postman](https://www.getpostman.com), for example), make a `POST` request to `/api/admin/login` with `request headers` as follows:
```sh
Accept:application/json
Content-type:application/json
```
Given a request body below :
```json

	{
		"email": "admin@mail.com",
		"password": "Open1234"
	}
```
then the valid response you're getting should be :
```json

	{
		"status": "success",
		"data": {
			"token": "<<auth token here>>"
		}
	}
```

#### Logout
make a `GET` request to `/api/admin/logout` with `request headers` as follows:
```sh
Accept:application/json
Authorization:Bearer <<auth token>>
```

### Response macros
#### [JSend](https://github.com/omniti-labs/jsend)
* Response type : **Success**
```php

	return response()->success(['category'=>'Blog']);
```
will render response:
```json

	{
		"status": "success",
		"data": {
			"category": "Blog"
		}
	}
```
* Response type : **Fail**
```php

	return response()->fail([
		"errors"=>[
			['name'=>'field name is required'],
			['email'=>'invalid email format']
		]
	]);
```
will render response:
```json

	{
		"status": "fail",
		"data": {
			"errors":[
				{"name": "field name is required"},
				{"email": "invalid email format"}
			]
		}
	}
```

## Testing
Run the tests with:

``` bash
vendor/bin/phpunit
```
