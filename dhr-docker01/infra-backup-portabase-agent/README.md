# infra-backup-portabase-agent

Deploys a `portabase/agent` instances

## `.env` required

Yes - Required for Dockhand secrets manager integration

## Secrets required

`PORTABASE_AGENT_EDGEKEY_SHARED`
`PORTABASE_AGENT_EDGEKEY_VOLUME`

## Volumes required

Agent does not require any volumes for persistance.

Agents may attach to other containers volumes in order to perform backups of SQLite or Volume content.

Current volumes:
* `dockhand_dockhand_data` for Dockhand SQLite backups
