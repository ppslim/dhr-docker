# DHR Docker

Dockhand stacks for DHR project

## Container: infra-mariadb
Shared MariaDB instance, and SOCAT proxy instance

## Container: infra-nginx-proxy-manager
NGINX Proxy Manager Instance providing secured external HTTPS access to internal containers. Handles Letsencrypt renewal.

## Container: appfireflyiii
A Firefly III installation, consisting of core application and associated Alpine container for cron
