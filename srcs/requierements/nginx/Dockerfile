#Initial Setup
FROM  debian:buster
#Installing Nginx
RUN apt-get -y update && apt-get -y install nginx
#Configuration File
COPY conf/nginx.conf /etc/nginx/conf
#pourquoi conf.d

#Exposing Ports
EXPOSE 80/tcp
#Running Nginx
CMD ["/usr/sbin/nginx", "-g", "daemon off;"]
#what is deamon off ?