# Latest Ubuntu LTS
FROM    ubuntu:12.04

MAINTAINER Gustavo Salomé <gustavonips@gmail.com>

# Expose apache and ssh
EXPOSE 22 80

#
WORKDIR /var/www

# Share the volume at correct location
VOLUME /var/www

RUN echo 'debconf debconf/frontend select Noninteractive' | debconf-set-selections

# Basic setup
RUN \
    apt-get update && \
    apt-get upgrade -y && \
    apt-get install -y sudo apt-utils python-software-properties && \
    apt-add-repository -y ppa:ondrej/apache2 && \
    add-apt-repository -y ppa:ondrej/php5 && \
    apt-get update

RUN \
    apt-get install -y openssh-server memcached curl supervisor && \
    apt-get install -y apache2-mpm-worker libapache2-mod-fastcgi && \
    apt-get install -y php5-common php5-fpm && \
    apt-get install -y php5-apcu php5-gd php5-mcrypt php5-mysqlnd php5-curl php5-memcache php5-json

RUN mkdir -p /var/run/sshd
RUN mkdir -p /var/log/supervisor

# Conf files
ADD fastcgi.conf /etc/apache2/mods-enabled/fastcgi.conf
ADD supervisord.conf /etc/supervisor/conf.d/supervisord.conf

RUN a2enmod rewrite actions fastcgi alias

#Setup the server
CMD ["/usr/bin/supervisord"]
