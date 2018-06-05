# symfony_snippets with docker

#### make migrations, entities, controllers etc.

winpty docker-compose exec php-fpm php bin/console make:{migration/entity/controller}

#### migrate

winpty docker-compose exec php-fpm php bin/console doctrine:migrations:migrate

#### drop database

winpty docker-compose exec php-fpm php bin/console doctrine:database:drop --force

#### create database

winpty docker-compose exec php-fpm php bin/console doctrine:database:create


________________________________________________________________________________________________________________________________

# laravel snippets

#### link storage
php artisan storage:link

#### link storage manually
ln -sfn /var/www/source/public/ /var/www/source/public_html/storage

___________________________________________________________________________________________________________________________________


# docker_snippets

#### list all container ids

docker ps -aq

#### stop all running containers

docker stop $(docker ps -aq)

#### remove all containers

docker rm $(docker ps -aq)

#### remove all images

docker rmi $(docker images -q)
