# Docker's command 👩🏽‍🔧
 - **docker -v**: version de docker\
 - **loggin**: docker login (create id on website Docker Hub)\
 - **open  docker's terminal**: docker exec -it id_container /bin/bash\

 ## Images
 - **list images**: docker imag**e** ls **ou** docker image**s** \
 - **delete image**: docker image rm IMAGE_ID
 
 ## Volumes
 - **create a volune**: docker volume create my-vol\
 - **list volumes**: docker volume ls\
 - **inspect a volume**: docker volume inspect my-vol\
 - **remove a volume**:
    - docker volume rm my-vol\
    - if you have any problems: rm [xxxx] + docker volume rm my-vol\

 ## Container
 - **start a container with a volume**: docker run -d \
  --name devtest \
  -v my-vol:/app \
  nginx:latest \
 - **list all containers (off/on)**: docker ps -a **ou** docker container ls\
 - **delete conteneur**: docker rm ID **ou** docker rm [first 3 characters ID]\

---

# First example 🛷🌬

## 1. create vm with oracle & create files and directorys
## 2. install docker
sudo apt-get remove containerd.io\
sudo apt install docker.io docker-compose -y\
systemctl start docker\
sudo gpasswd -a $USER docker
#### if you have some problems
sudo systemctl daemon-reload\
sudo systemctl restart docker
#### check your process running
sudo docker ps **(process running)**

## 3. install docker compose
sudo curl -SL https://github.com/docker/compose/releases/download/v2.12.2/docker-compose-linux-x86_64 -o /usr/local/bin/docker-compose\
sudo chmod +x /usr/local/bin/docker-compose
/check
sudo docker-compose --version

## 4. simple exemple creation nginx
- Create Dockerfile
- sudo docker build . -t inception/nginx **(se placer dans le dossier nginx)**\
sudo docker run inception/nginx
docker ps **(check id du container)**\
docker run -d -p 80:80 nginx\
**connect to internet** \
sudo docker kill id_container  **(Fermer le container)**

---

# Using official Image Nginx Docker 🎢
- docker pull nginx
- docker run -d --name server -p 80:80 nginx
- docker ps
- doker kill id_container


---


