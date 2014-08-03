# Latest Ubuntu LTS
FROM    ubuntu:12.04

MAINTAINER Gustavo Salomé <gustavonips@gmail.com>

# Basic setup
RUN \
    apt-get update && \
    apt-get upgrade -y && \
    DEBIAN_FRONTEND=noninteractive apt-get install -y -q python-software-properties && \
    apt-add-repository -y ppa:ondrej/apache2 && \
    add-apt-repository -y ppa:ondrej/php5 && \
    apt-get update

RUN \
    DEBIAN_FRONTEND=noninteractive apt-get install -y -q memcached curl && \
    DEBIAN_FRONTEND=noninteractive apt-get install -y -q apache2-mpm-worker libapache2-mod-fastcgi && \
    DEBIAN_FRONTEND=noninteractive apt-get install -y -q php5-common php5-fpm && \
    DEBIAN_FRONTEND=noninteractive apt-get install -y -q php5-apcu php5-gd php5-mcrypt php5-mysqlnd php5-curl php5-memcache php5-json

# Enable apache default configuration
RUN echo "ServerName localhost" | tee /etc/apache2/conf-available/servername.conf
RUN a2enconf servername

# Enable apache modules
ADD fastcgi.conf /etc/apache2/mods-enabled/fastcgi.conf
RUN a2enmod rewrite actions fastcgi alias

#Env vars
ENV APACHE_RUN_USER www-data
ENV APACHE_RUN_GROUP www-data
ENV APACHE_LOG_DIR /var/log/apache2

RUN chown -R www-data:www-data /var/www

#
EXPOSE 80

WORKDIR /var/www

VOLUME ["/var/www","/etc/apache2/sites-enabled","/etc/apache2/conf-enabled"]

# Start the servers
CMD ["/usr/sbin/apachectl start && php-fpm -D"]
