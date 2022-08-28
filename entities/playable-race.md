# Playable Race

- Pretty static manifest of the playable races in World of Warcraft
- `Playable Race` has a many-to-one relationship with `Playable Faction`


## Schema and Storage
- Current known state is kept at **Cluster1.US.playable_races**
- { id, nme, fac }

## Known Issues
- **Dirty Data Issue:** Pandarens are represented 3 times in the data. One for Alliance, one for Horde, and once again as "Neutral"
  - We currently filter out all NEUTRAL races that we find, only Pandaren #3 as of 8-7-22
  - We allow both Pandaren to exist in the official list, one for each faction


## Pipeline Process
"Scan Playable Race" Pipeline

### >>> LEG 1: API Snapshot Retrieval
1. BlizzAPI: Get `Playable Race` Index
1. Collect `Playable Race` info { id, nme, fac }
1. Organize into `PlayableRaceSnapshot` { stamp, data [`Playable Race`] }
1. Save snapshot to **USBlizzData.US.PlayableRaceSnapshots**
1. Log Job Completion to **USBlizzData.US.Receipts_RunScans** of type "PLAYABLERACEINFO"

### >>> LEG 2: Mongo DB Trigger
1. MongoDB trigger **PropagatePlayableRaceInfo** fires on INSERT event on the **USBlizzData.US.PlayableRaceSnapshots**
1. For each `Playable Race` in snapshot, upsert into **Cluster1.US.playable_races**