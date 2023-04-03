# Inception
# First example

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
sudo docker kill <id>  **(Fermer le container)**

---

# docker's command
 ## loggin
 docker login (create id on website Docker Hub)
 ## open  docker's terminal
 docker exec -it <id> /bin/bash

