FROM ubuntu:12.04

MAINTAINER Gustavo Salomé <gustavonips@gmail.com>

# Basic setup
RUN \
    apt-get update && \
    apt-get upgrade -y && \
    DEBIAN_FRONTEND=noninteractive apt-get install -y python-software-properties && \
    apt-add-repository -y ppa:builds/sphinxsearch-beta && \
    apt-get update

# Install sphinxsearch, ssh server, supervisor and php command line
RUN \
    DEBIAN_FRONTEND=noninteractive apt-get install -y  php5-cli sphinxsearch


RUN \
    mkdir -p /var/lib/sphinxsearch/data && \
    mkdir -p /var/log/sphinxsearch && \
    mkdir -p /var/run/sphinxsearch

WORKDIR /var/lib/sphinxsearch

# Sphinx SphinQL & Plain Ports
EXPOSE 9306 9312

VOLUME ["/etc/sphinxsearch","/var/lib/sphinxsearch/data"]

CMD ["/usr/bin/searchd","--config","/etc/sphinxsearch/sphinx.conf","--nodetach"]
