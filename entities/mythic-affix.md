# Mythic+ Affix

- Variants of the Mythic Dungeons

## Schema and Storage
- Current known state is stored in **USBlizzData.US.MythicAffixes**
- { id, nme }

## Known Issues
- x

## Pipeline Process
"Scan Mythic Affix"
- Scrapes affixes from BlizzAPI endpoint
- Upsert into **USBlizzData.US.MythicAffixes**
