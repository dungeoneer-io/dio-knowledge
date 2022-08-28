# Playable Classes

- Pretty static manifest of the playable classes in World of Warcraft
- `Playable Class Specialization` entities relate to `Playable Class` in a many-to-one fashion and can be found, nested, in the spcs property


## Schema and Storage
- Current known state is kept at **Cluster1.US.playable_classes**
- { id, nme, spcs: [`Playable Class Specialization`] }

## Known Issues
- Source of truth can be found for data processing in the table, but front-end displays will likely have this hardcoded. Would be a great fix to auto PR a new list if Class/Specs ever get detected as new or deprecated

## Pipeline Process
"Scan Playable Class" Pipeline

### >>> LEG 1: API Snapshot Retrieval
1. BlizzAPI: Get `Playable Class` Index
1. Collect `Playable Class` info { id, nme, pt, spcs }
1. BlizzAPI: Get `Playable Class Specialization` Index
1. Collect `Playable Class Specialization` info { id, nme, r }
1. Nest Specs into *spcs* array
1. Organize into `PlayableClassSnapshot` { stamp, data [`Playable Class`] }
1. Save snapshot to **USBlizzData.US.PlayableClassSnapshots**
1. Log Job Completion to **USBlizzData.US.Receipts_RunScans** of type "PLAYABLECLASSINFO"

### >>> LEG 2: Mongo DB Trigger
1. MongoDB trigger **PropagatePlayableClassAndSpecInfo** fires on INSERT event on the **USBlizzData.US.PlayableClassSnapshots**
1. For each `Playable Class` in snapshot, upsert into **Cluster1.US.playable_classes**