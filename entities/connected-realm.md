# Connected Realms

- Cluster of realms that are grouped together upstream at Blizzard
- Primary designation for querying and identifying Mythic+ leaderboards

## Snapshots
- Crealm Snapshots are arrays of [`Connected Realm`] containing all CRealms listed on the region's index
## Schema and Storage
- Source of truth is **BlizzData.US.crealms**
- { id, realms: [`Realm`] }

## Involved Utilities
- `lmda-rlm-scanner` owned by Team Zephyr
    - obtain connected realm snapshots
    - harvest unique crealm entities
    - generate entity events