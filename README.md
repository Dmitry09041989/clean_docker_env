Create a project directory.

Project dir structure:

```text
project_folder/ {
 src
 nginx/conf
 mysql/data
 redis/data 
 }

```

Clone the repo into the project dir.

Clone the Laravel repo using the command below. (Laravel files will be located in ./src folder)  
>git clone https://github.com/laravel/laravel.git src

Configure the db environment variables.

```text
MYSQL_DATABASE: db_name
MYSQL_ROOT_PASSWORD: root_pw
MYSQL_PASSWORD: db_pw
MYSQL_USER: user_name
SERVICE_TAGS: dev
SERVICE_NAME: mysql
```

Configure the .env.example db variables

```text
DB_CONNECTION=mysql
DB_HOST=mysql
DB_PORT=3306
DB_DATABASE=db_name
DB_USERNAME=db_name
DB_PASSWORD=db_pw
```

Project directory must be as shown above.

Execute below command to start up docker environment.

Wait through the installation process.
>docker-compose up -d

Once the installation is complete run below command to install the dependencies.  

The Docker environment must be running while dependencies are installed.
>docker-compose exec app composer install

Create a copy of .env.example file and generate a new encryption key.
>docker-compose exec -T app cp .env.example .env

>docker-compose exec -T app php artisan key:generate

Clear configuration cache.

>docker-compose exec app php artisan config:clear

Run the migrations.

>docker-compose exec app php artisan migrate

To install redis, mailhog and more follow the instructions from the original article, starting from section 4.3.

[Link to the original article by Isaac Souza](https://www.linkedin.com/pulse/how-create-laravel-development-environment-using-docker-isaac-souza/)
