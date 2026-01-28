# Extension Mods Reference

Extension mods allow you to tag and categorize game entities for runtime behavior, enabling features like dynamic filtering, UI enhancements, and contextual interactions.

## Overview

Extension mods define **tags and attributes** for existing game entities. Unlike patch mods which modify files, extension mods provide metadata that OpenZT and other mods can use at runtime.

**Benefits:**
- Tag entities for runtime identification and filtering
- Enable cross-mod compatibility through shared tag systems
- No file conflicts - multiple mods can tag the same entity
- Foundation for advanced features like UI filtering and entity grouping

**Use Cases:**
- Grouping entities by type (e.g., "roof" objects that can be hidden)
- Categorizing items for UI organization
- Providing metadata for other mods to consume
- Enabling contextual behaviors based on entity properties

## Tags vs Attributes

| Feature | Tags | Attributes |
|---------|------|------------|
| Purpose | Categorization/grouping | Named properties with values |
| Values | String names | String key-value pairs |
| Example | `tags = ["roof", "decoration"]` | `attributes = { height = "large" }` |
| Use Case | Boolean membership (has/doesn't have) | Configuration data |

## Creating an Extension Mod

### Extension Definition Format

Extensions are organized by **entity type** in your `.toml` files:

```toml
[scenery.vondel_greenhouse_roof]
base = "legacy.scenery.vogrhrf1"
tags = ["roof"]

[animals.elephant]
base = "legacy.animals.elephant"
tags = ["big"]
attributes = { size = "large" }
```

### The `base` Field

The `base` field identifies which game entity you're extending:

```
legacy.{entity_type}.{entity_name}
```

Examples:
- `legacy.scenery.statue` - Scenery object named "statue"
- `legacy.animals.elephant` - Animal named "elephant"
- `legacy.buildings.restaurant` - Building named "restaurant"

### Entity Type Sections

| Section | Entity Type |
|---------|-------------|
| `[scenery.xxx]` | Scenery objects |
| `[animals.xxx]` | Animals |
| `[buildings.xxx]` | Buildings |
| `[fences.xxx]` | Fences |
| `[walls.xxx]` | Tank walls |
| `[paths.xxx]` | Paths |
| `[food.xxx]` | Food items |
| `[staff.xxx]` | Staff |
| `[guests.xxx]` | Guests |
| `[items.xxx]` | Items |

## Concrete Example: The Roof Tag System

The roof system is a **real, working example** of extensions in OpenZT. It allows hiding/showing roof objects with Ctrl+R.

### What It Does

1. Tags scenery objects as "roof" entities
2. Provides Ctrl+R keyboard shortcut to toggle roof visibility
3. Auto-hides newly placed roofs when roofs are currently hidden

### Mod Author Side (TOML)

To tag your scenery objects as roofs, add this to your mod's `defs/extensions.toml`:

```toml
[scenery.vondel_greenhouse_roof]
base = "legacy.scenery.vogrhrf1"
tags = ["roof"]

[scenery.my_custom_roof]
base = "legacy.scenery.myroof"
tags = ["roof"]
```

### How It Works

When you tag an object with the "roof" tag:

1. **Loading**: Your mod's extensions are loaded and stored
2. **Identification**: When you place an object in-game, OpenZT identifies its base string
3. **Matching**: The object's base is matched against registered extensions
4. **Behavior**: Tagged roofs respond to Ctrl+R and auto-hide when roofs are hidden

## Entity Type Reference

### Entity Types and Their Properties

| Type | Section Name | Has Subtypes | Default Subtype | Base Format Example |
|------|--------------|--------------|-----------------|---------------------|
| Scenery | `objects` | No | - | `legacy.scenery.statue` |
| Animals | `animals` | Yes | m (male) | `legacy.animals.elephant` |
| Buildings | `building` | No | - | `legacy.buildings.restaurant` |
| Fences | `fences` | Yes | f (fence) | `legacy.fences.wood` |
| Walls | `tankwall` | Yes | f (fence) | `legacy.walls.acrylic` |
| Paths | `paths` | No | - | `legacy.paths.grass` |
| Food | `food` | No | - | `legacy.food.burger` |
| Staff | `staff` | Yes | m (male) | `legacy.staff.keeper` |
| Guests | `guests` | No | - | `legacy.guests.adult` |
| Items | `items` | No | - | `legacy.items.icecream` |

### Finding Entity Base Strings

To find the correct base string for an entity:

1. **Check existing mods**: Look at other extension mods or the game's `.cfg` files
2. **Use the console**: Run `list_entities()` in the Lua console to see all entities
3. **Check entity files**: Look at the entity's `.cfg` file in the game resources
4. **For UCA, UCS and UCB files**: Use the UCA/UCS/UCB filename without the extensions so `vogrhrf1.ucs` becomes `legacy.scenery.vogrhrf1`

Example from a animal `.cfg` file (`animal01.cfg`):
```ini
[animals]
blckbuck = animals/blckbuck.ai
...
```
This corresponds to base: `legacy.animals.blckbuck`

## Hypothetical Examples

> **Note**: The following examples are **illustrative only**. They demonstrate what COULD be done with extensions, but these specific tags and attributes are not implemented in the base OpenZT system.

### Example 1: Decorative Items (Hypothetical)

```toml
# HYPOTHETICAL EXAMPLE - "decoration" tag is not implemented
[scenery.statue]
base = "legacy.scenery.statue"
tags = ["decoration"]      # illustrative - tag doesn't exist
```

### Example 2: Animal Size Categories (Hypothetical)

```toml
# HYPOTHETICAL EXAMPLE - "size" attribute is not implemented
[animals.elephant]
base = "legacy.animals.elephant"
tags = ["big"]             # illustrative - tag doesn't exist
attributes = { size = "large" }  # illustrative - attribute doesn't exist
```

### Example 3: Multi-Tag Entity (Hypothetical)

```toml
# HYPOTHETICAL EXAMPLE - These tags are not implemented
[scenery.fancy_fountain]
base = "legacy.scenery.fountain"
tags = ["decoration", "water_feature"]  # illustrative - tags don't exist
attributes = {
    maintenance = "high",      # illustrative - attribute doesn't exist
    value = "500"
}
```

> **Important**: To use new tags or attributes beyond "roof", you would need to modify the OpenZT source code to register them and implement their behavior. As a modder, you can currently only use the existing "roof" tag.

## Extension Validation

### What Gets Validated

When extensions are loaded, OpenZT validates:

1. **Base format**: Must match `legacy.{type}.{name}` pattern
2. **Entity type**: The type in the base must be valid (animals, scenery, etc.)
3. **Tag validity**: All tags must be registered for the entity's type
4. **Attribute validity**: All attributes must be registered for the entity's type

### Error Messages

```toml
# INVALID: Tag not registered for this entity type
[fences.iron]
base = "legacy.fences.iron"
tags = ["roof"]  # ERROR: "roof" tag only applies to scenery, not fences
```

```toml
# INVALID: Malformed base string
[scenery.myobject]
base = "scenery.myobject"  # ERROR: Missing "legacy." prefix
```

## Best Practices

### Tag Naming Conventions

- Use **lowercase** with underscores: `roof`, `water_feature`
- Use **nouns** for categories: `decoration`, `predator`
- Use **adjectives** for properties: `big`, `toxic`
- Keep names **short and descriptive**

### When to Use Tags vs Attributes

**Use tags when:**
- You need simple yes/no categorization
- The property doesn't need a value
- Multiple mods need to check for the same thing

**Use attributes when:**
- You need to store specific values
- The property has degrees or levels
- You need configuration data

### Using Existing Tags

Currently, the **roof** tag is the only tag implemented in base OpenZT. When creating mods:

1. **Use the "roof" tag**: Apply it to scenery objects that should hide with Ctrl+R
2. **Test your extensions**: Always validate that your extensions load correctly
3. **Coordinate with other modders**: If you're working on an OpenZT fork with custom tags, communicate with the community

## Complete Example: Roof Extension Mod

Here's a complete example of a mod that tags objects as roofs:

```toml
# meta.toml
name = "Roof Pack"
description = "Adds roof objects that can be hidden with Ctrl+R"
authors = ["Your Name"]
mod_id = "author.roof_pack"
version = "1.0.0"
ztd_type = "openzt"
```

```toml
# defs/extensions.toml
[scenery.japanese_temple_roof]
base = "legacy.scenery.japanroof"
tags = ["roof"]

[scenery.castle_turret_roof]
base = "legacy.scenery.turret"
tags = ["roof"]
```

Users can now:
- Press **Ctrl+R** to toggle all roof visibility
- Place roof objects and they'll respect the hidden state
- Other mods can check for the "roof" tag to include/exclude these objects

## Related Topics

- **[Patch Mods](patch_mods.md)** - For modifying game files
- **[Getting Started](getting-started.md)** - OpenZT basics
- **[Habitats and Locations](habitats_and_locations.md)** - Custom biomes and maps
