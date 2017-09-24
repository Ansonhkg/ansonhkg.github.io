---
layout: default
title: Notes
permalink: /mynotes/
---

# Laravel 5.5

## Consuming self API

```ruby
$request = Request::create('/api/users/1', 'GET');
$response = app()->handle($request)->getData();
```
## Call external API 
Guzzle is an HTTP client built with and for PHP. The cURL software has typically handled all of the HTTP heavy lifting in PHP, or in some cases of quick hacking, the good old file_get_contents() function. Guzzle is a bit more advanced and simple at the same time. The software itself is quite impressive, providing a nice elegant solution to the developer that is easy to use. All the complexity is hidden away in the class implementation.

#### Instsall Guzzle package via composer:

``` c
# If you have composer installed globally
composer require guzzlehttp/guzzle

# If you don't have composer
curl -sS https://getcomposer.org/installer | php
composer require guzzlehttp/guzzle
```

#### Use its namespace
``` ruby
use GuzzleHttp\Exception\GuzzleException;
use GuzzleHttp\Client;
```

#### Then use it easily, e.g:
``` ruby
$client = new Client(); //GuzzleHttp\Client
$response = $client->get('http://backend.dev/api/user');
return $response;
```




> Reference: 
- [Consuming my own Laravel API](https://stackoverflow.com/questions/16520691/consuming-my-own-laravel-api){:target="_blank"}
- [[4.2] Test Route Dispatching With Request Params](https://github.com/laravel/framework/pull/5886#issuecomment-57627117){:target="_blank"}
- [Using GuzzleHttp with Laravel](https://medium.com/laravel-5-the-right-way/using-guzzlehttp-with-laravel-1dbea1f633da)
- [Guzzle Documentation](http://guzzle.readthedocs.io/en/latest/)

