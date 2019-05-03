# Dokerize Symfony application

**Contains:**
- Nginx
- php7
- MySQL
- ELK stack (Elasticsearch, Kibana, Logstash) with Filebeat
- NodeJs

## Run symfony app in Docker containers:

1. 
    Clone this repo

2. 
    Go to the cloned folder
    ```bash
    cd docker-symfony
    ```
3.
    Create new empty folder (by default this folder must call 'app'. But if project folder have different name, you must change APP_DIR variable in docker/.env file to actual folder name. For example, `APP_DIR=../other_folder_name/`) and put you app in this folder.
    ##### Notice
    _You can clone any repository, like `git clone git@github.com:symfony/demo.git`_
    ##### Notice
    _If symfony version < 3.4 you must change NGINX_ROOT variable in docker/.env file to /var/www/html/app and use nginx configuration (changw file docker/nginx/default.conf) appropriate symfony version (for example for 2.8 version https://symfony.com/doc/2.8/setup/web_server_configuration.html#nginx)_

4.
    Go to the folder named 'docker' 
    ```bash
    cd docker
    ```
5. 
    Up the containers
    ```bash
    docker-compose up -d --build
    ```
6. 
    If you project need to install composer dependencies, run
    ```bash
    docker-compose run composer install
    ```

    or, before step 5, you can uncomment 'command: install' string in docker/docker-compose.yml file in composer service section.

7. 
    Yor project available in http://localhost/

If used webpack to build frontend run ```bash docker-compose run node yarn encore production```

### Other links:
* phpMyAdmin http://localhost:8080/
* Kibana http://localhost:5601/
* Elasticsearch http://localhost:9200/

After up the containers, a 'data' folder will appear in the 'docker-symfony' folder, which contains logs, elasticsearch indices and a database.
