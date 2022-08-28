# ZEPHYR Data Zone

Isolated to the seam-work with Blizzard Entertainment. Team ZEPHYR has a small scope focused on acquiring foundational data and establishing a single source of truth.


### Mission
Expose Blizzard Entity data (bE+) to all Dungeoneer.io apps via BlizzDataDb

### Sensitive Access
- Blizzard Account: dungeoneer.io@gmail.com
- API Acct + Key
- BlizzDataDB Connection String
- BlizzDataDB Write Access User Account

### Responsibilities
- Acquiring Snapshot data from Blizzard
  - Expire snapshots according to TOS
- Harvesting bE+ from snapshots
  - BlizzDataDb as source of truth for bE+
- Keep the seams between Blizzard-ZEPHYR and ZEPHYR-Dio in tact
  - No Dungeoneer domain knowledge or data
  - Only team to access Blizzard API


### From Idea:
Zephyr takes realtime available data from Blizzard Entertainment and makes it permanently available to Dungeoneer.
- Snapshots captured in RAW form, complete with TTL
- Repeatable transformation from RAW data to FACT tables occurs here
- No DIO Domain information is here
- Read only to any DIO tools outside of Zephyr
