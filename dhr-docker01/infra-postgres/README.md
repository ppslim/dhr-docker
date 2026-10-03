# infra-postgres

Deploys `postgres:15-alpine` and `postgres:17-alpine` instances

## `.env` required

None

## Secrets required

`POSTGRES_PASSWORD` postgres root password

Only used on initial deployment, but needed for the stack to functions

## Volumes required

None. Uses managed volumes

