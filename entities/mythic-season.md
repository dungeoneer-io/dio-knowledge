# Mythic+ Seasons

- Date period that demarcates time within Mythic Seasons as defined by Blizzard, usually between major patches


## Schema and Storage
- Current known state is kept at **Cluster1.US.mythic_seasons**
- { id, start, end, periods: [`Mythic Period`] }

## Known Issues
- Current season will have an end date of NULL

## Pipeline Process
"Scan Mythic Season" Pipeline

### >>> LEG 1: API Snapshot Retrieval
1. BlizzAPI: Get `Mythic Season` Index
1. Collect `Mythic Season` info { id, start, end }
1. BlizzAPI: Get `Mythic Period` Index
1. Collect `Mythic Period` info { id, start, end }
1. Nest Periods into *periods* array
1. Organize into `MythicSeasonSnapshot` { stamp, data [`Mythic Season`] }
1. Save snapshot to **USBlizzData.US.MythicSeasonSnapshots**
1. Log Job Completion to **USBlizzData.US.Receipts_RunScans** of type "MYTHICSEASONSINFO"

### >>> LEG 2: Mongo DB Trigger
1. MongoDB trigger **PropagateMythicSeasonInfo** fires on INSERT event on the **USBlizzData.US.MythicSeasonSnapshots**
1. For each `Playable Class` in snapshot, upsert into **Cluster1.US.mythic_seasons**