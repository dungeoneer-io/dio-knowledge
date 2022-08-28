# Mythic+ Periods

- Date period (week) intervals within a given `Mythic Season`
- Primary timeslice of Dungeoneer activity

## Schema and Storage
- Current known state is nested within `Mythic Season` entities on attribute *periods* at **Cluster1.US.mythic_seasons**
- { id, start, end}

## Known Issues
- x

## Pipeline Process
See "Scan Mythic Season" Pipeline detailed in `Mythic Season` [docs](./mythic-season.md)
