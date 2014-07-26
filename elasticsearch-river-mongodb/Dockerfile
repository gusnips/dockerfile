#
# ElasticSearch Dockerfile
#
# https://github.com/gusnips/dockerfile/elasticsearch-river-mongodb
#

# Pull base image.
FROM dockerfile/java

# Install ElasticSearch.
RUN \
  cd /tmp && \
  wget https://download.elasticsearch.org/elasticsearch/elasticsearch/elasticsearch-1.0.0.tar.gz && \
  tar xvzf elasticsearch-1.0.0.tar.gz && \
  rm -f elasticsearch-1.0.0.tar.gz && \
  mv /tmp/elasticsearch-1.0.0 /elasticsearch

# Install Plugins.
RUN \
  /elasticsearch/bin/plugin --install elasticsearch/elasticsearch-mapper-attachments/2.0.0 --verbose && \
  /elasticsearch/bin/plugin --install com.github.richardwilly98.elasticsearch/elasticsearch-river-mongodb/2.0.0 --verbose && \
  /elasticsearch/bin/elasticsearch restart

# Define mountable directories.
VOLUME ["/data"]

# Define working directory.
WORKDIR /data

# Define default command.
CMD ["/elasticsearch/bin/elasticsearch"]

# Expose ports.
#   - 9200: HTTP
#   - 9300: transport
EXPOSE 9200
EXPOSE 9300
