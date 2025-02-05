# Prerequisite
- OS Ubuntu focal/jammy
- Docker installed on VM, refer to here: https://docs.docker.com/engine/install/ubuntu/
- For detail configuration, refer here: https://www.digitalocean.com/community/tutorials/how-to-install-and-set-up-laravel-with-docker-compose-on-ubuntu-22-04

# Steps
1. Clone your source code into VM
2. List folder & enter the source code folder
3. Change owner of folder, into user you will create later in docker-compose 
4. Create docker-compose.yml file
5. Create Dockerfile
6. Create file nginx.conf
7. Create file mysql.ini
8. Build image
9. Create container

# Run After container up

```
docker-compose exec app ls -l (make sure you see group owner is your user)
docker-compose exec app rm -rf vendor composer.lock
docker-compose exec app composer install
docker-compose exec app php artisan key:generate
docker-compose exec app php artisan migrate:fresh
docker-compose exec app php artisan migrate:fresh --seed
docker-compose exec app php artisan db:seed --class=UserSeeder
```
