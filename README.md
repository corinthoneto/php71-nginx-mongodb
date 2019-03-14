# Docker, PHP 7.1, Nginx and MongoDB for Laravel/Lumen or any PHP applications

This setup is great for writing quick apps in PHP using Lumen from an any Docker client. It uses docker-compose to setup the application services.

## Clone this repo

```bash
git clone https://github.com/corinthoneto/php71-nginx-mongodb.git
cd php71-nginx-mongodb
```

## Create Lumen App

now, create the lumen (or Laravel) app inside `images/php` directory named

`For Latest lumen version`

```bash
cd images/php
docker run --rm -it -v $(pwd):/app corinthoneto/lumen-cli lumen new app
```
`For 5.6 lumen version`

```bash
cd images/php
docker run --rm -it -v $(pwd):/app corinthoneto/lumen-cli composer create-project laravel/lumen app "5.6.*"
```

The name `app` is for correct operation (in this case, to modify `docker-compose.yml` if using other name)

## Existing Lumen App (considering the `app` folder is your main application folder)

```bash
cd images/php/app
docker run --rm -it -v $(pwd):/app corinthoneto/lumen-cli composer install
```

## Install mongodb support on laravel/lumen
```bash
cd images/php/app 
docker run --rm -it -v $(pwd):/app corinthoneto/lumen-cli composer require jenssegers/mongodb --ignore-platform-reqs
```

### Configuration

To change configuration values, look in the `docker-compose.yml` file and change the `php` container's environment variables. These directly correlate to the Lumen environment variables.

## Docker and Docker Compose Setup

### [Docker for Mac](https://docs.docker.com/docker-for-mac/)

### [Docker for Windows](https://docs.docker.com/docker-for-windows/)

### [Docker for Linux](https://docs.docker.com/engine/installation/linux/)

### [Docker compose](https://docs.docker.com/compose/)

### Build & Run

```bash
Inside ../php71-nginx-mongodb
docker-compose up --build -d
```

Navigate to [http://localhost](http://localhost)

Success! You can now start developing your Lumen app on your host machine and you should see your changes on refresh! Classic PHP development cycle. A good place to start is `images/php/app/routes/web.php`.

Feel free to configure the default port 80 in `docker-compose.yml` to whatever you like.

### Stop Everything

```bash
Inside ../php71-nginx-mongodb
docker-compose stop
```
