# Wordpress Docker

## Requirements

- Docker & docker-compose
- Nodejs & npm

If you do not have **docker**, [install it](https://docs.docker.com/compose/install/).

On a Linux distro, you can install it via package manager, in a debian-based for example you can just run:

```
$ sudo apt install docker docker-composer
```

About **Nodejs & npm**, you can install it from [here](https://nodejs.org/en/).

## Usage

### Docker container

If you installed the requirements you are able to run the application using:

```
$ docker-compose up
```

It will download the related dependencies of the containers and start the project, next time you will need to just start the project you can use:

```
$ npm run docker:start
```

Open your command prompt terminal (on Windows is for example PowerShell), navigate to the repository folder and issue the command:

```
docker-compose up
```

It will set up the docker container and download the necessary dependencies within.

Now you can see the website in [http://localhost:80/](http://localhost:80/).

Make sure that your port 80 is not already used by another service like Apache2, nginx etc.

**WARNING: if you run this in production, comment the phpmyadmin section in docker-compose to not expose the phpmyadmin service to any user or change the mysql credentials**

More info about docker-configuration are available below

### CLI commands available

```
$ npm run docker:db:export
```

Export the mysql database of the current wordpress installation inside the /data/sql folder (backup)

```
$ npm run docker:db:import
```

Import the sql files under /data/sql folder inside the mysql database of the current wordpress installation (restore backup)

## How to export/import database

This repository integrates a script under `/apps/db_exporter` folder that helps you to export the entire database in a SQL dump format.
This script uses the /conf/dist/conf.sh file to configure the db credentials. If you need to change those configurations, you can just
copy/paste that file inside the /conf/ folder to override default values (the files in that directory are git-ignored).

**NOTE:** by default sql files will be exported inside the /data/sql folder

### database export

`npm run docker:db:export`

### database import

`npm run docker:db:import`
