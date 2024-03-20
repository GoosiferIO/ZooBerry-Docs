# UI General API

The UI General API contains generalized utility functions for interacting with the game's user interface. Generally speaking, you can use this API to obtain state information when clicking on entities, world objects, and perhaps even the game's UI.

## Usage

All commands in this API are static functions and the UI General object is available as a global variable called `ztUIGeneral` in the Lua scripting environment.

Example Script:
```Lua
function emu_run()
    local selected_entitytype = ztUIGeneral.getSelectedEntityType()
    local buildingtype = ZTBuildingType.new(selected_entity)
    io.write("Selected building purchase cost: " .. guesttype:cPurchaseCost())
end
```

## Definitions

| Command  | Description |
| ------------- | ------------- |
| `getSelectedEntity()` | Returns an instance of the selected entity. |
| `getSelectedEntityType()` | Returns an instance of the selected entity type. |
| `makeSelectableByType(int entity_id)` | Make an entity type selectable. Takes in an entity ID as an argument. For a list of entity IDs, see [List of Notable Entity IDs](/docs/zt1/reference/string-tables/entity-ids.md). |
| `makeSelectable(table entities)` | Make a range of entities selectable. Takes in a table of entities as an argument. |