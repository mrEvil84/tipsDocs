Laravel Tips

-- installation sail

--- [Install all]

```
curl -s https://laravel.build/example-app | bash
```

--- [Install with selected services]

```
curl -s "https://laravel.build/example-app?with=mysql,redis" | bash
```

[mysql, pgsql, mariadb, redis, memcached, meilisearch, typesense, minio, selenium, mailpit]

--- [Default dev cointainer]

```
curl -s "https://laravel.build/example-app?with=mysql,redis&devcontainer" | bash
```

-- up
```
./vendor/bin/sail up
```
-- db migrate
```
./vendor/bin/sail artisan migrate
```
-- entry point of all requests

```
public/index.php
```

-- creating instalce of app

```
bootstrap/app.php
```

-- next steps
```

handleCommand - consoleKernel
()handleRequest - httpKernel
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
```



