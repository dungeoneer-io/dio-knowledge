# Realms

- Login destination for WoW players, natural grouping for playerbases
- BlizzAPI relies upon *slug* attribute for queries as ID
- Realms belong to `Connected Realm` entities, nested at the "realms" attribute

## Schema and Storage
- Source of truth is **BlizzData.US.realms**
- { id, region, name, category, locale, timezone, type, slug, crlm }


## Involved Utilities
- `lmda-rlm-scanner` owned by Team Zephyr
    - obtain connected realm snapshots
    - harvest unique realm entities
    - generate entity events