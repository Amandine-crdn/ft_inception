# Docker's command 👩🏽‍🔧
go to [Official Website Docker](https://docs.docker.com/engine/reference/commandline/docker/)


 - **loggin**: docker login (create id on website Docker Hub)
 - **open  docker's terminal**: docker exec -it id_container /bin/bash => effectuer nos propres tests

 ### [Images]

 - **list images**: ```docker image ls``` **ou** ```docker images``` 
 - **delete image**: ```docker image rm [image_id]```
 ### [Volumes]
 - **create a volume**: ```docker volume create my-vol```
 - **list volumes**: ```docker volume ls```
 - **inspect a volume**: ```docker volume inspect my-vol```
 - **remove a volume**:
    - ```docker volume rm my-vol```
    - if you have any problems: ```rm [xxxx] + docker volume rm my-vol```
 ### [Container]
 - **build a container**: ```docker build -t [container_name] .```
 - **start a container with a volume**: ```docker run -d \ --name devtest \ -v my-vol:/app \ nginx:latest \ ```
 - **list all containers (stopped && running)**: ```docker ps -a``` **ou** ```docker container ls``` \
 - **delete conteneur**: ```docker rm [id]``` **ou** ```docker rm [first 3 characters id]```
 - **delete all conteneur**: ```docker rm $(docker ps -a -q)```
 ### [Network]
  **docker network [CMD]**
  - **Connect a container to a network**:    ```connect [network] [id_container/name]```
  - **Create a network**: ```create [network]```     
  - **Disconnect a container from a network**: ```disconnect [network] [id_container/name]``` 
  - **Display detailed information on one or more networks**: ```inspect [network]```

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
- Create Dockerfile (FROM debian:buster)
- ```sudo docker build . -t [container_name]``` *de preference pour le sujet* **ou** ```sudo docker build .```  **(you must be in the nginx folder)**
- ```sudo docker run -i --name [container_name] [image_name]``` \ *--name [container_name]* is not mandatory cause you will use docker-compose after in your eextension file .yml
- **(check container's id)**: ```docker ps```
- ```docker run -d -p 80:80 nginx```
**connect to internet** \
- **(Close the container)**: ```sudo docker kill id_container```


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

**TSL** (*Transport Layer Security*) remplce le **SSL** (*Secure Sockets Layer*), corrige vulnerabilite d'ancien protocole


---


# Step

```docker build -t [container_name] . ```\
```docker image ls ```\
**Démarrer une image  + acceder au terminal du container:** ```docker run -it [image_name]```\
