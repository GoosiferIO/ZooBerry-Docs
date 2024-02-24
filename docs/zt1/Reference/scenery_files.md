!!! note "Incomplete"
    This page is incomplete. Pull requests welcome.

# Scenery Documentation

Scenery includes buildings, foliage, rocks, terrain, toys, zoos, and other zoo utilities.

Usually found inside an entity's `.ucb` or `.ai` file, the following tables describe attributes that can  be given to the entities mentioned. Example files can be found in a respective `/scenery` directory.

## `[Icon]`

`[Icon]` defines the directory for that entity's four icons.

| Key                  | Value | Description|
|----------------------|------|-----|
| `Icon` | `<dir>` | Directory to the icon graphic |

<h3>Example</h3>

```INI
[Icon]
Icon = objects/uforidgs/SE/SE
Icon = objects/uforidgs/SW/SW
Icon = objects/uforidgs/NW/NW
Icon = objects/uforidgs/NE/NE
```

## `[Characteristics/Integers]`

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
| `cHabitat` | `<int>` | What habitat the entity belongs to. Below are possible values. `9414` makes entities unplaceable in exhibits. `9411` allows entities placeable in all exhibits. For a full list of possible values, please see [Entity IDs](./entity_ids.md#terrain)|
| `cHideBuilding` | `<0/1>` | Hide building or show? |
| `cUsersStayOutside` | `<0/1>` | Prevent a user from entering entity? |
| `cTimeInside` | `<int>` | How long should a user be inside of a building. It mmight make sense to match this value with length of sound file if provided. 
| `cUsedThought` | `<int>` | A user's thought after using the entity. Works similar in concept to other key/value strings above. |   
| `cHideUser` | `<0/1>` | Should a user be hidden when using entity? |

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

This section might need another look. This category possibly assigns the entity to a subcategory type in Zoo Tycoon for various stat checks.

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