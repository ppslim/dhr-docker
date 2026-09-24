# infra-maridb

Deploys a `mariadb:lts` instance

## `.env` required

None

## Secrets required

`MYSQL_ROOT_PASSWORD` mariadb root password

Only used on initial deployment, but needed for the stack to functions

## Volumes required

`infra-external-mariadb`
Must be created as an external volume and will store the mariadb databases
