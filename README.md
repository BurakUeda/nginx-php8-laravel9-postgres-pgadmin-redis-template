## Disclaimer
Hi there!\
I am relatively new to Docker. I was searching for a Docker/Composer project template with PHP 8, Laravel 8, Nginx, Redis, Postgres and PgAdmin but couldn't find the exact setup I needed. So I tried and built one by myself. After a lot of tweaking, I finally got it working. So I am making it public just in case anyone else need this exact setup.

As I said, I am new to this and I am sure you can find some redundant/unnecessary parts in it. Or it might not work at all in your particular environment. Use at your own risk.

## What is included
- PHP 8.2
- Nginx
- Redis
- MailHog
- Postgres
- PgAdmin
- Laravel 8

## PHP extensions
- gd 
- mbstring 
- pdo_pgsql 
- redis
- intl 
- imagick 

# Usage
Clone the repository and enter the folder. Make necessary changes to docker-compose.yml file (Database settings etc.) and run
<pre>
docker-compose build
docker-compose up -d
</pre>

## Creating Laravel project
Inside the **app** folder, run
<pre>
docker-compose exec php sh
composer create-project laravel/laravel=8 ./ --prefer-dist --ignore-platform-reqs
</pre>

## Updating Composer and installing Node modules
While inside the project folder, run
<pre>
docker-compose exec php composer update
docker-compose exec php npm install
</pre>
