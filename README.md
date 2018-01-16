[![](https://images.microbadger.com/badges/image/fjudith/nexus.svg)](https://microbadger.com/images/fjudith/nexus "Get your own image badge on microbadger.com")
[![Build Status](https://travis-ci.org/fjudith/docker-nexus.svg?branch=master)](https://travis-ci.org/fjudith/docker-nexus)

# Introduction

Nexus is an open source repository manager which enables the management of various package formats.

* Bower
* Docker (a.k.a Private Registry)
* Git LFS
* Maven 2
* NPM
* NuGET
* Python PL
* Raw
* Ruby Gem
* Yum

# Description

The Dockerfile builds from "sonatype/nexus3" and "nginx" images see:

* https://hub.docker.com/u/sonatype/nexus3
* https://hub.docker.com/u/_/nginx

[3.7.1, latest](https://github.com/fjudith/docker-nexus/tree/3.6.2)
[3.7.1, nginx](https://github.com/fjudith/docker-nexus/tree/3.6.2/nginx)

The nginx container stands as a Reverse proxy/SSL Terminator to Nexus in order route request to the docker registry based on the user-agent.

## Roadmap

* [x] Self-Signed certificate autogen
* [x] Docker registry routing based on user-gent
* [ ] Let's encrypt certificate autogen
* [x] Support SSL certificate mount to `/etc/nginx/ssl/nginx.crt|nginx.key`

# Quick Start

First run the `nexus` container

```bash
docker run -d --name="nexus" -p 8081:8081 -p 5000:5000 fjudith/nexus
```

Then run the `nginx` container

```bash
docker run -it --name="nexus-nginx" --link nexus:nexus -p 80:80 -p 443:443 fjudith/nexus:nginx
```

Start a web browser session to http://ip or htts://ip

# Environmnet variables

### Nexus container



### Nginx container

* **LETS_ENCRYPT_ENABLED**: Enables Let's Encrypt certificate instead of self-signed; default `false`
* **PUBLIC_DNS**: DNS domain to be used as certificate "CN" record; default `draw.example.com`
* **ORGANISATION_UNIT**: Organisation unit to be used as certificate "OU" record; default `Cloud Native Application`
* **ORGANISATION**: Organisation name to be used as certificate "O" record; default `example inc`
* **CITY**: City name to be used as certificate "L" record; default `Paris`
* **STATE**: State name to be used as certificate "ST" record; default `Paris`
* **COUNTRY_CODE**: Country code to be used as certificate "C" record; default `FR`

# Reference

* https://hub.docker.com/u/sonatype/nexus3
* 