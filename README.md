# The Patient Experience Tracker Project
The Patient Experience Tracker is an online data collection tool that is intended to
facilitate collecting the Patient Reported Outcome Measures (PROMs) and the Patient Reported Experience
Measures (PREMs). 

## Table of Contents

- [1.0 Security](#security)
- [2.0 Background](#background)
- [3.0 Install](#install)
- [4.0 Usage](#usage)
- [5.0 API](#api)
- [6.0 Maintainers](#maintainers)
- [7.0 Contributing](#contributing)
- [8.0 License](#license)

## 1.0 Security

## 2.0 Background

Authentication is handled by auth0, a third-party provider, to successfully add properly handled user security, and password encryption. 

## 3.0 Install

Follow the below installation steps to start the site.

### 3.1 Step One
Install git cli locally on your development computer

On Mac:

A Mac OS binary installer is available at: [Mac OS Binary Installer](https://git-scm.com/download/mac)

On Windows:
Likely the easiest way to install via Windows is by installing Github Desktop, a GUI solution for git that includes git cli, it is available here: 
[Github Desktop](https://desktop.github.com/)

### 3.2 Step Two
You should create a fork of the repo, clone the repo down, and then add push to your fork. At the end
you PR into the main repository.

Next go into the desired directory you wish to install git into on your machine. Then type:

```
git clone https://github.com/CodeItQuick/VWS-Open-Source.git
```

### 3.3 Step Three
Next install docker.

On Mac:
Docker desktop for mac is available on [Get Docker Desktop for Mac on Dockerhub](https://hub.docker.com/editions/community/docker-ce-desktop-mac/)

On Windows:
Docker desktop for Windows is available on [Get Docker Desktop for Windows on Dockerhub](https://hub.docker.com/editions/community/docker-ce-desktop-windows/)

### 3.4 Step Four

Install the environment files that hold passwords. Working env files with default passwords are given for development
environments in '.env-example' files in two directories. Copy or rename these env files to correctly load the environment folder (that holds passwords).

```
cp ./src/.env-example ./src/.env
```

### 3.5 Step Five

We'll need to install the composer and npm packages included with the project. To install the missing required composer packages simply run:

```
docker-compose run --rm composer update
```

### 3.6 Step Six
Finally, spin up the database, and then the VWS PHP Laravel server with the following console commands

```
docker-compose up -d --build nginx
```

Note: You may need to create the directory mysql in the project folder, if you do please let me know so that I can add it to the readme (or submit a PR
to add it yourself). Thanks.

### 3.7 Step Six

The database needs to be created, tables made, and created through Artisan. For instance, if we wanted to create a Users table:

```
docker-compose run --rm artisan migrate:make create_users_table
docker-compose run --rm artisan migrate
docker-compose run --rm artisan db:seed
```

However, once migrations are created we will only ever need to run the latter two commands.

For more information, please read the [Laravel documentation on migrations.](https://laravel.com/docs/4.2/migrations)

### 3.8 Other Useful Commands & Information
To check what ports these two services are running on the following console command will run them:
```
docker-compose ps
```

Visit localhost to see the current website!

At any time if you wish to take down the website this is done with the command:

```
docker-compose down
```

## 4.0 Usage

To run the server through a simple php command, assuming all extensions are installed, 

```
docker-compose up 
```

Then visit localhost:8080 in the browser to see the webpage.

Note: you may have to connect to the container remotely with VSCode, and/or you could mess with the ports
by adding ports: '8080:8080' to the config under myapp for docker-compose.yml.
## 5.0 API

## 6.0 Maintainers

[@CodeItQuick](https://github.com/CodeItQuick)

## 7.0 Contributing

See [the contributing file](contributing.md)!

PRs accepted.

Small note: If editing the README, please conform to the [standard-readme](https://github.com/RichardLitt/standard-readme) specification.

## 8.0 License

MIT © 2020 CodeItQuick
