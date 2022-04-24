### Prontus CMS - docker example implementation

First working implementation example of containerization for the not very well known CMS called *Prontus*, developed by a chilean company. Still needs some dependency de-bloat, etc.

Includes an example Dockerfile which assumes the source code is in the current directory inside the folder 'prontus', and another, which downloads the zip file from source.
The build also makes use of a local apt packages cache listening on port 8123, to speed-up the development and the addition of packages (the config code for this cache can be found [here](https://github.com/cafade/polipo-web-cache-proxy-config).

Requires a separate container for a mysql/mariadb database, a cloud based instance, etc.

---
Build the container from the cloned dir of the repo like:
``` bash
# docker build --build-arg BUILD_DATE=$(date -u +'%Y-%m-%dT%H:%M:%SZ') -t custom-prontus/prontus-slim:0.0.1 .
```

Run the container like:
``` bash
# docker run --name prontus-dev -v prontus_data:/var/www/prontus/web -v apache_conf:/etc/apache2 -h prontus-dev --restart unless-stopped -p 80:80 -it custom-prontus/prontus-slim:0.0.1
```

