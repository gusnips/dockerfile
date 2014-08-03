sphinxsearch-beta
============

Sphinx-beta in an Ubuntu 12.04 Docker container

### Basic usage

```sh
docker run -p 9306:9306 -v /my/config/folder:/etc/sphinxsearch gusnips/sphinxsearch
```

Configuration folder (would be "/my/config/folder" in the above command) must contain a `sphinx.conf` file, which will be used as sphinx `config` parameter

### Command line client

Exposing Sphinx SphinQL & Plain Ports
```sh
docker run -p 9312:9312 -p 9306:9306 -v /my/config/folder:/etc/sphinxsearch gusnips/sphinxsearch
```

Then, check the Sphinx instance inside the container with:

```sh
mysql -h0 -P9311
```

### Persistent data

```sh
docker run --name sphinx -d -p 9312:9312 -p 9306:9306 -v $(pwd)/sphinx/conf:/etc/sphinxsearch -v $(pwd)/sphinx/data:/var/lib/sphinxsearch/data gusnips/sphinxsearch
```

`$(pwd)` exemplified aboce is the current directory

### Build

```sh
docker build -t="gusnips/sphinxsearch" .
```
