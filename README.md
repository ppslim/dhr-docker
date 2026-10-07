# DHR Docker

Dockhand stacks for DHR project

## Stack information
Stacks carry one of two prefixes

* `infra` - Infrastrucute stacks
* `app` - Application stacks

### Stacks `infra`

* `infra-nginx-proxy-manager` - Proxy frontend to service apps. Provides letsencrypt renewal.
* `infra-mariadb` - Shared MariaDB instance + SOCAT proxy. Provides databases
  * `nginxproxy` NGINX Proxy Manager
  * `firefly` Firely III
* infra-postgres - Shared Postgres 15 & 17 instances + SOCAT proxies for each
  * Postgres 15 Databases
    * `ghostfolio` Ghostfolio
  * Postgres 17 Databases
    * `portabase` Portabase manager
* `infra-backup-portabase` - Portabase Manager instance
* `infra-backup-portabase-agent` - Portabase Agents used for shared or exclusive DB backups

### Stacks `app`

* `app-fireflyiii` - Firefly III finance manager and cron instance
* `app-ghostfolio` - Ghostfolio and Redis cache instances

## Network information
The following networks are defined with the following config

* `infra-net-shared`
  * Description: Bridge services two purposes
    * Ingress of exposed ports to containers - Avoid expose if possible
    * Container to internet communication
  * Internal: FALSE
  * Manually defined: TRUE
  * Extra info: Inter Container Communications is disabled
    * `com.docker.network.bridge.enable_icc=false`

* `infra-net-nginxproxy`
  * Description: Used for ICC between Ingres NGINX proxy and applications
  * Internal: TRUE
  * Manually defined: TRUE
  * Extra info: Any application that needs a proxy should attach here. The application should define a custom network alias to avoid ICC being blocked if also attached to `infra-net-shared`
    * e.g. if app is `app-sampleapp`, ensure it has alias `app-sampleapp-proxyendpoint`

* `infra-net-mariadb`
  * Description: Used for application to MariaDB server ICC
  * Internal: TRUE
  * Manually defined: TRUE
  * Extra info: None


* `infra-net-postgres`
  * Description: Used for application to Postgres 15/17 server ICC
  * Internal: TRUE
  * Manually defined: TRUE
  * Extra info: None

* `infra-net-portabase`
  * Description: Used for Portabase inter agent ICC
  * Internal: TRUE
  * Manually defined: TRUE
  * Extra info: New agents should attach here, and seperately to respective DB network

Applications may also use there own `default` network in docker comose for ICC within a stack, but **MUST** define that at `internal: true`. They should attach to some appropriate network above where egress, direct ingress or indirect reverse proxy access should apply.

## Compose notes

### Stacks with Doppler Secrets

If stacks require Doppler Secrets, ensure the stack has a `.env` file that containts the following.

```shell
# Required for Dockhand secrets management on Doppler
DOCKHAND_SECRET_SELECTOR=x
```