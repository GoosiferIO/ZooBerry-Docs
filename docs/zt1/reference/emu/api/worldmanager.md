# World Manager API

## Overview

The World Manager API is a collection of functions that allow you to interact with the game's world and control the generalized state of the game. At the moment this is limited to obtaining entity instances from the current world state. In other words: if your game was able to successfully load an animal, building, guest, or staff member, you can use this API to obtain a reference to it as an entity type or entity.

For more information on entities and entity types, see [Operating on Entities](/docs/zt1/advanced/operating-on-entities.md).

## Usage

All commands in this API are static functions and the World Manager object is available as a global variable called `ztWorldMgr` in the Lua scripting environment.

Example Script:
```lua
function emu_run ()
    local all_animals = ztWorldMgr.getAllEntitiesOfType({5012, 5013})
    for i, animal in ipairs(all_animals) do
        local animal_type = ZTAnimalType.new(animal)
        emuConsole.print("Animal name: " .. animal_type:name())
    end
```

!!! info "Note"
    The `ZTAnimalType` API is not yet implemented in EMU API. This is a hypothetical example, but can be reproduced successfully with any of the EntityType APIs documented at [Entity Types](/docs/zt1/reference/emu/api/entitytypes.md).

## Definitions

| Command  | Description |
| ------------- | ------------- |
| `getAllEntitiesOfType(table entity_ids)` | Returns a table of all entities of the specified type IDs. For a list of entity IDs, see [List of Notable Entity IDs](/docs/zt1/reference/string-tables/entity-ids.md). |
| `getEntityTypeByID(int entity_id)` | Returns an instance of the specified entity type. |
| `setVanishGuard(table entities, bool vanish_guard)` | Set the vanish guard of a range of entities. A vanish guard sets a fence visibility and indestructible state. |
| `isEntityNull(void* entity)` | Returns a boolean value indicating whether the entity is null. |