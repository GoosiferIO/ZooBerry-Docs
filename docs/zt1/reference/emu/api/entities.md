# Entity API

## Overview

The Entity API contains functions for interacting with entities in the game. Please note that there is a fundamental difference between an entity and an entity type. An entity is an instance of an entity type, and an entity type is a template for an entity. For more information on entities and entity types, see [Operating on Entities](/docs/zt1/advanced/operating-on-entities.md).

## Usage

This API requires an instance of an entity to be passed as an argument to a `BFEntity` object or one of its subclasses. For example, to obtain an instance of an entity, you might use the `getAllEntitiesOfType` function in the [World Manager API](/docs/zt1/reference/emu/api/worldmanager.md).

Example Script:
```lua
function emu_run ()
    local all_animals = ztWorldMgr.getAllEntitiesOfType({5012, 5013})
    for i, animal in ipairs(all_animals) do
        local animal_entity = ZTEntity.new(animal)
        emuConsole.print("Animal name: " .. animal_entity:name())
    end
end
```

!!! info "Note"
    The `ZTEntity` API is not yet implemented in EMU API. This is a hypothetical example, but can be reproduced successfully with any of the EntityType APIs documented at [Entity Types](/docs/zt1/reference/emu/api/entitytypes.md).

It's worth noting that as of this writing, the `BFEntity` API is not yet fully implemented in EMU API. There is simple access to some of the entity's functions and properties, but not all. This is a work in progress. Only the `BFEntity` class is documented here, but because it's a chain of inheritance, you can technically use any of the subclasses detailed below as the class for the `BFEntity` object.

## BFEntity

| Command  | Description |
| ------------- | ------------- |
| `visible()` | Returns a boolean value indicating whether the entity is visible. |
| `visible(bool visible)` | Set the visibility of the entity. |
| `name()` | Returns the name of the entity. |

The only other class currently available in the EMU API and has access to the same functions as `BFEntity` is `ZTGuest`. There are currently no unique functions to `ZTGuest` to list.

