# Patch Mods Reference

Patch mods allow you to modify existing game files without replacing them entirely, enabling multiple mods to alter the same files and coexist peacefully.

## Overview

Traditional mods work by replacing entire files. Patch mods define **specific changes** to files rather than replacing them completely. This allows Mod A to increase the elephant's speed while Mod B adds new behaviors to the same elephant - both changes will be applied.

**Benefits:**
- Multiple mods can modify the same files without conflicts
- Change only what you need (precision)
- Enhance or tweak content from other mods (cross-mod support)
- Easier to maintain than full file replacements

## File Structure

Patches are defined in `patch.toml` in your mod's root directory (alongside `meta.toml`):

```toml
# Optional metadata
[patch_meta]
on_error = "continue"  # "continue", "abort", "abort_mod"

# Optional file-level conditions (skip entire file if conditions fail)
[patch_meta.condition]
mod_loaded = "RequiredMod"

# Individual patches
[patches.patch_name]
operation = "set_key"
target = "economy"
section = "checks"
key = "newguest"
value = "1"
```

Each patch has a unique name and specifies an operation. Patches execute in order of appearance.

## File-Level Operations

### Replace
Replace entire file with your version.

```toml
[patches.replace_animal]
operation = "replace"
target = "animals/elephant.ai"
source = "patches/elephant.ai"
```

### Merge
Merge INI files together.

```toml
[patches.merge_configs]
operation = "merge"
target = "animals/elephant.ai"
source = "patches/elephant.ai"
merge_mode = "patch_priority"  # or "base_priority" (default: patch_priority)
```

**Merge modes:**
- `patch_priority`: Your values overwrite existing values when keys conflict
- `base_priority`: Existing values preserved; patch only adds new keys

### Delete
Remove a file from the game.

```toml
[patches.remove_anteater]
operation = "delete"
target = "animals/anteater.ai"
```

### Set Palette
Change animation palette reference (for texture mods).

```toml
[patches.hd_palette]
operation = "set_palette"
target = "animals/tiger/pltiger/N"
palette = "patches/bengal.pal"
```

## Element-Level Operations (INI Files)

Work on specific sections and keys within INI files (`.ini`, `.ai`, `.cfg`, `.uca`, `.ucs`, `.ucb`, `.scn`, `.lyt`).

### Set Single Key
```toml
[patches.set_newguest_chance]
operation = "set_key"
target = "economy"
section = "checks"
key = "newguest"
value = "1"
```

### Set Multiple Keys
```toml
[patches.zoo_test_hacl]
operation = "set_keys"
target = "economy"
section = "characteristic"
keys = {cCreateGuestChangeVeryLow = 100, cCreateGuestChangeLow = 100, cCreateGuestChangeMed = 100, cCreateGuestChangeHigh = 100, cCreateGuestChangeVeryHigh = 100}
```

### Append Single Value
Add to array (repeated keys). **Always use for arrays, not `set_key`**.

```toml
[patches.add_behavior]
operation = "append_value"
target = "animals/elephant.ai"
section = "m/Characteristics/Integers"
key = "cPrey"
value = "5015"
```

### Append Multiple Values
```toml
[patches.add_behaviors]
operation = "append_values"
target = "animals/elephant.ai"
section = "m/Characteristics/Integers"
key = "cPrey"
values = ["5015", "5041", "5045"]
```

### Remove Single Key
```toml
[patches.remove_setting]
operation = "remove_key"
target = "config/settings.ini"
section = "Debug"
key = "LogLevel"
```

### Remove Multiple Keys
```toml
[patches.cleanup_debug]
operation = "remove_keys"
target = "config/settings.ini"
section = "Debug"
keys = ["LogLevel", "DebugMode", "Verbose"]
```

### Add Section
```toml
[patches.add_section]
operation = "add_section"
target = "config/settings.ini"
section = "NewFeature"
keys = { Enabled = "true", Value = "100" }
on_exists = "error"  # "error", "merge", "skip", "replace" (default: error)
```

**on_exists modes:**
- `error`: Fail if section exists
- `merge`: Merge keys with existing section (your keys overwrite on conflict)
- `skip`: Skip if section exists
- `replace`: Delete existing section and create new one

### Clear Section
Remove all keys from section (keeps section).

```toml
[patches.reset_cache]
operation = "clear_section"
target = "config/settings.ini"
section = "Cache"
```

### Remove Section
Delete entire section.

```toml
[patches.remove_deprecated]
operation = "remove_section"
target = "config/settings.ini"
section = "Deprecated"
```

## Variable Substitution

Reference dynamic values from your mod or other mods using `{variable}` syntax.

**Syntax:**
- Current mod: `{type.name}` (e.g., `{habitat.swamp}`)
- Cross-mod: `{mod.type.name}` (e.g., `{lunar.habitat.crater}`)

**Variable types:**
```toml
# Habitat - resolves to habitat string ID
value = "{habitat.swamp}"           # Your mod's habitat
value = "{lunar.habitat.crater}"    # Another mod's habitat

# Location - resolves to location string ID
value = "{location.moon}"           # Your mod's location
value = "{lunar.location.base}"     # Another mod's location

# String - resolves to string content from registry
value = "{string.9500}"             # String by ID
```

**Supported operations:** `set_key`, `set_keys`, `append_value`, `append_values`, `add_section`

**Examples:**
```toml
# Single variable
[patches.assign_habitat]
operation = "set_key"
target = "animals/crocodile.ai"
section = "Habitat"
key = "cHabitat"
value = "{habitat.swamp}"

# Multiple variables
[patches.configure_exhibit]
operation = "set_keys"
target = "exhibits/moon.cfg"
section = "Config"
keys = {
    cHabitat = "{habitat.lunar}",
    cLocation = "{location.moon}",
    NameID = "{string.10500}"
}

# Mixed with text
[patches.set_description]
operation = "set_key"
target = "animals/elephant.ai"
section = "Info"
key = "Description"
value = "Lives in {string.10500} regions"
```

### Legacy Entity Variables

Reference vanilla Zoo Tycoon entities from the original game using `{legacy.entity_type.entity_name}` syntax.

**Syntax patterns:**
- Basic: `{legacy.entity_type.entity_name}` (uses default subtype if applicable)
- With attribute: `{legacy.entity_type.entity_name.attribute}`
- With subtype: `{legacy.entity_type.entity_name.subtype.attribute}`

**Entity types with subtypes** (use default when not specified):
| Entity Type | Default Subtype | Available Subtypes |
|-------------|-----------------|-------------------|
| animals | m (male) | m, f (female), y (young) |
| staff | m (male) | m, f (female) |
| fences | f (fence) | f, g (gate) |
| walls | f (wall) | f, g (gate) |

**Entity types without subtypes:**
- buildings, food, guests, items, paths, scenery

**Examples:**
```toml
# Animals with subtypes (uses default "m")
value = "{legacy.animals.elephant}"        # Male elephant name ID
value = "{legacy.animals.elephant.f.name_id}"  # Female elephant name ID

# Buildings without subtypes
value = "{legacy.buildings.restroom}"       # Restroom name ID
value = "{legacy.buildings.restroom.name_id}"  # Same as above

# Fences with subtypes
value = "{legacy.fences.atltank}"           # Default fence type
value = "{legacy.fences.atltank.g.name_id}" # Gate fence type

# Guests (entity name is section)
value = "{legacy.guests.adult}"             # Adult guest name ID
```

**Note:** Legacy entity types correspond to Zoo Tycoon's original config files (e.g., `animals/` → `.ai` files, `buildings/` → `.bld` files).

## Conditional Patching

Apply patches only when conditions are met.

**Condition types:**
- `mod_loaded`: Check if mod ID is loaded (string)
- `key_exists`: Check if section and key exist (table with `section` and `key`)
- `value_equals`: Check if key has specific value (table with `section`, `key`, and `value`)

All conditions must pass (AND logic).

**Patch-level conditions:**
```toml
# Mod loaded
[patches.dolphin_compat]
operation = "set_key"
target = "animals/dolphin.ai"
section = "Habitat"
key = "WaterDepth"
value = "10"
condition.mod_loaded = "DolphinExpansion"

# Key exists
[patches.upgrade_setting]
operation = "set_key"
target = "config/settings.ini"
section = "Graphics"
key = "AntiAliasing"
value = "4x"
condition.key_exists = { section = "Graphics", key = "AntiAliasing" }

# Value equals
[patches.upgrade_quality]
operation = "set_key"
target = "config/settings.ini"
section = "Graphics"
key = "TextureQuality"
value = "high"
condition.value_equals = { section = "Graphics", key = "TextureQuality", value = "medium" }

# Multiple conditions
[patches.advanced_ai]
operation = "merge"
target = "animals/elephant.ai"
source = "patches/elephant_ai.ai"
condition.mod_loaded = "AdvancedAI"
condition.key_exists = { section = "AI", key = "AdvancedMode" }
condition.value_equals = { section = "AI", key = "AdvancedMode", value = "true" }
```

**File-level conditions:**
Skip entire patch file if conditions fail.

```toml
[patch_meta.condition]
mod_loaded = "RequiredExpansion"

# For key_exists/value_equals, specify target
[patch_meta.condition]
target = "config/settings.ini"
key_exists = { section = "Graphics", key = "HDTextures" }
```

## Error Handling

```toml
[patch_meta]
on_error = "continue"  # "continue", "abort", "abort_mod"
```

**Error modes:**
- `continue` (default): Log error, continue to next patch
- `abort`: Stop processing this patch file, continue loading mod (with rollback)
- `abort_mod`: Stop loading this mod entirely (with rollback)

### Rollback Behavior

When using `abort` or `abort_mod`, OpenZT uses a **shadow-based rollback system** that ensures patch failures don't leave files in a partially modified state:

**How it works:**
1. OpenZT creates shadow copies of all files that will be modified by the patch batch
2. Patches are applied to the shadow copies, not the live resource system
3. On success: Shadow changes are committed to the resource system
4. On failure: Shadow is discarded, leaving original files unchanged (automatic rollback)

**Performance:**
- Memory efficient: Only affected files are cloned
- No explicit restore logic needed (drop shadow = rollback)
- Minimal overhead: Shadow creation + commit typically adds <200ms

**Example:**
```toml
[patch_meta]
on_error = "abort"  # If any patch fails, rollback all changes in this file

[patches.modify_elephant]
operation = "set_key"
target = "animals/elephant.ai"
section = "Stats"
key = "Speed"
value = "15"

[patches.modify_tiger]
operation = "set_key"
target = "animals/tiger.ai"
section = "Stats"
key = "Speed"
value = "20"
```

If `modify_tiger` fails (e.g., file not found), the changes to `elephant.ai` are rolled back automatically.

## Execution Order

### Inter-Mod Execution Order

1. Patches execute during mod loading at game startup
2. Mods load in order specified in `zoo.ini`
3. Each mod's patches run when that mod loads
4. Later mods can patch files from earlier mods or base game

Patches target the **cumulative state** of files (base game + all previously loaded mods).

### Intra-Mod Definition File Loading Order

Within a single mod, definition files (`.toml` files in `defs/` directory) are loaded in a **deterministic order** to ensure patches can reliably reference habitats and locations defined earlier in the same mod.

**Category-Based Loading:**

Definition files are categorized based on their contents:

1. **NoPatch** - Files with only habitats/locations, no patches
2. **Mixed** - Files with both habitats/locations AND patches
3. **PatchOnly** - Files with only patches, no habitats/locations

**Loading Order Within a Mod:**

```
1. All NoPatch files (alphabetically)
   ├─ 00-habitats.toml
   ├─ 01-locations.toml
   └─ Animals-Only.toml      (case-insensitive sort)

2. All Mixed files (alphabetically)
   ├─ 50-mixed-content.toml
   └─ 51-more-mixed.toml

3. All PatchOnly files (alphabetically)
   ├─ 98-patches.toml
   └─ 99-more-patches.toml
```

**Why This Matters:**

- **Habitats/locations are registered before patches that use them** - NoPatch and Mixed files define habitats/locations first, ensuring PatchOnly files can reference them
- **Predictable execution** - Alphabetical sorting within categories means `01-*.toml` always loads before `02-*.toml`
- **Cross-file references work** - A PatchOnly file can use `{habitat.swamp}` if any NoPatch or Mixed file defines `swamp`
- **Self-references work** - A Mixed file can define a habitat and immediately patch it in the same file

**Example Structure:**
```
your-mod/
├── meta.toml
└── defs/
    ├── 00-habitats.toml      # NoPatch - defines swamp, desert habitats
    ├── 01-locations.toml     # NoPatch - defines africa, asia locations
    ├── 50-mixed.toml         # Mixed - defines ocean habitat + patches using it
    └── 99-patches.toml       # PatchOnly - patches using swamp, desert, ocean
```

**Important Notes:**

- **Use identifiers, not display names** - Variable substitution uses the TOML key identifier:
  ```toml
  # In 00-habitats.toml
  [habitats.swamp_habitat]  # ← This is the identifier
  name = "Swamp Habitat"    # ← This is the display name

  # In 99-patches.toml - Use the identifier!
  value = "{habitat.swamp_habitat}"  # ✓ Correct
  value = "{habitat.Swamp Habitat}"  # ✗ Wrong - will fail
  ```
- **Alphabetical sorting is case-insensitive** - `Animals.toml` and `animals.toml` sort the same
- **Numeric prefixes control order** - Use `00-`, `01-`, `02-` etc. to control loading sequence
- **Within-file patch order** - Patches within a single file execute in the order they appear

### Patch Execution Order Within Files

Patches within a single definition file execute in the order they appear:

```toml
[patches.first]
operation = "set_key"
# ...

[patches.second]
operation = "set_key"
# ... (executes after 'first')

[patches.third]
operation = "set_key"
# ... (executes after 'second')
```

This matters when multiple patches modify the same file or key - later patches override earlier ones.

## Technical Notes

**Case Sensitivity:**
- Section and key names are case-insensitive (matching Zoo Tycoon's INI behavior)
- File paths are case-insensitive
- Variable names are case-sensitive

**File Format Support:**
- Element operations: Only INI-like files (`.ini`, `.ai`, `.cfg`, `.uca`, `.ucs`, `.ucb`, `.scn`, `.lyt`)
- File operations: Any file type (`replace`, `delete`, `set_palette`)

**Array Handling:**
- Zoo Tycoon uses repeated keys for arrays
- `append_value`/`append_values`: Add to arrays
- `set_key`/`set_keys`: Replace entire value (destroys array if used on array key)
- `remove_key`: Removes all instances (entire array)

## Troubleshooting

**"Target file not found":**
- Check file path spelling and case
- Verify file exists in base game or previously loaded mod
- Check mod load order (if patching another mod's file)

**"Section not found" (for remove operations):**
- Warning only; operation is skipped

**"Invalid file type for element operation":**
- Element operations only work on INI-like files (`.ini`, `.ai`, `.cfg`, `.uca`, `.ucs`, `.ucb`, `.scn`, `.lyt`)

**Variable resolution errors:**
- "Undefined variable": habitat/location/string doesn't exist in mod or referenced mod
- "Mod not loaded": Cross-mod reference to mod that isn't loaded or loads after yours
- "Invalid syntax": Check `{variable}` syntax for typos or unclosed braces

**Patches not applying with abort/abort_mod:**
- Ensure all patches in the file are valid before rollback occurs
- Check OpenZT logs for specific error that triggered rollback
- Verify patches are in same `patch.toml` file (rollback scope is per-file)
- Test with `on_error = "continue"` first to identify which patch is failing

## Best Practices

**Developing patch mods:**

1. **Start with `continue` mode** - Use `on_error = "continue"` during development to see all errors at once
2. **Check the logs** - Review `openzt.log` in Zoo Tycoon directory for detailed patch application messages
3. **Test incrementally** - Add a few patches at a time, test, then add more
4. **Use descriptive names** - Name patches clearly (e.g., `increase_elephant_speed` not `patch1`)
5. **Add comments** - Use TOML comments to document what patches do and why
6. **Switch to abort mode** - Once patches work reliably, use `on_error = "abort"` for automatic rollback
7. **Test with other mods** - Verify your patches work alongside popular mods
8. **Document dependencies** - If your patches require other mods, use `mod_loaded` conditions AND declare them in `meta.toml`

**Example well-structured patch file:**
```toml
# Patch metadata
[patch_meta]
on_error = "abort"  # Rollback all changes if any patch fails

# Only apply if HD Texture Pack is loaded
[patch_meta.condition]
mod_loaded = "HDTexturePack"

# Update elephant to use HD textures
[patches.elephant_hd_palette]
operation = "set_palette"
target = "animals/elephant/adult/male/n"
palette = "animals/elephant/hd.pal"

# Increase elephant visibility with HD textures
[patches.elephant_visibility]
operation = "set_key"
target = "animals/elephant.ai"
section = "Graphics"
key = "Brightness"
value = "1.2"
```

**Corresponding meta.toml:**
```toml
id = "ElephantHDCompat"
name = "Elephant HD Compatibility"
version = "1.0.0"
author = "YourName"
description = "Compatibility patches for elephants with HD Texture Pack"

[dependencies]
HDTexturePack = ">=1.0.0"
```

## See Also

- **[PATCH_SCHEMA.md](PATCH_SCHEMA.md)**: Complete technical schema documentation
- **[Habitats and Locations](habitats_and_locations.md)**: Define custom habitats and locations
