FROM debian:buster

RUN apt-get update
RUN apt-get install -y mariadb-server \
    mariadb-client 

COPY ./conf/mysqld.conf	/etc/mysql/mariadb.conf.d/50-server.cnf
COPY mariadb.sh /usr/local/bin/

RUN chmod +x /usr/local/bin/mariadb.sh

ENTRYPOINT ["/bin/bash", "/usr/local/bin/mariadb.sh" ]

