FROM debian:buster

# Installation de WordPress
RUN apt-get update
RUN apt-get -y install wget
RUN apt-get install -y php7.3\
						php-fpm\
						php-mysql\
						mariadb-client

RUN wget https://fr.wordpress.org/wordpress-6.0-fr_FR.tar.gz -P /var/www
RUN cd /var/www && tar -xzf wordpress-6.0-fr_FR.tar.gz && rm wordpress-6.0-fr_FR.tar.gz
RUN	chown -R root:root /var/www/wordpress

RUN wget https://raw.githubusercontent.com/wp-cli/builds/gh-pages/phar/wp-cli.phar
RUN chmod +x wp-cli.phar
RUN mv wp-cli.phar /usr/local/bin/wp

COPY ./conf/www.conf /var/www/html/
COPY ./conf/auto_config.sh /usr/local/bin/

ENTRYPOINT ["/bin/bash", "/usr/local/bin/auto_config.sh" ]

#ENTRYPOINT ["mysql"]
#ENTRYPOINT ["sh", "auto_config.sh"]
