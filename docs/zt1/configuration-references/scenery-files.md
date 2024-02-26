!!! note "Incomplete"
    This page is incomplete. Pull requests welcome.

# Scenery Documentation

This page assumes the game directory definition of what a 'scenery' item entails. Under the 'scenery' folder under the game's assets, it includes buildings, foliage, rocks, terrain, toys, zoos, and other zoo utilities.

The main configuration for these files are in `.ucb`, `.ucs`, or `.ai` format, but they are really `.INI` files. The following tables describe attributes that can  be given to the entities mentioned. Example files can be found in a respective `/scenery` directory.

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

These characteristics usually require an integer value to be set. They are used to define the entity's behavior and appearance.

### Standard Characteristics

These characteristics are standard across most scenery.

| Key                  | Value | Description|
|----------------------|------|-----|
| `cNameID`            | `<int>` | Integer key associated with a string that gives the entity its name. Value of `19000`means the string is defined inside of the `.ucb` file. If it's a 4-digit number it's a key associated with a string in a `.dll` lang file. |
| `cHelpID` | `<int>` | Same concept as `cNameID`: keys for strings, but this one is for tooltips. If `cNameID` is set to `19000`, ZT ignores `cHelpID`. |
| `cFootprintX` | `<int>` | Size of entity footprint in X direction. Value of `1` can be used for `1/4` or `1/2` tiles, otherwise must be an even integer. |
| `cFootprintY` | `<int>` | Size of entity footprint in Y direction. Value of `1` can be used for `1/4` or `1/2` tiles, otherwise must be an even integer. |
|`cPurchaseCost` | `<int>` | Price of entity |
| `cHeight` | `<int>` | Height of entity. Consistent with construction tool height. |

### Designation Characteristics
| Key                  | Value | Description|
|----------------------|------|-----|
| `cCommerce` | `<int>` | Setting this to `1` designates the entity as a commerce entity, enabling the entity to sell goods. Set to `0` or delete line to exclude this configuration. |
| `cFoliage` | `<int>` | Setting this to `1` designates the entity as foliage. Also allows it to count toward exhibit suitability. Set to `0` or delete line to exclude this configuration. |
| `cShelter` | `<int>` | Setting this to `1` designates the entity as a shelter. Set to `0` or delete line to exclude this configuration. |
| `cRock` | `<int>` | Setting this to `1` designates the entity as a rock. Set to `0` or delete line to exclude this configuration. |
| `cFood` | `<int>` | Setting this to `1` designates the entity as animal food. Set to `0` or delete line to exclude this configuration. |

### Terrain Placement Characteristics
| Key                  | Value | Description|
|----------------------|------|-----|
| `cSwims` | `<int>` | Setting this to `1` allows the object to be placed on water. Set to `0` or delete line to exclude this configuration. |
| `cUnderwater` | `<int>` | Setting this to `1` allows an entity to be placed underwater. Set to `0` or delete line to exclude this configuration. |
| `cHabitat` | `<int>` | What habitat the entity belongs to. `9414` makes entities unplaceable in exhibits. `9411` allows entities placeable in all exhibits. For a full list of possible values, please see [Entity IDs](../string-tables/entity-ids.md#habitat) |
| `cOnlySwims` | `<int>` | Setting this to `1` makes it so the object is only placeable on water and not on land. Set to `0` or delete line to exclude this configuration. |
| `cSurface` | `<int>` | Setting this to `1` allows an entity to be placed on water surface. Set to `0` or delete line to exclude this configuration. |
| `cLand` | `<int>` | |

### Misc String Characteristics

`cNameID` and `cHelpID` are a couple already described under [Standard Characteristics](#standard-characteristics). Here are a few more:

| Key                  | Value | Description|
|----------------------|------|-----|
| `cUsedThought` | `<int>` | A user's thought after using the entity. Works similar in concept to other key/value strings above. |   
| `cLocation` | `<int>` | Assigns a location to the entity. For a list of locations and their respective values, please see [Entity IDs](../string-tables/entity-ids.md#locations) |

### Graphics Characteristics

These characteristics influence the appearance of the entity.

| Key                  | Value | Description|
|----------------------|------|-----|
| `cIsColorReplaced` | `<int>` | Setting this to `1` allows the entity to be color-replaced. Needs to pair with a respective `[colorrep]` section with additional configuration settings in the same file. Set to `0` or delete line to exclude this configuration. |
| `cDeadOnLand` | `<int>` | Setting this to `1` allows a 'dead on land' status. If the entity is placed on land, a 'dead' graphic is displayed. Set to `0` or delete line to exclude this configuration. |
| `cDeadUnderwater` | `<int>` | Setting this to `1` allows a 'dead underwater' status. If the entity is placed underwater, a 'dead' graphic is displayed. Set to `0` or delete line to exclude this configuration. |
| `cUsesRealShadows` | `<int>` | |
| `cHasShadowImages` | `<int>` | |

### User Interaction Characteristics

These characteristics influence how the user interacts with the entity. A user can be a guest or an animal.

| Key                  | Value | Description|
|----------------------|------|-----|
| `cAdultChange` | `<int>` | How happy a guest is after using the entity. Negative values are possible if you want them to hate it. | 
| `cChildChange` | `<int>` | Same as above but specifically child guests. |
| `cHideUser` | `<int>` | Setting this to `1` hides the user while using the entity. Set to `0` or delete line to exclude this configuration. |
| `walkable` | `<int>` | Setting this to `1` allows guests and animals to walk through the object. Set to `0` or delete line to exclude this configuration. |
| `cCapacity` | `<int>` | How many users may use entity at a time. It is recommended to match this value with `capacity` under `[slot]`|
| `cBathroomChange` | `<int>` | Unknown |
| `cAngryBathroomChange` | `<int>` | Unknown |
| `cUsersStayOutside` | `<int>` | Setting this to `1` makes it so the user stays outside of the entity. Set to `0` or delete line to exclude this configuration. |
| `cEnergyChange` | `<int>` | |
| `cUserUsesExit` | `<int>` | |
| `cRandomUse` | `<int>` | Setting this to `1` enables random interaction with entity. Set to `0` or delete line to exclude this configuration. |
| `cMinUsePeriod` | `<int>` | If used, define minimum use period. |
| `cMaxUsePeriod` | `<int>` | If used, define maximum use period. |
| `cToySatisfaction` | `<int>` | |
| `cUserTeleportsInside` | `<int>` | |
| `cTimeInside` | `<int>` | How long should a user be inside of a building. It mmight make sense to match this value with length of sound file if provided. 
| `cHideBuilding` | `<int>` | Setting this to `1` hides the building while in use. Set to `0` or delete line to exclude this configuration. |
| `cUserUsesEntranceAsEmergencyExit` | `<int>` | Setting this to `1` makes it so the user uses the entrance as an emergency exit. Set to `0` or delete line to exclude this configuration. |
| `cUserUsesExit` | `<int>` | Setting this to `1` makes it so the user uses the exit. Set to `0` or delete line to exclude this configuration. |

### I/O Characteristics

These characteristics influence how the player interacts with the entity.

| Key                  | Value | Description|
|----------------------|------|-----|
| `cNeedsConfirm` | `<int>` | Setting this to `1` makes it so the entity needs confirmation window when bulldozed. Set to `0` or delete line to exclude this configuration. |
| `cDeletable` | `<int>` | Setting this to `1` allows the entity to be deleted by the player after placement or spawn. Set to `0` or delete line to exclude this configuration. |
| `cUseNumbersInName` | `<int>` | Setting this to `1` enumerates entity name in the UI. Set to `0` or delete line to exclude this configuration. |
| `cMoveable` | `<int>` | Setting this to `1` allows the entity to be moved by the player. Set to `0` or delete line to exclude this configuration. |
| `cAutoRotate` | `<int>` | Setting this to `1` automatically rotates the object on placement. Set to `0` or delete line to exclude this configuration. |
| `cSelectable` | `<int>` | Setting this to `1` allows the entity to be selected. Set to `0` or delete line to exclude this configuration. |

### Misc Characteristics

| Key                  | Value | Description|
|----------------------|------|-----|
| `walkableByTall` | `<int>` |  |
| `cExplosionSound` | `<string dir>` | Directory to sound file to play on explosion. |
| `cExplosionSoundAtten` | `<int>` | Volume of explosion sound. |
| `cRubbleable` | `<int>` |  |
| `cDepth` | `<int>` | |
| `cHasUnderwaterSection` | `<int>` | |
| `cDeadStateHeight` | `<int>` | |
| `cBlocksLOS` | `<int>` | |
| `cDirectEntrance` | `<int>` | Moves user toward entity more quickly |
| `cShow` | `<int>` | |
| `cUsesTreeRubble` | | |
| `cEstheticWeight` | | |
| `cGawkOnlyFromFront` | | |
| `cExpansionID` | | |
| `cAvoidEdges` | `<int>` | Setting this to `1` prevents entity to be placed next to fences or tank walls. Set to `0` or delete line to exclude this configuration. |
| `cFoodUnits` | `<int>` | How much food the entity provides until it's empty. |
| `cMaxFoodUnits` | `<int>` | Maximum food units the entity can hold. |
| `cFoodCategory` | `<int>` | Category of food the entity provides. |
| `cKeeperFoodType` | `<int>` | |

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

## `[Characteristics/Floats]`

!!! note "Incomplete"
    This section is incomplete. Needs remaining characteristics defined.

These characteristics usually require a float value to be set. Since floats are decimal numbers, these characteristics are usually used to
set prices for things such as upkeep and other costs.

| Key                  | Value | Description|
|----------------------|------|-----|
| `cUpkeep` | `<float>` | How much it costs per month to upkeep entity. |


## `[Animations]`

!!! note "Incomplete"
    This section is incomplete. Needs missing definitions.

| Key                  | Value | Description|
|----------------------|------|-----|
| `idle` | `idle` | Idle defines your entity as having graphics without animation. Can sometimes be a directory to a `.ani` file. |
| `used` | `used` | Used defines your entity as having graphics with animation. |
| `explode` | `<string dir>` | |
| `giant` | | |
| `small` | `small` | Usually a graphic that displays a low quantity of the entity it represents. Typically used in animal food. |
| `mid` | `mid` | Usually a graphic that displays a medium quantity of the entity it represents. Typically used in animal food. |   
| `full` | `full` | Usually a graphic that displays a high quantity of the entity it represents. Typically used in animal food. | 
| `empty` | `empty` | Usually a graphic that displays an empty quantity of the entity it represents. Typically used in animal food. |  
| `idledead` | `dead` | Graphics for when the entity is dead. | 
| `shadowidle` | | |
| `underidle` | | |

<h3>Example 1</h3>
```INI
[Animations]
idle = idle
```

<h3>Example 2</h3>
```INI
[Animations]
idle = idle
used = used
```

<h3>Example 3</h3>
```INI
[Animations]
idle = idle
used = idle
idledead = dead
```

## `[EstheticBonus]`

`[EstheticBonus]` defines how much a guest will enjoy looking at an entity. There's a different value for each type of guest. Every value maps a guest entity type with an esthetic bonus value. Please see [Entity IDs](./entity-ids.md#guests) for guest entity definitions.

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
- `animalrest`
- `animalsex`
- `showtrick`

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

## `[slots]`

This category defines the slots for the entity. Slots are used to define where animals or guests can interact with the entity. Typically this should only be necessary for entities where guests or animals require a specific spot to interact with the entity, such as buildings, shelters, picnic tables, etc.

| Key                  | Value | Description|
|----------------------|------|-----|
| `name` | `<string name>` | Name of the slot. There should be as many of this attribute as there are slots. |

<h3>Example</h3>

From `picnic.ai`.

```INI
[slots]
name=slot0
name=slot1
name=slot2
name=slot3
```

For each slot there should then be a `[slot]` section with the same name. For the purpose of this reference guide, we'll define the attributes for such slots below under the `[slot#]` section.

### `[slot#]`

| Key                  | Value | Description|
|----------------------|------|-----|
| `slotpos` | `<int>` | Position of the slot. This can also be defined as the spot in the entity where the user will begin its 'used' animation. |
| `entrpos` | `<int>` | Position of the entrance. This is the spot outside of the entity where the user paths to. |
| `exitpos` | `<int>` | Position of the exit. This is the spot where the user will appear once they've used the entity. |
| `capacity` | `<int>` | How many users may use entity at a time. It is recommended to match this value with `cCapacity` under `[Characteristics/Integers]`|
| `facing` | `<int>` | Direction the user is facing while using the entity. |

!!! warning 
    If you have issue with a user leaving the entity facing the wrong direction, removing `cUserUsesEntranceAsEmergencyExit = 1` and `cUserUsesExit = 1` from `[Characteristics/Integers]` might fix it.

Example:

```INI
[slot0]
slotpos=-16
slotpos=16

entrpos=-16
entrpos=48

exitpos=-16
exitpos=48

capacity=1
facing=7
```

!!! note "Slots and Coordinates"
    Notice that each `slotpos`, `entrpos`, and `exitpos` attribute has two values. This is because they are world coordinates. The first value is the X coordinate and the second value is the Y coordinate. The X coordinate is the horizontal axis and the Y coordinate is the vertical axis. Both are needed to define a position in the game world. The game will crash if you only define one of the two.

    For a guided tutorial on slots, please read Jay's [Slot Information Guide](http://www.ztcdd.org/DG/index.php?topic=4202.0) at the Zoo Tycoon Community Download Directory.