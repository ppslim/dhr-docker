# infra-backup-portabase

Deploys a `portabase/portabase` instances

## `.env` required

Yes - Required for Dockhand secrets manager integration

## Secrets required

Polls in from `infrastructure` / `dpl_portabase`
* `POSTGRES_DB`
* `POSTGRES_HOST`
* `POSTGRES_PASSWORD`
* `POSTGRES_PORT`
* `POSTGRES_USER`
* `PROJECT_SECRET`

## Volumes required

Agent does not require any volumes for persistance.

Agents may attach to other containers volumes in order to perform backups of SQLite or Volume content.

Current volumes:
* `dockhand_dockhand_data` for Dockhand SQLite backups
