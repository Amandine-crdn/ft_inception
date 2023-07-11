# Install your virtual machine
- download your image and create VM on VirtualBox
  ```sudo apt-get update```
  ```sudo apt install vim``` and if you need the IDE of your choice (VSCode for exemple)
  ```sudo apt-get install git```
  ```sudo apt-get install build-essential```
  ```apt-get install curl -y```
  
# Create new ssh key on your intra
  ```ssh-keygen```
  ```cat ~/.ssh/id_rsa.pub```
  clone your repository and open the subject

# Install docker compose
*https://docs.docker.com/compose/install/linux/#install-the-plugin-manually*
``` sudo curl -L "https://github.com/docker/compose/releases/download/1.29.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose```
```sudo chmod +x /usr/local/bin/docker-compose```
```sudo ln -s /usr/local/bin/docker-compose /usr/bin/docker-compose```
**to check** ```docker-compose -v```
**install docker command** ```sudo apt install docker```
```sudo snap refresh```
```sudo snap install docker ```

---

# Create your first container NGINX

## create Dockerfile
*https://aws.plainenglish.io/how-to-create-custom-nginx-docker-image-cd02242a2478* 
  ```sudo docker build -t image_name .``` **to check** ```sudo docker image ls```
  ```sudo docker run -d --name container_name -p 8080:80 nginximage``` **to check** ```sudo docker ps -a```
  **to check** ```xdg-open http://localhost:8080```
  **delete container** ```sudo docker rm -f container_name```
  **delete image** ```sudo docker rmi -f image_name``` ou ```docker system prune -a```

## ssl
*https://docs.docker.com/engine/security/certificates/*
- in the Dockerfile
  ```openssl genrsa -out client.key 4096```
  ```openssl req -new -x509 -text -key client.key -out client.cert```
- create nginx.conf
to know the correct path to write line copy in the Dockerfile, search the location of conf file in the terminal of the container
```sudo docker exec -it container_name /bin/bash```
  
**don't forget to copy your configure file in the correct path /etc/nginx/sites-enabled/nginx.conf**



---

# Create Wordpress container

## create dockerfile
*https://www.massolit-media.com/tech-writing/wordpress-and-docker-dockerfiles/*
## installing the necessary software

## configure PHP sous debian buster
*https://www.geek17.com/fr/content/debian-10-buster-installer-et-configurer-la-derniere-version-de-nginx-et-php-73-fpm-105*
*https://www.digitalocean.com/community/tutorials/php-fpm-nginx*

*https://webhostinggeeks.com/howto/how-to-run-wordpress-on-nginx-php-fpm-and-mysql/*
in php.ini: ```cgi.fix_pathinfo=0```


cli
*https://developer.wordpress.org/cli/commands/config/create/*
to check in containers'terminal : ```wp --info``` *https://wp-cli.org/fr/*

https://devops.tutorials24x7.com/blog/containerize-wordpress-with-nginx-php-mysql-and-phpmyadmin-using-docker-containers
**http://localhost:8080/** should be show you the main page of the site WP

on my terminal I write ```sudo apt-get install software-properties-common
sudo add-apt-repository ppa:ondrej/php
sudo apt-get update
sudo apt-get install php7.3``` to allow php find package then I can install php-fpm ``````

```/etc/php/7.3/fpm/```
**php.ini** *https://webhostinggeeks.com/howto/how-to-run-wordpress-on-nginx-php-fpm-and-mysql/*
**www.config** *https://www.digitalocean.com/community/tutorials/php-fpm-nginx*
we must show to Nginx how use php => modify config
*https://codingwithmanny.medium.com/custom-wordpress-docker-setup-8851e98e6b8*
*https://www.digitalocean.com/community/tutorials/php-fpm-nginx*
# set the wp-config-sample.php
*https://developer.wordpress.org/cli/commands/config/create/*


## create mariadb
*https://mariadb.com/kb/en/configuring-mariadb-with-option-files/*
*https://tuto.grademe.fr/inception/#mariadb*

## create docker-compose.yml 
*https://openclassrooms.com/fr/courses/2035766-optimisez-votre-deploiement-en-creant-des-conteneurs-avec-docker/6211677-creez-un-fichier-docker-compose-pour-orchestrer-vos-conteneurs*

##debugging with ```sudo docker logs ID_CONTAINER```
```sudo docker run -it ID_IMAGE```






# Docker's command 👩🏽‍🔧
go to [Official Website Docker](https://docs.docker.com/engine/reference/commandline/docker/)
https://docs.docker.com/engine/reference/builder/

 - **loggin** docker login (create id on website Docker Hub)
 - **open  docker's terminal** ```docker exec -it id_container /bin/bash``` => effectuer nos propres tests

 ### [Images]
 - **list images** ```docker image ls```
 - **delete image** ```docker rmi [image_id]```
 - **delete ALL images** ```docker system prune -a```

 ### [Container]
 - **build a container** ```docker build -t [container_name] .```
 - **start a container with a volume** ```docker run -d && --name devtest && -v my-vol/app && nginxlatest```
 - **list all containers (stopped && running)** ```docker ps -a``` ou ```docker container ls``` 
 - **delete conteneur** ```docker rm [id]``` ou ```docker rm [first 3 characters id]```
 - **delete all conteneur** ```docker rm $(docker ps -a -q)```

 ### [Volumes]
 - **create a volume** ```docker volume create my-vol```
 - **list volumes** ```docker volume ls```
 - **inspect a volume** ```docker volume inspect my-vol```
 - **remove a volume**
    - ```docker volume rm my-vol```
    - if you have any problems ```rm [xxxx] + docker volume rm my-vol```

 ### [Network]
  **docker network [CMD]**
  - **Connect a container to a network**    ```connect [network] [id_container/name]```
  - **Create a network** ```create [network]```     
  - **Disconnect a container from a network** ```disconnect [network] [id_container/name]``` 
  - **Display detailed information on one or more networks** ```inspect [network]```

---

# First example 🛷🌬

## 1. create a virtual machine (here Debian) with Oracle/VirtualBox & create files and folders
## 2. install docker
```sudo apt-get remove containerd.io```\
```sudo apt install docker.io docker-compose -y```\
```systemctl start docker```\
```sudo gpasswd -a $USER docker```
#### if you have some problems
```sudo systemctl daemon-reload``` \
```sudo systemctl restart docker```
#### check your process running
```sudo docker ps ```

## 3. install docker compose (__to delete maybe__)
```sudo curl -SL https://github.com/docker/compose/releases/download/v2.12.2/docker-compose-linux-x86_64 -o /usr/local/bin/docker-compose``` \
```sudo chmod +x /usr/local/bin/docker-compose``` \
*to check*: ```sudo docker-compose --version```

## 4. simple nginx creation example  
- **Create Dockerfile** (FROM debian:buster)
- ```sudo docker build . -t [image_name]``` *de preference pour le sujet* **ou** ```sudo docker build .```  **you must be in the nginx folder**
- ```sudo docker run -p80:80 -i --name [container_name] [image_name]``` *--name [container_name]* is not mandatory cause you will use docker-compose after in your eextension file .yml
- **Check container's id** ```docker ps```
- ```docker run -d -p 80:80 nginx```
**Connect to internet** \
- **Close the container** ```sudo docker kill id_container```


---

# Using official Image Nginx Docker 🎢
- ```docker pull nginx```
- ```docker run -d --name server -p 80:80 nginx```
- ```docker ps```
- ```doker kill id_container```


---

# .env

- configurer nom de domaine: DOMAIN_NAME=[login].42.fr


---

# DEFINITION ❤️

Le **Docker Engine** est un outil client-serveur sur lequel repose la technologie de container pour prendre en charge les tâches de création d'applications basées container. Le moteur crée un processus daemon server-side permettant d'héberger les images, les containers, les réseaux et les volumes de stockage.

Les **Daemon** servent en général à répondre à des requêtes du réseau, à l'activité du matériel ou à d'autres programmes en exécutant certaines tâches.

**Host**: équipement accueillant des applications logiciel, le fichier *hosts* est utilisé par le système lors d'une connexion à Internet

**Les bases de données** ont pour but de stocker, organiser et analyser les données. Elles sont stockées sous forme de fichiers ou d’ensembles de fichiers.

**Le port 80** *http://localhost:80* => acces http
**Le port 443** *http://localhost:443* => acces https (SSL)
avec TLS => (HTTPS) socket.

**TSL** (*Transport Layer Security*) remplace le **SSL** (*Secure Sockets Layer*), corrige vulnerabilite d'ancien protocole


---


# Step by step to build a container

## Create a Dockerfile
-> With *FROM *Initial Setup *debian:buster*
-> With *RUN* Installing Nginx to avoid reinstallation each time a new container terminal is launched, add -y to allow choice "yes"
   add utils \
   download the main tool for managing/creating the SSL certificate \ 
   create folder to allow stock the certificat and the key for sécurisate connexion.






```docker build -t [image_name] . ```\
```docker image ls ```\
**Démarrer une image** ```docker run -p80:80 -i --name [container_name] [image_name]```\
*in an other window* **Acceder au terminal du container** ```docker exec -it [id_container] /bin/bash``` ou ```docker exec -it [container_name] /bin/bash``` \
**leave terminal's container** ```exit``` \
**stop running image** Ctrl + C


TIPS:
- Ctrl Droit + F to allow full screen VM
- ```curl localhost``` => afficher page http
- checker si pour ouvert ```nmap 127.0.0.1 -p 443```

## Add root privileges to user to allow connection to login.42.fr
adduser login sudo

## Rendre le nom de domaine accessible en local
/etc/hosts 


