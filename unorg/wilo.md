
## Nice to haves for later
- Event feed that lists when new items appear and when items are no longer appearing in the foundational dataset lists
- Load each into daily CRON jobs on AWS
- Daily CRON Job: Deprecation Check for `Connected Realm` entities, missing for 48+ hours and minimum snapshot count absent
- How to do mythic dungeon sot listings? vary by period on durations


## RISKS
- Mongo triggers for Run propagation relies on hardcoded CLS<->SPC and US Region CRLM maps
- Time sensitive endpoint scans might need an additional leg of their journey
  - Realms, Crealms, Classes, Specs are **not** time sensitive
  - `Mythic Dungeon Runs` are time sensitive
  - **Consider** if the model changes on blizzard's end, there is no recovering the failed scans
    - Additional leg would scan straight JSON into storage then inform next leg that a new snapshot is available to process. If that job fails, we can re-run scans when the transformer is upgraded
- Can only have 5 triggers built into MongoDB free instances
  - worth upgrading? -or- connecting to prod databases from scanners and propagating manually?

spin out: address people making new characters by old characters name. assume lookup goes to character/slug with most recent "foundOn" type stamp. otherwise, you may need to disambiguate with deeper link. that's painful.
