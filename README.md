# laravel_10_crud
    - This is a laravel 10 CRUD app **with** recycle bin feature.
    - forked from: [https://github.com/Kingsconsult/laravel_8_recycle_bin](https://github.com/Kingsconsult/laravel_8_recycle_bin)

# upgrade laravel 8.0 project to laravel 10

1. In /composer.json replace the following entries:

    - "php": "^7.3"  **with**   "php": "^8.1"
    - "laravel/framework": "^8.0"  **with**  "laravel/framework": "^10.0"
    - "nunomaduro/collision": "^5.0"  **with**  "nunomaduro/collision": "^7.0"
    - "phpunit/phpunit": "^9.3"  **with**  "phpunit/phpunit": "^10.0"

2. Remove the following entries from composer.json

    - "fideloper/proxy": "^4.2"
    - "fruitcake/laravel-cors": "^2.0"
    - "facade/ignition": "^2.3.6"

3. In /App/Http/Kernel.php replace:

    - \Fruitcake\Cors\HandleCors::class  **with**  \Illuminate\Http\Middleware\HandleCors::class

4. In /App/Http/Middleware/TrustProxies.php replace:

    - use Fideloper\Proxy\TrustProxies as Middleware;  **with**  use Illuminate\Http\Middleware\TrustProxies as Middleware;

    - Request::HEADER_X_FORWARDED_ALL;    **with** the following lines:
  
      - Request::HEADER_X_FORWARDED_FOR |
        Request::HEADER_X_FORWARDED_HOST |
        Request::HEADER_X_FORWARDED_PORT |
        Request::HEADER_X_FORWARDED_PROTO |
        Request::HEADER_X_FORWARDED_AWS_ELB;

5. run command/> composer update

and enjoy...
