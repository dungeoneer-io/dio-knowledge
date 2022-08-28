# Playable Role

- In World of Warcraft character parties, each character is assigned a role: *Tank*, *Healer*, or *Damage Dealer*
    - 1/1/3 is the standard party allocation in a 5 character party

## Schema and Storage
- No entity management, this can be highly variant as each character can swap roles as they move from specialization to specialization

## Known Issues
- `Mythic Dungeon Run` may need to map `Playable Class Specialization` entities to `Playable Role` but this is not an official mapping and would need to be manually maintained

## Numerical Representation
- `1` Tank
- `2` Healer
- `3` Damage
