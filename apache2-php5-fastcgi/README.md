# Apache2 PHP5 using fastcgi

Created to run a Yii Framework application and use an external mysql server  
Works if you input a docker mysql container too!

## Stack

+ `ubuntu 12.04`
+ `apache 2.4 mpm worker with fastcgi`
+ `php 5.5 fpm`
+ `curl`
+ `memcached` you know, for cache

PHP extensions

+ `php-curl` enable php curl extension
+ `php-memcache` PHP MemCache
+ `php-mysqlnd` MySQL client
+ `php5-apcu` APC cache
+ `php5-gd` gd image library
+ `php5-mcrypt` useful for password hashing
+ `php5-fpm` fastcgi service

Apache modules

+ `rewrite`
+ `actions`
+ `fastcgi`
+ `alias`

## How to use

you need [Docker](http://www.docker.com/) installed first

```sh
docker run -p 80 -v $(pwd):/var/www gusnips/apache2-php5-fastcgi
```

Now access [http://localhost](http://localhost) and be happy!  

You could replace $(pwd) with your apache entry folder, like `~/htdocs` or something  

