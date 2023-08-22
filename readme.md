# docker-compose 3.9 with MariaDB, Nginx and PHP 8.1 with ionCube Loader and Xdebug

## ARM.64 M1 M2 (MacBooks)


Just run: 

`docker compose build`

When ready:

`docker compose up`

## x86_64 (Intel)

Change the name of the file docker-compose.yml.x86_64.example to docker-compose.override.yml and follow the previus steps. 

# Review the output

Navigate to `localhost:8016/info.php` and you will see the phpinfo() output.

Now you are ready to copy  your PHP code  to 

`./www/html/`

Happy developing!






