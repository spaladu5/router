# Router
A simple router for PHP, inspired by Express.js and Laravel.

## Description
This is a simple router. It is a simple router that uses the `window.location` object to determine the current route and render the appropriate component.

## Installation
```bash
composer require josegarcia/router
```

## Usage

```php
<?php

require_once __DIR__ . '/vendor/autoload.php';

use Garcia\Router;

// Example of a simple route
Router::addRoute('GET', '/health', fn () => 'Hello, world!');

// Example of a route with a parameter
Router::addRoute('GET', '/health/:id', fn ($params) => "User ID: {$params['id']}");

// Example of a route that returns a JSON response
Router::get( '/api/health/:id', fn ($params) => ['id' => $params['id'], 'name' => 'John Doe', 'email' => 'john@example.com']);

// Example of rendering a view
Router::get('/view', fn () => [
    // we need to pass the view name and the data to be rendered as a template
    'view' => 'template',
    // we can also pass the path to the views directory
    'path' => 'views',
    // we can also pass the data to be rendered
    'data' => [
        'name' => 'John Doe'
    ]
]);

// Example of rendering
Router::get('/redirect', fn () => redirect('http://www.example.com'));

Router::run();
```

## License
MIT
