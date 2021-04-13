The installation has been done using a Docker image for Sentrifugo (http://www.sentrifugo.com/), an
open-source HRMS tool.


### How to run ###

1. : Download Sentrifugo.zip for Linux. Place it in the root directory.
Name it `Sentrifugo.zip`.

On a fresh start, run `docker-compose up`.

### Implementation ###

* Sentrifugo runs inside an Ubuntu 16.04 Docker Container with PHP 7.0 and Nginx.

#### `sentrifugo-app` ###


1. `sentrifugo-app` is an nginx application container.
   This has `nginx` and `php-fpm`.
2. Sentrifugo is installed to `/sentrifugo/`



