<p align="right" width="100%">
    <img src="https://drive.usercontent.google.com/download?id=1KbYhPopR37y50wHRMne7FRKLLUN-usi1" height="100">
</p>

# Tyzen9's docker-piwigo-mysql
Docker container that provides both Piwigo and MySQL services

## Prerequisites
Install [Docker Engine](https://docs.docker.com/get-docker/) or [Docker Desktop](https://docs.docker.com/desktop/) if you require the Docker user interface.  In production it's generally best to use [Docker Engine](https://docs.docker.com/get-docker/) on a Linux host operating system.

This documentation assumes you have a working knowledge of [Docker](https://www.docker.com/), [MySQL](https://www.mysql.com/), and [Piwigo](https://piwigo.org/).

## Configuration
This `docker-compose` implementation is configured using a `.env` file.  
The `.env` file contains comments explaining what each configuration value does.

1. Rename the `.env.sample` file to `.env`
2. Edit the `.env` file and populate the parameters according to your environment.

If you desire the ability to connect to the MySQL instance from another machine (for example with MySQL Workbench), then uncomment the following lines in the `docker-compose.yml` file by removing the `#` characters:

```yaml
    # ports:
    #  - ${MYSQL_EXTERNAL_PORT}:3306
```

## Development Deployment
Once the `.env` file is created and populated according to the needs of your development environment, using the command prompt navigate to the project's root directory and run the following command:

```
docker compose up
```

> **Note**
> After using 'docker-compose up', 'docker-compose start' and 'docker-compose stop' commands may be used.

## First time Piwigo "Installation"
When running the service for the first time on `http://host_name:<PIWIGO_EXTERNAL_PORT>`, you will be prompted to install Piwigo. You will need information from the `.env` file to complete this.

<p align="center" width="100%">
    <img src="./docs/images/piwigoInstall.png" width=50% height=50%>
</p>

### Database Configuration

1. For the `Host` use `mysql`, which is the service name in the `docker-compose.yml` file
2. For `User` use the `MYSQL_USER` from the `.env` file
3. For `Password` use the `MYSQL_PASSWORD` from the `.env` file
4. For `Database name` use the `MYSQL_DATABASE` from the `.env` file

### Administration Configuration

These are the settings that are used to configure the Piwigo administration console.  You should use a strong username and password combination here.

Finally, click `Start Installation` and you Piwigo is set and ready to be used.  The first thing you will likely want to do is login to the Administration Panel and [import your galleries](https://piwigo.org/doc/doku.php?id=user_documentation:learn:add_picture). 