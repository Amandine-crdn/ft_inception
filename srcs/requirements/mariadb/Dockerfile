FROM debian:buster

RUN apt-get update
RUN apt-get install -y mariadb-server \
    mariadb-client 

COPY ./conf/mysqld.conf	/etc/mysql/mariadb.conf.d/50-server.cnf

#RUN mkdir -p /var/run/mysqld \
#&& chown -R mysql:mysql /var/run/mysqld \
#&& chmod 777 /var/run/mysqld

COPY mariadb.sh /usr/local/bin/

RUN chmod +x /usr/local/bin/mariadb.sh

#EXPOSE 3306

ENTRYPOINT ["/bin/bash", "/usr/local/bin/mariadb.sh" ]

#CMD ["mysqld", "--bind-address=0.0.0.0"]
