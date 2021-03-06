# Docker Forma LMS
[![Docker Image Version (latest by date)](https://img.shields.io/docker/v/nicholaswilde/formalms)](https://hub.docker.com/r/nicholaswilde/formalms)
[![Docker Pulls](https://img.shields.io/docker/pulls/nicholaswilde/formalms)](https://hub.docker.com/r/nicholaswilde/formalms)
[![GitHub](https://img.shields.io/github/license/nicholaswilde/docker-formalms)](./LICENSE)
[![hadolint](https://github.com/nicholaswilde/docker-cryptpad/workflows/hadolint/badge.svg?branch=main)](https://github.com/nicholaswilde/docker-formalms/actions?query=workflow%3Ahadolint)
[![yamllint](https://github.com/nicholaswilde/docker-cryptpad/workflows/yamllint/badge.svg?branch=main)](https://github.com/nicholaswilde/docker-formalms/actions?query=workflow%3Ayamllint)
[![pre-commit](https://img.shields.io/badge/pre--commit-enabled-brightgreen?logo=pre-commit&logoColor=white)](https://github.com/pre-commit/pre-commit)

A docker container for the e-learning platform [Forma LMS](https://www.formalms.org/) based on the official php:7.0-apache image.

## Dependencies

In order to run this container you'll need: 

A compatible SQL database:

* MySQL 5.0 or higher or MariaDB  5.5 or higher
* UTF8 character set
* MySQL strict mode disabled

## Usage

### docker cli

The web page runs on the default http port

```shell
docker run -p 8080:80 nicholaswilde/formalms
```
Then you can go to `http://localhost:8080/install` to complete the installation.

### Volume

The default UID and GID for the `app` volume is `www-data:www-data` or `33:33`

### docker-compose

See [docker-compose.yaml](./docker-compose.yaml).

This will install both Forma LMS and a MySQL database
You can use [the forma.cnf file in this repository](https://github.com/nicholaswilde/docker-formalms/blob/master/config/forma.cnf) to set both character set to utf8 and disable strict mode at creation time, otherwise you'll have to do it manually.

As with `docker run` got to the web page `http://localhost:8080/install` to complete the installation.

With this compose file you can just set `db` as the database host during installation and `formalms` as database name, user and password.
The database is not exposed outside of the stack, but you can always change the database parameters to be on the safer side.

## Development

See [Wiki](https://github.com/nicholaswilde/docker-template/wiki/Development).

## Troubleshooting

See [Wiki](https://github.com/nicholaswilde/docker-template/wiki/Troubleshooting).

## Pre-commit hook

If you want to automatically generate `README.md` files with a pre-commit hook, make sure you
[install the pre-commit binary](https://pre-commit.com/#install), and add a [.pre-commit-config.yaml file](./.pre-commit-config.yaml)
to your project. Then run:

```bash
pre-commit install
pre-commit install-hooks
```
Currently, this only works on `amd64` systems.

## Built With

* Forma LMS v2.3.0.2
* PHP v7.0
* MySQL v5.7

## Acknowledgments

* [The Forma LMS project](https://www.formalms.org/)

## License

[Apache 2.0 License](./LICENSE)

## Authors

* **Lorenzo Dallagà** - *Initial work*
* [RazgulTraka](https://github.com/RazgulTraka)
* [Nicholas Wilde](https://github.com/nicholaswilde)
