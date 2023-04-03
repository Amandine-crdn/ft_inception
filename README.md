# Inception

## 1. create vm with oracle
## 2. creates files ans directorys
## 3. install docker
sudo apt-get remove containerd.io\
sudo apt install docker.io docker-compose -y\
systemctl start docker\
sudo gpasswd -a $USER docker
#### si pb
sudo systemctl daemon-reload\
sudo systemctl restart docker
#### check
sudo docker ps **(process running)**

## 4. install docker compose
sudo curl -SL https://github.com/docker/compose/releases/download/v2.12.2/docker-compose-linux-x86_64 -o /usr/local/bin/docker-compose\
sudo chmod +x /usr/local/bin/docker-compose
/check
sudo docker-compose --version

## 5. simple exemple creation nginx
- Create Dockerfile
- 
sudo docker build . -t inception/nginx **(se placer dans le dossier nginx)**\
sudo docker run inception/nginx
docker ps **(check id du container)**\
docker run -d -p 80:80 nginx
# connect to internet


## Fermer le container
sudo docker kill <id>



## Docker
 # se connecter
 docker login (create id on website Docker Hub)
 # Ouvrir un terminal docker
 docker exec -it <id> /bin/bash

