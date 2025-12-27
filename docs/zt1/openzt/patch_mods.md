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
target = "animals/elephant.ai"
section = "Stats"
key = "Speed"
value = "15"
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
target = "config/settings.ini"
source = "patches/settings.ini"
merge_mode = "patch_priority"  # or "base_priority" (default: patch_priority)
```

**Merge modes:**
- `patch_priority`: Your values overwrite existing values when keys conflict
- `base_priority`: Existing values preserved; patch only adds new keys

### Delete
Remove a file from the game.

```toml
[patches.remove_old_animal]
operation = "delete"
target = "animals/oldanimal.ai"
```

### Set Palette
Change animation palette reference (for texture mods).

```toml
[patches.hd_palette]
operation = "set_palette"
target = "animals/elephant/adult/male/n"  # No extension
palette = "animals/elephant/hd.pal"
```

## Element-Level Operations (INI Files)

Work on specific sections and keys within INI files (`.ini`, `.ai`, `.cfg`, `.uca`, `.ucs`, `.ucb`, `.scn`, `.lyt`).

### Set Single Key
```toml
[patches.set_resolution]
operation = "set_key"
target = "config/settings.ini"
section = "Graphics"
key = "Resolution"
value = "1920x1080"
```

### Set Multiple Keys
```toml
[patches.configure_audio]
operation = "set_keys"
target = "config/settings.ini"
section = "Audio"
keys = { Volume = "100", Enabled = "true", MusicVolume = "80" }
```

### Append Single Value
Add to array (repeated keys). **Always use for arrays, not `set_key`**.

```toml
[patches.add_behavior]
operation = "append_value"
target = "animals/elephant.ai"
section = "Behaviors"
key = "Action"
value = "swim"
```

### Append Multiple Values
```toml
[patches.add_behaviors]
operation = "append_values"
target = "animals/elephant.ai"
section = "Behaviors"
key = "Action"
values = ["climb", "jump", "run"]
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
value = "Lives in {habitat.savanna} regions"
```

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
- `abort`: Stop processing this patch file, continue loading mod
- `abort_mod`: Stop loading this mod entirely

!!! warning "Current Limitation"
    Only `on_error = "continue"` is currently supported. `abort` and `abort_mod` require snapshot/rollback functionality (coming in future update).

## Execution Order

1. Patches execute during mod loading at game startup
2. Mods load in order specified in `zoo.ini`
3. Each mod's patches run when that mod loads
4. Patches within a mod execute in order they appear in `patch.toml`
5. Later mods can patch files from earlier mods or base game

Patches target the **cumulative state** of files (base game + all previously loaded mods).

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

## See Also

- **[PATCH_SCHEMA.md](PATCH_SCHEMA.md)**: Complete technical schema documentation
- **[Habitats and Locations](habitats_and_locations.md)**: Define custom habitats and locations
