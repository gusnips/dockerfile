FROM ubuntu:12.04

MAINTAINER Gustavo Salomé <gustavonips@gmail.com>

# Basic setup
RUN \
    apt-get update && \
    apt-get upgrade -y && \
    DEBIAN_FRONTEND=noninteractive apt-get install -y -q mysql-server-5.5

RUN sed -i -e"s/^bind-address\s*=\s*127.0.0.1/bind-address = 0.0.0.0/" /etc/mysql/my.cnf

# Remove pre-installed database
RUN rm -rf /var/lib/mysql/*

# Runner utility
ADD config_and_run_mysql.sh /usr/local/bin/config_and_run_mysql.sh
RUN chmod +x /usr/local/bin/config_and_run_mysql.sh

EXPOSE 3306

VOLUME ["/var/lib/mysql"]

CMD ["/usr/local/bin/config_and_run_mysql.sh"]
