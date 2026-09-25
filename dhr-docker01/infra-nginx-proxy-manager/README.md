# infra-nginx-proxy-manager

Deploys a `jc21/nginx-proxy-manager:latest` instance.

* Proxy HTTP/S requests from external networks to containers
* Letsencrypt TLS cert renewal

## Dependancies

Requires Mariadb Server

## `.env` required

Yes

## Secrets required

`DATABASE_PASSWORD`
`MYSQL_ROOT_PASSWORD` Defined but not required


## Volumes required

Two volumes are defined. One for Database / config, the other for Letsencrypt
