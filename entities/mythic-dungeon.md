# Mythic+ Dungeons

- `Mythic Dungeon` data varies in upgrade speeds and participation by period (and mostly by season)

## Schema and Storage
- Current known state is stored at **USBlizzData.US.PeriodDungeonSnapshots**
- { stamp, period, data: [`Mythic Dungeon`] }

## Known Issues
- Unique to the period on which it participates
- Final resting place undetermined at this time. Maybe nested in periods in seasons?

## Pipeline Process
"Scan Mythic Dungeon" Pipeline

### API Snapshot Retrieval
1. BlizzAPI: Get `Mythic Dungeon` Index
1. Collect `Mythic Dungeon` info { id, nme, map, zone, did, upg: { 1: 0, 2: 0, 3: 0 } }
1. Organize into `PeriodDungeonSnapshot` { stamp, period, data [`Mythic Dungeon`] }
1. Save snapshot to **USBlizzData.US.PeriodDungeonSnapshots**
1. Log Job Completion to **USBlizzData.US.Receipts_RunScans** of type "MYTHICDUNGEONINFO"
