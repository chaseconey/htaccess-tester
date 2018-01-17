
## Apache .htaccess Tester

[![Docker Pulls](https://img.shields.io/docker/pulls/chaseconey/htaccess-tester.svg?style=flat-square)]()
[![Docker Build Status](https://img.shields.io/docker/build/chaseconey/htaccess-tester.svg?style=flat-square)]()

A simple Docker container with mod_rewrite enabled for testing all of your .htaccess needs.

This image currently supports the latest version of Apache 2.4 and uses the official [httpd image](https://hub.docker.com/_/httpd/) to do so.

## Usage

### Via Docker Hub (simple)

The easiest way to get your htaccess tester up and running is to pull the off-the-shelf image from Docker Hub and link the folder with your htaccess into the running container.

For example, if you had a directory that looked like this:

```
.
├── .htaccess
└── index.html
```

you could simply link the entire directory into the web root of the container like so:

```
    docker run -p 8080:80 -v "$PWD:/usr/local/apache2/htdocs" chaseconey/htaccess-tester
```

and navigate via browser or some other client such as `curl` to [https://localhost:8080](https://localhost:8080).

### Via Github/Docker Compose (more control)

For a little bit more control over the apache environment, you might just clone the repository locally and modify the `Dockerfile`/`docker-compose.yml` to your liking.

To test your .htaccess, simply boot up your container, and add your rules. By default, you can hit the running container via [http://localhost:8080](http://localhost:8080)

* Boot container using compose - `docker-compose up`
* Make edits to .htaccess - `vim .htaccess`
* Test .htaccess by visiting expected url - `curl -IL http://localhost:8080/rawr`

Any changes that are made to the `httpd.conf` will require a full rebuild of the image

```
    docker-compose build --force-rm --no-cache --pull
```
