# WordPress (FPM Edition) - Docker

Notes on deploying a single site [WordPress FPM Edition](https://hub.docker.com/_/wordpress/) instance as a docker deployment orchestrated by Docker Compose.

- Use the FPM version of WordPress (v5-fpm)
- Use MySQL as the database (v8)
- Use Nginx as the web server (v1)
- Use phpMyAdmin as the database management tool (latest)
- Include self-signed SSL certificate ([Let's Encrypt localhost](https://letsencrypt.org/docs/certificates-for-localhost/) format)

## 1 - Requirements

### Docker
You can download and install Docker and Docker-compose depending on your platform :

- https://docs.docker.com/install/
- https://docs.docker.com/compose/install/


### TaskFile
Install TaskFile:
 ```bash
 sh -c "$(curl --location https://taskfile.dev/install.sh)" -- -d
 
 ## For MacOS only
 brew install go-task/tap/go-task
 ```
For more info about TaskFile, visit: https://taskfile.dev/#/installation


## 2 - Configuration
### Update environment variables 
In .env file, replace variables to fit your needs
 ```bash
# MySQL Settings
WORDPRESS_DB_NAME=wordpress
ORDPRESS_DB_USER=wordpress
WORDPRESS_DB_PASSWORD=password123!
MYSQL_ROOT_PASSWORD=rootpassword123!

# Nginx Settings
NGINX_PROJECT=local
NGINX_HOST=wordpress.fr
 ```

### 
Add a `local.wordpress.fr` to your `/etc/hosts` file (depending on variables NGINX_PROJECT & NGINX_HOST configured in previous step) :
 ```bash
# /etc/hosts
 127.0.0.1 local.wordpress.fr
 ::1 local.wordpress.fr
 ```


## 3 - Install

### Site 
Copy content of website in the wordpress folder 



### Run
You can install project using docker compose commands `build, up.` or by just running the following task command:
 ```bash
 task install
 
 ## list all tasks
 task --list
 ```

## 4 - Check it out
- https://local.wordpress.fr