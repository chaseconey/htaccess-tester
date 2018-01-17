
## Apache .htaccess Tester

A simple Docker container with mod_rewrite enabled for testing all of your .htaccess needs

## Usage

To test your .htaccess, simply boot up your container, and add your rules. By default, you can hit the running container via [http://localhost:8080](http://localhost:8080)

* Boot container using compose - `docker-compose up`
* Make edits to .htaccess - `vim .htaccess`

Any changes that are made to the `httpd.conf` will require a full rebuild of the image

```
    docker-compose build --force-rm --no-cache --pull
```
