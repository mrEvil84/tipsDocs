# Laravel Tips

## Installation sail

### Install all

```
curl -s https://laravel.build/example-app | bash
```

### Install with selected services

```
curl -s "https://laravel.build/example-app?with=mysql,redis" | bash
```

[mysql, pgsql, mariadb, redis, memcached, meilisearch, typesense, minio, selenium, mailpit]

### Default dev container

```
curl -s "https://laravel.build/example-app?with=mysql,redis&devcontainer" | bash
```

### up
```
./vendor/bin/sail up
```
### db migrate
```
./vendor/bin/sail artisan migrate
```

## Entry point of all requests

```
public/index.php
```

### Creating instance of app

```
bootstrap/app.php
```

###  next steps (Kernel) request lifecycle
```

handleCommand - consoleKernel
handleRequest - httpKernel

Kernel (hanle) // take Request , return Response 
   |
   |
bootstrapers // run before request is executed
	     // error handling, configure logging etc.
	     // internal laravel config 
   |
   |
middleware // reading,writing http session
           // determining app maintenance mode 
           // veryfying csrf token and more.
    |
    |
loading service providers // bootstraping framework components (every major feature offered by Laravel is bootstrapped and configured by a service provider)
    |
 register() - // on each loaded provider
 boot()     - // on each loaded provider 
    | 
 bootstrap/providers.php // 3rd party service providers for self defining -> @see app/Providers -> AppServiceProvider
    |
 Router (handling request) // dispatch Request to a route or Controller, run route speciffic middleware
    |
 (route middleware) // filter or examine http request entering to app      
    |
 Controller 
    |
 Response
    | 
 Response middleware // chance to modify Response by Middleware 
    |
 send() // method in kernel that sends response to browser         
    
```



