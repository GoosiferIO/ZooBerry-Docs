!!! note "Incomplete"
    This page is incomplete. Pull requests welcome.

# Scenery Documentation

This page assumes the game directory definition of what a 'scenery' item entails. Under the 'scenery' folder under the game's assets, it includes buildings, foliage, rocks, terrain, toys, zoos, and other zoo utilities.

The main configuration for these files are in `.ucb`, `.ucs`, or `.ai` format, but they are really `.INI` files. The following tables describe attributes that can  be given to the entities mentioned. Example files can be found in a respective `/scenery` directory.

Please note that this guide is meant for reference only and is not in any way meant to imply the use of every attribute or section to make a specific kind of scenery or building entity. Instead, please refer to either official files or available mods for ideas. Use this guide to then experiment and create a derivative work.

## `[<Codename>]`

Scenery configuration files require a unique 8-character codename that will be used across the project.

<h3>Example codenames</h3>

- `uforidgs`
- `F5DAD057`
- `blnstngs`

For personal use a unique codename might not matter so much, but if you'd like to minimize compatibility clashes with other mods due to codename conflicts, it might be a good idea to pick a non-generalized name.

## `[Icon]`

`[Icon]` defines the directory for that entity's four icons.

| Key                  | Value | Description|
|----------------------|------|-----|
| `Icon` | `<dir>` | Directory to the icon graphic |

<h3>Example</h3>

```INI
[Icon]
Icon = objects/<Codename>/SE/SE
Icon = objects/<Codename>/SW/SW
Icon = objects/<Codename>/NW/NW
Icon = objects/<Codename>/NE/NE
```

## `[Characteristics/Integers]`

!!! note "Incomplete"
    This section is incomplete. Needs remaining characteristics defined.

This defines misc. characteristics about an entity. 

Usually found inside an entity's `.ucb` or `.ai` file. Can be found in a respective /scenery/other directory.

This isn't comprehensive, but here are a few:


| Key                  | Value | Description|
|----------------------|------|-----|
| `cNameID`            | `<int>` | Integer key associated with a string that gives the entity its name. Value of `19000`means the string is defined inside of the `.ucb` file. If it's a 4-digit number it's a key associated with a string in a `.dll` lang file. |
| `cHelpID` | `<int>` | Same concept as `cNameID`: keys for strings, but this one is for tooltips. If `cNameID` is set to `19000`, ZT ignores `cHelpID`. |
|`cPurchaseCost` | `<int>` | Price of entity |
| `cFootprintX` | `<int>` | Size of entity footprint in X direction. Value of `1` can be used for `1/4` or `1/2` tiles, otherwise must be an even integer. |
| `cFootprintY` | `<int>` | Size of entity footprint in Y direction. Value of `1` can be used for `1/4` or `1/2` tiles, otherwise must be an even integer. |
| `cHeight` | `<int>` | Height of entity. Consistent with construction tool height. |
| `cSelectable` | `<0/1>` | Can the entity be selected. |
| `cNeedsConfirm` | `<0/1>` | Does entity need confirmation window when bulldozed. |
| `cMoveable` | `<0/1>` | Can the entity be moved after placed. |
| `cAdultChange` | `<int>` | How happy a guest is after using the entity. Negative values are possible if you want them to hate it. | 
| `cChildChange` | `<int>` | Same as above but specifically child guests. |
| `cCommerce` | `<int>` | Does a user need to pay to use this entity? |
| `cHabitat` | `<int>` | What habitat the entity belongs to. `9414` makes entities unplaceable in exhibits. `9411` allows entities placeable in all exhibits. For a full list of possible values, please see [Entity IDs](./entity-ids.md#habitat)|
| `cHideBuilding` | `<0/1>` | Hide building or show? |
| `cUsersStayOutside` | `<0/1>` | Prevent a user from entering entity? |
| `cTimeInside` | `<int>` | How long should a user be inside of a building. It mmight make sense to match this value with length of sound file if provided. 
| `cUsedThought` | `<int>` | A user's thought after using the entity. Works similar in concept to other key/value strings above. |   
| `cHideUser` | `<int>` | Setting this to `1` hides the user while using the entity. Set to `0` or delete line to exclude this configuration. |
| `cAutoRotate` | `<int>` | Setting this to `1` automatically rotates the object on placement. Set to `0` or delete line to exclude this configuration. |
| `cSwims` | `<int>` | Setting this to `1` allows the object to be placed on water. Set to `0` or delete line to exclude this configuration. |
| `cOnlySwims` | `<int>` | Setting this to `1` makes it so the object is only placeable on water and not on land. Set to `0` or delete line to exclude this configuration. |
| `walkable` | `<int>` | Setting this to `1` allows guests and animals to walk through the object. Set to `0` or delete line to exclude this configuration. |
| `cFoliage` | `<int>` | Should this foliage count toward exhibit suitability? `0` for no, `1` for yes. As the name implies, usually used for foliage. |

<h3>Example</h3>
```INI
[Characteristics/Integers]
cPurchaseCost = 2000
cFootprintX = 12
cFootprintY = 6
cHabitat = 9414
cHeight = 3
cHelpID = 32610
cNameID = 2610
cCommerce = 1
cSelectable = 1
cNeedsConfirm = 1
cAdultChange = 10
cChildChange = 15
cEnergyChange = -100
cHideUser = 1
cHideBuilding = 0
cUserStaysOutside = 0
cCapacity = 10
cTimeInside = 12
cUsedThought = 8761
cIsColorReplaced = 0
cMoveable = 1
cSwims = 1
```

## `[Animations]`

| Key                  | Value | Description|
|----------------------|------|-----|
| `idle` | `idle` | Idle defines your entity as having graphics without animation. |
| `used` | `used` | Used defines youru entity as having graphics with animation. |

```INI
[Animations]
idle = idle
```

## `[EstheticBonus]`

`[EstheticBonus]` defines how much a guest will enjoy looking at an entity. There's a different value for each type of guest. Every value maps a guest entity type with an esthetic bonus value. Please see [Entity IDs](./entity_ids.md#guests) for guest entity definitions.

### Usage 

Simply tweak the second `v` attribute for each to your preference.

<h3>Example (from `carousal.ai`)</h3>

```INI
[EstheticBonus]
; man
v = 9503
v = 10
; woman
v = 9504
v = 10
; boy
v = 9505
v = 20
; girl
v = 9506
v = 20
```

## `[Satisfies]`

!!! note "Incomplete"
    This section is incomplete. Needs remaining subcategories.

This category assigns the entity to a subcategory type in Zoo Tycoon for various stat checks.

An (incomplete) list of possible values:

- `building`
- `familybathroom`
- `bathroom`
- `fun`

<h3>Example (from `carousal.ai`):</h3>

```INI
[Satisfies]
building
fun
```

## `[UseSound]`

Defines a playable sound for the entity.

| Key                  | Value | Description|
|----------------------|------|-----|
| `alwayson` | `<0/1>` | Is the sound always playing? |
| `loops` | `<0/1>` | Does the sound loop on playback. |
| `name` | `<string dir>` | Directory of sound file to play. |
| `attenuation` | `<int>` | Volume of sound. |

<h3>Example (from `carousal.ai`)</h3>

```INI
[UseSound]
alwayson = 0
loops = 1
name = scenery/building/carousel.wav
attenuation = 1500
```