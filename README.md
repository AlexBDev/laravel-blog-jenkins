[![Build Status](https://travis-ci.org/AlexBDev/laravel-blog-jenkins.svg?branch=master)](https://travis-ci.org/AlexBDev/laravel-blog-jenkins)

## Stack

- PHP-FPM 7.1 (composer)
- NGINX 1.13
- MySQL 5.7
- Maildev
- PhpMyAdmin

## How to use

### Nginx

- Add your nginx configuration for different sites under sites directory, check the example example.site.conf
- Add domain name in `/etc/hosts` with ip 172.45.0.10

### Docker

- To deal with permission between shared volumes with host and guest, you must run

```bash
$ source user-permission.sh
```

- Run docker-compose.yml

```bash
$ docker-compose up -d
```

- Open your browser to http://example.mysite (or another configured domain name)

### Port

- 8080:80 NGINX (172.45.0.10)
- 1080:80 Maildev front web
- 1025:25 Maildev smtp
- 8888:80 PhpMyAdmin

# Bootstrap laravel

Create database from mysql or phpmyadmin (http://localhost:8888)

```bash
$ docker-compose exec php bash 
$ composer install
$ php artisan migrate
```

## Additional tools

* phploc

use example:
`vendor/bin/phploc app/`


## Tips

`PATH="./vendor/bin:$PATH"`

To run your project commands without calling _./vendor/bin_
