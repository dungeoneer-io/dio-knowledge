# Connected Realms

- Cluster of realms that are grouped together upstream at Blizzard
- Primary designation for querying and identifying Mythic+ leaderboards

## Schema and Storage
- Source of truth is **BlizzData.US.crealms**
- { id, realms: [`Realm`], firstSeen, lastSeen }

## Involved Utilities
- `lmda-rlm-scanner` owned by Team Zephyr
    - obtain connected realm snapshots
    - harvest unique crealm entities
    - generate entity events