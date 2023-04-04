#Initial Setup
FROM  debian:buster

#Installing Nginx here avoids reinstallation each time a new container terminal is launched
#y mean yes
RUN apt-get -y update
RUN apt-get -y install nginx
RUN apt-get install curl -y
#télécharger l’outil principal pour la gestion/création de certificat SSL
RUN apt-get -y install openssl
#créer un dossier, qui permettra de stocker le certificat et la clef pour une connexion sécurisée.
RUN mkdir -p /etc/nginx/ssl
#générer un certificat SSL 
RUN openssl req -x509 -nodes -out /etc/nginx/ssl/inception.crt -keyout /etc/nginx/ssl/inception.key -subj "/C=FR/ST=IDF/L=Paris/O=42/OU=42/CN=acerdan.42.fr/UID=login"

#Configuration File
#install packages utile
COPY conf/nginx.conf /etc/nginx/nginx.conf
#pourquoi conf.d

#Exposing Ports
EXPOSE 80/tcp
#Running Nginx
CMD ["/usr/sbin/nginx", "-g", "daemon off;"]
# ENTRYPOINT [ "bash" ]
#what is deamon off ?