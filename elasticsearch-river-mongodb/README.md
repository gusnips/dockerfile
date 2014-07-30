## ElasticSearch + MongoDB River Plugin Dockerfile


This repository contains **Dockerfile** of [ElasticSearch](http://www.elasticsearch.org/) installed with [MongoDB River Plugin](https://github.com/richardwilly98/elasticsearch-river-mongodb)


### Dependencies

* [Docker](https://www.docker.io/) [Not using yet?](https://docs.docker.com/installation/#installation)

It's usually useful to have mongodb running. If you don't have it yet, try the [official version](https://index.docker.io/u/dockerfile/mongodb/)

```sh
docker run -d -p 27017:27017 --name mongodb dockerfile/mongodb
```
### Installation

Download [the image build](https://index.docker.io/u/gusnips/elasticsearch-river-mongodb/) from public [Docker Registry](https://index.docker.io/):  
`docker pull gusnips/elasticsearch-river-mongodb`

alternatively, you can build an image from Dockerfile:  
`docker build -t="gusnips/elasticsearch-river-mongodb" github.com/gusnips/dockerfile/elasticsearch-river-mongodb`


### Usage

   ```sh
    docker run -d -p 9200:9200 -p 9300:9300 --name elasticsearch gusnips/elasticsearch-river-mongodb
   ```

#### Attach persistent/shared directories

  1. Create a mountable data directory `<data-dir>` on the host.

  2. Create ElasticSearch config file at `<data-dir>/elasticsearch.yml`.

    ```yml
    path:
      logs: /data/log
      data: /data/data
    ```

  3. Start a container by mounting data directory and specifying the custom configuration file:

    ```sh
    docker run -d -p 127.0.0.1:9200:9200 -p 127.0.0.1:9300:9300  --name elasticsearch -v <data-dir>:/data gusnips/elasticsearch-river-mongodb /elasticsearch/bin/elasticsearch -Des.config=/data/elasticsearch.yml
    ```

After few seconds, open `http://localhost:9200` to see the result.

## Versions

+ [ElasticSearch](http://www.elasticsearch.org/) 1.0.0
+ [MongoDB River Plugin](https://github.com/richardwilly98/elasticsearch-river-mongodb) 2.0.0
+ [Mapper Attachments Type for Elasticsearch](https://github.com/elasticsearch/elasticsearch-mapper-attachments) (MongoDB River Plugin dependency) 2.0.0
