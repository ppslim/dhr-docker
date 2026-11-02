# infra-openldap

Deploys a `bitnamilegacy/openldap:latest` instance.

* OpenLDAP instance that does not expose ports externally
* External access should be exposed using NGINX Proxy Manager Streams

## Dependancies

No external services are required.

NGINX Proxy Manager only exposes it externally, but we do not depend on this

## `.env` required

Yes

## Secrets required

`LDAP_ADMIN_USERNAME` The admin username
`LDAP_ADMIN_PASSWORD` The admin passsword
`LDAP_ROOT` The DN of the root of our tree

## Volumes required

Two volumes are defined for ldap config directory
