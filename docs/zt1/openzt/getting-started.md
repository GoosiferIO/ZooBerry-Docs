# Getting Started

This page will lay out the basics of OpenZT modding, including filetypes, folder layout and meta info

## Filetypes
All config files use the [toml format](https://toml.io/), which looks very similar to the INI-like format the Zoo Tycoon uses, but with much better support and an official spec.

Toml files should always have the `.toml` file type, regardless of use.

Currently all graphics files remain the same as in Zoo Tycoon, new formats will likely be added in the future to make creating mods easier.

## File/Folder structure

The following top level structure is mandatory (unused folders can be left out, but definitions must be in a folders called Defs, resources in a folder called Resources etc)

```
Defs
Resources
meta.toml
```

### meta.toml
`meta.toml` contains all the meta information about your mod.

```toml
name="my example mod"
description="a mod full of examples"
authors=["Finn"]
mod_id="finn.my_example_mod"
version="1.0.0"
link="https://myexamplewebsite.com/myexamplemod"
ztd_type="openzt"
dependencies=[
    {mod_id="finn.my_other_example_mod", name="My Example Mod", min_version="1.1.2", optional=true, ordering="before"},
    {ztd_name="traditional_scenery.ztd", name="Traditional Scenery", ordering="after"},
    {dll_name="langusa.dll", name="English Language", optional=true}
]
```

Lets break this file down

#### meta.toml

| Field Name   | Purpose                                                                                                                                                                                                         | Example                          | Mandatory                                          |
|--------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------|----------------------------------------------------|
| name         | This is the mod name displayed to the user                                                                                                                                                                      | "My example mod"                 | Yes, cannot be empty                               |
| description  | A short description of what your mod does                                                                                                                                                                       | "Adds a Dodo to the game"        | Yes, cannot be empty                               |
| authors      | A list of authors                                                                                                                                                                                               | ["Finn", Goosifer"]              | Yes, must contain at least one author              |
| mod_id       | A short unique string for your mod, generally in the form "author.mod_name" or "author.project.mod_name", used to make sure two versions of the same mod aren't loaded and to resolve dependencies between mods | "finn.my_mod"                    | Yes, cannot be empty or contain spaces             |
| version      | Used to differentiate different versions of the same mod, must be 3 numbers separated by periods                                                                                                                | "1.0.4"                          | Yes, cannot be empty, must contain a valid version |
| link         | An optional link for the author to advertise themselves                                                                                                                                                         | "https://www.mywebsite.com/mods" | No                                                 |
| ztd_type     | The type of mod, can be "legacy" for a vanilla Zoo Tycoon mod, "openzt" for an OpenZT mod or "combined" if it contains files from both vanilla Zoo Tycoon and OpenZT | "combined"| No, defaults to "openzt" if left empty |
| dependencies | A list of dependencies that this mod requires or is usually used with.                                                                                                                                          |                                  | No                                                 |

##### Dependencies

| Field Name   | Purpose                                                                                                                              | Example                  | Mandatory                             |
|--------------|--------------------------------------------------------------------------------------------------------------------------------------|--------------------------|---------------------------------------|
| (identifier) | One of: `mod_id`, `ztd_name`, or `dll_name` (exactly one required)                                                               | See below                | Yes (one of the three)                |
| name         | Human-readable name of the dependency                                                                                               | "My other mod"           | Yes                                   |
| min_version  | Minimum version (ONLY works with `mod_id`, ignored for `ztd_name`/`dll_name`)                                                     | "1.1.4"                  | No, must be valid version if supplied |
| optional     | Whether the dependency is required                                                                                                   | true                     | No, defaults to false                 |
| ordering     | Indicates whether the dependency should be loaded before or after the current mod ("before", "after", or "none")                    | "before"                 | No, defaults to "none"                |

###### Dependency Identifier Types

Choose **ONE** identifier type per dependency:

**`mod_id`** (Recommended for OpenZT mods)
- References another OpenZT mod by its unique `mod_id`
- Supports version checking with `min_version`
- Most reliable for OpenZT mods
- Example: `{ mod_id = "finn.animals", name = "Animal Pack", min_version = "2.0.0" }`

**`ztd_name`** (For traditional mods)
- References a mod by its `.ztd` filename (e.g., `"my_mod.ztd"`)
- Does NOT support `min_version` (will be ignored with a warning)
- Use when depending on mods that don't have OpenZT metadata
- Example: `{ ztd_name = "scenery_pack.ztd", name = "Scenery Pack" }`

**`dll_name`** (For game language DLLs)
- References Zoo Tycoon language DLLs (must end with `.dll`)
- Only validates against language DLLs matching `lang*.dll` pattern
- Does NOT support `min_version` (will be ignored with a warning)
- Example: `{ dll_name = "langusa.dll", name = "English Language", optional = true }`


### Defs
Defs are where Mod definitions go, these are `.toml`` files organised however you want, in as many subfolders as you want. Types of definitions can be mixed within the same file, partitioned into seperate files, however you wish, OpenZT does not care.

### Resources
Similar to the `defs` folder, you may organise resources however you please, the filepath is taken from the `.toml` file in `defs` that is using the resource. There is also no restriction on how many `.toml` files in `defs` can reference a specific resource.
